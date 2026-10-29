# Matriz de rastreabilidade do briefing

Legenda: **CONCLUÍDO** = requisito de planejamento atendido por evidência documental, sem alegar implementação; **PARCIAL** = parte da evidência documental disponível; **PENDENTE** = atividade não concluída; **BLOQUEADA** = depende de insumo externo. Aprovação ou execução futura não torna, por si só, um plano incompleto.

| Requisito do BRIEFING.md | Evidência documental | Estado | Observação |
|---|---|---|---|
| Entender prompt injection e risco para agentes externos | 01, 02 | CONCLUÍDO | Inclui direta e indireta. |
| Serviço independente consumido por API | 01, 06, 07 | CONCLUÍDO | Sem integração assumida com Intelliway. |
| Decisões ALLOW, REVIEW e BLOCK | 01, 06, 07, 08 | CONCLUÍDO | Política versionável proposta. |
| Usuários: consumidor, analista e product owner | README; 01, 03, 09 | CONCLUÍDO | Perfis e necessidades planejados; o vínculo com histórias oficiais é avaliado separadamente e permanece bloqueado. |
| Inventariar histórias oficiais com ID, título, prioridade e critérios | 03 | BLOQUEADA | `docs/requisitos/` não existe e o briefing não reproduz a especificação. |
| Rastrear cada história entre requisito, solução, critério e Sprint | 03, 12 | BLOQUEADA | Depende do inventário e dos critérios oficiais. |
| Selecionar P0 oficiais obrigatórias e P1/P2 oficiais | 03, 12 | BLOQUEADA | A fonte oficial permanece ausente. O catálogo local tem prioridades propostas, sem equivalência oficial presumida. |
| Elaborar catálogo local de User Stories propostas pelo grupo | 03; matriz abaixo | CONCLUÍDO DOCUMENTALMENTE | 15 propostas, com oito P0, cinco P1 e duas P2, 50 critérios futuros; não significa implementação ou validação da Intelliway. |
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
| Kanban da Sprint 1 | 16 | CONCLUÍDO | Atividades, prioridades de trabalho, dependências e evidências registradas. |
| Aceite do grupo e adequação ao template oficial | README; 12, 16 | PARCIAL | Template consultado e estrutura comparada; faltam identificação acadêmica e aceite do grupo. |
| Repositório privado e acesso da tutoria | README; 12, 16 | PARCIAL | Endereço e visibilidade privada verificados; acesso da tutoria ainda não confirmado. |

## Coerência técnica

- A API recebe conteúdo textual e `source_type`; OCR e consumidor são anteriores a ela.
- O motor é discriminativo em todas as versões propostas; IA Generativa não participa da decisão de produção.
- `risk_score` e `decision` são distintos; `score_type` impede interpretação indevida de heurística como probabilidade.
- Registro, portal, revisão e dataset futuro possuem fronteiras de privacidade, auditoria e versionamento.
- Métricas, experimentos, integrações e infraestrutura não são apresentados como executados. Licenças declaradas por fontes externas não equivalem a aprovação de uso; a divergência da fonte candidata está explícita.

## Lacunas da proposta

1. **BLOQUEADA:** especificação oficial de User Stories, com IDs, prioridades e critérios de aceite. O MVP local e sua rastreabilidade estão propostos; cobertura oficial integral continua não demonstrada.
2. Política organizacional de retenção, base legal, papéis de controlador/operador e decisão de DPO/jurídico.
3. Fontes de dados aprovadas, snapshots, licenças verificadas e disponibilidade de revisores humanos.
4. Requisitos não fornecidos de volume, SLO de latência, tolerância a risco, autenticação e infraestrutura.
5. Identificação acadêmica, responsáveis e aceite do grupo (S1-14–S1-15). O README registra a comparação com o template e a possibilidade de omitir pastas sem uso.

## Estado compartilhado de execução

**Proposta técnica — não implementada.** S1-01–S1-11 e S1-13 possuem evidência de produção documental, sem aceite presumido. Nenhuma tarefa está registrada como em andamento ou em revisão. Histórias, rastreabilidade oficial e seleção do MVP seguem bloqueadas (S1-21–S1-23). Admissibilidade das fontes e gates institucionais permanecem no Backlog (S1-19). Consulte [Kanban](16-kanban-sprint1.md), [roadmap](12-roadmap.md) e [README](../README.md).

## Rastreabilidade das histórias propostas pelo grupo

**User Stories propostas pelo grupo — sujeitas à validação perante a especificação oficial da Intelliway.** Esta matriz é do planejamento local da Fase 3 acadêmica/Sprint 1 do Challenge, não da homologação de requisitos oficiais. O catálogo contém critérios com IDs US-xxx-CAxx no documento 03; todos estão não executados.

| História | Capacidade e componente | Prioridade proposta | Dependências locais | Sprint principal futura | Referências técnicas | Validação oficial |
|---|---|---|---|---|---|---|
| [US-001](03-user-stories.md#us-001) | Análise textual via API | P0 | US-002, US-003, US-004, US-005, US-006 | 4 | [06](06-arquitetura-solucao.md), [07](07-contrato-api.md) | Pendente: especificação ausente |
| [US-002](03-user-stories.md#us-002) | Origem padronizada do conteúdo | P0 | Gates comuns; sem história local prévia | 4 | [07](07-contrato-api.md), [08](08-rpa-ocr-rag.md) | Pendente: especificação ausente |
| [US-003](03-user-stories.md#us-003) | Detecção discriminativa em PT-BR | P0 | US-006, US-012, US-014 | 3 | [02](02-modelo-de-ameacas.md), [04](04-planejamento-dataset.md), [05](05-plano-nlp-modelos.md), [11](11-metricas-avaliacao.md) | Pendente: especificação ausente |
| [US-004](03-user-stories.md#us-004) | Decisão operacional estruturada | P0 | US-003, US-012 | 4 | [06](06-arquitetura-solucao.md), [07](07-contrato-api.md), [11](11-metricas-avaliacao.md) | Pendente: especificação ausente |
| [US-005](03-user-stories.md#us-005) | Registro seguro e auditável da decisão | P0 | US-002, US-004, US-012 | 4 | [06](06-arquitetura-solucao.md), [07](07-contrato-api.md), [10](10-governanca.md), [14](14-politicas-operacionais.md), [15](15-registro-de-decisoes.md) | Pendente: especificação ausente |
| [US-006](03-user-stories.md#us-006) | Inferência sem LLM generativo | P0 | Gates comuns; sem história local prévia | 3 | [01](01-visao-geral.md), [05](05-plano-nlp-modelos.md), [06](06-arquitetura-solucao.md), [15](15-registro-de-decisoes.md) | Pendente: especificação ausente |
| [US-007](03-user-stories.md#us-007) | Ingestão de e-mail e página web | P1 | US-001 | 4 | [06](06-arquitetura-solucao.md), [07](07-contrato-api.md), [08](08-rpa-ocr-rag.md) | Pendente: especificação ausente |
| [US-008](03-user-stories.md#us-008) | Análise de texto extraído por OCR | P1 | US-001 | 4 | [06](06-arquitetura-solucao.md), [07](07-contrato-api.md), [08](08-rpa-ocr-rag.md) | Pendente: especificação ausente |
| [US-009](03-user-stories.md#us-009) | Proteção de documentos recuperados por RAG | P1 | US-001 | 4 | [02](02-modelo-de-ameacas.md), [06](06-arquitetura-solucao.md), [08](08-rpa-ocr-rag.md) | Pendente: especificação ausente |
| [US-010](03-user-stories.md#us-010) | Histórico, detalhe e indicadores administrativos | P1 | US-005, US-012 | 5 | [07](07-contrato-api.md), [09](09-wireframes-portal.md), [10](10-governanca.md), [11](11-metricas-avaliacao.md) | Pendente: especificação ausente |
| [US-011](03-user-stories.md#us-011) | Revisão humana aditiva | P1 | US-010 | 5 | [07](07-contrato-api.md), [09](09-wireframes-portal.md), [10](10-governanca.md), [15](15-registro-de-decisoes.md) | Pendente: especificação ausente |
| [US-012](03-user-stories.md#us-012) | Versionamento mínimo e linhagem dos artefatos | P0 | Gates comuns; sem história local prévia | 2 | [04](04-planejamento-dataset.md), [05](05-plano-nlp-modelos.md), [07](07-contrato-api.md), [10](10-governanca.md), [15](15-registro-de-decisoes.md) | Pendente: especificação ausente |
| [US-013](03-user-stories.md#us-013) | Curadoria de feedback para retreinamento | P2 | US-011, US-012 | 6 | [04](04-planejamento-dataset.md), [10](10-governanca.md), [14](14-politicas-operacionais.md), [15](15-registro-de-decisoes.md) | Pendente: especificação ausente |
| [US-014](03-user-stories.md#us-014) | Comparação reproduzível de baselines e DeBERTa | P0 | US-012 | 3 | [04](04-planejamento-dataset.md), [05](05-plano-nlp-modelos.md), [11](11-metricas-avaliacao.md) | Pendente: especificação ausente |
| [US-015](03-user-stories.md#us-015) | Filtros e análise por origem, risco e versão | P2 | US-010 | 5 | [07](07-contrato-api.md), [09](09-wireframes-portal.md), [11](11-metricas-avaliacao.md) | Pendente: especificação ausente |

A regra de prioridades e a antecipação de US-012/US-014 estão justificadas em [03 — Revisão técnica](03-user-stories.md#revisão-técnica-das-prioridades). Manifestos de versão começam na Sprint 2; avaliação e política evoluem na Sprint 3; API, persistência e integrações na Sprint 4; portal/revisão na Sprint 5; feedback curado na Sprint 6. O núcleo de versionamento não depende da UI de versões e não cria ciclo entre registro e portal.
