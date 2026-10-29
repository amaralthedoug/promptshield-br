# User Stories e matriz de rastreabilidade

## Situação da especificação oficial

**User Stories propostas pelo grupo — sujeitas à validação perante a especificação oficial da Intelliway.**

A Fase 3 é a identificação da entrega atual do curso; este planejamento corresponde à **Sprint 1 do Challenge Intelliway**. Não há implementação funcional ou critérios executados. O catálogo abaixo foi elaborado para o planejamento do grupo a partir do briefing e da documentação existente. Não foi fornecido nem aprovado oficialmente pela Intelliway; o aceite interno do grupo também precisa ser registrado.

O [briefing](../BRIEFING.md) menciona uma especificação externa, mas não reproduz suas histórias. A fonte oficial permanece ausente do workspace; `docs/requisitos/` não existe. Assim, o planejamento local está disponível, mas a validação oficial de IDs, prioridades, critérios e cobertura de P0 continua **bloqueada**.

| Fonte | Estado | O que permite afirmar |
|---|---|---|
| Briefing local | Disponível | Contexto e capacidades para elaborar propostas locais. |
| Catálogo US-001–US-015 deste documento | Proposto; não implementado | Prioridades e critérios de autoria do grupo para discussão/planejamento. |
| Especificação oficial Intelliway | Ausente | Não permite alegar P0 oficial integralmente coberta ou aprovação de P1/P2. |

## Matriz de rastreabilidade das histórias oficiais

Esta seção é reservada ao confronto com a fonte oficial. US-001–US-015 são IDs locais; não reutilizar esses IDs como se fossem da empresa. A futura relação pode ser de uma história oficial para várias propostas e vice-versa, preservando lacunas e divergências.

| ID/título oficial | Prioridade e critérios oficiais | Propostas locais relacionadas | Arquitetura/evidência | Sprint | Estado |
|---|---|---|---|---|---|
| Não disponível | Não disponível | A mapear após recebimento da fonte | Matriz oficial ainda não preenchida | A confirmar | **BLOQUEADA** |

## Regra de seleção do escopo

**P0 proposta:** mínimo necessário para demonstrar o valor central com segurança, rastreabilidade e decisão técnica fundamentada. **P1 proposta:** expansão de canais e operação administrativa. **P2 proposta:** evolução após o núcleo e suas dependências. Essas classes locais não substituem prioridades oficiais.

Após receber a especificação, todas as P0 oficiais devem ser contempladas no MVP; cada P1/P2 oficial será analisada por valor, esforço, risco e dependências. Renomear ou repriorizar propostas não altera o requisito oficial. Aprovação de prioridade pelo grupo ou pela Intelliway não é presumida.

## Revisão técnica das prioridades

| Capacidades planejadas | Classificação preliminar | Prioridade proposta nesta revisão | Justificativa |
|---|---|---|---|
| API, origem, detecção, decisão, registro e inferência sem LLM generativo (US-001–US-006) | P0 | P0 | Formam o núcleo independente e seus controles mínimos. |
| E-mail/web, OCR, RAG, portal e revisão (US-007–US-011) | P1 | P1 | Expandem fontes e operação sem alterar a fronteira textual da API. |
| Versionamento (US-012) | P2 | **P0** | Dataset/modelo/política já precisam de identidade nos experimentos e no contrato. O inventário mínimo é antecipado; UI de versões permanece no portal. |
| Feedback para retreinamento (US-013) | P2 | P2 | Depende de revisão, adjudicação, curadoria e aprovação, sem treino automático. |
| Comparação com DeBERTa PT-BR (US-014) | P2 | **P0** | O briefing exige planejar comparação de baselines e modelo profundo. Para o MVP proposto, evidência orienta a escolha; DeBERTa não é adoção obrigatória nem superioridade presumida. |
| Análises avançadas (US-015) | P2 | P2 | Filtros adicionais podem evoluir após histórico mínimo e RBAC. |

**Total: 15 histórias propostas — oito P0, cinco P1 e duas P2.** Prioridade não é ordem rígida de execução: um manifesto P0 nasce na Sprint 2, o experimento P0 ocorre na Sprint 3 e o serviço P0 se integra na Sprint 4. Nenhuma história é implementada na Sprint 1.

## Índice do catálogo proposto

| ID | Título | Prioridade proposta | Sprint principal de implementação/avaliação | Dependências locais |
|---|---|---|---|---|
| [US-001](#us-001) | Análise textual via API | P0 | 4 | US-002, US-003, US-004, US-005, US-006 |
| [US-002](#us-002) | Origem padronizada do conteúdo | P0 | 4 | Nenhuma história local; ver gates de dados/infraestrutura. |
| [US-003](#us-003) | Detecção discriminativa em PT-BR | P0 | 3 | US-006, US-012, US-014 |
| [US-004](#us-004) | Decisão operacional estruturada | P0 | 4 | US-003, US-012 |
| [US-005](#us-005) | Registro seguro e auditável da decisão | P0 | 4 | US-002, US-004, US-012 |
| [US-006](#us-006) | Inferência sem LLM generativo | P0 | 3 | Nenhuma história local; ver gates de dados/infraestrutura. |
| [US-007](#us-007) | Ingestão de e-mail e página web | P1 | 4 | US-001 |
| [US-008](#us-008) | Análise de texto extraído por OCR | P1 | 4 | US-001 |
| [US-009](#us-009) | Proteção de documentos recuperados por RAG | P1 | 4 | US-001 |
| [US-010](#us-010) | Histórico, detalhe e indicadores administrativos | P1 | 5 | US-005, US-012 |
| [US-011](#us-011) | Revisão humana aditiva | P1 | 5 | US-010 |
| [US-012](#us-012) | Versionamento mínimo e linhagem dos artefatos | P0 | 2 | Nenhuma história local; ver gates de dados/infraestrutura. |
| [US-013](#us-013) | Curadoria de feedback para retreinamento | P2 | 6 | US-011, US-012 |
| [US-014](#us-014) | Comparação reproduzível de baselines e DeBERTa | P0 | 3 | US-012 |
| [US-015](#us-015) | Filtros e análise por origem, risco e versão | P2 | 5 | US-010 |

## Catálogo proposto

Critérios a seguir são condições verificáveis para aceitação futura, não resultados medidos ou testes já executados. Gates comuns: fonte de dados admissível, conjunto rotulado, decisões de produto/segurança, ambiente e alinhamento oficial quando disponível. Ausência de história local dependente não elimina esses insumos externos. Não há metas de qualidade numéricas aprovadas; aceitar um classificador exige defini-las na validação, não inventá-las nesta proposta.

### US-001

**Título:** Análise textual via API

**Ator:** Sistema consumidor

**Descrição:** Como sistema consumidor, quero enviar conteúdo textual para análise via API, para avaliar o risco antes de encaminhá-lo ao agente.

**Prioridade proposta:** P0

**Justificativa de negócio:** Oferece a fronteira independente de integração e evita análise apenas após a execução do agente.

**Critérios de aceitação verificáveis:**

- **US-001-CA01:** Uma requisição autenticada para POST /v1/analyze com content textual não vazio e source_type permitido recebe a estrutura de análise definida no contrato, sem executar instruções contidas no texto.
- **US-001-CA02:** JSON malformado, entrada fora do contrato e payload excessivo recebem os erros 400/422/413 aplicáveis, sem conteúdo ecoado e sem decision de sucesso.
- **US-001-CA03:** Indisponibilidade do motor ou da persistência obrigatória produz erro explícito 503; não gera ALLOW por ausência de análise.

**Dependências:** [US-002](#us-002), [US-003](#us-003), [US-004](#us-004), [US-005](#us-005), [US-006](#us-006)

**Sprint planejada:** 4 (implementação/avaliação futura; planejamento na Sprint 1).

**Referência técnica:** [06-arquitetura-solucao.md](06-arquitetura-solucao.md); [07-contrato-api.md](07-contrato-api.md).

**Status:** proposta documental; não implementada; sujeita ao aceite do grupo e confronto com a fonte oficial.

### US-002

**Título:** Origem padronizada do conteúdo

**Ator:** Sistema consumidor

**Descrição:** Como sistema consumidor, quero identificar a origem de cada conteúdo por source_type, para rastrear o canal de entrada e aplicar a política correspondente.

**Prioridade proposta:** P0

**Justificativa de negócio:** Permite avaliar risco por origem e investigar injeção indireta sem confundir proveniência com confiança.

**Critérios de aceitação verificáveis:**

- **US-002-CA01:** O contrato aceita exatamente user_text, email, web_page, document, rag_chunk, image_ocr e pdf_ocr; valor ausente ou fora do enum é rejeitado antes da inferência.
- **US-002-CA02:** Em uma análise válida, source_type da resposta e do evento auditável coincide com a origem informada; não é deduzido silenciosamente pelo modelo.
- **US-002-CA03:** source_id é opcional; quando usado, segue pseudonimização e não substitui o campo source_type.

**Dependências:** Nenhuma história local; sujeita aos gates comuns acima.

**Sprint planejada:** 4 (implementação/avaliação futura; planejamento na Sprint 1).

**Referência técnica:** [07-contrato-api.md](07-contrato-api.md); [08-rpa-ocr-rag.md](08-rpa-ocr-rag.md).

**Status:** proposta documental; não implementada; sujeita ao aceite do grupo e confronto com a fonte oficial.

### US-003

**Título:** Detecção discriminativa em PT-BR

**Ator:** Sistema consumidor

**Descrição:** Como sistema consumidor, quero obter a classificação de risco de prompt injection em PT-BR, para reduzir o encaminhamento de instruções maliciosas sem bloquear indevidamente mensagens legítimas.

**Prioridade proposta:** P0

**Justificativa de negócio:** É o valor central da solução; inclui ataques diretos, indiretos e hard negatives corporativos.

**Critérios de aceitação verificáveis:**

- **US-003-CA01:** Para entradas válidas, o motor retorna benign ou injection e identifica a versão do pipeline/modelo; os subtipos humanos direto/indireto permanecem na anotação de avaliação.
- **US-003-CA02:** O relatório de avaliação utiliza corpus PT-BR com rótulos adjudicados, divisão por famílias, hard negatives e teste congelado; informa precision, recall, F1, AUC, suporte e FP/FN por origem quando calculáveis.
- **US-003-CA03:** O pipeline preserva acentos/contexto e registra chunking de textos longos, sem truncamento silencioso; configuração, limite do tokenizer e agregação são rastreáveis.
- **US-003-CA04:** Aceite de qualidade depende de limites definidos por produto/segurança na validação antes do teste final; sem esse registro, não se declara eficácia ou aprovação do modelo.

**Dependências:** [US-006](#us-006), [US-012](#us-012), [US-014](#us-014)

**Sprint planejada:** 3 (implementação/avaliação futura; planejamento na Sprint 1).

**Referência técnica:** [02-modelo-de-ameacas.md](02-modelo-de-ameacas.md); [04-planejamento-dataset.md](04-planejamento-dataset.md); [05-plano-nlp-modelos.md](05-plano-nlp-modelos.md); [11-metricas-avaliacao.md](11-metricas-avaliacao.md).

**Status:** proposta documental; não implementada; sujeita ao aceite do grupo e confronto com a fonte oficial.

### US-004

**Título:** Decisão operacional estruturada

**Ator:** Sistema consumidor

**Descrição:** Como sistema consumidor, quero receber ALLOW, REVIEW ou BLOCK junto de score e versões, para aplicar uma ação explícita e rastreável ao conteúdo analisado.

**Prioridade proposta:** P0

**Justificativa de negócio:** Separa o resultado estatístico da tolerância operacional a erro e incerteza.

**Critérios de aceitação verificáveis:**

- **US-004-CA01:** A resposta válida contém analysis_id, request_id, classification, decision, risk_score, score_type, model_version, policy_version, source_type, reason_codes e created_at conforme o contrato.
- **US-004-CA02:** risk_score permanece entre 0 e 100; heuristic_risk não é descrito como probabilidade; calibrated_probability só é usado após calibração validada, com probabilidade multiplicada por 100.
- **US-004-CA03:** Para thresholds versionados, a regra-base devolve ALLOW abaixo do allow_threshold, REVIEW do allow_threshold inclusive ao block_threshold exclusive e BLOCK a partir do block_threshold; casos de fronteira são verificados.
- **US-004-CA04:** ALLOW permite encaminhar sob controles, REVIEW retém e BLOCK impede encaminhamento; erros não contêm decision permissiva fictícia.

**Dependências:** [US-003](#us-003), [US-012](#us-012)

**Sprint planejada:** 4 (implementação/avaliação futura; planejamento na Sprint 1).

**Referência técnica:** [06-arquitetura-solucao.md](06-arquitetura-solucao.md); [07-contrato-api.md](07-contrato-api.md); [11-metricas-avaliacao.md](11-metricas-avaliacao.md).

**Status:** proposta documental; não implementada; sujeita ao aceite do grupo e confronto com a fonte oficial.

### US-005

**Título:** Registro seguro e auditável da decisão

**Ator:** Analista

**Descrição:** Como analista, quero consultar metadados auditáveis de cada decisão, para investigar eventos preservando privacidade e integridade da evidência.

**Prioridade proposta:** P0

**Justificativa de negócio:** Sustenta auditoria, métricas e contestação sem transformar o histórico em depósito de conteúdo sensível.

**Critérios de aceitação verificáveis:**

- **US-005-CA01:** Cada análise bem-sucedida gera evento correlacionável por analysis_id/request_id, com origem, classe, score, decisão, data e versões; a resposta não confirma auditoria se o registro obrigatório falhar.
- **US-005-CA02:** Texto bruto e credenciais não são persistidos por padrão nem aparecem em logs; acesso excepcional a conteúdo requer autorização, finalidade e retenção registradas.
- **US-005-CA03:** Consultas futuras exigem papel autorizado e segregação de acesso; alteração de rótulo ou política não apaga a saída original.
- **US-005-CA04:** A verificação do registro pode ocorrer pela persistência controlada antes do portal; sua UI pertence à US-010 e não é dependência para registrar eventos.

**Dependências:** [US-002](#us-002), [US-004](#us-004), [US-012](#us-012)

**Sprint planejada:** 4 (implementação/avaliação futura; planejamento na Sprint 1).

**Referência técnica:** [06-arquitetura-solucao.md](06-arquitetura-solucao.md); [07-contrato-api.md](07-contrato-api.md); [10-governanca.md](10-governanca.md); [14-politicas-operacionais.md](14-politicas-operacionais.md); [15-registro-de-decisoes.md](15-registro-de-decisoes.md).

**Status:** proposta documental; não implementada; sujeita ao aceite do grupo e confronto com a fonte oficial.

### US-006

**Título:** Inferência sem LLM generativo

**Ator:** Product owner

**Descrição:** Como product owner, quero manter a classificação independente de LLM generativo em tempo de inferência, para atender à restrição do Challenge e controlar dependências operacionais.

**Prioridade proposta:** P0

**Justificativa de negócio:** É uma restrição explícita do briefing e vale para qualquer versão do motor.

**Critérios de aceitação verificáveis:**

- **US-006-CA01:** O inventário do fluxo de análise identifica apenas regras ou classificadores discriminativos na geração de classification e risk_score; nenhuma chamada generativa decide entradas.
- **US-006-CA02:** A classificação permanece disponível em cenário controlado sem serviço ou credencial de LLM generativo, desde que as dependências discriminativas e de registro estejam disponíveis.
- **US-006-CA03:** Qualquer uso de IA Generativa é identificado fora do caminho de decisão: preparação de candidatos de dados revisados ou avaliador futuro do portal.

**Dependências:** Nenhuma história local; sujeita aos gates comuns acima.

**Sprint planejada:** 3 (implementação/avaliação futura; planejamento na Sprint 1).

**Referência técnica:** [01-visao-geral.md](01-visao-geral.md); [05-plano-nlp-modelos.md](05-plano-nlp-modelos.md); [06-arquitetura-solucao.md](06-arquitetura-solucao.md); [15-registro-de-decisoes.md](15-registro-de-decisoes.md).

**Status:** proposta documental; não implementada; sujeita ao aceite do grupo e confronto com a fonte oficial.

### US-007

**Título:** Ingestão de e-mail e página web

**Ator:** Sistema consumidor automatizado

**Descrição:** Como sistema consumidor automatizado, quero preparar textos de e-mails e páginas web para consulta à API, para interceptar instruções indiretas antes de compor o contexto do agente.

**Prioridade proposta:** P1

**Justificativa de negócio:** Amplia a proteção aos canais corporativos previstos no briefing, mantendo o classificador desacoplado do coletor.

**Critérios de aceitação verificáveis:**

- **US-007-CA01:** Cenários sintéticos de e-mail e página web têm texto extraído e JSON padronizado com source_type=email ou web_page e proveniência minimizada.
- **US-007-CA02:** O consumidor consulta a API antes de repassar o conteúdo ao agente e registra a ação: seguir somente sob ALLOW, reter em REVIEW, impedir encaminhamento em BLOCK.
- **US-007-CA03:** Falha/timeout não libera ação sensível; retries respeitam o limite e a idempotência planejados, sem executar a ação de negócio em duplicidade.

**Dependências:** [US-001](#us-001)

**Sprint planejada:** 4 (implementação/avaliação futura; planejamento na Sprint 1).

**Referência técnica:** [06-arquitetura-solucao.md](06-arquitetura-solucao.md); [07-contrato-api.md](07-contrato-api.md); [08-rpa-ocr-rag.md](08-rpa-ocr-rag.md).

**Status:** proposta documental; não implementada; sujeita ao aceite do grupo e confronto com a fonte oficial.

### US-008

**Título:** Análise de texto extraído por OCR

**Ator:** Sistema consumidor automatizado

**Descrição:** Como sistema consumidor automatizado, quero analisar textos extraídos de imagens e PDFs por OCR, para reduzir o risco de instruções ocultas em documentos visuais.

**Prioridade proposta:** P1

**Justificativa de negócio:** Cobre a superfície visual sem exigir upload binário no endpoint de classificação.

**Critérios de aceitação verificáveis:**

- **US-008-CA01:** O fluxo aplica validação do arquivo e extração/OCR antes de POST /v1/analyze; envia texto com image_ocr ou pdf_ocr e metadata.ocr_applied=true, sem binários no endpoint.
- **US-008-CA02:** A avaliação planejada inclui baixo contraste, texto pequeno/rodapé e casos legítimos; registra página e confiança da extração conforme esquema a estabilizar, sem alegar eficácia antecipada.
- **US-008-CA03:** Baixa confiança ou ausência de texto confiável retém o item no consumidor para revisão; não fabrica decision=REVIEW da API. Se entrada inválida for enviada, a API devolve o erro previsto sem decisão de sucesso.

**Dependências:** [US-001](#us-001)

**Sprint planejada:** 4 (implementação/avaliação futura; planejamento na Sprint 1).

**Referência técnica:** [06-arquitetura-solucao.md](06-arquitetura-solucao.md); [07-contrato-api.md](07-contrato-api.md); [08-rpa-ocr-rag.md](08-rpa-ocr-rag.md).

**Status:** proposta documental; não implementada; sujeita ao aceite do grupo e confronto com a fonte oficial.

### US-009

**Título:** Proteção de documentos recuperados por RAG

**Ator:** Sistema consumidor RAG

**Descrição:** Como sistema consumidor RAG, quero analisar chunks recuperados antes de inseri-los no contexto, para evitar que instruções indiretas contaminem a resposta do agente.

**Prioridade proposta:** P1

**Justificativa de negócio:** Demonstra a fronteira de confiança em recuperação de conhecimento sem depender do EvaGPT.

**Critérios de aceitação verificáveis:**

- **US-009-CA01:** Um cenário inteiramente sintético contém documentos legítimos e chunks contaminados; cada chunk é consultado como source_type=rag_chunk, com referência de documento/ordem preservada na rastreabilidade.
- **US-009-CA02:** O contexto do agente recebe somente chunks ALLOW; REVIEW segue para revisão e BLOCK não é inserido, com ação correlacionada à análise.
- **US-009-CA03:** Os rótulos de avaliação dos chunks não são entregues ao classificador como sinal de entrada; documentos/famílias de teste não são usados para ajustar o modelo ou a política.

**Dependências:** [US-001](#us-001)

**Sprint planejada:** 4 (implementação/avaliação futura; planejamento na Sprint 1).

**Referência técnica:** [02-modelo-de-ameacas.md](02-modelo-de-ameacas.md); [06-arquitetura-solucao.md](06-arquitetura-solucao.md); [08-rpa-ocr-rag.md](08-rpa-ocr-rag.md).

**Status:** proposta documental; não implementada; sujeita ao aceite do grupo e confronto com a fonte oficial.

### US-010

**Título:** Histórico, detalhe e indicadores administrativos

**Ator:** Analista e product owner

**Descrição:** Como analista e product owner, quero consultar histórico, detalhes e indicadores no portal administrativo, para acompanhar decisões e desempenho com acesso proporcional ao papel.

**Prioridade proposta:** P1

**Justificativa de negócio:** Torna os registros úteis para operação e produto sem expor dados brutos por padrão.

**Critérios de aceitação verificáveis:**

- **US-010-CA01:** Login federado e RBAC controlam, conforme o papel, o acesso às rotas GET /v1/admin/analyses, GET /v1/admin/analyses/{analysis_id}, GET /v1/admin/metrics e GET /v1/admin/model-versions; API Key de consumidor não autoriza administração.
- **US-010-CA02:** Histórico é paginado e o detalhe mostra origem, decisão, score_type, versões e trilha permitida; conteúdo bruto não é exibido por padrão.
- **US-010-CA03:** Indicadores mostram janela, origem, versões e denominadores; precision/recall/F1/AUC aparecem apenas com avaliação rotulada válida. Ausência de dados mostra estado vazio, sem números fictícios.

**Dependências:** [US-005](#us-005), [US-012](#us-012)

**Sprint planejada:** 5 (implementação/avaliação futura; planejamento na Sprint 1).

**Referência técnica:** [07-contrato-api.md](07-contrato-api.md); [09-wireframes-portal.md](09-wireframes-portal.md); [10-governanca.md](10-governanca.md); [11-metricas-avaliacao.md](11-metricas-avaliacao.md).

**Status:** proposta documental; não implementada; sujeita ao aceite do grupo e confronto com a fonte oficial.

### US-011

**Título:** Revisão humana aditiva

**Ator:** Revisor humano

**Descrição:** Como revisor humano, quero registrar revisão fundamentada de uma classificação, para corrigir ambiguidades e produzir feedback auditável.

**Prioridade proposta:** P1

**Justificativa de negócio:** Reduz o custo de decisões incorretas e cria evidência de curadoria sem apagar a decisão automática.

**Critérios de aceitação verificáveis:**

- **US-011-CA01:** POST /v1/admin/analyses/{analysis_id}/review exige papel de revisor, rótulo, justificativa e decisão recomendada; o schema final deve manter os campos de auditoria previstos.
- **US-011-CA02:** A revisão acrescenta identidade pseudonimizada, data e versão observada, preservando score, decisão original e revisões anteriores.
- **US-011-CA03:** Rótulos inconclusivos permanecem pendentes de adjudicação e feedback revisado não entra automaticamente no dataset ou no treino.

**Dependências:** [US-010](#us-010)

**Sprint planejada:** 5 (implementação/avaliação futura; planejamento na Sprint 1).

**Referência técnica:** [07-contrato-api.md](07-contrato-api.md); [09-wireframes-portal.md](09-wireframes-portal.md); [10-governanca.md](10-governanca.md); [15-registro-de-decisoes.md](15-registro-de-decisoes.md).

**Status:** proposta documental; não implementada; sujeita ao aceite do grupo e confronto com a fonte oficial.

### US-012

**Título:** Versionamento mínimo e linhagem dos artefatos

**Ator:** Responsável de ML e governança

**Descrição:** Como responsável de ml e governança, quero versionar modelos, datasets e políticas de decisão, para reproduzir avaliações e explicar a origem de cada decisão.

**Prioridade proposta:** P0

**Justificativa de negócio:** Versões já fazem parte do contrato e são pré-requisito da auditoria desde o primeiro experimento; não podem surgir apenas na evolução final.

**Critérios de aceitação verificáveis:**

- **US-012-CA01:** Cada avaliação associa dataset_version, divisão por famílias, fonte/licença e configuração a model_version e ao pipeline de normalização/OCR aplicável.
- **US-012-CA02:** Cada alteração de thresholds ou regra gera policy_version distinta e registra motivo, parâmetros, responsável funcional e aprovação exigida; versões usadas nas decisões permanecem consultáveis.
- **US-012-CA03:** O inventário de artefatos identifica a última versão aprovada e os passos de rollback; produção de uma versão candidata não equivale à sua promoção.
- **US-012-CA04:** A entrega desta história é incremental: manifesto/rastreabilidade na Sprint 2, associação a experimentos/política na Sprint 3 e campos expostos na API na Sprint 4. O portal da Sprint 5 não bloqueia o versionamento mínimo.

**Dependências:** Nenhuma história local; sujeita aos gates comuns acima.

**Sprint planejada:** 2 (implementação/avaliação futura; planejamento na Sprint 1).

**Referência técnica:** [04-planejamento-dataset.md](04-planejamento-dataset.md); [05-plano-nlp-modelos.md](05-plano-nlp-modelos.md); [07-contrato-api.md](07-contrato-api.md); [10-governanca.md](10-governanca.md); [15-registro-de-decisoes.md](15-registro-de-decisoes.md).

**Status:** proposta documental; não implementada; sujeita ao aceite do grupo e confronto com a fonte oficial.

### US-013

**Título:** Curadoria de feedback para retreinamento

**Ator:** Curador de dados

**Descrição:** Como curador de dados, quero usar feedback humano validado para planejar o retreinamento, para melhorar cobertura do detector sem incorporar rótulos ou textos indevidos.

**Prioridade proposta:** P2

**Justificativa de negócio:** Permite evolução controlada após existir revisão humana com rastreabilidade.

**Critérios de aceitação verificáveis:**

- **US-013-CA01:** Cada candidato ao dataset referencia análise/revisão, origem, rótulo adjudicado, revisão humana e admissibilidade; item sem licença/proveniência suficiente ou com dado indevido não é aprovado.
- **US-013-CA02:** Curadoria distingue aprovado, restrito/rejeitado e pendente; aprovação não altera automaticamente o modelo em uso nem o teste congelado.
- **US-013-CA03:** O plano do próximo ciclo identifica nova dataset_version, separação sem leakage, comparação com baseline, gate humano de promoção e rollback; treinamento só ocorre mediante etapa futura autorizada.

**Dependências:** [US-011](#us-011), [US-012](#us-012)

**Sprint planejada:** 6 (implementação/avaliação futura; planejamento na Sprint 1).

**Referência técnica:** [04-planejamento-dataset.md](04-planejamento-dataset.md); [10-governanca.md](10-governanca.md); [14-politicas-operacionais.md](14-politicas-operacionais.md); [15-registro-de-decisoes.md](15-registro-de-decisoes.md).

**Status:** proposta documental; não implementada; sujeita ao aceite do grupo e confronto com a fonte oficial.

### US-014

**Título:** Comparação reproduzível de baselines e DeBERTa

**Ator:** Responsável de ML

**Descrição:** Como responsável de ml, quero comparar Regex e TF-IDF com um candidato DeBERTa avaliado e adaptado para PT-BR, para selecionar o motor com evidência de qualidade e viabilidade em CPU.

**Prioridade proposta:** P0

**Justificativa de negócio:** A comparação sustenta a escolha do classificador; não é preciso adotar DeBERTa se ele não superar os baselines ou não cumprir o orçamento aprovado.

**Critérios de aceitação verificáveis:**

- **US-014-CA01:** Regras, TF-IDF/classificador e DeBERTa usam os mesmos splits congelados e relatório por origem/hard negative; hiperparâmetros e thresholds não são ajustados no teste.
- **US-014-CA02:** O relatório distingue candidato original, avaliação PT-BR e adaptação; fine-tuning e eventual LoRA usam somente dados admissíveis, com configuração, seed, versões e custo registrados.
- **US-014-CA03:** Precision, recall, F1, PR-AUC/ROC-AUC, FP/FN e limites de contexto são reportados quando calculáveis; CPU registra hardware, memória, entrada, aquecimento, p95 e throughput, sem prometer os SLOs antes da medição.
- **US-014-CA04:** A decisão de manter baseline, promover candidato ou adiar adoção é registrada com limites definidos previamente na validação. Sem compute/dados admissíveis, a comparação permanece pendente e não é marcada concluída.

**Dependências:** [US-012](#us-012)

**Sprint planejada:** 3 (implementação/avaliação futura; planejamento na Sprint 1).

**Referência técnica:** [04-planejamento-dataset.md](04-planejamento-dataset.md); [05-plano-nlp-modelos.md](05-plano-nlp-modelos.md); [11-metricas-avaliacao.md](11-metricas-avaliacao.md).

**Status:** proposta documental; não implementada; sujeita ao aceite do grupo e confronto com a fonte oficial.

### US-015

**Título:** Filtros e análise por origem, risco e versão

**Ator:** Analista e product owner

**Descrição:** Como analista e product owner, quero filtrar análises por origem, faixa de risco e versões, para investigar padrões de erro e comparar comportamento entre versões.

**Prioridade proposta:** P2

**Justificativa de negócio:** Aprofunda a investigação após histórico e indicadores mínimos estarem disponíveis.

**Critérios de aceitação verificáveis:**

- **US-015-CA01:** Os filtros já previstos de período, source_type, decisão, score, model_version, policy_version e status de revisão podem ser combinados sem retornar itens fora dos critérios.
- **US-015-CA02:** Resultados e agregados exibem o recorte aplicado e o denominador; versões só são comparadas com conjunto/janela identificados e sem alegar causalidade a partir do volume.
- **US-015-CA03:** Filtros respeitam RBAC e minimização; ausência de resultados mostra estado vazio e acesso negado não expõe conteúdo ou métricas de outro escopo.

**Dependências:** [US-010](#us-010)

**Sprint planejada:** 5 (implementação/avaliação futura; planejamento na Sprint 1).

**Referência técnica:** [07-contrato-api.md](07-contrato-api.md); [09-wireframes-portal.md](09-wireframes-portal.md); [11-metricas-avaliacao.md](11-metricas-avaliacao.md).

**Status:** proposta documental; não implementada; sujeita ao aceite do grupo e confronto com a fonte oficial.

## Procedimento para desbloqueio e aceite

1. Obter a especificação oficial com fonte, versão e data identificadas.
2. Transcrever fielmente IDs, títulos, prioridades e critérios oficiais, em seção separada do catálogo local.
3. Mapear histórias oficiais às propostas, componentes, critérios locais e Sprints, registrando coberto/parcial/ausente e justificativa; não presumir equivalência apenas pelo título.
4. Garantir todas as P0 oficiais e registrar a seleção fundamentada de P1/P2; reconciliar divergências com o grupo.
5. Atualizar README, matriz, roadmap e Kanban; validar arquitetura/contrato se o confronto exigir ajuste. Registrar aprovação e evidência antes de declarar cobertura oficial.

## Perfis mencionados no briefing

| Perfil | Necessidade proposta | Histórias relacionadas |
|---|---|---|
| Sistema consumidor | Analisar antes de encaminhar conteúdo e aplicar decisão. | US-001–US-004, US-007–US-009 |
| Analista/revisor | Investigar eventos e registrar revisão preservando trilha. | US-005, US-010–US-011, US-015 |
| Product owner | Controlar risco, comparar versões e acompanhar qualidade. | US-006, US-010, US-014–US-015 |
| ML/curadoria/governança | Competências de apoio ao ciclo de dados/modelos, já previstas no roadmap. | US-012–US-014 |

A [matriz do briefing](13-matriz-rastreabilidade.md) contém o vínculo proposta → componente → documento → Sprint. O [roadmap](12-roadmap.md) preserva os gates e a diferença entre Fase 3 acadêmica e Sprint 1 do Challenge.
