# Roadmap proposto

## Status e premissas de planejamento

**Proposta técnica — não implementada.** A Sprint 1 é documental e permanece aberta. Sprints 2–6 são sequenciamento proposto, sem datas comprometidas ou responsabilidades nominais atribuídas. Os integrantes do Grupo 2 estão identificados no README; a distribuição das tarefas está **a definir**. A especificação oficial de User Stories está ausente; o briefing não reproduz IDs, prioridades ou critérios. O confronto e a cobertura P0/P1/P2 oficiais permanecem bloqueados. O catálogo local contém 15 histórias propostas, com oito P0, cinco P1 e duas P2, sem aprovação oficial presumida. **Fase 3 é a entrega acadêmica atual; Sprint 1 é a etapa documental do Challenge, não a Sprint 3 do roadmap.**

O [README](../README.md), o [Kanban](16-kanban-sprint1.md) e a [rastreabilidade](13-matriz-rastreabilidade.md) distinguem produção documental, aceite e implementação. As [pendências externas](../entrega/pendencias-externas.md) registram os insumos ainda necessários.

| Sprint | Entregáveis planejados | Dependências | Evidência de aceite proposta |
|---|---|---|---|
| 1 — Planejamento | Proposta técnica, catálogo local US-001–US-015, resumo acadêmico da Fase 3, riscos, contrato preliminar, wireframes, rastreabilidade, README e Kanban. | Briefing, histórias oficiais, revisão do grupo e identificação acadêmica. | Coerência documental, escopo oficial mapeado e adequação ao template. |
| 2 — Dados e baselines | Manifesto de fontes/licenças, protocolo de rotulagem, corpus revisado, Regex e TF-IDF experimentais. | Catálogo local como hipótese de trabalho, confronto oficial antes de aceite do MVP, fontes aprovadas, revisores e ambiente. | Dados versionados com controles de leakage e baselines avaliados sob escopo oficial. |
| 3 — Motor profundo | Avaliação DeBERTa/multilíngue, possível LoRA, calibração e comparação. | Dados curados, CPU/GPU e teste congelado. | Relatório reproduzível por origem, sem extrapolar experimentos. |
| 4 — Serviço e integração simulada | API funcional, consumidor automatizado simulado, OCR e RAG sintético. | Contrato estável e políticas de autenticação/falhas aprovadas. | Fluxos demonstráveis ALLOW, REVIEW e BLOCK. |
| 5 — Portal e governança | Portal administrativo, revisão humana, métricas e auditoria. | Registro de eventos, RBAC e retenção aprovada. | Acesso por perfil e trilha de revisão verificáveis. |
| 6 — Validação final | Avaliação integrada, red team controlado e entrega final. | Critérios oficiais rastreados e ambiente estável. | Evidência para cada requisito oficial. |

## Status compartilhado da Sprint 1

| IDs | Trabalho | Estado atual | Evidência ou condição para avanço |
|---|---|---|---|
| S1-01–S1-11 e S1-13 | Proposta, README, Kanban e alinhamento. | Produção documental concluída | Arquivos locais; não implica aceite institucional ou implementação. |
| S1-14 | Atribuir responsáveis e obter aceite do grupo. | Backlog | Integrantes identificados; faltam distribuição de tarefas e aceite, que depende também de S1-23. |
| S1-15 | Adequar ao template da coordenação. | Backlog; comparação parcial disponível | Template consultado; grupo, integrantes e RMs confirmados; faltam tutor/turma e decisões acadêmicas aplicáveis. |
| S1-16 | Alinhar visibilidade do repositório com a orientação acadêmica. | Backlog | Repositório público por decisão do responsável; briefing orienta privado. Acesso de leitura já disponível. |
| S1-19 | Rever admissibilidade das fontes e gates institucionais. | Backlog | Metadados conflitantes de licença do dataset candidato; aprovações não presumidas. |
| S1-21 | Obter histórias oficiais. | Bloqueado | Especificação oficial necessária. |
| S1-22 | Inventariar IDs, prioridades, critérios e rastreabilidade. | Bloqueado | Depende de S1-21. |
| S1-23 | Incluir todas as P0 e decidir P1/P2. | Bloqueado | Depende de S1-22 e decisão explícita do grupo. |

Não há tarefa registrada como em andamento ou em revisão. A Sprint permanece aberta até resolver as lacunas oficiais e acadêmicas e registrar o aceite do grupo.

## Gates de requisitos e MVP

| Gate | Entrada necessária | Resultado esperado | Regra |
|---|---|---|---|
| G1 — Disponibilização | Especificação oficial em docs/requisitos/ ou outra fonte acessível. | Inventário de histórias, IDs e prioridades. | Sem G1, validação oficial do MVP bloqueada; planejamento local pode avançar como proposta. |
| G2 — Rastreabilidade | Critérios oficiais de aceitação. | Requisito → solução → evidência → Sprint. | Rastrear cada história oficial disponível. |
| G3 — Escopo obrigatório | Prioridades oficiais P0/P1/P2. | Escopo obrigatório do MVP. | Incluir todas as P0. |
| G4 — Escopo opcional | Valor, esforço, dependências e viabilidade. | Proposta de P1/P2 e decisão registrada. | Proposta não equivale a seleção aprovada. |

## Responsabilidades por competência

| Competência | Responsabilidade planejada | Responsável nominal |
|---|---|---|
| Arquitetura de IA | Contrato, componentes, política e integração. | A definir |
| ML/NLP | Dataset, baselines, modelo profundo e avaliação. | A definir |
| Segurança de IA | Ameaças, red team controlado e falha segura. | A definir |
| Requisitos | Histórias oficiais, rastreabilidade e aceite. | A definir |
| UX | Fluxos de portal e revisão humana. | A definir |
| Governança | Privacidade, licenças, retenção, auditoria e versões. | A definir |
| Organização acadêmica | Identificação do grupo e adequação ao template. | A definir |

Os nomes e RMs do Grupo 2 estão confirmados no README. A distribuição de responsabilidades exige decisão do grupo; não atribuir papéis por inferência da autoria Git.

## Dependências futuras de adoção

Verificar licenças, snapshots e origem antes de usar dados. Definir custos de FP/FN, capacidade de REVIEW, volume e latência medida antes de adotar thresholds e SLOs. Obter decisões de arquitetura/segurança sobre identidade, armazenamento e infraestrutura e decisões institucionais sobre privacidade/retenção antes de operação real. Essas aprovações não são resultados desta Sprint.

## Alocação das histórias propostas por Sprint

Prioridades são locais e não substituem o gate oficial. As Sprints indicam execução futura, não trabalho já implementado nesta entrega.

| Sprint | Histórias e marcos propostos | Dependência ou critério de passagem |
|---|---|---|
| 1 — Documentação atual | Elaborar US-001–US-015, critérios futuros e matriz; produzir resumo Fase 3 em Markdown/PDF. | Não executar critérios de software. Identificação acadêmica depende de confirmação. |
| 2 — Dados e baselines | Iniciar US-012 (P0): manifestos/linhagem e versões; preparar dados e baselines para US-014. | Licenças e curadoria, splits por famílias e teste congelado; histórico de versões independente do portal. |
| 3 — Motor e decisão | US-006 (P0), US-014 (P0), US-003 (P0); evoluir US-012 com experimentos e política. | US-014 depende do manifesto inicial de US-012. Escolha do motor exige avaliação PT-BR, CPU e custos de erro previamente definidos. Não é obrigatório promover DeBERTa. |
| 4 — API e integração simulada | US-002, US-004, US-005 e US-001 (P0); US-007–US-009 (P1); expor versões de US-012. | Contrato, motor e persistência estabilizados; mesma Sprint permite integração sequencial, sem portal como pré-requisito do registro. |
| 5 — Operação administrativa | US-010–US-011 (P1); US-015 (P2), conforme capacidade do grupo. | Eventos e RBAC disponíveis; filtros avançados dependem do histórico básico e não bloqueiam o núcleo. |
| 6 — Evolução e validação | US-013 (P2), avaliação integrada e regressão controlada. | Feedback adjudicado e curado, admissibilidade e versão do dataset; nenhum retreinamento automático. |

US-012 é incremental: a conclusão do manifesto habilita experimentos sem exigir que API/portal já existam. US-014 é gate da seleção do motor; CPU e dados indisponíveis mantêm o experimento pendente. Aceite de P0/P1/P2 oficiais depende sempre do confronto com a fonte da Intelliway, independentemente do progresso das propostas locais.
