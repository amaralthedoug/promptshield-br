# Visão geral — PromptShield BR

## Problema e justificativa

Agentes de IA que leem e-mails, documentos, páginas web, resultados de RAG e imagens transformadas por OCR recebem conteúdo externo no mesmo contexto em que processam instruções legítimas. Uma instrução maliciosa pode induzir o agente a desobedecer suas regras, revelar informações ou executar uma ação fora do fluxo autorizado. Esse risco é denominado *prompt injection*; quando chega por uma fonte consumida pelo agente, trata-se de injeção indireta.

O problema é especialmente relevante em PT-BR. Detectores preparados predominantemente em inglês podem falhar diante de variações linguísticas, acentuação, informalidade, contexto corporativo e textos benignos que mencionam termos como “ignore” ou “instrução”. A referência da OWASP descreve a injeção como uma vulnerabilidade estrutural e recomenda defesa em camadas, não uma garantia de eliminação do risco ([OWASP LLM01:2025](https://genai.owasp.org/llmrisk/llm01-prompt-injection/)).

## Público-alvo

| Perfil | Necessidade proposta |
|---|---|
| Sistema consumidor | Consultar uma decisão estruturada antes de encaminhar conteúdo a um agente. |
| Analista de segurança/operação | Investigar eventos, corrigir decisões ambíguas e produzir rótulos auditáveis. |
| Product owner | Acompanhar métricas, versões e risco operacional sem acessar o texto além do necessário. |

## Objetivo

Planejar um serviço independente, consumido por API, para detectar prompt injection em conteúdo PT-BR e aplicar uma política que devolva `ALLOW`, `REVIEW` ou `BLOCK`, com registro mínimo de eventos e futuro portal administrativo. A proposta preserva a separação entre o serviço e quaisquer sistemas, dados ou infraestrutura da Intelliway, que não estão disponíveis ao grupo.

## Escopo proposto

- Receber conteúdo textual normalizado de texto, e-mail, página web, documento, trecho de RAG e OCR.
- Aplicar motor discriminativo de detecção e política de decisão versionada.
- Registrar metadados e resultado de forma minimizada para métricas e revisão humana.
- Planejar OCR, consumidor automatizado, portal, governança, dados e evolução de modelos.

## Exclusões desta Sprint

- Código funcional, deploy, banco de dados, treinamento, inferência real, React, API executável e protótipos clicáveis.
- Integração com EvaGPT ou qualquer sistema da Intelliway.
- Uso de LLM generativo como classificador da API.
- Dados reais de clientes, alegações de métricas medidas ou de eficácia em produção.

## Benefícios esperados

O serviço proposto cria um ponto de controle reutilizável antes da entrada de conteúdo em agentes, padroniza decisões para diversos consumidores e estabelece evidências para governança e melhoria contínua. Ele não substitui privilégio mínimo, validação de saída, confirmação humana e controles do agente; complementa-os em uma arquitetura de defesa em profundidade.
