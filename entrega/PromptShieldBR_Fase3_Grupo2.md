# PromptShield BR - Fase 3

Challenge Intelliway | Detecção de Prompt Injection em PT-BR

**Etapa do projeto:** Sprint 1 - Proposta técnica documentada

**Grupo:** Grupo 2

**Integrantes e respectivos RMs:**

- Cláudio Sartori - RM 567194

- Douglas Rafael do Amaral - RM 566740

- Pedro Alves da Silva - RM 567029

- William A. C. Vasconcelos - RM 567096

## Resumo da entrega

A entrega da Fase 3 apresenta o planejamento da Sprint 1 do Challenge Intelliway, voltado à segurança de agentes de inteligência artificial que consomem conteúdo externo. O PromptShield BR propõe detectar tentativas de prompt injection em português brasileiro por meio de um serviço independente, consumido por API. A solução planejada separa classificação, score de risco e decisões ALLOW, REVIEW ou BLOCK, mantendo a inferência independente de LLM generativo. A documentação reúne modelo de ameaças, catálogo de histórias propostas, estratégia de dataset PT-BR com hard negatives e prevenção de data leakage, baselines Regex e TF-IDF e avaliação futura de DeBERTa. Também descreve arquitetura com OCR e RAG, registros auditáveis, wireframes do portal administrativo, revisão humana, governança e roadmap. Esta Sprint é exclusivamente documental: não apresenta implementação funcional nem métricas experimentais.

## Componentes preparados

| Componente | Conteúdo preparado |
|---|---|
| Análise do problema | Modelo de ameaças diretas e indiretas; ativos, perfis e riscos. |
| User Stories | 15 histórias propostas: 8 P0, 5 P1 e 2 P2; critérios e dependências. |
| Dataset PT-BR | Fontes candidatas, licenças pendentes, rotulagem, hard negatives e splits. |
| Baselines | Planejamento de regras/Regex e TF-IDF com classificador linear. |
| Modelo profundo | Proposta de avaliação DeBERTa em PT-BR e fine-tuning; LoRA como opção. |
| Arquitetura | Serviço independente: API, motor, OCR, RAG, registros e portal. |
| Contrato da API | Exemplos JSON, source_type, score, decisões e versões. |
| Portal administrativo | Wireframes, navegação, histórico e revisão humana aditiva. |
| Governança | Propostas de LGPD, minimização, riscos, auditoria e versionamento. |
| Roadmap | Sprints futuras, gates de dados/modelos e validação oficial pendente. |

## Repositório GitHub

[https://github.com/amaralthedoug/promptshield-br](https://github.com/amaralthedoug/promptshield-br)

Repositório público, com endereço e visibilidade verificados.

## Observação acadêmica

A Fase 3 corresponde à entrega atual do curso e apresenta a Sprint 1 do Challenge Intelliway como proposta técnica documentada, sem implementação funcional ou métricas experimentais. O catálogo contém **User Stories propostas pelo grupo — sujeitas à validação perante a especificação oficial da Intelliway**; não comprova cobertura integral das P0 oficiais.
