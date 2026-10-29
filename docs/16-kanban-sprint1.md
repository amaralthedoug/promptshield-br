# Kanban da Sprint 1

## Escopo e interpretação

Snapshot: 29/10/2026. **Proposta técnica — não implementada.** Este quadro acompanha documentação e organização acadêmica, não execução de software. Prioridades Alta/Média/Baixa indicam ordenação de trabalho e não substituem P0/P1/P2 oficiais. Todos os responsáveis estão **a definir**.

Concluído significa produção do artefato documental indicado. Não implica aceite do grupo, tecnologia validada, conformidade operacional, experimento concluído ou cobertura de histórias oficiais. A Sprint 1 permanece aberta. Tarefas históricas S1-17–S1-18 foram preservadas com o status anterior e não são reavaliadas no double-check atual.

## Backlog

| ID | Descrição | Prioridade | Evidência | Responsável | Status | Dependência |
|---|---|---|---|---|---|---|
| S1-14 | Atribuir responsáveis e obter revisão/aceite do grupo | Alta | Sem responsáveis nominais ou aceite registrado | A definir | Backlog | Minutas disponíveis; aceite final depende também de S1-23 |
| S1-15 | Verificar e completar adequação ao template oficial | Alta | [Comparação na auditoria](../entrega/relatorio-auditoria-final.md); identificação acadêmica ainda pendente | A definir | Backlog | Grupo confirma turma, identificação e decisões acadêmicas |
| S1-16 | Configurar destino Git e verificar privacidade/acesso da tutoria | Alta | Atividade administrativa preservada; não verificada nesta auditoria | A definir | Backlog | Conta, destino e autorização de administração |
| S1-17 | Gravar/publicar vídeo da Sprint 1 e registrar URL no README | Alta | Registro histórico do planejamento; não reavaliado neste double-check | A definir | Backlog | S1-14, S1-15, S1-23; critérios do briefing |
| S1-18 | Criar e conferir arquivo .txt de submissão | Alta | Registro histórico do planejamento; não reavaliado neste double-check | A definir | Backlog | S1-16, S1-17; critérios do briefing |
| S1-19 | Rever admissibilidade das fontes e gates institucionais | Média | [Dataset](04-planejamento-dataset.md): metadados de licença divergentes; [decisões](15-registro-de-decisoes.md) pendentes | A definir | Backlog | Curadoria, esclarecimento da origem/licença e decisões institucionais quando aplicáveis |
| S1-20 | Decidir sobre criação do quadro GitHub Projects | Baixa | [Somente plano local](17-plano-github-projects.md) | A definir | Backlog | Autorização explícita separada para criação remota |

## Em andamento

Nenhuma tarefa registrada neste snapshot. Não há evidência de atividade atribuída em execução.

## Em revisão

Nenhuma tarefa registrada neste snapshot. S1-14 prevê revisão do grupo; não há evidência de encaminhamento ou aceite.

## Concluído

| ID | Descrição | Prioridade | Evidência | Responsável | Status | Dependência |
|---|---|---|---|---|---|---|
| S1-01 | Documentar problema, perfis e modelo de ameaças | Alta | [Visão geral](01-visao-geral.md), [ameaças](02-modelo-de-ameacas.md) | A definir | Concluído | Briefing |
| S1-02 | Documentar estratégia PT-BR de dataset e rotulagem | Alta | [Dataset](04-planejamento-dataset.md) | A definir | Concluído | Briefing |
| S1-03 | Documentar pré-processamento, baselines e avaliação profunda | Alta | [NLP](05-plano-nlp-modelos.md) | A definir | Concluído | S1-02, artefato de planejamento |
| S1-04 | Documentar arquitetura, OCR, consumidor e RAG | Alta | [Arquitetura](06-arquitetura-solucao.md), [ingestão](08-rpa-ocr-rag.md) | A definir | Concluído | S1-01, S1-03, artefatos de planejamento |
| S1-05 | Documentar contrato textual da API e semântica de decisão | Alta | [Contrato](07-contrato-api.md) | A definir | Concluído | S1-04 |
| S1-06 | Produzir wireframes estáticos e navegação do portal | Média | [Wireframes](09-wireframes-portal.md) | A definir | Concluído | S1-04, S1-05 |
| S1-07 | Documentar governança, políticas e ADRs propostos | Alta | [Governança](10-governanca.md), [políticas](14-politicas-operacionais.md), [decisões](15-registro-de-decisoes.md) | A definir | Concluído | S1-01, S1-04; aprovação institucional continua futura |
| S1-08 | Documentar métricas e SLOs preliminares | Alta | [Avaliação](11-metricas-avaliacao.md) | A definir | Concluído | S1-02, S1-03 |
| S1-09 | Documentar roadmap e explicitar lacunas de rastreabilidade | Alta | [Roadmap](12-roadmap.md), [matriz](13-matriz-rastreabilidade.md), [histórias](03-user-stories.md) | A definir | Concluído | Briefing; mapeamento oficial bloqueado |
| S1-10 | Criar README indexado com status da proposta | Alta | [README](../README.md) | A definir | Concluído | S1-01–S1-09 |
| S1-11 | Criar Kanban baseado em evidências | Alta | [Este Kanban](16-kanban-sprint1.md) | A definir | Concluído | S1-01–S1-10 |
| S1-12 | Documentar estrutura e montagem do GitHub Projects | Média | [Plano Projects](17-plano-github-projects.md) | A definir | Concluído | S1-11 |
| S1-13 | Alinhar README, Kanban, roadmap e rastreabilidade | Alta | [README](../README.md), [roadmap](12-roadmap.md), [matriz](13-matriz-rastreabilidade.md), [auditoria](../entrega/relatorio-auditoria-final.md) | A definir | Concluído | S1-10–S1-12 |

## Bloqueado

| ID | Descrição | Prioridade | Evidência | Responsável | Status | Dependência |
|---|---|---|---|---|---|---|
| S1-21 | Obter especificação oficial de User Stories | Alta | [Auditoria de histórias](03-user-stories.md): fonte ausente | A definir | Bloqueado | Fonte oficial da turma ou do grupo |
| S1-22 | Inventariar IDs, prioridades, critérios e completar rastreabilidade | Alta | [Matriz de histórias](03-user-stories.md) contém somente pendência bloqueada | A definir | Bloqueado | S1-21 |
| S1-23 | Selecionar todas as P0 e obter decisão sobre P1/P2 | Alta | [Gates do MVP](12-roadmap.md): não há prioridades oficiais disponíveis | A definir | Bloqueado | S1-22 e decisão explícita do grupo |

## Transições e encerramento

- Backlog → Em andamento: atribuir responsável e registrar início real.
- Em andamento → Em revisão: vincular entregável e identificar revisor.
- Em revisão → Concluído: registrar aceite e evidência dos critérios da tarefa.
- Qualquer status → Bloqueado: registrar insumo ausente, impacto e condição para desbloqueio.
- Concluído → Em revisão: reabrir se mudança de requisito ou inconsistência invalidar a evidência.

As tarefas concluídas foram avaliadas pela produção local dos documentos; transições históricas não conhecidas não devem ser inventadas. S1-13 trata do alinhamento documental; S1-14, do aceite do grupo.

O gate histórico completo da Sprint inclui S1-14–S1-18 e S1-21–S1-23, além de destinação registrada para S1-19. Este gate é preservado como planejamento, sem avaliar os materiais excluídos da auditoria atual. S1-20 é opcional: quadro remoto não é pré-requisito do Kanban Markdown. Aprovações de produção e implementação pertencem a gates futuros.

O [relatório](../entrega/relatorio-auditoria-final.md) define a contagem documental atual e seu recorte; não equivale ao encerramento de toda a entrega acadêmica. Consulte [README](../README.md), [roadmap](12-roadmap.md) e [plano Projects](17-plano-github-projects.md). Nenhuma issue ou Project remoto foi criado.
