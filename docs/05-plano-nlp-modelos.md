# Plano de NLP e modelos

## Pipeline textual proposto

1. **Preservação controlada:** guardar representação original apenas conforme política de retenção; gerar uma cópia de processamento.
2. **Unicode:** aplicar NFC para reduzir formas canonicamente equivalentes, conforme UAX #15 ([Unicode](https://www.unicode.org/reports/tr15/)). Registrar transformações relevantes para auditoria.
3. **Caixa e acentuação:** manter texto original para modelo profundo e auditoria; criar representação auxiliar em minúsculas e, para regras específicas, variante sem acentos. Não remover acentos globalmente: “pode” e “pôde”, por exemplo, podem carregar contexto.
4. **Caracteres invisíveis/controle:** detectar, contar e normalizar de forma conservadora; sinalizar em metadados, sem apagar evidência.
5. **Texto longo:** segmentar em chunks sobrepostos respeitando frases/parágrafos e preservar `document_id`, ordem e offsets. O score do documento será a agregação versionada dos chunks, com destaque para o chunk de maior risco.

## Baselines em progressão

| Camada | Proposta | Justificativa | Limitação conhecida |
|---|---|---|---|
| 1 | Regex e regras interpretáveis | Rápida, auditável e útil para padrões explícitos e sinais de ofuscação. | Baixa cobertura semântica; pode elevar falsos positivos. |
| 2 | TF-IDF de n-gramas de palavra/caractere + classificador linear | Baseline estatístico leve, comparável e executável em CPU. | Sensível a domínio, contexto e evasões novas. |
| 3 | DeBERTa discriminativo ajustado | Captura contexto e relações entre termos melhor que n-gramas. | Custo maior, janela limitada e risco de transferência inadequada do inglês. |

Os três serão comparados sob o mesmo conjunto de teste congelado, mesmas fontes, mesmas métricas e mesma política de agregação. O baseline não é mero fallback: ele define a linha de base verificável que o modelo profundo deve superar.

## Transformer e modelo profundo

Transformers usam mecanismos de atenção para relacionar tokens na entrada sem recorrer a recorrência; a arquitetura foi apresentada em *Attention Is All You Need* ([Vaswani et al., 2017](https://arxiv.org/abs/1706.03762)). Para a Sprint futura, o candidato inicial é `deepset/deberta-v3-base-injection`, um classificador DeBERTa já ajustado à tarefa, documentado como binário, com metadados de idioma inglês e alemão ([model card](https://huggingface.co/deepset/deberta-v3-base-injection)).

A escolha é um ponto de partida, não uma validação para PT-BR. A estratégia proposta é: medir zero-shot por origem; comparar com alternativas multilíngues; ajustar somente com dados licenciados e revisados em PT-BR; e testar LoRA como adaptação de menor número de parâmetros. LoRA, se adotado, será comparado contra fine-tuning completo apenas com orçamento, reprodutibilidade e desempenho documentados.

## CPU, limites e decisão de adoção

Inferência em CPU é viável como hipótese para classificadores menores, mas latência, memória e throughput precisam ser medidos no ambiente-alvo. A versão base DeBERTa pode exigir quantização ou modelo menor; nenhum resultado de latência é alegado nesta Sprint; o documento 11 contém somente metas preliminares não aprovadas. Entradas além da janela do modelo exigem chunking e agregação, pois truncar silenciosamente pode ocultar o trecho malicioso.

O motor da API continuará discriminativo. IA Generativa poderá apoiar apenas a criação de candidatos sintéticos, sempre revisados e marcados, e o avaliador futuro do portal; ela não classificará requisições de produção.

## Fundamentação e limites do candidato

[DeBERTa](https://arxiv.org/abs/2006.03654) separa representações de conteúdo e posição no mecanismo de atenção; [DeBERTaV3](https://arxiv.org/abs/2111.09543) altera o pré-treino para replaced token detection e compartilhamento de embeddings com gradientes desacoplados. Essas propriedades justificam estudar um encoder contextual, sem provar superioridade neste domínio. A card do candidato não demonstra PT-BR; o benchmark publicado pelo fornecedor não é resultado deste projeto.

[LoRA](https://arxiv.org/abs/2106.09685) mantém pesos base congelados e treina adaptações de baixo posto. Menos parâmetros treináveis não implica automaticamente menor memória de inferência ou menor latência em CPU. Compatibilidade das camadas, orçamento de treino e efeito no teste precisam de experimento.

A [configuração pública do candidato](https://huggingface.co/deepset/deberta-v3-base-injection/raw/main/config.json) mapeia `LEGIT` para 0 e `INJECTION` para 1; a API proposta normaliza para `benign` e `injection`. Não se deriva direta/indireta de um classificador binário. A configuração indica limite posicional de 512; o orçamento útil por chunk deve considerar tokenizer e tokens especiais, sem equiparar tokens a caracteres.

Separar custo de treino/fine-tuning do custo de inferência em CPU. A avaliação futura deve registrar processador, RAM, threads, versões, precisão numérica, tamanho de entrada, aquecimento, repetições, p95 e throughput antes de adotar o candidato. Não há garantia de que LoRA ou quantização resolvam o orçamento de CPU.
