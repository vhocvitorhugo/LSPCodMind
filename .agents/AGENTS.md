# Regras do Projeto e Diretrizes para IA — LSPCodMind

> [!IMPORTANT]
> **DIRETRIZ CRÍTICA DE COMPORTAMENTO:**
> O pedido do usuário para "analisar a pasta .agents" ou a injeção destas regras no contexto **SIGNIFICA CUMPRIMENTO ESTRITO**. Você está terminantemente proibido de concluir um chat, finalizar uma tarefa de código ou dizer que terminou sem ANTES passar pelo checklist obrigatório da Seção 2 (incluindo atualização do `CHANGELOG.md` e versionamento Git com push). Ignorar estas regras é considerado uma falha grave na sua execução.

Este documento contém regras rígidas que DEVEM ser seguidas obrigatoriamente em todas as interações e alterações no projeto **LSPCodMind** (agente técnico Senior/LSP → Java).

## 1. Validação de Entendimento e Uso de Skills

- **Revisão Obrigatória de Diretrizes:** Antes de propor ou realizar qualquer alteração, o agente DEVE obrigatoriamente ler e revisar este arquivo (`.agents/AGENTS.md`) para garantir que todas as etapas do fluxo de trabalho sejam respeitadas.
- **Confirmação de Entendimento (Obrigatório):** Antes de iniciar a execução de qualquer demanda, o agente DEVE obrigatoriamente retornar uma mensagem ao usuário detalhando/resumindo o que entendeu da tarefa solicitada. Isso se aplica independentemente de estar operando no modo auto-plan ou não.
- **Sincronização Obrigatória (Git Pull):** Antes de realizar qualquer alteração no código, o agente DEVE obrigatoriamente executar o comando `git pull` (ou propor ao usuário que o faça) para garantir que a pasta local possua as atualizações mais recentes do repositório, evitando conflitos com alterações feitas por outros desenvolvedores.
- **Uso Obrigatório das Skills do Projeto:** Antes de realizar qualquer alteração ou atendimento técnico do agente, consulte **somente** os artefatos listados abaixo (raiz do repositório e este arquivo). Skills de diretórios globais fora do repositório (`~/.codex/skills`, `~/.agents/skills`, etc.) **não** são autorizadas neste projeto, salvo pedido explícito do usuário.
- **Roteamento:** O arquivo `router.md` é a autoridade de menu, seleção de fluxo, evidência, sigilo e continuidade. Em demandas de uso do agente (não de manutenção do repositório), siga o Router antes de executar uma skill principal.
- **Evite Achismo:** Se houver dúvida técnica sobre LSP, Senior, banco, equivalência ou conversão, consulte as bases internas (Skills 6–8 e 10) e diga quando não houver evidência verificável.
- **Documentação do Projeto:** Diretrizes de IA e regras operacionais do repositório ficam em `.agents/`. As skills e o router ficam na raiz do projeto (`router.md`, `skill-*.md`). Não invente pasta `docs/` na raiz sem pedido do usuário.

### Artefatos oficiais do LSPCodMind

Sempre utilize os arquivos abaixo como base para decisões técnicas e de planejamento:

- **Router (controle de interação e menu):**
  - [router.md](../router.md)

- **Skills principais (menu do usuário):**
  - [skill-01-mentoria-tecnica.md](../skill-01-mentoria-tecnica.md) — Mentoria Técnica
  - [skill-02-diagnostico-debug.md](../skill-02-diagnostico-debug.md) — Diagnóstico e Debug
  - [skill-03-desenvolvimento-orientado.md](../skill-03-desenvolvimento-orientado.md) — Desenvolvimento Orientado
  - [skill-04-analisador-regras.md](../skill-04-analisador-regras.md) — Analisador de Regras
  - [skill-05-conversao-lsp-java.md](../skill-05-conversao-lsp-java.md) — Conversão LSP para Java

- **Bases internas (não aparecem no menu):**
  - [skill-06-base-documentacao-links.md](../skill-06-base-documentacao-links.md) — Documentação e links autorizados
  - [skill-07-base-banco-dados.md](../skill-07-base-banco-dados.md) — Banco de dados / aliases / domínios
  - [skill-08-base-conversao-lsp-java.md](../skill-08-base-conversao-lsp-java.md) — Base de conversão HCM/Ponto
  - [skill-09-testes-comportamento.md](../skill-09-testes-comportamento.md) — Testes de comportamento do agente
  - [skill-10-exemplos-conversao-lsp-java.md](../skill-10-exemplos-conversao-lsp-java.md) — Exemplos sanitizados de conversão

## 2. Conclusão de Tarefas e Registro de Atualizações

Sempre que concluir a implementação de uma nova funcionalidade, alteração técnica ou correção neste repositório, você DEVE obrigatoriamente seguir os passos abaixo:

1. **Conferência de Consistência:** Verifique se Router e skills permanecem alinhados (menu, roteamento, política de evidência, entrega consolidada LSP → Java, proibição de Senior SQL 2 quando aplicável). Se a mudança afetar comportamento do agente, valide mentalmente ou execute os cenários relevantes da Skill 9.
2. **Registro no Changelog:** Adicione as modificações no arquivo `CHANGELOG.md` na raiz do repositório.
3. **Limpeza de Artefatos:** Antes de dar a tarefa como concluída, remova lixo acidental (arquivos temporários, `.DS_Store` se gerado pela alteração, trechos de debug, comentários mortos introduzidos na mudança).
4. **Versionamento e Deploy (Git):** Ao finalizar as etapas acima, você DEVE obrigatoriamente enviar as alterações para o repositório.
   - **Verificação Prévia:** Se a IDE apontar que o Git não está configurado (`fatal: not a git repository`), inicialize-o IMEDIATAMENTE (`git init`), defina a branch principal (`git branch -M main`), adicione o remote oficial (`git remote add origin https://github.com/vhocvitorhugo/LSPCodMind.git`) e faça o commit inicial antes de prosseguir com os passos abaixo.
   - Execute os comandos sequencialmente:
   - `git status` (para verificar os arquivos modificados)
   - `git add .` (para adicionar todos os arquivos relevantes; não versionar segredos)
   - `git commit -m "[prefixo] [descrição curta e clara da alteração]"` (ex: `git commit -m "feature/ Adapta AGENTS.md ao LSPCodMind"`)
     - **ATENÇÃO:** NUNCA use mensagens genéricas como "Alteração 24/07". O commit deve descrever exatamente o que foi feito.
     - **Regras para o [prefixo]:** O agente deve identificar a natureza da mudança e iniciar a mensagem OBRIGATORIAMENTE com um dos seguintes prefixos:
       - `feature/` (código/conteúdo novo / nova funcionalidade)
       - `fix/` (correção de bug)
       - `refactor/` (reorganização/melhoria sem mudar o propósito)
       - `hotfix/` (correção urgente)
   - `git push` (para enviar ao repositório remoto)
   - **Regras de inserção no CHANGELOG.md:**
     - Coloque a nova entrada no topo, agrupada pela data do dia da modificação (ex: `## Atualização de 31/07/2026`).
     - Se já existir um bloco com a data de hoje no topo, **NÃO crie um novo bloco**. Apenas adicione os itens dentro das categorias apropriadas desse bloco existente.
     - **Não repita atualizações:** Agrupe as alterações semelhantes listando os locais afetados em um único item.
   - **Categorização no CHANGELOG.md:**
     - `### features` (Novidade): Algo novo que não existia antes.
     - `### improvements` (Alteração): Melhoria de algo que já existia.
     - `### technicalNotes` (Nota Técnica): Alterações estruturais ou invisíveis ao usuário final do agente (refatoração, organização do repo, diretrizes de IA).
5. **Resumo pós-alteração (Obrigatório):** Depois de qualquer alteração, no resumo final do que foi feito apresentado ao usuário, o agente DEVE obrigatoriamente informar:
   - **Modelo / Agente de IA:** Qual modelo ou agente de IA foi utilizado para realizar a alteração (ex.: Composer, Claude, GPT).
   - **Esforço:** O esforço/nível empregado na tarefa executada (ex.: baixo, médio, alto — ou a métrica de esforço disponível no ambiente).
   - **Tokens:** Quantidade de tokens consumidos para atender às alterações solicitadas nesta interação (entrada + saída, ou o total reportado pelo ambiente). Se o ambiente não fornecer o valor exato, informar a melhor estimativa disponível e marcar como estimativa.
   - **Skills utilizadas:** Quais skills/arquivos foram consultados ou aplicados na execução (com link/caminho quando aplicável).
   - Exemplo de bloco no final da resposta:
     ```
     ---
     Modelo: Composer
     Esforço: baixo
     Tokens: ~12.000 (estimativa; entrada + saída desta demanda)
     Skills: .agents/AGENTS.md (diretrizes); router.md (contexto do projeto)
     ```

## 3. Escopo deste repositório

Este projeto **não** é uma aplicação web com build `dist`/Vite/PHP. É o repositório do agente **LSPCodMind** (Router + skills em Markdown).

Não aplique checklists de frontend, Design System Tailwind, `npm run build`, pasta `public_html` ou páginas React de atualizações/funcionalidades — isso pertence a outros projetos e não deve ser reintroduzido aqui.
