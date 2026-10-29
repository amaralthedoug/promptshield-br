# Modelo de ameaças

## Conceitos

**Prompt injection direta** ocorre quando o próprio usuário envia uma instrução para alterar o comportamento esperado do agente. **Indireta** ocorre quando essa instrução está em conteúdo externo posteriormente lido pelo agente — por exemplo, e-mail, página, documento ou imagem. A OWASP diferencia ambos os casos e destaca que fontes externas ampliam a superfície de ataque ([glossário OWASP](https://genai.owasp.org/glossary/prompt-injection/)).

## Ativos, atores e fronteiras

| Elemento | Risco |
|---|---|
| Regras e prompt de sistema do agente consumidor | Exfiltração ou substituição de instruções. |
| Dados acessíveis ao agente | Divulgação de dados corporativos, pessoais ou sigilosos. |
| Ferramentas e permissões do agente | Envio de e-mail, alteração, exclusão ou consulta indevida. |
| Disponibilidade do fluxo | Sobrecarga, retenções excessivas ou desvio de processo. |
| Registro de análises e rótulos | Exposição de conteúdo ou manipulação de evidências. |
| Modelo e política de decisão | Evasão, envenenamento futuro e deriva de desempenho. |

| Ator | Capacidade considerada |
|---|---|
| Atacante externo | Publicar página, enviar e-mail/anexo, fornecer imagem ou texto. |
| Usuário mal-intencionado | Inserir instrução direta no canal permitido. |
| Usuário legítimo | Produzir texto benigno semelhante a um ataque. |
| Operador interno indevido | Consultar eventos ou alterar rótulos/políticas sem autorização. |

## Vetores e cenários corporativos

| Vetor | Cenário | Impacto | Controle proposto |
|---|---|---|---|
| E-mail | Rodapé oculto pede desvio de procedimento. | Exfiltração/ação indevida. | Análise prévia, retenção `BLOCK`, confirmação para ações críticas. |
| Página web | Conteúdo recuperado por agente contém instrução conflitante. | Contaminação de contexto/RAG. | `source_type=web_page`, isolamento da fonte e detector. |
| Documento/RAG | Trecho indexado tenta redefinir prioridade de instruções. | Resposta manipulada. | Origem por chunk, decisão antes de compor contexto. |
| Imagem/PDF | Texto de baixo contraste ou pequeno é extraído por OCR. | Injeção multimodal indireta. | OCR em múltiplas passagens, confiança e revisão. |
| Texto direto | Pedido para revelar regras internas ou executar ação não autorizada. | Bypass operacional. | Classificação, validação e privilégio mínimo no consumidor. |
| Portal | Alteração não auditada de rótulo. | Retreinamento contaminado. | RBAC, trilha imutável e dupla revisão em amostras críticas. |

## Mitigações e limites

1. **Defesa em camadas:** detector, política de decisão, menor privilégio, validação determinística de saída e confirmação humana em ações de alto impacto.
2. **Separação de confiança:** `source_type`, identificador de fonte e proveniência acompanham cada análise; conteúdo externo nunca recebe a mesma confiança de instruções do sistema.
3. **Resiliência a evasão:** normalização Unicode, preservação de uma cópia para auditoria controlada, treinamento com variantes e avaliação por origem.
4. **Falha segura proporcional:** indisponibilidade do detector não deve virar autorização silenciosa; o consumidor aplica política explícita por criticidade, como reter conteúdo de alto risco.
5. **Limite reconhecido:** nenhum classificador elimina prompt injection. A decisão é um sinal de risco, não autorização para ampliar permissões do agente.
