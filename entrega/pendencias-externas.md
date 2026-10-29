# Pendências externas — auditoria documental da Sprint 1

## Escopo e estado

Registro de 29/10/2026, vinculado ao [relatório final](relatorio-auditoria-final.md). **Proposta técnica — não implementada. Prontidão documental condicionada.** Materiais de apresentação e arquivo de submissão não são avaliados nem pontuados neste registro. Não foram alteradas configurações Git ou remotas.

IDs E01–E08 são pendências desta auditoria, não User Stories oficiais. Os requisitos R referem-se à matriz auditada; S1 refere-se ao Kanban. Responsáveis nominais permanecem **a definir**; os papéis abaixo indicam quem precisa fornecer informação ou decidir, sem nomeação presumida.

## Pendências documentais prioritárias

| ID | O que falta e por quê | Impacto | Fonte ou responsável funcional | Quando resolver | Evidência de encerramento | Vínculos |
|---|---|---|---|---|---|---|
| E01 | Especificação oficial Intelliway com IDs, títulos, prioridades e critérios. Não está no workspace; o briefing apenas menciona a fonte externa. | **Crítico para prontidão documental:** impede provar cobertura oficial e selecionar MVP. | Grupo obtém documento do canal oficial da turma; tutoria esclarece eventual ausência. Responsável nominal a definir. | Antes de declarar cobertura P0/P1/P2 ou documentação pronta. | Fonte/versionamento acessíveis; inventário fiel; todas as P0 mapeadas; decisão P1/P2 fundamentada; critérios ligados à arquitetura, evidência e Sprint. Atualizar 03/12/13, README e relatório. | R04–R07; S1-21–S1-23 |
| E02 | Esclarecer licença/proveniência de deepset/prompt-injections: card contém apache-2.0 no nível superior e cc-by-4.0 em dataset_info. Não presumir qual prevalece. | **Alta antes de uso dos dados; parcial documental:** fonte não pode ser apresentada como aprovada para ingestão/tradução/redistribuição. | Mantenedor da fonte, curadoria e grupo; jurídico quando aplicável. Responsável nominal a definir. | Antes de coletar, traduzir, redistribuir ou treinar com a fonte. | Registro do snapshot, origem, termos esclarecidos e atribuição; ou decisão fundamentada do grupo por outra fonte com termos verificados. Atualizar 04/README e R08. | R08; S1-19 |
| E03 | Nomes do grupo/integrantes, identificação acadêmica aplicável e alocação das tarefas. Competências existem; não há informação para nomear pessoas. | **Alta documental:** responsabilidades dos integrantes não demonstradas integralmente. | Grupo fornece identificação e distribuição por competência/tarefa. Responsável nominal a definir. | Antes do aceite final do planejamento. | README com identificação confirmada e 12/16 com responsáveis reais ou justificativa explícita validada pelo grupo. Registrar revisão/aceite sem inferir nomes da autoria Git. | R36; S1-14 |
| E04 | Confirmar tutor/turma, enquadramento e informações acadêmicas do template, inclusive decisão aplicável de participação na competição. A estrutura foi comparada, mas esses dados não podem ser inventados. | **Alta documental:** adequação ao template permanece parcial. | Grupo e tutoria da turma. Responsável nominal a definir. | Antes de concluir adequação acadêmica. | Identificação e decisões confirmadas no README; eventuais diferenças estruturais justificadas. Não copiar identidades demonstrativas do template. | R38; S1-15 |

## Dependências futuras e administrativas

Estas dependências não adicionam requisitos ao denominador R01–R40. Sua aprovação não é exigida como se a Sprint 1 já operasse em produção. Manter sua natureza proposta explícita evita afirmações sem evidência.

| ID | Dependência | Impacto e horizonte | Quem precisa decidir | Condição de encerramento |
|---|---|---|---|---|
| E05 | Revisores, inventário do corpus, snapshots, orçamento de compute e ambiente-alvo. | Necessário nas Sprints 2–3; não há métrica ou capacidade de CPU medida. | Grupo, ML e curadoria, responsáveis a definir. | Dataset admissível/versionado, protocolo de revisão e ambiente descritos; experimentos reprodutíveis futuros. |
| E06 | IdP, infraestrutura, armazenamento, capacidade de REVIEW, custos FP/FN, thresholds e SLOs. | Gate para implementação/adoção controlada nas Sprints seguintes. Não converter proposta em aprovação. | Produto, arquitetura, ML e segurança, responsáveis a definir. | Decisões registradas, critérios mensuráveis e evidência de validação; atualizar ADRs e política sem alterar requisito oficial. |
| E07 | Controlador, operador, encarregado, bases legais, prazos, fornecedores e regras operacionais. | **Crítico antes de operação real com dados pessoais**, mas não lacuna criada de aprovação jurídica da Sprint documental. | Organização competente e jurídico/DPO, ainda não identificados. | Aprovação institucional documentada antes de operação; não atribuir papéis ou bases legais à Intelliway por inferência. |
| E08 | Evidência autorizada de privacidade/acesso da tutoria e eventual quadro remoto. | Atividade administrativa fora do percentual documental; GitHub Projects continua opcional. | Titular do repositório e grupo. | Verificação futura com autorização apropriada; nenhuma alteração de conta, permissões, colaboradores ou remote nesta auditoria. |

## O que não está pendente como implementação da Sprint 1

A ausência de API funcional, modelo treinado pela equipe, dataset coletado, benchmark, frontend, banco ou deploy está coerente com o briefing. Não criar código, pastas vazias, números de desempenho, responsáveis fictícios ou um protótipo para elevar o percentual. O template consultado permite omitir diretórios sem uso.

## Sequência de resolução proposta

1. Resolver E01; a quantidade real de histórias poderá alterar o inventário da auditoria.
2. Completar E03/E04 com o grupo e registrar aceite.
3. Esclarecer E02 antes de confirmar admissibilidade da fonte ou iniciar coleta.
4. Planejar E05–E07 nas Sprints correspondentes; tratar E08 separadamente sem mudanças administrativas nesta auditoria.
5. Repetir o double-check e recalcular os percentuais sobre o inventário atualizado, sem transformar bloqueios em atendidos por mera existência de arquivo.

## Critério de prontidão

Não declarar **DOCUMENTAÇÃO PRONTA PARA SUBMISSÃO** enquanto houver lacuna crítica documental ou cobertura oficial desconhecida. No estado atual, E01 bloqueia essa declaração; E02–E04 mantêm itens parciais explicitados no relatório. Esta conclusão trata somente da documentação no recorte auditado, sem avaliar os materiais expressamente excluídos.
