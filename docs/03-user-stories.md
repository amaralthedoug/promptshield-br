# User Stories e matriz de rastreabilidade

## Situação da especificação oficial

O `BRIEFING.md` informa que a especificação de User Stories da Intelliway foi apresentada no kick-off e disponibilizada no canal Geral da turma. Na auditoria documental desta Sprint, não foi encontrado o diretório `docs/requisitos/`, nem qualquer arquivo alternativo que contenha as histórias oficiais. Logo, IDs, títulos, prioridades e critérios de aceitação não estão disponíveis no workspace.

| Fonte esperada | Resultado da verificação | Impacto | Estado |
|---|---|---|---|
| `docs/requisitos/` | Diretório inexistente. | Não há especificação oficial local para extrair histórias. | **BLOQUEADA** |
| `BRIEFING.md` | Confirma a existência de histórias externas, mas não as reproduz. | Não permite transcrição de ID, prioridade ou critério oficial. | **BLOQUEADA** |

Não serão inventadas User Stories, IDs, critérios ou classificações P0/P1/P2. As capacidades descritas nos documentos 01–13 são propostas técnicas e **não constituem histórias oficiais**.

## Matriz de rastreabilidade das histórias oficiais

Esta é a estrutura que receberá uma linha para cada história oficial assim que a fonte for disponibilizada. Atualmente não há linhas de história porque nenhuma está disponível.

| ID e título original | Prioridade oficial | Descrição funcional | Ator | Valor de negócio | Critérios de aceitação verificáveis | Dependências técnicas | Sprint planejada | Evidência documental | Status de planejamento | Justificativa para o MVP |
|---|---|---|---|---|---|---|---|---|---|---|
| **BLOQUEADA — especificação oficial ausente** | Não classificável | Não disponível. | Não disponível. | Não avaliável. | Não disponível. | Recebimento da fonte oficial. | Não definível. | Seções 01–13 descrevem capacidades, mas não substituem requisitos oficiais. | **BLOQUEADA** | Não é possível incluir ou excluir requisito do MVP sem prioridade oficial. |

## Regra de seleção do escopo

| Prioridade | Regra aplicável após receber a especificação | Estado atual |
|---|---|---|
| P0 | Todas as histórias P0 integrarão obrigatoriamente o MVP. | BLOQUEADA: prioridades não fornecidas. |
| P1 | Serão propostas ao grupo após análise explícita de valor, esforço, dependências e viabilidade. | BLOQUEADA: histórias não fornecidas. |
| P2 | Serão propostas ao grupo após análise explícita de valor, esforço, dependências e viabilidade. | BLOQUEADA: histórias não fornecidas. |

Proposta não significa decisão aprovada. A seleção de P1/P2 somente será registrada após haver texto, prioridade e critérios oficiais para análise.

## Procedimento para desbloqueio e aceite

1. Adicionar a especificação oficial em `docs/requisitos/` ou referenciá-la em local acessível ao grupo.
2. Transcrever literalmente ID, título, prioridade, ator e critérios de aceitação de cada história.
3. Mapear cada critério para a solução proposta, evidência documental e Sprint planejada.
4. Incluir todas as P0 no MVP; avaliar P1/P2 sem alterar suas prioridades oficiais.
5. Considerar este documento desbloqueado somente quando toda história oficial disponível tiver rastreabilidade entre requisito, solução, critério e Sprint.

## Perfis mencionados no briefing

| Perfil | Necessidade a confirmar na história oficial | Evidência de capacidade já planejada |
|---|---|---|
| Sistema consumidor | Consultar uma decisão antes de encaminhar conteúdo ao agente. | 06, 07 e 08 |
| Analista | Consultar histórico e realizar revisão humana auditável. | 09 e 10 |
| Product owner | Acompanhar desempenho e versões do modelo. | 09, 10 e 11 |
