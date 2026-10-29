# Plano de configuração do GitHub Projects

## Finalidade e limite de autorização

**Status: somente plano local.** Quadro proposto: `PromptShield BR — Sprint 1`, para organizar a documentação e as atividades do [Kanban](16-kanban-sprint1.md). A solução permanece proposta técnica, não implementada. Nenhum Project, issue, label, convite ou configuração remota é criado por este documento; isso exige autorização explícita separada.

## Estrutura e colunas

Usar uma visualização Board agrupada por Status e uma Table para evidências e dependências. IDs S1 permanecem estáveis; números de issues serão identificadores separados.

| Coluna | Entrada | Saída |
|---|---|---|
| Backlog | Tarefa identificada, sem início real registrado. | Responsável atribuído e início registrado. |
| Em andamento | Trabalho iniciado e responsável identificado. | Entregável e revisor identificados. |
| Em revisão | Entregável encaminhado ao revisor. | Aceite evidenciado ou ajustes solicitados. |
| Concluído | Critérios da tarefa atendidos com evidência. | Reabrir se evidência perder validade. |
| Bloqueado | Insumo ausente impede avanço. | Insumo recebido e desbloqueio registrado. |

Campos propostos: ID da tarefa (texto), Status (seleção), Prioridade (Alta/Média/Baixa), Sprint, Responsável (Assignees), Evidência (texto/link), Dependência (texto/link) e critérios no corpo da issue. Manter **a definir** enquanto não houver responsável real. Não inventar integrantes ou datas.

Prioridade de trabalho é diferente da prioridade oficial de história. Criar campo de prioridade oficial somente após receber a especificação, sem inferir P0/P1/P2. Artefatos documentais existentes podem ser importados como concluídos com evidência; não inventar transições históricas.

## Labels propostas

| Label | Uso |
|---|---|
| `type:documentation` | Artefato da proposta técnica. |
| `type:academic-delivery` | Organização acadêmica prevista no Kanban. |
| `type:requirements` | Histórias oficiais e rastreabilidade. |
| `area:architecture` | Componentes, API, OCR e consumidor. |
| `area:data-ml` | Dataset, rotulagem, modelos e avaliação. |
| `area:governance` | Privacidade, licenças, aprovações e segurança. |
| `priority:high`, `priority:medium`, `priority:low` | Ordenação local de trabalho; nunca P0/P1/P2 inferido. |
| `blocked:external-input` | Insumo oficial ou institucional ausente. |
| `scope:sprint-1` | Planejamento documental e organização da Sprint. |
| `optional` | Decisão de criar quadro remoto, não exigência mínima. |

Status pertence ao campo Status, sem labels duplicadas que possam divergir.

## Issues sugeridas

Após autorização, usar uma issue por tarefa S1, copiando descrição, prioridade, evidência, responsável, dependência e status do [Kanban](16-kanban-sprint1.md). Ele é o inventário das tarefas, enquanto o relatório de auditoria conta requisitos documentais do briefing.

| IDs | Assunto | Estado de importação |
|---|---|---|
| S1-01–S1-09 | Artefatos individuais: ameaças, dados, NLP, arquitetura, contrato, wireframes, governança, métricas e roadmap. | Concluído somente para produção documental, com evidência. |
| S1-10–S1-13 | README, Kanban, plano Projects e alinhamento. | Concluído somente para produção documental. |
| S1-14 | Atribuir responsáveis e obter aceite do grupo. | Backlog |
| S1-15 | Completar adequação ao template e identificação acadêmica. | Backlog; comparação parcial registrada |
| S1-16 | Verificar destino Git, privacidade e acesso da tutoria. | Backlog; atividade administrativa separada |
| S1-17–S1-18 | Atividades históricas de apresentação e submissão. | Preservar estado do Kanban; fora da auditoria atual |
| S1-19 | Rever admissibilidade das fontes e gates institucionais. | Backlog |
| S1-20 | Decidir sobre criação do quadro opcional. | Backlog; opcional |
| S1-21 | Obter histórias oficiais. | Bloqueado |
| S1-22 | Inventariar histórias e rastreabilidade. | Bloqueado por S1-21 |
| S1-23 | Incluir todas as P0 e decidir P1/P2. | Bloqueado por S1-22 |

São sugestões, não números reais de issues. Não criar histórias oficiais por inferência. Planejar issues de implementação após o gate de requisitos, sem conclusão prematura.

## Critérios de encerramento

| Tipo de trabalho | Evidência necessária |
|---|---|
| Produção documental | Arquivo, seções solicitadas, links válidos e status explícito. |
| Revisão do grupo | Revisor, achados, ajustes e aceite datado. |
| Histórias oficiais | Fonte acessível, IDs/prioridades/critérios fiéis, todas as P0 e decisão P1/P2. |
| Template | Comparação registrada e destinação das diferenças. |
| Acesso do repositório | Evidência autorizada de destino, visibilidade e acesso; convite não equivale a aceite. |
| Planejamento de dados/governança | Revisão de admissibilidade e gates institucionais explícitos, sem aprovação presumida. |

As demais atividades históricas seguem os critérios do briefing e não são avaliadas neste double-check. Encerrar uma issue sobre API proposta não comprova funcionamento dessa API. O quadro não substitui as evidências acadêmicas.

## Modelo de issue

```markdown
## Tarefa
- ID: S1-XX
- Descrição: <entregável concreto>
- Sprint: 1 — Planejamento documental
- Prioridade: <Alta / Média / Baixa; não é prioridade oficial de história>
- Responsável: A definir
- Status: <Backlog / Em andamento / Em revisão / Concluído / Bloqueado>

## Contexto
<O que é necessário, por que importa e qual requisito do briefing sustenta.>

## Escopo
<Documento ou atividade; preservar limite documental da Sprint.>

## Dependências
- <IDs, insumo oficial ou autorização necessária.>

## Critérios de aceitação
- [ ] <Critério observável do entregável.>
- [ ] Evidência vinculada e afirmações verificadas.
- [ ] README, Kanban, roadmap e rastreabilidade alinhados quando afetados.

## Evidência
<Caminhos do repositório ou referências verificáveis.>

## Bloqueio e condição de desbloqueio
<Insumo ausente e condição para retomada; usar Nenhum quando aplicável.>

## Revisão
- Revisor: A definir
- Decisão/data: Pendente
```

## Passos manuais para montagem futura

Checklist proposto, sem afirmar inspeção da interface atual do GitHub. Nomes de controles e campos podem variar conforme conta e permissões.

1. Obter autorização explícita para criar recursos remotos e confirmar conta e destino.
2. Verificar privacidade do repositório e acesso conforme o briefing; conferir separadamente a visibilidade do Project.
3. Criar Board privado `PromptShield BR — Sprint 1` na conta ou organização confirmada.
4. Configurar Status e campos propostos; adicionar visualização Table.
5. Criar as labels autorizadas, sem atribuir prioridades oficiais ausentes.
6. Criar issues autorizadas com IDs S1 e adicioná-las ao Project, preservando evidências e responsáveis desconhecidos.
7. Importar artefatos documentais concluídos com seus links e incluir issues fechadas na visualização, quando necessário.
8. Registrar dependências e manter S1-21–S1-23 bloqueadas até os insumos chegarem.
9. Revisar automações antes de ativá-las; fechamento só implica conclusão após verificar critérios, sem expor conteúdo privado.
10. Conferir quadro contra o Kanban e registrar URL real no README somente após criação/verificação.
11. Atualizar issue/Project e Kanban conjuntamente; refletir mudanças pertinentes no README, roadmap e rastreabilidade.

Nenhuma alteração de conta, Git, permissões, colaboradores ou remote foi executada nesta auditoria.
