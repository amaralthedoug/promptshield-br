# Métricas, SLOs e plano de avaliação

## Regra de interpretação

Métricas e SLOs abaixo são **metas preliminares**, não medições. Antes de vigorar, exigem teste de carga no hardware-alvo, volume esperado, perfil de payload, custo aceitável e aprovação de produto/segurança. Cada relatório futuro informa versão de modelo, política, dataset, janela, percentil, origem e exclusões.

## Métricas de qualidade do detector

| Métrica | Definição | Uso |
|---|---|---|
| Precision | `TP / (TP + FP)` | Reduzir bloqueio indevido de conteúdo legítimo. |
| Recall | `TP / (TP + FN)` | Impedir ataque de alcançar agente. |
| F1-score | Média harmônica de precision e recall. | Comparar modelos no mesmo conjunto. |
| Taxa de falso positivo | `FP / (FP + TN)` | Medir custo operacional de bloqueio. |
| `REVIEW rate` | `REVIEW / total`. | Planejar carga humana. |
| Matriz de confusão | TP, FP, TN e FN da classificação binária; decisões operacionais avaliadas separadamente. | Diagnosticar erro sem transformar REVIEW em classe de ataque. |
| PR-AUC/ROC-AUC | Área sob curvas. | Comparar score antes de fixar limiar; priorizar PR-AUC em ataques raros. |

Avaliar por `source_type`, ataque/hard negative, tamanho/chunking, confiança de OCR, `model_version`, `policy_version` e versão de dataset. O teste congelado não participa de treinamento, escolha de threshold ou geração de exemplos.

## SLOs e limites propostos

| Dimensão | Meta preliminar | Escopo e observação |
|---|---|---|
| Classificação CPU | p95 ≤ 800 ms por chunk dentro da janela do modelo. | Mede somente motor; validar por modelo/hardware. |
| API sem OCR | p95 ≤ 1,5 s e p99 ≤ 3 s. | Da entrada validada à resposta; exclui extração/OCR. |
| OCR | p95 ≤ 8 s por página padrão. | Imagem/PDF em condições definidas futuramente; baixa confiança não conta como sucesso sem sinalização. |
| Documento extenso | Resposta síncrona até 15 s; além disso, fluxo assíncrono planejado. | Requer contrato de job futuro; não implementado nesta Sprint. |
| Disponibilidade | ≥ 99,5% mensal. | Exclui janela de manutenção aprovada; requer observabilidade e definição de cálculo. |
| Erro de servidor | < 1% de 5xx mensal. | 4xx e 429 reportados separadamente, não ocultados. |
| Payload textual | Até 256 KiB e 100.000 caracteres Unicode por requisição. | Limite preventivo; documentos devem usar chunking, não truncamento. |
| Rate limit padrão | 60 req/min/chave, burst 20. | Configurável por cliente e evidência de carga. |

Os valores não afirmam capacidade real. CPU, memória, concorrência, modelo, idioma, OCR e banco alteram os resultados; qualquer SLO só será aceito após medição repetível em homologação.

## Metodologia de calibração de thresholds

1. Congelar conjunto de validação representativo e separar teste final.
2. Produzir curva de precision-recall, curva de calibração e matriz por múltiplos pares `allow_threshold`/`block_threshold`.
3. Definir custos com stakeholders: falso negativo em ação privilegiada, falso positivo em conteúdo legítimo e custo/capacidade da fila `REVIEW`.
4. Selecionar política por `source_type` apenas se houver justificativa, amostra suficiente e versionamento explícito; evitar regra opaca por cliente individual.
5. Validar política candidata no teste congelado, registrar `policy_version` e monitorar pós-promoção.

O intervalo entre thresholds é uma zona deliberada de incerteza: ele reduz automatismo quando o score não sustenta `ALLOW` ou `BLOCK`. Threshold não é propriedade imutável do modelo e não deve ser escolhido com base em acurácia isolada.

## Confiabilidade e observabilidade propostas

Medir disponibilidade, 5xx, timeout, saturação, fila, `429`, latência por estágio (validação, classificação, OCR, persistência), uso de CPU/memória, falha de dependência e taxa de fallback para `REVIEW`. Alertar em degradação sustentada, regressão por origem, aumento de FP/FN revisados e aumento anormal de revogação/autenticação falha.

Antes de promover versão, comparar com Regex e TF-IDF na mesma divisão, além de DeBERTa/LoRA quando aplicável. A promoção exige não regressão dentro dos limites aprovados e plano de rollback; não existe resultado medido nesta Sprint.

## Separação entre avaliação do motor e da política

Para o detector binário, a classe positiva é `injection`; agregar subtipos conforme documento 04. TP/FN usam exemplos de ataque com rótulo humano adjudicado; FP/TN, exemplos benignos. Precisão/recall/F1 e matriz binária são calculados sobre o mesmo conjunto rotulado, com cutoff de classificação selecionado na validação e registrado; esse cutoff é distinto dos dois thresholds da política. Reportar suporte por classe, origem e família. Quando um denominador for zero ou faltar uma classe para AUC, indicar métrica não calculável, sem inventar valor.

A política tem três saídas. Reportar tabela rótulo humano × decisão, taxa de REVIEW sobre requisições válidas, proporção resolvida automaticamente e erros entre decisões automáticas, sempre com seus denominadores. Não contar REVIEW como acerto nem descartá-lo silenciosamente; divulgar cobertura, carga humana e casos sem rótulo. Precision/recall de produção exigem amostras rotuladas representativas; revisar somente REVIEW cria viés de seleção. Agregados de volume não demonstram qualidade do modelo.

PR-AUC/ROC-AUC usam scores contínuos e rótulos binários adjudicados, não as decisões ALLOW/REVIEW/BLOCK como score ordinal. Hiperparâmetros, normalização, vocabulário TF-IDF, pesos e thresholds não são ajustados no teste congelado. Se a avaliação final falhar, registrar o resultado e voltar à validação; não iterar no mesmo teste como se continuasse independente.
