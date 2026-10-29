# Registro de decisões, pendências e riscos

## Como interpretar este registro

As decisões são propostas documentais. `PROPOSTA` não equivale a aprovação, implementação ou conformidade. `BLOQUEADA` identifica o que depende de pessoa, órgão ou informação institucional inexistente. Aprovação futura deve registrar data, aprovador, escopo, evidência e versão de política.

## Decisões propostas

| ID | Decisão proposta | Justificativa | Evidência | Status | Aprovação necessária |
|---|---|---|---|---|---|
| GD-01 | Não persistir texto por padrão. | Minimiza exposição e atende finalidade transitória. | 10, 14 | PROPOSTA | Controlador, DPO/jurídico e segurança. |
| GD-02 | Reter metadados e decisões minimizados por 180 dias. | Viabiliza métricas e auditoria proporcional. | 14 | PROPOSTA | Controlador, DPO/jurídico e segurança. |
| GD-03 | Reter revisão humana e logs por 365 dias. | Sustenta contestação e investigação anual proposta. | 10, 14 | PROPOSTA | Controlador, DPO/jurídico e segurança. |
| GD-04 | Reter dataset aprovado por 12 meses, com revalidação semestral. | Evita corpus indefinido e preserva reprodutibilidade limitada. | 04, 10, 14 | PROPOSTA | Curadoria, jurídico e ML. |
| GD-05 | Usar RBAC e acesso excepcional auditado. | Reduz abuso de privilégio e exposição interna. | 10, 14 | PROPOSTA | Segurança e plataforma. |
| GD-06 | Registrar `REVIEW` como evento adicional. | Preserva saída original, explicabilidade e contestação. | 07, 09, 10 | PROPOSTA | Produto, segurança e ML. |
| GD-07 | Aprovação humana antes de usar dado em treino. | Impede rótulo automático, dado pessoal e fonte sem licença. | 04, 10, 14 | PROPOSTA | Curadoria, jurídico e ML. |
| GD-08 | Promover modelo só após avaliação de não regressão e plano de rollback. | Média melhor pode ocultar piora em origem crítica. | 05, 10, 11 | PROPOSTA | ML, produto e segurança. |
| GD-09 | API sem LLM generativo como classificador. | Regra explícita do Challenge. | 01, 05, 06 | DEFINIÇÃO DO CHALLENGE | Não requer decisão do grupo. |
| GD-10 | Definir controlador, operador, encarregado e bases legais antes da operação real. | Papéis e hipóteses não podem ser inferidos. | 10 | **BLOQUEADA** | Organização e jurídico/DPO. |
| GD-11 | Usar API Key para consumidores e OIDC/MFA para administração. | Separa identidade de aplicação e pessoa; evita usar API Key como login humano. | 06, 07, 14 | PROPOSTA | Segurança e plataforma. |
| GD-12 | Adotar FastAPI e serviço de classificação separado. | Mantém contrato HTTP desacoplado do motor e facilita troca de versão. | 06, 07 | PROPOSTA | Arquitetura e plataforma. |
| GD-13 | Usar SQLite em desenvolvimento e PostgreSQL em homologação/produção. | Equilibra simplicidade local com concorrência, backup e operação futura. | 06 | PROPOSTA | Arquitetura, segurança e plataforma. |
| GD-14 | Aplicar fail-safe em falha de análise para ações sensíveis. | Indisponibilidade não deve virar autorização silenciosa. | 06, 07, 14 | PROPOSTA | Produto, segurança e consumidor. |
| GD-15 | Calibrar thresholds por custo de erro, validação e capacidade de REVIEW. | Score isolado não define risco operacional aceitável. | 06, 07, 11 | PROPOSTA | Produto, ML e segurança. |

## Registro de `REVIEW` e rótulos

Para cada `REVIEW`, registrar `analysis_id`; versão de modelo, política, normalização e OCR; `source_type`; score e decisão original; motivo; rótulo humano; decisão recomendada; justificativa; revisor pseudonimizado; data; curadoria; e vínculo com dataset caso aprovado. Alterações são aditivas: preservam rótulo anterior, autor, data, justificativa e aprovador. Feedback não entra automaticamente em treino.

## Gates do ciclo de vida do modelo

| Gate | Evidência exigida | Decisão humana proposta | Resultado |
|---|---|---|---|
| Dados | Manifesto, licença, origem, revisão e prevenção de leakage. | Curadoria e jurídico, quando aplicável. | Aprovar, restringir ou rejeitar fonte. |
| Treino | Dataset, configuração e reprodutibilidade. | Responsável de ML. | Aceitar candidata ou repetir experimento. |
| Avaliação | Métricas por origem/versão, matriz, FP/FN e latência. | ML, produto e segurança. | Promover, manter baseline ou rejeitar. |
| Pré-produção | Política, monitoramento, acesso e rollback. | Produto e segurança. | Liberar controladamente ou bloquear. |
| Pós-promoção | `REVIEW rate`, FP, FN, deriva, incidentes e acesso. | Comitê funcional definido. | Manter, ajustar, suspender ou rollback. |

Regressão é piora relevante frente ao baseline em métrica, origem, ataque, hard negative, latência ou segurança, conforme limiares futuros. Degradação é mudança persistente em produção. Rollback restaura a última versão aprovada, preserva evidência e não apaga histórico.

## ADRs — decisões arquiteturais propostas

### ADR-01 — Autenticação de consumidores e administração

| Campo | Registro |
|---|---|
| Contexto | A API é consumida por sistemas automatizados, enquanto o portal contém operação humana e dados sensíveis. |
| Alternativas | (A) Uma API Key para todos os acessos; (B) API Key para consumidores e login próprio; (C) API Key para consumidores e OIDC/OAuth 2.0 com MFA para administração. |
| Decisão proposta | C: `X-API-Key` para cliente de API e OIDC/OAuth 2.0 com MFA/token curto para `/v1/admin/*`. |
| Justificativa | API Key identifica aplicação; OIDC/RBAC oferece identidade humana, sessões e revogação adequadas ao portal. |
| Consequências | Requer IdP, gestão de chaves, RBAC server-side e trilha de auditoria. |
| Riscos | Vazamento de chave, configuração incorreta de scopes ou dependência do IdP; mitigar com secret manager, rotação, MFA e logs. |

### ADR-02 — Limites, idempotência e falha segura

| Campo | Registro |
|---|---|
| Contexto | Classificação e OCR podem consumir CPU; falhas de rede podem induzir duplicação ou encaminhamento inseguro. |
| Alternativas | (A) Sem limites e retry livre; (B) Rate limit sem idempotência; (C) Rate limit por cliente, limites de payload, `Idempotency-Key` e retries limitados. |
| Decisão proposta | C: limites configuráveis, no máximo duas tentativas idempotentes e `REVIEW`/retenção em ação sensível quando análise falhar. |
| Justificativa | Reduz consumo irrestrito, evita eventos duplicados e não converte falha em `ALLOW`. |
| Consequências | Consumidores precisam tratar 413/429/503 e manter fila controlada. |
| Riscos | Limite inadequado gera indisponibilidade percebida; revisar com teste de carga e SLOs. |

### ADR-03 — Serviço de classificação independente em FastAPI

| Campo | Registro |
|---|---|
| Contexto | Motor evolui de Regex para TF-IDF e DeBERTa, enquanto contrato de consumidor deve permanecer estável. |
| Alternativas | (A) Lógica do modelo acoplada ao consumidor; (B) único processo monolítico sem fronteira; (C) API FastAPI e serviço lógico de classificação separado. |
| Decisão proposta | C: FastAPI como fronteira HTTP e classificador isolado por interface/versionamento. |
| Justificativa | Facilita validação, observabilidade, rollback e troca de modelo sem alterar consumidores. |
| Consequências | Exige contrato interno, health/readiness e gestão de dependência. |
| Riscos | Mais componentes e latência; manter separação inicialmente lógica e medir antes de distribuir processos. |

### ADR-04 — Banco e ambientes

| Campo | Registro |
|---|---|
| Contexto | Desenvolvimento individual precisa ser simples; operação com eventos, revisão e múltiplos usuários exige maior robustez. |
| Alternativas | (A) SQLite em todos os ambientes; (B) PostgreSQL desde o início; (C) SQLite em desenvolvimento e PostgreSQL em homologação/produção. |
| Decisão proposta | C, com migração versionada e validada antes de produção. |
| Justificativa | Reduz atrito local e planeja concorrência, backup, RBAC e observabilidade para ambientes compartilhados. |
| Consequências | Exige compatibilidade de esquema, migração e testes entre bancos. |
| Riscos | Divergência de comportamento; homologação deve usar PostgreSQL antes de qualquer produção. |

### ADR-05 — Score, thresholds e decisão ternária

| Campo | Registro |
|---|---|
| Contexto | Um score pode ser heurístico ou calibrado; decisão automática envolve custo de erro e risco da ação. |
| Alternativas | (A) Um único cutoff binário; (B) cliente decide pelo score; (C) política versionada com `ALLOW`, `REVIEW` e `BLOCK`. |
| Decisão proposta | C: motor devolve classificação/score; política versionada aplica dois thresholds e a API devolve decisão. |
| Justificativa | Mantém incerteza no fluxo `REVIEW`, evita interpretação incorreta de score e torna tolerância a risco auditável. |
| Consequências | Requer capacidade de revisão e avaliação de calibração/FP/FN. |
| Riscos | Thresholds inadequados elevam bloqueio ou vazamento; selecionar com validação e custos aprovados. |

### ADR-06 — Containers e ambientes progressivos

| Campo | Registro |
|---|---|
| Contexto | API, OCR, portal e banco terão dependências distintas e não há infraestrutura Intelliway disponível. |
| Alternativas | (A) Deploy manual por ambiente; (B) container único para todos os componentes; (C) imagens por componente e promoção desenvolvimento → homologação → produção. |
| Decisão proposta | C como estratégia futura, com configuração/segredos externos e imagens imutáveis. |
| Justificativa | Reprodutibilidade e isolamento de dependências; não substitui controles de rede, acesso ou dados. |
| Consequências | Exige pipeline, registro de imagens, scan e gestão de configuração. |
| Riscos | Falsa percepção de segurança; mitigar com hardening, scan, RBAC e aprovação de ambientes. |

## Matriz de riscos proposta

Escalas: probabilidade/impacto `Baixa`, `Média` ou `Alta`; criticidade qualitativa sujeita à validação institucional.

| ID | Risco | Probabilidade | Impacto | Criticidade | Mitigação proposta | Responsável funcional |
|---|---|---|---|---|---|---|
| RG-01 | Texto pessoal retido além da necessidade. | Média | Alta | Alta | Não persistir por padrão, exceção temporal e expurgo verificável. | DPO e segurança. |
| RG-02 | Texto sensível exposto em dashboard, log ou exportação. | Média | Alta | Alta | Mascaramento, segregação, RBAC e auditoria. | Segurança e produto. |
| RG-03 | Controlador, operador ou base legal incorretos. | Média | Alta | Alta | Avaliação pré-operação e instruções/contratos documentados. | Jurídico/DPO e controlador. |
| RG-04 | Pedido de titular atendido inadequadamente. | Baixa | Alta | Média | Canal, identificação proporcional e trilha de resposta. | DPO/controlador. |
| RG-05 | Incidente não escalado/comunicado corretamente. | Baixa | Alta | Média | Runbook, registro e avaliação pelo controlador. | Segurança, DPO e controlador. |
| RG-06 | Falso positivo bloqueia conteúdo legítimo. | Média | Média | Média | Hard negatives, `REVIEW`, monitoramento de FP e limiares. | Produto e ML. |
| RG-07 | Falso negativo alcança agente privilegiado. | Média | Alta | Alta | Defesa em camadas, menor privilégio, confirmação humana e red team. | Segurança, ML e consumidor. |
| RG-08 | Rótulo/dataset manipulado, incorreto ou sem licença. | Média | Alta | Alta | Curadoria, versionamento, dupla revisão e manifesto. | Curador de dados e ML. |
| RG-09 | Modelo degrada após atualização ou deriva. | Média | Média | Média | Teste congelado, corte por origem, monitoramento e rollback. | ML e produto. |
| RG-10 | Credencial de API/portal é exposta. | Média | Alta | Alta | Secret manager, rotação, escopo mínimo e revogação. | Segurança e administrador técnico. |
| RG-11 | Geração sintética reproduz dado, viés ou ataque reutilizável. | Média | Média | Média | Sem conteúdo real, revisão dupla e acesso restrito. | Curador e segurança. |
| RG-12 | Detector usado para vigilância ou decisão sobre pessoas. | Baixa | Alta | Média | Uso aceitável, RBAC, revisão de finalidade e bloqueio. | Product owner e jurídico/DPO. |

## Pendências institucionais

1. Nomear controlador, operador, encarregado e responsáveis funcionais.
2. Validar finalidade, bases legais, aviso de privacidade, canal de titulares e fornecedores.
3. Aprovar/ajustar prazos, exceções e descarte.
4. Definir identidade, chaves, logs, backups e resposta a incidentes.
5. Definir limiares de regressão, risco aceitável, SLOs e autoridade de rollback.
6. Aprovar curadoria, licença e uso de dados públicos/sintéticos.
