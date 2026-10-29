# Relatório final de auditoria documental — Sprint 1

## Resumo executivo e parecer

**Data da revisão: 29/10/2026. Escopo: double-check documental da proposta PromptShield BR para o Challenge Intelliway/FIAP.**

**Conformidade documental integral: 82,5% — 33 de 40 requisitos auditados.** Há três requisitos parcialmente atendidos e quatro bloqueados por ausência da especificação oficial das User Stories. Não restou requisito classificado como não atendido sem evidência após as correções; isso não elimina os bloqueios nem comprova cobertura oficial.

**Parecer: documentação tecnicamente consistente para revisão acadêmica, com prontidão condicionada. Ainda não está pronta para submissão.** A ausência de histórias oficiais impede demonstrar P0, fundamentar P1/P2 e rastrear critérios à arquitetura e às próximas Sprints. Também faltam identificação acadêmica e alocação nominal pelo grupo. A fonte pública candidata exige esclarecimento de licença antes de uso.

A banca aqui é uma perspectiva analítica multidisciplinar, não uma avaliação oficial da FIAP ou manifestação de professores identificados. Não se atribui nota acadêmica ou certificação de conformidade jurídica.

## Fonte de verdade, inventário e limites

O [BRIEFING.md](../BRIEFING.md) fornecido no repositório é a fonte principal, em especial §§2–5. Ele foi lido integralmente; não se afirma autenticação contra o Portal do Aluno. Foram lidos integralmente README e os 17 documentos de `docs/`, além das orientações locais e da configuração de editor. A pasta `entrega/` não existia no início desta auditoria; os dois relatórios atuais foram criados nesta execução.

Não há `AGENTS.md` físico nos diretórios aplicáveis verificados; foram consideradas as instruções fornecidas na conversa, com prevalência da instrução atual de PT-BR e correções documentais autorizadas. Não foi encontrada especificação oficial de histórias em qualquer arquivo do inventário; `docs/requisitos/` está ausente. Não se pesquisou conteúdo privado da turma sem fonte disponível.

Materiais de apresentação e arquivo de submissão estão **integralmente fora da avaliação, da contagem e do parecer desta auditoria**, conforme o recorte solicitado. A leitura do briefing não os torna itens auditados. Privacidade/acesso do repositório permanecem dependências administrativas não verificadas, fora do percentual documental. IoT/MQTT é opcional no briefing e também não integra o denominador. Não se exige implementação, corpus coletado, métricas medidas, OpenAPI executável, Docker ou frontend funcional nesta Sprint.

## Método de contagem e criticidade

Os IDs **R01–R40 são itens desta auditoria**, não IDs de User Stories oficiais. Cada linha representa uma unidade documental verificável extraída do briefing; assuntos repetidos entre disciplinas são consolidados. A revisão do README e os testes cruzados não adicionam pontos duplicados ao denominador. Kanban e Projects apoiam R36/R37; não são requisitos extras de ferramenta obrigatória.

- **Atendido:** planejamento exigido presente, coerente e evidenciado no nível de proposta da Sprint 1.
- **Parcial:** existe planejamento, mas falta parte da informação documental necessária.
- **Bloqueado:** cobertura não pode ser determinada sem fonte oficial ou insumo externo essencial; não é considerado atendido.
- **Não atendido:** requisito avaliável sem evidência suficiente e sem bloqueio externo identificado.

Criticidade **Crítica** impede declarar cobertura oficial ou altera restrição central do Challenge; **Alta** afeta qualidade, rastreabilidade ou viabilidade; **Média** afeta apresentação/clareza. Criticidade não é prioridade oficial P0/P1/P2 e não multiplica os pesos: todas as 40 linhas têm peso 1.

| Estado final | IDs | Contagem | Cálculo | Percentual |
|---|---|---|---|---|
| Atendido | R01–R03, R09–R35, R37, R39–R40 | 33 | 33 ÷ 40 × 100 | 82,5% |
| Parcial | R08, R36, R38 | 3 | 3 ÷ 40 × 100 | 7,5% |
| Bloqueado | R04–R07 | 4 | 4 ÷ 40 × 100 | 10,0% |
| Não atendido | Nenhum | 0 | 0 ÷ 40 × 100 | 0,0% |
| Total | R01–R40 | 40 | 40 ÷ 40 × 100 | 100,0% |

O percentual é **posterior às correções desta execução**. Não concede meio ponto a itens parciais e não remove bloqueados do denominador. Não equivale ao percentual de P0 atendidas: a quantidade de histórias oficiais é desconhecida. Ao receber a especificação, reabrir o escopo e revisar a matriz, sem preservar artificialmente o percentual atual.

## Matriz de conformidade

| ID | Requisito documental | Origem no briefing | Evidência por arquivo/seção | Status | Criticidade | Ação corretiva ou condição |
|---|---|---|---|---|---|---|
| R01 | Problema de negócio e objetivo em PT-BR | §§2–3; §5, Descrição do Problema | [README — Problema de negócio](../README.md#problema-de-negócio-e-objetivos-da-plataforma); [01 — Problema e justificativa](../docs/01-visao-geral.md#problema-e-justificativa) | Atendido | Alta | Nenhuma correção pendente no nível de proposta. |
| R02 | Distinguir prompt injection direta e indireta | §3, compreensão do problema | [README — Problema de negócio](../README.md#problema-de-negócio-e-objetivos-da-plataforma); [02 — Conceitos](../docs/02-modelo-de-ameacas.md#conceitos) | Atendido | Alta | Definições explícitas; não tratar palavra isolada como ataque. |
| R03 | Ativos, atores e perfis consumidor/analista/product owner | §3, compreensão; §5, perfis | [01 — Público-alvo](../docs/01-visao-geral.md#público-alvo); [02 — Ativos, atores e fronteiras](../docs/02-modelo-de-ameacas.md#ativos-atores-e-fronteiras); README, tabela de perfis | Atendido | Alta | Perfis planejados; vinculação a histórias avaliada em R07. |
| R04 | Inventário fiel das histórias oficiais, IDs e prioridades | §3, escolha das User Stories; §5, User Stories Selecionadas | [03 — Situação da especificação oficial](../docs/03-user-stories.md#situação-da-especificação-oficial) | Bloqueado | Crítica | Obter especificação oficial e registrar versão/fonte; não inferir IDs. |
| R05 | Cobertura de todas as histórias P0 obrigatórias | §3, escolha das User Stories | [03 — Regra de seleção do escopo](../docs/03-user-stories.md#regra-de-seleção-do-escopo) | Bloqueado | Crítica | Após R04, incluir cada P0 e demonstrar planejamento correspondente. |
| R06 | Seleção fundamentada de P1/P2 | §3; §5, User Stories Selecionadas | [03 — Regra de seleção do escopo](../docs/03-user-stories.md#regra-de-seleção-do-escopo); [12 — Gates](../docs/12-roadmap.md#gates-de-requisitos-e-mvp) | Bloqueado | Crítica | Após R04, comparar valor/esforço/dependências e registrar decisão do grupo. |
| R07 | Critérios e rastreabilidade história → arquitetura → Sprint | §3, arquitetura atende às histórias; §5, seleção e evolução | [03 — Matriz oficial](../docs/03-user-stories.md#matriz-de-rastreabilidade-das-histórias-oficiais); [12 — Gates](../docs/12-roadmap.md#gates-de-requisitos-e-mvp) | Bloqueado | Crítica | Transcrever critérios oficiais e ligar cada história a solução, evidência e Sprint. Estrutura vazia não prova cobertura. |
| R08 | Planejamento de fontes PT-BR, proveniência e licenças | §3, dataset; §5, Dados | [04 — Fontes candidatas](../docs/04-planejamento-dataset.md#fontes-candidatas-e-admissibilidade); README, Dataset PT-BR | Parcial | Alta | Fontes/estratégia existem; esclarecer conflito apache-2.0/cc-by-4.0 e origem antes de confirmar admissibilidade. Não é exigida coleta nesta Sprint. |
| R09 | Exemplos corporativos diretos, indiretos e benignos no README | §4, Simulação de Dados; §5, Dados | [README — Dataset PT-BR](../README.md#dataset-pt-br-e-estratégia-de-classificação); [04 — Taxonomia](../docs/04-planejamento-dataset.md#taxonomia-e-exemplos-ilustrativos) | Atendido | Alta | Exemplos identificados como ilustrativos, sem dados reais. |
| R10 | Hard negatives e revisão contextual planejados | §3, dataset; §4, NLP e geração sintética | [04 — Taxonomia](../docs/04-planejamento-dataset.md#taxonomia-e-exemplos-ilustrativos); [04 — Qualidade](../docs/04-planejamento-dataset.md#qualidade-rotulagem-e-prevenção-de-data-leakage) | Atendido | Alta | Manter citação, treinamento e mensagens corporativas legítimas como cortes futuros. |
| R11 | Geração sintética revisada e identificada | §4, Generative IA & Advanced Net | [04 — Fontes e metadados](../docs/04-planejamento-dataset.md#metadados-mínimos); [14 — Geração sintética](../docs/14-politicas-operacionais.md#geração-sintética-de-ataques) | Atendido | Alta | Plano exige revisão e proveniência; não alega corpus gerado. |
| R12 | Separação treino/validação/teste e prevenção de leakage | §3, dataset; §5, Dados | [04 — Qualidade](../docs/04-planejamento-dataset.md#qualidade-rotulagem-e-prevenção-de-data-leakage); [04 — Compatibilidade](../docs/04-planejamento-dataset.md#compatibilidade-dos-rótulos-com-o-motor) | Atendido | Alta | Split por família antes da tradução, deduplicação, teste congelado e risco de sobreposição com pré-treino/fine-tuning declarados. |
| R13 | Pré-processamento PT-BR justificado | §4, Processamento de Linguagem Natural | [05 — Pipeline textual](../docs/05-plano-nlp-modelos.md#pipeline-textual-proposto) | Atendido | Alta | Unicode, caixa, acentos e chunking definidos sem apagar evidência ou truncar silenciosamente. |
| R14 | Baseline simbólico Regex/regras | §4, Processamento de Linguagem Natural | [05 — Baselines](../docs/05-plano-nlp-modelos.md#baselines-em-progressão) | Atendido | Alta | Comparação proposta, sem implementação exigida nesta Sprint. |
| R15 | Baseline TF-IDF com classificador clássico | §4, Processamento de Linguagem Natural | [05 — Baselines](../docs/05-plano-nlp-modelos.md#baselines-em-progressão); [04 — Compatibilidade](../docs/04-planejamento-dataset.md#compatibilidade-dos-rótulos-com-o-motor) | Atendido | Alta | Classificador linear proposto; IDF/vocabulário ajustados somente no treino. |
| R16 | Transformer e candidato DeBERTa fundamentados | §4, NLP e Generative IA & Advanced Net | [05 — Transformer](../docs/05-plano-nlp-modelos.md#transformer-e-modelo-profundo); [05 — Fundamentação](../docs/05-plano-nlp-modelos.md#fundamentação-e-limites-do-candidato) | Atendido | Alta | Papers primários e card; transferência PT-BR declarada como hipótese. |
| R17 | Estratégia de fine-tuning, incluindo LoRA como opção | §4, plano de modelo profundo | [05 — Fundamentação](../docs/05-plano-nlp-modelos.md#fundamentação-e-limites-do-candidato) | Atendido | Média | LoRA explicada e condicionada a experimento, sem prometer aceleração em CPU. |
| R18 | Planejamento de execução e avaliação em CPU | §4, arquitetura de IA | [05 — CPU](../docs/05-plano-nlp-modelos.md#cpu-limites-e-decisão-de-adoção); [11 — SLOs](../docs/11-metricas-avaliacao.md#slos-e-limites-propostos) | Atendido | Alta | Plano registra orçamento de entrada, memória e medição futura; nenhuma garantia de capacidade. |
| R19 | API sem LLM generativo para classificação | §4, regra do Challenge | [01 — Exclusões](../docs/01-visao-geral.md#exclusões-desta-sprint); [05 — CPU](../docs/05-plano-nlp-modelos.md#cpu-limites-e-decisão-de-adoção); [15 — GD-09](../docs/15-registro-de-decisoes.md#decisões-propostas) | Atendido | Crítica | Motor discriminativo; Generative AI restrita a dados revisados e avaliador futuro do portal. |
| R20 | Cenário RAG simulado para injeção indireta | §4, Generative IA & Advanced Net | [08 — RAG simulado](../docs/08-rpa-ocr-rag.md#rag-simulado) | Atendido | Alta | Documentos sintéticos e chunks analisados antes de contexto; sem integração EvaGPT presumida. |
| R21 | RPA/consumidor automatizado e ingestão texto/e-mail/web | §4, AI for Robotic Process Automation | [08 — Consumidor automatizado](../docs/08-rpa-ocr-rag.md#consumidor-automatizado-proposto) | Atendido | Alta | Origem, consulta prévia e ações seguir/reter/bloquear documentadas. |
| R22 | Fluxo imagem/PDF, pré-processamento e OCR justificado | §4, Visão Computacional | [08 — OCR](../docs/08-rpa-ocr-rag.md#ocr-de-imagens-e-pdfs-digitalizados) | Atendido | Alta | Tesseract/OpenCV planejados; OCR antes da API textual; baixa confiança não vira autorização. |
| R23 | Casos ilustrativos visuais maliciosos e legítimos | §4, Visão Computacional e Simulação de Dados | [08 — OCR, tabela de casos](../docs/08-rpa-ocr-rag.md#ocr-de-imagens-e-pdfs-digitalizados) | Atendido | Média | Cenários descritivos de baixo contraste, rodapé e hard negatives; não comprovam detecção visual. Não se exige protótipo. |
| R24 | Serviço independente e fronteira Intelliway explícita | §2; §3, arquitetura | [06 — Decisão arquitetural](../docs/06-arquitetura-solucao.md#decisão-arquitetural-proposta); README, Contexto | Atendido | Crítica | Sem acesso ou integração com código, banco ou infraestrutura da empresa. |
| R25 | Diagrama consumidor/API/motor/registro/portal e OCR | §4, Arquitetura; §5, desenho simples | [README — Arquitetura](../README.md#arquitetura-proposta); [06 — Decisão arquitetural](../docs/06-arquitetura-solucao.md#decisão-arquitetural-proposta) | Atendido | Alta | Mermaid corresponde às fronteiras; alternativas de modelos e persistência esclarecidas. |
| R26 | Contrato preliminar e exemplos JSON de requisição/resposta | §4, Arquitetura e Contrato; §5, Contrato da API | [README — Exemplos](../README.md#exemplos-documentais-da-api); [07 — POST](../docs/07-contrato-api.md#post-v1analyze) | Atendido | Alta | JSON ilustrativo e consistente, sem comandos de execução fictícios. |
| R27 | Campos, origem e source_type padronizados | §4, RPA e contrato JSON | [07 — POST](../docs/07-contrato-api.md#post-v1analyze); [04 — Compatibilidade](../docs/04-planejamento-dataset.md#compatibilidade-dos-rótulos-com-o-motor); [08 — Consumidor](../docs/08-rpa-ocr-rag.md#consumidor-automatizado-proposto) | Atendido | Alta | Sete origens canônicas; campos de linhagem e anotação não confundidos com decisão. |
| R28 | Separação classificação/score/ALLOW-REVIEW-BLOCK | §2; §4, contrato da API | [06 — Política](../docs/06-arquitetura-solucao.md#política-de-decisão); [07 — Semântica](../docs/07-contrato-api.md#semântica-de-score-e-decisão) | Atendido | Alta | Escala e intervalos explícitos sem valores inventados; erros não fabricam decisão. |
| R29 | Wireframes e fluxo administrativo | §4, Front End & Mobile Development; §5, Wireframes | [09 — Login](../docs/09-wireframes-portal.md#login); [09 — Correspondência](../docs/09-wireframes-portal.md#correspondência-com-contrato-e-estados-da-interface) | Atendido | Alta | Login OIDC, dashboard, histórico, detalhe e revisão; vínculo a rotas e estados vazios explícito. |
| R30 | Privacidade, LGPD e papéis institucionais sem presunção | §3, riscos; §4, Governança | [10 — Escopo](../docs/10-governanca.md#escopo-e-status-normativo); [10 — Papéis](../docs/10-governanca.md#papéis-e-bases-legais-candidatas) | Atendido | Alta | Proposta e dependências explícitas; sem parecer jurídico ou base legal atribuída. |
| R31 | Retenção, acesso, incidentes e uso indevido | §3, riscos; §4, Governança | [14 — Retenção](../docs/14-politicas-operacionais.md#política-de-retenção-proposta); [15 — Riscos](../docs/15-registro-de-decisoes.md#matriz-de-riscos-proposta) | Atendido | Alta | Texto não persistido por padrão; revisão com acesso excepcional e prazos propostos. |
| R32 | Governança de dados sintéticos e licenças | §4, Governança e Simulação de Dados | [10 — Governança de modelo](../docs/10-governanca.md#governança-do-modelo-e-dados); [14 — Geração sintética](../docs/14-politicas-operacionais.md#geração-sintética-de-ataques) | Atendido | Alta | Gate de aprovação documentado; admissibilidade concreta da fonte está separada em R08. |
| R33 | Métricas precision/recall/F1/AUC e método sem resultados fictícios | §4, Governança; §5, Estratégia do motor | [11 — Métricas](../docs/11-metricas-avaliacao.md#métricas-de-qualidade-do-detector); [11 — Separação](../docs/11-metricas-avaliacao.md#separação-entre-avaliação-do-motor-e-da-política) | Atendido | Alta | Classe positiva, denominadores, REVIEW, teste congelado e viés de revisão explicitados. |
| R34 | Versionamento de modelo, dataset, política e revisão | §4, Governança e contrato | [10 — Governança de modelo](../docs/10-governanca.md#governança-do-modelo-e-dados); [15 — Registro de REVIEW](../docs/15-registro-de-decisoes.md#registro-de-review-e-rótulos) | Atendido | Alta | Revisão aditiva, versões e rollback planejados. |
| R35 | Roadmap com etapas e dependências | §3, evolução; §5, Próximas Etapas | [12 — Roadmap](../docs/12-roadmap.md#status-e-premissas-de-planejamento); [12 — Gates](../docs/12-roadmap.md#gates-de-requisitos-e-mvp) | Atendido | Alta | Sequência 1–6 proposta; sem prazos contratuais ou histórias inferidas. |
| R36 | Planejamento de atividades e responsabilidades dos integrantes | §5, Planejamento das Próximas Etapas | [12 — Responsabilidades](../docs/12-roadmap.md#responsabilidades-por-competência); [16 — Backlog](../docs/16-kanban-sprint1.md#backlog) | Parcial | Alta | Competências/tarefas existem; grupo precisa fornecer integrantes e alocação nominal. Não inferir do Git. |
| R37 | README navegável e índice complementar | §5, README Organizado | [README — Índice](../README.md#índice-da-documentação); [16 — Kanban](../docs/16-kanban-sprint1.md) | Atendido | Média | Links para todos os documentos e relatórios; Kanban e Projects são organização adicional, não requisito de ferramenta obrigatório. |
| R38 | Adequação verificável ao template oficial FIAP | §5.1, modelo oficial | [README — Identificação acadêmica](../README.md#identificação-acadêmica-e-adequação-ao-template); seção Comparação com o template deste relatório | Parcial | Alta | Estrutura compatível com dispensa de pastas sem uso; faltam nome do grupo, integrantes, tutor/turma e decisão acadêmica aplicável. |
| R39 | Clareza, justificativas e referências técnicas rastreáveis | §4, Documentação Técnica | [05 — Fundamentação](../docs/05-plano-nlp-modelos.md#fundamentação-e-limites-do-candidato); [15 — ADRs](../docs/15-registro-de-decisoes.md#adrs--decisões-arquiteturais-propostas); README, Referências | Atendido | Média | Referências consultadas e limitações registradas; fonte disponível não comprova desempenho ou licença. |
| R40 | Escopo documental e ausência de implementação alegada | §5.1, foco em planejamento, sem código exigido | README, abertura; [01 — Exclusões](../docs/01-visao-geral.md#exclusões-desta-sprint); [16 — Escopo](../docs/16-kanban-sprint1.md#escopo-e-interpretação) | Atendido | Alta | Sem software/protótipo; distinguir produção, aceite e execução. |


## Double-check de consistência técnica

| Verificação | Resultado final e evidência |
|---|---|
| Diagramas × texto | README e 06 representam consumidor, OCR anterior à API, motor, política, registro, banco e portal. A legenda esclarece alternativas de modelos e dependência de persistência, sem cascata presumida. |
| Endpoints × JSON | `POST /v1/analyze` recebe texto; exemplos do README reproduzem 07. Rotas administrativas correspondem ao mapa de telas em 09. Health público reduzido a status. |
| Campos | `content`, `source_type`, `risk_score`, `score_type`, `classification`, `decision` e versões coerentes. Campo de linhagem do dataset não é apresentado como endpoint implementado. |
| source_type | Vocabulário único em 04, 07, 08 e README: `user_text`, `email`, `web_page`, `document`, `rag_chunk`, `image_ocr`, `pdf_ocr`. |
| Classes × score × decisão | 04 mapeia subtipos humanos para a tarefa binária; 05 mapeia LEGIT/INJECTION; 06–07 definem escala, intervalos e política; 11 separa matriz binária de tabela de decisões. |
| Generative AI | Restrita a preparação de dados revisados e avaliador futuro do portal. Nenhum caminho de decisão da API depende de LLM generativo. |
| Data leakage | Split por cenário/família antes da tradução, TF-IDF ajustado no treino, teste congelado e possível sobreposição com fine-tuning prévio declarados. É estratégia, não prevenção já demonstrada em corpus. |
| Hard negatives | 04 e README incluem citação, treinamento e mensagens legítimas; 08 acrescenta casos visuais descritivos. |
| Métricas | 11 distingue metas/resultados, conjunto rotulado, denominadores, REVIEW e viés de revisão. Nenhuma performance do fornecedor foi transferida ao projeto. |
| Modelo e CPU | 05 fundamenta Transformer/DeBERTa/LoRA, corrige idiomas da card, declara limites de tokens e necessidade de benchmark de CPU. |
| Governança × arquitetura | 10/14/15 preveem minimização, exceções de conteúdo, RBAC, curadoria e rollback; 09 não oferece conteúdo bruto por padrão ou login local contraditório. |
| Funções do portal | Cinco telas exigidas e navegação presentes; 09 liga telas às rotas, versões e estados vazios/erro. Não se exige protótipo. |
| Roadmap × dependências | 12 condiciona Sprints futuras a dados, requisitos, contrato e decisões institucionais. Responsáveis por competência existem; nomes permanecem parciais. |
| Cobertura P0 | Não verificável: especificação ausente. Nenhum critério oficial é inferido a partir de propostas de capacidade. |

## Inconsistências encontradas e corrigidas

| ID | Achado anterior | Correção e arquivos |
|---|---|---|
| C01 | README e parte do planejamento em English, contrariando a instrução atual. | Tradução para PT-BR de README, 12, 16 e 17; trechos residuais de 13; orientação local atualizada. Estruturas/IDs preservados, sem nova arquitetura. |
| C02 | README apenas encaminhava ao contrato; não continha JSON nem os três perfis em tabela. | Incluídos exemplos idênticos a 07, definições direta/indireta e perfis existentes em 01/03. |
| C03 | 01 confundia classificar conteúdo com decisão ternária. | Objetivo reformulado para detecção seguida de política de decisão. |
| C04 | Dataset com subtipos, motor binário e wireframes com rótulos sem mapeamento explícito. | 04/05/07/09 explicam agregação, LEGIT/INJECTION, uncertain e revisão. |
| C05 | Score calibrado sem esclarecer escala; limites inclusivos dos thresholds indefinidos. | 06/07/README mantêm 0–100, explicitam fator 100 e intervalos simbólicos, sem thresholds numéricos aprovados. |
| C06 | Health dizia somente liveness, mas exemplo expunha service_version. | 07 mantém apenas status; não há API executada. |
| C07 | OCR falho podia aparentar decisão válida da API mesmo sem texto. | 06/08/14 distinguem revisão prévia no consumidor, erro sem decisão e classificação textual válida. |
| C08 | Login sugeria senha local, contrário à proposta OIDC. | 09 usa redirecionamento ao IdP/MFA e registra dependência institucional; sem novo endpoint de senha. |
| C09 | Fluxo de ingestão omitia linha explícita user_text; diagrama sugeria cascata de três modelos. | Linha direta em 08; alternativas de modelos e relação registro/resposta esclarecidas em 06 e README. |
| C10 | Matriz de confusão “por decisão” misturava classificação binária com REVIEW; risco de avaliar apenas itens revisados. | 11 separa avaliação do motor/política, cobertura, denominadores e viés de seleção. |
| C11 | Plano dizia não haver meta de latência, embora 11 trouxesse metas preliminares; língua do modelo descrita de modo impreciso. | 05 distingue meta de medição; 05/06/README refletem inglês/alemão da card e ausência de prova PT-BR. |
| C12 | LoRA/DeBERTa sem referências primárias específicas e pouco detalhe de CPU. | 05/README vinculam papers e configuração, distinguindo custo de treino/inferência e limitações. |
| C13 | Licença do dataset mencionada de modo incompleto. | 04/README registram metadados divergentes da card; admissibilidade continua pendência externa, sem decidir licença. |
| C14 | Risco de leakage com dados usados no fine-tuning do candidato e ajuste de IDF não explicitado. | 04/11 distinguem treino/validação/teste e requerem linhagem e avaliação futura independente. |
| C15 | GD-08 dizia promover “após regressão”. | 15 corrige para avaliação de não regressão. |
| C16 | Matriz/roadmap confundiam plano concluído com validação futura e traziam fragmentos em English. | 12/13/16 harmonizam status; revisão do grupo e responsabilidades continuam abertas. |
| C17 | Adequação ao template não havia sido comparada; fonte LGPD era cópia intermediária. | Comparação verificável registrada abaixo; referência legal em 10/README aponta ao texto oficial. |
| C18 | Auditoria sem diretório próprio e sem navegação no README. | Criados os dois relatórios em entrega/ e incluídos seus links no README e planejamento. |

A nova verificação de links e anchors após as alterações está registrada em “Verificações finais”. Referências externas com páginas acessíveis foram mantidas; disponibilidade não é garantia permanente ou validação de licenças.

## Comparação com o template

Foi consultado o [README do Enterprise Challenge](https://github.com/CaiqueFiap-2026/TEMPLATE-TIAO-2026/blob/main/1TIAO/ENTERPRISE%20CHALLENGE/README.md) e a árvore do [template oficial](https://github.com/CaiqueFiap-2026/TEMPLATE-TIAO-2026/tree/main), em leitura pública. A consulta de `main` retornou o SHA `53ced5ec91571e06398e0ac9c90e58cb78ed4c02`; esse identificador fixa a referência de comparação, sem copiar o template inteiro.

A árvore apresenta 1TIAO/2TIAO e Enterprise Challenge. O próprio README permite usar somente pastas pertinentes. Portanto, a organização atual de documentos não exige criação artificial de src/data nem migração para um ano/turma presumido. README de projeto, descrição, estrutura, links e decisões estão presentes. Faltam identificação do grupo/integrantes, confirmação do tutor/turma e decisão acadêmica aplicável sobre participação. Não se copia nome de professor ou link de integrante do template como se pertencesse ao grupo.

A seção genérica de execução do template é não aplicável à Sprint documental, conforme o briefing. Não se inventam comandos, releases ou licença do projeto a partir da licença do template. R38 permanece parcial pela identificação e adequação final pendentes, não por ausência de código ou pastas vazias.

## Qualidade técnica e acadêmica

| Perspectiva | Avaliação fundamentada | Limite ou recomendação |
|---|---|---|
| IA/ML | Progressão Regex → TF-IDF → encoder e avaliação sob dados comuns adequadas à Sprint de planejamento; 04/05/11. | Realizar experimentos somente nas próximas Sprints, após gates de dados. |
| NLP/Transformers | Normalização conservadora, hard negatives e transferência linguística reconhecidos; 04/05. | Confirmar tokenizer, adaptação e orçamento de CPU, sem presumir qualidade PT-BR. |
| Arquitetura | Serviço independente, fronteiras HTTP/OCR, segregação e falha segura coerentes; 06/07/08. | Estabilizar detalhes do contrato e IdP antes da implementação, sem transformá-los em lacunas de protótipo nesta Sprint. |
| Segurança de LLMs | Ameaças diretas/indiretas e defesa em camadas explícitas; 02/06/14. | Testar evasão e abuso futuramente; nenhum detector confere imunidade ao agente. |
| Produto/Requisitos | Problema, valor e perfis claros; 01/03/12. | Bloqueio crítico de histórias impede comprovar MVP oficial; completar R04–R07. |
| UX | Wireframes estáticos cobrem telas solicitadas e revisão humana; 09. | Validar linguagem, navegação e estados com usuários depois; não alegar pesquisa de UX feita. |
| Governança | Proposta diferencia obrigação aplicável, boa prática e decisão institucional; 10/14/15. | Esclarecer licença, registrar responsáveis e obter decisões antes de dados reais/operação. |

Clareza e organização melhoraram com PT-BR uniforme, exemplos locais e índice. As disciplinas conectam ingestão/OCR a NLP, política, portal e governança. A viabilidade permanece hipótese técnica bem delimitada, não resultado experimental. ADRs apresentam alternativas e consequências sem impor novas decisões. As ressalvas são apropriadas ao planejamento; não substituem histórias oficiais ou nomes ainda desconhecidos.

## Pendências críticas, não críticas e recomendações

**Críticas documentais:** R04–R07, todas originadas na falta da especificação oficial. Obter a fonte, inventariar histórias, comprovar cobertura de P0, decidir P1/P2 e preencher critérios/rastreabilidade por Sprint.

**Altas, ainda documentais:** R36/R38, identificação acadêmica e alocação de integrantes; fonte é o grupo/tutoria, sem inferência de nomes. S1-14/S1-15 seguem abertos.

**Alta antes de uso dos dados:** R08, esclarecer licenças/proveniência do dataset candidato ou registrar decisão fundamentada do grupo por outra fonte com termos verificados. A estratégia geral continua documentada; nenhum download de corpus ou uso em treino foi realizado.

**Dependências futuras, sem nova exigência acadêmica:** IdP, infraestrutura, revisão humana disponível, capacidade de CPU, thresholds, retenção e papéis institucionais. Aprovações de produção não são condição inventada para entregar uma proposta; precisam apenas continuar explícitas como dependências. Planejar essas decisões nas Sprints futuras.

Recomendações: resolver primeiro R04–R07; completar identificação/responsabilidades; resolver R08 antes de ingestão; manter cada alteração futura ligada à fonte, arquivo e critério oficial. Não alterar arquitetura por conveniência durante o preenchimento de histórias sem revisão do grupo. Detalhes e condições de desbloqueio estão em [pendencias-externas.md](pendencias-externas.md).

## Referências e rastreabilidade das consultas

Consultas públicas realizadas em 29/10/2026. Nenhuma consulta externa substituiu o briefing ou forneceu histórias oficiais.

| Fonte | Verificação e uso |
|---|---|
| [OWASP LLM01:2025](https://genai.owasp.org/llmrisk/llm01-prompt-injection/) e [glossário](https://genai.owasp.org/glossary/prompt-injection/) | Conceitos de ameaça e defesa em camadas em 01/02/10; páginas acessíveis. |
| [Attention Is All You Need](https://arxiv.org/abs/1706.03762) | Fundamentação da atenção/Transformer em 05; resumo primário consultado, sem transportar benchmarks. |
| [DeBERTa](https://arxiv.org/abs/2006.03654) e [DeBERTaV3](https://arxiv.org/abs/2111.09543) | Fundamentação das variantes em 05; resumos consultados, sem evidência de desempenho deste projeto. |
| [LoRA](https://arxiv.org/abs/2106.09685) | Técnica de adaptação em 05; resumo primário, sem prometer benefício de inferência local. |
| [Model card](https://huggingface.co/deepset/deberta-v3-base-injection/raw/main/README.md) e [configuração](https://huggingface.co/deepset/deberta-v3-base-injection/raw/main/config.json) | Idiomas en/de, modelo binário, mapeamento LEGIT/INJECTION e limite posicional; não prova PT-BR. |
| [Dataset card](https://huggingface.co/datasets/deepset/prompt-injections/raw/main/README.md) | Detectada divergência de metadados apache-2.0/cc-by-4.0; termos/proveniência seguem não resolvidos. |
| [Unicode UAX #15](https://www.unicode.org/reports/tr15/) | Normalização em 05; fonte normativa acessível. |
| [FastAPI — Security](https://fastapi.tiangolo.com/tutorial/security/) e [Containers](https://fastapi.tiangolo.com/deployment/docker/) | Referências de arquitetura acessíveis; não comprovam implementação. |
| [OWASP API2:2023](https://api-security.owasp.org/editions/2023/en/0xa2-broken-authentication/) e [API Top 10](https://devguide.owasp.org/en/07-training-education/07-api-top-ten/) | Segregação de clientes/pessoas e controles de recursos em 06; recomendações existentes coerentes. |
| [Tesseract](https://tesseract-ocr.github.io/tessdoc/) | Ferramenta OCR e licença declarada na documentação; não valida eficácia em texto oculto. |
| [LGPD — Planalto](https://www.planalto.gov.br/ccivil_03/_ato2015-2018/2018/lei/l13709.htm) | Texto oficial substitui referência intermediária em 10; auditoria não constitui revisão jurídica artigo por artigo. |
| [ANPD — agentes de tratamento](https://www.gov.br/anpd/pt-br/centrais-de-conteudo/materiais-educativos-e-publicacoes/guia-orientativo-para-definicoes-dos-agentes-de-tratamento-de-dados-pessoais-e-do-encarregado), [guia de segurança](https://www.gov.br/anpd/pt-br/centrais-de-conteudo/materiais-educativos-e-publicacoes/guia-vf.pdf) e [incidentes](https://www.gov.br/anpd/pt-br/canais_atendimento/agente-de-tratamento/comunicado-de-incidente-de-seguranca-cis) | Páginas oficiais acessíveis. Os dois guias são apresentados por páginas de acesso/download; não se alega revisão integral dos PDFs nesta auditoria. |
| [Template Enterprise Challenge](https://github.com/CaiqueFiap-2026/TEMPLATE-TIAO-2026/blob/main/1TIAO/ENTERPRISE%20CHALLENGE/README.md) | Conteúdo e árvore consultados pelo conector GitHub somente de leitura. |

## Arquivos alterados e preservação

Adequação de idioma e navegação: README, docs/12, docs/13, docs/16 e docs/17. Correções técnicas pontuais: docs/01, docs/04–docs/11, docs/14 e docs/15. Orientação local de idioma: .Codex/napkin.md. Novos arquivos: este relatório e pendencias-externas.md. Documentos 02/03, briefing e configuração de editor foram preservados.

Não houve implementação, protótipo, geração de corpus, instalação de dependências, commit, push, troca de conta, alteração de configuração Git, remote, permissões ou colaboradores.

## Verificações finais

Verificação documental executada após as correções:

- 22 arquivos Markdown conferidos; 156 links locais, incluindo 70 referências a seções, resolvidos sem erro.
- Cinco blocos JSON válidos; requisição e resposta do README iguais às do contrato.
- 40 IDs de requisito únicos, com 33 atendidos, três parciais e quatro bloqueados; percentuais recalculados a partir das linhas.
- 23 IDs de tarefa únicos no Kanban; índice cobre os 17 documentos e os dois relatórios.
- Briefing, documentos 02/03 e configuração de editor preservados por comparação de hashes; nenhum arquivo anterior removido.
- Configuração, HEAD, refs e demais arquivos de controle Git preservados. A comparação ampla de .git observou apenas acréscimo de objetos internos do tipo blob, sem mudança de refs/index ou objetos commit novos; a origem desses blobs não foi determinada pela auditoria. Não se afirma igualdade integral da pasta .git.
- Nenhuma private key ou token GitHub/AWS reconhecível pelos padrões verificados encontrado nos arquivos; essa inspeção não é garantia de ausência absoluta de segredos.

Foram alterados 17 arquivos existentes: `.Codex/napkin.md`, `README.md`, `docs/01-visao-geral.md`, `docs/04-planejamento-dataset.md`, `docs/05-plano-nlp-modelos.md`, `docs/06-arquitetura-solucao.md`, `docs/07-contrato-api.md`, `docs/08-rpa-ocr-rag.md`, `docs/09-wireframes-portal.md`, `docs/10-governanca.md`, `docs/11-metricas-avaliacao.md`, `docs/12-roadmap.md`, `docs/13-matriz-rastreabilidade.md`, `docs/14-politicas-operacionais.md`, `docs/15-registro-de-decisoes.md`, `docs/16-kanban-sprint1.md` e `docs/17-plano-github-projects.md`. Dois relatórios foram criados em `entrega/`.

A sintaxe e as relações dos diagramas Mermaid foram inspecionadas no texto; não se declara validação visual em renderer externo. Não foram escritos testes de software ou executada uma aplicação: os checks são de documentos e exemplos.

## Conclusão de prontidão

O conjunto cobre a maior parte da proposta técnica esperada para a Sprint 1, com limites e hipóteses explícitos. **Não recebe o status “DOCUMENTAÇÃO PRONTA PARA SUBMISSÃO”**: R04–R07 permanecem bloqueados; R08/R36/R38 ainda estão parciais. Resolver essas pendências e repetir o double-check antes de afirmar cobertura oficial. O parecer se restringe à documentação técnica e acadêmica incluída nesta auditoria.
