# Matriz de rastreabilidade do briefing

Legenda: **CONCLUÍDO** = requisito de planejamento atendido por evidência documental, sem alegar implementação; **PARCIAL** = parte da evidência documental disponível; **PENDENTE** = atividade não concluída; **BLOQUEADA** = depende de insumo externo. Aprovação ou execução futura não torna, por si só, um plano incompleto. A contagem do double-check atual está exclusivamente na matriz R01–R40 do [relatório](../entrega/relatorio-auditoria-final.md); esta tabela agrupa itens e não constitui seu denominador.

| Requisito do BRIEFING.md | Evidência documental | Estado | Observação |
|---|---|---|---|
| Entender prompt injection e risco para agentes externos | 01, 02 | CONCLUÍDO | Inclui direta e indireta. |
| Serviço independente consumido por API | 01, 06, 07 | CONCLUÍDO | Sem integração assumida com Intelliway. |
| Decisões ALLOW, REVIEW e BLOCK | 01, 06, 07, 08 | CONCLUÍDO | Política versionável proposta. |
| Usuários: consumidor, analista e product owner | README; 01, 03, 09 | CONCLUÍDO | Perfis e necessidades planejados; o vínculo com histórias oficiais é avaliado separadamente e permanece bloqueado. |
| Inventariar histórias oficiais com ID, título, prioridade e critérios | 03 | BLOQUEADA | `docs/requisitos/` não existe e o briefing não reproduz a especificação. |
| Rastrear cada história entre requisito, solução, critério e Sprint | 03, 12 | BLOQUEADA | Depende do inventário e dos critérios oficiais. |
| Selecionar P0 obrigatórias e propor P1/P2 | 03, 12 | BLOQUEADA | Prioridades oficiais não foram fornecidas; não haverá inferência. |
| Dataset PT-BR com fontes, traduções e sintéticos revisados | 04 | PARCIAL | Estratégia documentada; a card da fonte candidata contém licenças divergentes, exigindo esclarecimento da proveniência. |
| Ataques, hard negatives, metadados e separação sem leakage | 04 | CONCLUÍDO | Estratégia por família e antes de tradução. |
| Baselines Regex e TF-IDF/classificador | 05 | CONCLUÍDO | Propostos, não implementados. |
| DeBERTa, Transformer, LoRA e CPU | 05 | CONCLUÍDO | Adoção condicionada a avaliação em PT-BR. |
| Proibição de LLM generativo na classificação da API | 01, 05, 06 | CONCLUÍDO | Uso limitado a dados e avaliador futuro. |
| Fluxos texto, e-mail, página, documento e RAG | 06, 08 | CONCLUÍDO | Inclui origem padronizada. |
| Imagem/PDF, pré-processamento, OCR e exemplos | 08 | CONCLUÍDO | Tesseract/OpenCV planejados. |
| Consumidor automatizado/RPA | 06, 08 | CONCLUÍDO | Fluxo e responsabilidades documentados. |
| Cenário RAG simulado | 08 | CONCLUÍDO | Base inteiramente sintética planejada. |
| Diagrama componentes e fluxo OCR/consumidor | 06, 08 | CONCLUÍDO | Mermaid incluído. |
| Contrato API, score, decisão e origem | 07 | CONCLUÍDO | Distingue score heurístico e probabilidade calibrada. |
| Health e endpoints administrativos planejados | 07 | CONCLUÍDO | Documentais nesta Sprint. |
| Wireframes login, dashboard, histórico, detalhe e revisão | 09 | CONCLUÍDO | Wireframes estáticos. |
| Navegação e consumo de dados do portal | 06, 09 | CONCLUÍDO | Registro alimenta portal futuro. |
| LGPD, privacidade, licença, uso indevido e retenção | 10 | CONCLUÍDO | Requer avaliação jurídica/organizacional futura. |
| Indicadores: precision, recall, F1 e REVIEW | 09, 11 | CONCLUÍDO | Não há valores medidos. |
| Matriz de confusão, falsos positivos e latência | 11 | CONCLUÍDO | Protocolo de medição definido. |
| Registro por versão de modelo | 06, 07, 10, 11 | CONCLUÍDO | Inclui política e normalização. |
| Planejamento das próximas Sprints e responsabilidades | 12, 16 | PARCIAL | Etapas e dependências documentadas; alocação nominal ainda a definir pelo grupo. |
| IoT/MQTT opcional | — | PENDENTE | Opcional e fora do escopo desta proposta. |
| README organizado | README; 16 | CONCLUÍDO | Contexto, perfis, exemplos JSON, dados, arquitetura e índice presentes; histórias oficiais mantidas como bloqueadas. |
| Materiais de apresentação e arquivo de submissão | 16 | FORA DO ESCOPO | Sem avaliação ou pontuação neste double-check; planejamento anterior preservado. |
| Kanban da Sprint 1 e plano GitHub Projects | 16, 17 | CONCLUÍDO | Documentos locais existentes (S1-11–S1-12); nenhum recurso remoto criado. |
| Aceite do grupo e adequação ao template oficial | README; 12, 16; relatório | PARCIAL | Template consultado e estrutura comparada; faltam identificação acadêmica e aceite do grupo. |
| Repositório privado e acesso da tutoria | 12, 16 | NÃO VERIFICADO | Atividade administrativa preservada; nenhuma configuração ou permissão alterada. Não entra no percentual documental. |

## Auditoria de coerência

- A API recebe conteúdo textual e `source_type`; OCR e consumidor são anteriores a ela.
- O motor é discriminativo em todas as versões propostas; IA Generativa não participa da decisão de produção.
- `risk_score` e `decision` são distintos; `score_type` impede interpretação indevida de heurística como probabilidade.
- Registro, portal, revisão e dataset futuro possuem fronteiras de privacidade, auditoria e versionamento.
- Métricas, experimentos, integrações e infraestrutura não são apresentados como executados. Licenças declaradas por fontes externas não equivalem a aprovação de uso; a divergência da fonte candidata está explícita.

## Lacunas da proposta

1. **BLOQUEADA:** especificação oficial de User Stories, com IDs, prioridades e critérios de aceite. Sem ela, não há seleção de MVP nem rastreabilidade integral.
2. Política organizacional de retenção, base legal, papéis de controlador/operador e decisão de DPO/jurídico.
3. Fontes de dados aprovadas, snapshots, licenças verificadas e disponibilidade de revisores humanos.
4. Requisitos não fornecidos de volume, SLO de latência, tolerância a risco, autenticação e infraestrutura.
5. Identificação acadêmica, responsáveis e aceite do grupo (S1-14–S1-15). A comparação do template está registrada no relatório; a dispensa de pastas sem uso foi confirmada. Criação de quadro remoto continua opcional e não executada (S1-20).

## Estado compartilhado de execução

**Proposta técnica — não implementada.** S1-01–S1-13 possuem evidência de produção documental, sem aceite presumido. Nenhuma tarefa está registrada como em andamento ou em revisão. Histórias, rastreabilidade oficial e seleção do MVP seguem bloqueadas (S1-21–S1-23). Admissibilidade das fontes e gates institucionais permanecem no Backlog (S1-19). Tarefas históricas S1-17–S1-18 estão preservadas no Kanban, sem avaliação no recorte atual. Consulte [Kanban](16-kanban-sprint1.md), [roadmap](12-roadmap.md) e [README](../README.md).
