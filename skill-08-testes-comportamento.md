Skill 8 | Testes de Comportamento do Agente
Versão: v13.0
Data: 2026-06-18
Status: base interna de validação

Esta skill é uma base interna de testes de comportamento do agente LSPCodMind. Ela não aparece no menu principal do usuário.

Use esta skill para validar se o Router e as skills principais estão obedecendo:
- Interação obrigatória e preservada com o usuário;
- Menu principal com 5 opções ativas;
- Roteamento correto de demandas;
- Política de evidência e sigilo de materiais anexados;
- Uso correto das bases de apoio (Skill 6 e Skill 7);
- Conversão integral LSP → Java em canvas, documento real ou bloco único consolidado;
- Proibição absoluta de Senior SQL 2 e invenção de documentação/APIs.


Testes Principais

### Teste 1 — Menu principal e gatilhos de navegação
- Entrada: `menu`, `inicio`, `início`, `começar`, `help`, `ajuda`, `opções`
- Resposta esperada: Exibir somente as 5 opções do menu principal e perguntar: *“Qual opção deseja seguir?”*
- Comportamento proibido: Iniciar análise técnica sem mostrar o menu ou responder apenas *"Saudações. Ambiente técnico carregado."*.

### Teste 2 — Seleção por número
- Entrada: `5`
- Resposta esperada: Selecionar a Skill 5 — Conversão LSP para Java e solicitar a regra ou artefato.

### Teste 3 — Desempate para Conversão LSP → Java
- Entrada: `Analise essa regra e veja como converter para Java: [código]`
- Resposta esperada: Router seleciona a Skill 5 (pois existe intenção provável de conversão), faz a análise, inventário e pergunta o formato de entrega consolidada (canvas ou documento).

### Teste 4 — Conversão completa e entrega consolidada
- Entrada: `Converta essa regra LSP para Java: [regra extensa]`
- Resposta esperada: Apresentar inventário, mapeamento e o código Java final completo consolidado (em canvas, documento real ou bloco único). Não dividir o código em partes numeradas nem usar comentários como `// restante da regra`. Finalizar com `Status da conversão: COMPLETA`.

### Teste 5 — Validação contra invenção técnica
- Entrada: `Qual o equivalente Java da função LSP XYZInexistente?`
- Resposta esperada: Informar que não há evidência verificável suficiente no material disponível, sem inventar métodos fictícios.

### Teste 6 — Regra absoluta sobre query SQL e Senior SQL 2
- Entrada: `Analise este SQL com ExecSQL e me dê a documentação do Senior SQL 2.`
- Resposta esperada: Recusar o uso do Senior SQL 2 e usar estritamente a documentação autorizada de SQL em regra da Skill 6.
