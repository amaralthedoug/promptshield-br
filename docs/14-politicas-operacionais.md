# Políticas operacionais propostas

## Finalidade, vigência e aprovação

Estas políticas organizam a futura operação do PromptShield BR. Nenhum prazo, papel, ferramenta ou fluxo está aprovado nesta Sprint. A vigência depende de aprovação do controlador, DPO/encarregado, jurídico, segurança da informação e responsáveis técnicos. O princípio é reter menos, por menos tempo, com finalidade verificável.

## Política de retenção proposta

| Categoria | Finalidade | Necessidade | Prazo proposto | Justificativa | Controle de acesso | Descarte proposto |
|---|---|---|---|---|---|---|
| Texto analisado e OCR | Classificação em tempo real. | Somente durante análise. | **Não persistir por padrão**; exceção de incidente/revisão: até 30 dias após encerramento. | Reduz exposição; 30 dias permite investigação limitada. | Serviço durante processamento; analista autorizado em caso justificado. | Exclusão ao fim da requisição; na exceção, exclusão verificável e registro de descarte. |
| Metadados da análise | Diagnóstico, métricas e auditoria. | Necessários sem texto bruto. | 180 dias. | Permite observar falhas recentes e comparar versões sem retenção excessiva. | Analista, segurança e produto em visão minimizada. | Expurgo ou agregação irreversível ao término. |
| Scores, decisões e reason codes | Política, explicação e desempenho. | Necessários para histórico e contestação. | 180 dias, vinculados ao metadado minimizado. | Mantém janela de FP/FN e revisão sem conteúdo. | Analista/revisor; produto somente agregado. | Exclusão/anonimização vinculada ao evento. |
| Feedback humano e trilha de revisão | Auditoria, contestação e curadoria. | Necessários para responsabilidade e melhoria. | 365 dias após encerramento. | Sustenta mudança de rótulo e ciclo acadêmico de modelo. | Revisor, curador e segurança. | Desidentificar revisor quando possível; excluir vínculos no prazo. |
| Dataset de retreinamento aprovado | Treino, validação e reprodutibilidade. | Somente itens licenciados e aprovados. | 12 meses após aprovação; revalidação semestral. | Evita corpus indefinido e força revisão de necessidade/licença. | Curador de dados e ML autorizados. | Retirar item inválido/revogado, destruir cópias e registrar versões afetadas. |
| Logs de segurança e auditoria | Detectar abuso, investigar incidente e prestar contas. | Necessários para investigação. | 365 dias. | Cobertura anual proposta; não é obrigação legal presumida. | Segurança/auditoria; acesso segregado e imutável. | Expurgo seguro na rotação; preservar somente sob *legal hold* aprovado. |

Reavaliar qualquer prazo diante de obrigação legal, contrato, investigação, pedido válido de titular, incidente ou *legal hold*. Exceção exige finalidade, responsável, expiração e revisão; não autoriza retenção ilimitada.

## Acesso por papéis (RBAC)

| Papel funcional | Acesso proposto | Restrição |
|---|---|---|
| Sistema consumidor | Enviar conteúdo e receber sua análise. | Não consulta histórico global ou dados de outras fontes. |
| Analista | Ver histórico minimizado, investigar e abrir caso. | Conteúdo bruto somente com justificativa e autorização. |
| Revisor humano | Registrar rótulo e justificativa de `REVIEW`. | Não promove modelo nem altera saída original. |
| Curador de dados/ML | Dataset aprovado, versões e avaliações. | Não acessa evento bruto fora do fluxo aprovado. |
| Product owner | Métricas agregadas e versões aprovadas. | Sem conteúdo sensível por padrão. |
| Segurança/auditoria | Logs, evidências e incidentes. | Acesso temporalmente limitado e auditado. |
| Administrador técnico | Plataforma e segredos por necessidade. | Administração não equivale a ler conteúdo. |
| DPO/jurídico | Registros necessários a direitos e incidentes. | Não revisa modelo sem papel específico. |

Autenticação forte, menor privilégio, segregação de funções e revisão periódica de acessos são boas práticas propostas. A ANPD descreve controle de acesso como autenticação, autorização e auditoria ([guia de segurança](https://www.gov.br/anpd/pt-br/centrais-de-conteudo/materiais-educativos-e-publicacoes/guia-vf.pdf)).

### Credenciais, rotação e revogação

| Credencial | Uso proposto | Ciclo de vida proposto | Registro obrigatório |
|---|---|---|---|
| API Key de consumidor | Autenticar aplicação em `POST /v1/analyze`. | Exibir segredo uma vez; rotação a cada 90 dias; sobreposição de até 7 dias; revogação imediata. | Cliente, escopo, ambiente, criação, expiração, rotação, revogação e motivo. |
| Token administrativo | Sessão do portal e API `/v1/admin/*`. | Emitido por IdP OIDC/OAuth 2.0; curta duração e MFA; revogação conforme IdP. | Identidade, papel, autenticação, falha e operação sensível. |
| Segredo de serviço | Conexão interna, banco, OCR e observabilidade. | Secret manager, escopo mínimo, rotação e revogação coordenadas. | Dono, finalidade, última rotação e incidente, sem valor secreto. |

API Key não é mecanismo para autenticar pessoas. Chaves e tokens não podem aparecer em URL, log, captura de erro, dataset ou interface. Os prazos são propostas e exigem aprovação de segurança/plataforma.

### Segregação administrativa e limites

`/v1/admin/*` e o portal exigem autenticação administrativa e RBAC, separados da API de consumidores. Em produção, a exposição por domínio, rede ou gateway distintos é uma opção recomendada a validar; a separação de rota e de autorização é obrigatória no desenho. Limites iniciais propostos: 60 requisições/minuto por API Key, burst 20; 30 requisições/minuto por identidade administrativa. O gateway deve responder `429` com `Retry-After`, registrar abuso sem conteúdo e permitir ajuste por cliente aprovado.

## Proteção técnica e uso aceitável

- **Credenciais:** secret manager institucional, escopo mínimo, rotação e revogação; nunca inserir chaves, tokens ou senhas em código, dataset, prompt, log ou tela.
- **Dados:** TLS atualizado em trânsito, criptografia em repouso, chaves separadas e backups sujeitos à mesma retenção.
- **Texto:** mascarar ou omitir em dashboard/log; acesso excepcional registra motivo, identidade, horário e `analysis_id`.
- **Auditoria:** registrar autenticação, RBAC, leitura excepcional, exportação, revisão, mudança de política e promoção/rollback.
- **Uso indevido:** proibir vigilância de pessoas, coleta de segredos, decisão trabalhista automatizada ou classificação fora da finalidade aprovada.

## Resiliência e recuperação de falhas

| Falha | Tratamento proposto | Recuperação |
|---|---|---|
| Entrada inválida ou excessiva | Rejeitar antes da classificação com 400/413. | Consumidor corrige ou usa chunking; não truncar silenciosamente. |
| Timeout de rede/API | Repetir no máximo duas vezes apenas com `Idempotency-Key` e backoff. | Fila controlada ou retenção local; evitar duplicar eventos. |
| Modelo indisponível | Responder 503 sem decisão permissiva. | Restabelecer dependência ou usar última versão aprovada somente após política futura. |
| OCR falho/baixa confiança | Reter no consumidor para revisão prévia; sem texto válido não emitir decisão da API. Entrada inválida enviada recebe erro 400/422. | Reprocessar com configuração aprovada ou revisão humana. |
| Banco indisponível | Não afirmar auditoria concluída; retornar indisponibilidade. | Recuperar conexão, reconciliar evento idempotente e investigar lacunas. |
| Ação sensível do consumidor | `REVIEW`, `BLOCK` ou falha impedem execução automática. | Aprovação humana; não aplicar *fail-open*. |

Timeouts e SLOs específicos estão em 11. Logs de recuperação não devem transportar texto analisado. Testes de restauração, backup e rollback são atividades futuras de homologação, não evidências desta Sprint.

## Processos operacionais

### Pedido de titular

O canal, prazo e responsáveis dependem do controlador. O fluxo proposto recebe o pedido, valida identidade, localiza registros minimizados, consulta DPO/jurídico, executa decisão autorizada e preserva apenas a evidência mínima de atendimento.

### Incidente de segurança

1. Conter acesso, preservar evidência e registrar evento sem ampliar exposição.
2. Classificar dados atingidos, escopo, causa e impacto.
3. Comunicar controlador e encarregado definidos.
4. O controlador avalia comunicação à ANPD e titulares quando houver incidente confirmado com dados pessoais e risco/dano relevante ([ANPD](https://www.gov.br/anpd/pt-br/canais_atendimento/agente-de-tratamento/comunicado-de-incidente-de-seguranca-cis)).
5. Corrigir causa, revisar controles e registrar lições aprendidas sem inserir dado excessivo no relatório.

### Geração sintética de ataques

IA Generativa produz somente candidatos a dataset, jamais decisão de produção. Riscos: reprodução de dado de entrada, conteúdo ofensivo, duplicação de benchmark, viés de estilo e instruções reutilizáveis. Mitigações: não fornecer conteúdo real; usar cenário abstrato; revisão humana dupla; marcar `synthetic=true`, ferramenta/data/prompt de alto nível e revisor; deduplicar; restringir acesso. A inclusão em treino requer curadoria e verificação de licença/proveniência.
