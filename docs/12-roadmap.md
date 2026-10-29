# Roadmap proposto

## Status e premissas de planejamento

**Proposta técnica — não implementada.** A Sprint 1 é documental e permanece aberta. Sprints 2–6 são sequenciamento proposto, sem datas comprometidas ou responsáveis nominais. Os responsáveis estão **a definir**. A especificação oficial de User Stories está ausente; o briefing não reproduz IDs, prioridades ou critérios. A seleção P0/P1/P2 permanece bloqueada.

O [README](../README.md), o [Kanban](16-kanban-sprint1.md) e a [rastreabilidade](13-matriz-rastreabilidade.md) distinguem produção documental, aceite e implementação. O [relatório da auditoria](../entrega/relatorio-auditoria-final.md) contém a avaliação atual no escopo solicitado, sem avaliar os materiais de apresentação e submissão tratados separadamente.

| Sprint | Entregáveis planejados | Dependências | Evidência de aceite proposta |
|---|---|---|---|
| 1 — Planejamento | Proposta técnica, riscos, contrato preliminar, wireframes, rastreabilidade, README, Kanban e plano Projects. | Briefing, histórias oficiais, revisão do grupo e identificação acadêmica. | Coerência documental, escopo oficial mapeado e adequação ao template. |
| 2 — Dados e baselines | Manifesto de fontes/licenças, protocolo de rotulagem, corpus revisado, Regex e TF-IDF experimentais. | Escopo oficial selecionado, fontes aprovadas, revisores e ambiente. | Dados versionados com controles de leakage e baselines avaliados sob escopo oficial. |
| 3 — Motor profundo | Avaliação DeBERTa/multilíngue, possível LoRA, calibração e comparação. | Dados curados, CPU/GPU e teste congelado. | Relatório reproduzível por origem, sem extrapolar experimentos. |
| 4 — Serviço e integração simulada | API funcional, consumidor automatizado simulado, OCR e RAG sintético. | Contrato estável e políticas de autenticação/falhas aprovadas. | Fluxos demonstráveis ALLOW, REVIEW e BLOCK. |
| 5 — Portal e governança | Portal administrativo, revisão humana, métricas e auditoria. | Registro de eventos, RBAC e retenção aprovada. | Acesso por perfil e trilha de revisão verificáveis. |
| 6 — Validação final | Avaliação integrada, red team controlado e entrega final. | Critérios oficiais rastreados e ambiente estável. | Evidência para cada requisito oficial. |

## Status compartilhado da Sprint 1

| IDs | Trabalho | Estado atual | Evidência ou condição para avanço |
|---|---|---|---|
| S1-01–S1-13 | Proposta, README, Kanban, plano Projects e alinhamento. | Produção documental concluída | Arquivos locais; não implica aceite institucional ou implementação. |
| S1-14 | Atribuir responsáveis e obter aceite do grupo. | Backlog | Sem nomes/aceite; aceite final depende também de S1-23. |
| S1-15 | Adequar ao template da coordenação. | Backlog; comparação parcial disponível | Template consultado; faltam identificação acadêmica, turma e decisão do grupo. |
| S1-16 | Configurar destino Git e verificar privacidade/acesso. | Backlog; não verificado nesta auditoria | Atividade administrativa separada; nenhuma configuração alterada. |
| S1-17–S1-18 | Materiais de apresentação e submissão do planejamento anterior. | Fora do escopo desta auditoria | Preservados no Kanban; não entram no cálculo ou parecer atual. |
| S1-19 | Rever admissibilidade das fontes e gates institucionais. | Backlog | Metadados conflitantes de licença do dataset candidato; aprovações não presumidas. |
| S1-20 | Decidir sobre criação de GitHub Projects. | Backlog; opcional | Plano local; criação remota depende de autorização separada. |
| S1-21 | Obter histórias oficiais. | Bloqueado | Especificação oficial necessária. |
| S1-22 | Inventariar IDs, prioridades, critérios e rastreabilidade. | Bloqueado | Depende de S1-21. |
| S1-23 | Incluir todas as P0 e decidir P1/P2. | Bloqueado | Depende de S1-22 e decisão explícita do grupo. |

Não há tarefa registrada como em andamento ou em revisão. A auditoria técnica não encerra a Sprint. O parecer documental depende da resolução das lacunas oficiais e acadêmicas; os demais gates históricos do Kanban não são avaliados neste double-check.

## Gates de requisitos e MVP

| Gate | Entrada necessária | Resultado esperado | Regra |
|---|---|---|---|
| G1 — Disponibilização | Especificação oficial em docs/requisitos/ ou outra fonte acessível. | Inventário de histórias, IDs e prioridades. | Sem G1, MVP bloqueado. |
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

A distribuição nominal exige informação do grupo. Não atribuir nomes por inferência da autoria Git.

## Dependências futuras de adoção

Verificar licenças, snapshots e origem antes de usar dados. Definir custos de FP/FN, capacidade de REVIEW, volume e latência medida antes de adotar thresholds e SLOs. Obter decisões de arquitetura/segurança sobre identidade, armazenamento e infraestrutura e decisões institucionais sobre privacidade/retenção antes de operação real. Essas aprovações não são resultados desta Sprint.
