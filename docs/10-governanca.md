# Governança, privacidade e ciclo de vida do modelo

## Escopo e status normativo

Este documento é uma **proposta de governança para planejamento**. Não constitui parecer jurídico, política aprovada, definição de base legal nem comprovação de conformidade. A LGPD atribui direitos aos titulares e obrigações aos agentes de tratamento; controlador, operador, encarregado, finalidade detalhada e hipótese legal devem ser definidos institucionalmente antes de qualquer operação real ([LGPD, arts. 17, 18 e 46](https://www.planalto.gov.br/ccivil_03/_ato2015-2018/2018/lei/l13709.htm)).

| Tipo de enunciado | Significado neste projeto |
|---|---|
| **Obrigação legal aplicável** | Dever que pode incidir se houver tratamento de dados pessoais, sujeito à análise do controlador e do jurídico. |
| **Boa prática técnica proposta** | Controle recomendado para reduzir risco; não é apresentado como obrigação legal autônoma. |
| **Aprovação institucional necessária** | Tema que não pode ser decidido pelo grupo: papéis, base legal, prazo, ferramenta, contrato e resposta a incidente. |

## Categorias de dados, finalidade e necessidade

| Categoria | Exemplos possíveis | Finalidade estritamente proposta | Necessidade e tratamento |
|---|---|---|---|
| Conteúdo analisado | Corpo de e-mail, documento, página, chunk RAG, texto de OCR. | Classificar risco de prompt injection. | Pode conter dado pessoal; processar somente o necessário e não registrar por padrão. |
| Dados pessoais comuns | Nome, e-mail, cargo, identificador de chamado, endereço eventualmente presente no conteúdo. | Contexto técnico mínimo e atendimento de solicitação, quando necessário. | Aplicar minimização, pseudonimização de `source_id` e acesso restrito. |
| Dados pessoais sensíveis | Saúde, biometria, origem racial, opinião política, religião, filiação, vida sexual ou dado genético, se incluídos pela fonte. | Não são necessários ao objetivo do detector. | Não coletar deliberadamente; se incidentais, conter e submeter à avaliação do DPO/jurídico. |
| Metadados operacionais | `source_type`, tamanho, hash, horário, `analysis_id`, versão do modelo/política. | Auditoria, métricas e diagnóstico. | Preferir metadados agregados ou pseudonimizados; evitar URL completa, assunto e identificadores diretos. |
| Score e decisão | `risk_score`, `score_type`, `decision`, `reason_codes`. | Aplicar política e acompanhar desempenho. | Não são dados pessoais por si, mas podem tornar-se associados a alguém via metadados. |
| Feedback humano | Rótulo, justificativa, revisor pseudonimizado e data. | Contestação, melhoria e governança. | Restringir acesso; não incluir texto bruto sem curadoria. |
| Dados de treinamento | Exemplos públicos licenciados, próprios ou sintéticos revisados. | Treinar/avaliar classificador futuro. | Proibir dados reais de clientes nesta Sprint; aprovar origem, licença e uso antes da inclusão. |

## Papéis e bases legais candidatas

O papel de cada agente não decorre do nome do produto. A ANPD mantém guia específico para definir agentes de tratamento e encarregado ([guia orientativo](https://www.gov.br/anpd/pt-br/centrais-de-conteudo/materiais-educativos-e-publicacoes/guia-orientativo-para-definicoes-dos-agentes-de-tratamento-de-dados-pessoais-e-do-encarregado)).

| Tema | Proposta para análise | Estado |
|---|---|---|
| Controlador | Organização que define finalidade e meios essenciais. | **A confirmar institucionalmente.** |
| Operador | Prestador que trata em nome e conforme instruções do controlador. | **A confirmar institucionalmente.** |
| Encarregado/DPO | Canal entre controlador, titulares e ANPD, quando aplicável. | **A confirmar institucionalmente.** |
| Consentimento | Candidato em fluxo voluntário específico; não presumir que serve para todo uso. | Depende de validação jurídica. |
| Execução de contrato | Candidato quando indispensável ao serviço contratado. | Depende de finalidade e relação contratual reais. |
| Legítimo interesse | Pode ser avaliado para segurança, com necessidade, balanceamento e transparência. | Não usar sem avaliação formal. |
| Obrigação legal/regulatória | Pode aplicar-se a retenção ou comunicação exigida por norma específica. | Não foi identificada obrigação específica para este Challenge. |

Para dados pessoais sensíveis, hipóteses adicionais e mais restritas podem ser exigidas; nenhuma base será inferida. Detectar prompt injection não autoriza reutilizar conteúdo para treino, vigilância de pessoas ou análise comportamental incompatível.

## Direitos dos titulares e processo proposto

O art. 18 contempla confirmação, acesso, correção, anonimização/bloqueio/eliminação, portabilidade quando aplicável, informação sobre compartilhamento e revogação de consentimento. O processo abaixo requer aprovação do controlador:

1. Receber solicitação em canal definido pelo encarregado.
2. Validar identidade proporcionalmente, sem coletar dados excessivos.
3. Localizar registros por identificador pseudonimizado e retenção, evitando busca ampla de conteúdo.
4. Classificar pedido, consultar DPO/jurídico diante de exceção legal ou conflito com segurança/auditoria.
5. Responder no prazo aplicável e registrar a evidência mínima de atendimento, correção, bloqueio ou descarte autorizado.

## Segurança de armazenamento e transmissão

| Controle | Classificação | Proposta |
|---|---|---|
| Criptografia em trânsito | Boa prática técnica. | TLS atualizado entre consumidor, API, portal e serviços internos. |
| Criptografia em repouso | Boa prática técnica. | Criptografar conteúdo excepcional, backups e eventos; gerir chaves fora do código. |
| Separação de dados | Boa prática técnica. | Separar conteúdo bruto, evento, telemetria e dataset; impedir texto em logs técnicos. |
| Controle de acesso | Boa prática técnica. | RBAC, menor privilégio, MFA para usuários privilegiados e auditoria de acesso. |
| Segurança de dados pessoais | Obrigação legal aplicável. | Adotar medidas técnicas e administrativas adequadas ao risco, nos termos do art. 46, sujeitas à avaliação institucional. |
| Comunicação de incidente | Obrigação legal condicionada. | O controlador avalia incidente confirmado com dado pessoal e risco/dano relevante; comunicação segue regulamentação aplicável ([ANPD](https://www.gov.br/anpd/pt-br/canais_atendimento/agente-de-tratamento/comunicado-de-incidente-de-seguranca-cis)). |

## Governança do modelo e dados

| Artefato | Registro mínimo proposto | Controle de mudança |
|---|---|---|
| Classificador | `model_version`, arquitetura, parâmetros, data, responsável, dataset e relatório de avaliação. | Aprovação humana antes de promoção; rollback para versão anterior aprovada. |
| Dataset | `dataset_version`, fontes/licenças, hashes, split, curadoria e revisores pseudonimizados. | Inclusão somente após aprovação; não misturar dados operacionais sem autorização. |
| Política de decisão | `policy_version`, limiares, regras, justificativa e vigência. | Mudança registrada e avaliada separadamente do modelo. |
| Normalização/OCR | Versão de pipeline, configuração e impacto esperado. | Comparar regressões antes de adoção. |
| REVIEW | `analysis_id`, saída original, rótulo humano, justificativa, revisor, data e curadoria. | Não sobrescrever decisão do modelo; criar evento adicional imutável. |

### Atualização, regressão e rollback

1. Propor mudança com hipótese, impacto, versão e plano de rollback.
2. Validar licença/proveniência e aprovar dados de treinamento.
3. Avaliar candidata contra baseline e teste congelado por `source_type`, hard negatives, FP/FN e latência.
4. Registrar decisão humana de promover, rejeitar ou adiar.
5. Monitorar a versão; diante de regressão, incidente ou desvio de política, suspender e restaurar a última versão aprovada com trilha de auditoria.

Precision, recall, F1, taxa de falsos positivos e `REVIEW rate` são métricas propostas, não resultados existentes. Monitorar falsos positivos é prioritário porque bloqueios injustificados interrompem fluxos legítimos.

## Relação com segurança de LLMs

A OWASP destaca que injeção indireta chega por fontes externas e que privilégio mínimo, separação de conteúdo não confiável e aprovação humana para ações críticas reduzem impacto ([OWASP LLM01:2025](https://genai.owasp.org/llmrisk/llm01-prompt-injection/)). O detector é uma camada de sinalização: não autoriza acesso a dados, não substitui validação de saída e não torna um agente imune a ataques.

As políticas detalhadas estão em [14-politicas-operacionais.md](14-politicas-operacionais.md); decisões, pendências e riscos em [15-registro-de-decisoes.md](15-registro-de-decisoes.md).
