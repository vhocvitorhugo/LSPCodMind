<h1 align="center">LSPCodMind</h1>

<p align="center">
  <b>Framework de Agente de IA para Senior Sistemas: LSP, Mentoria, Debug e Engenharia Reversa</b>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/SENIOR_SISTEMAS-HCM_%7C_ERP-blue?style=for-the-badge" alt="Senior Sistemas" />
  <img src="https://img.shields.io/badge/LSP-5.10.4-orange?style=for-the-badge" alt="LSP 5.10.4" />
  <img src="https://img.shields.io/badge/LSPCodMind-v1.16-success?style=for-the-badge" alt="LSPCodMind v1.16" />
</p>

---

O **LSPCodMind** é um framework de agente em formato modular **Router + Skills**, focado na plataforma **Senior Sistemas**: mentoria técnica, diagnóstico de regras, desenvolvimento orientado e engenharia reversa de legado LSP.

**Versão atual: v1.16** — progressive disclosure com `skill-*-referencia-*` (padrão LSP→JAVA); **teto de 10** arquivos `skill-*.md` (sem contar o Router).

---

## Principais funcionalidades

- **Mentoria Técnica** — conceitos, sintaxe LSP, arquitetura Senior, documentação e boas práticas  
- **Diagnóstico e Debug** — erros, logs, exceções, integrações, cursores e performance  
- **Desenvolvimento Orientado** — criação/refatoração de regras LSP com código completo comentado + gate Skill 9  
- **Analisador de Regras** — engenharia reversa, variáveis, fluxo de negócio e riscos  
- **Check Determinístico (Skill 9)** — auditoria PASS/FAIL antes de apresentar regra gerada ou corrigida  

> **Fora de escopo:** conversão/migração LSP → Java (removida nesta versão).

---

## Arquitetura

O **Prompt Router** (`router.md`) controla menu, roteamento, evidência, sigilo, proibição de Senior SQL 2 e o gate Skill 9. **Não conta** no teto de 10.

| Papel | Arquivo | Menu? |
| :--- | :--- | :--- |
| Router (autoridade global) | [`router.md`](router.md) | — |
| Skills 1–4 (fluxos do usuário) | [`skill-01`](skill-01-mentoria-tecnica.md) … [`skill-04`](skill-04-analisador-regras.md) | Sim |
| Skill 6 — núcleo docs | [`skill-06-base-documentacao-banco.md`](skill-06-base-documentacao-banco.md) | Não |
| Skill 6 — links (sob demanda) | [`skill-06-referencia-links.md`](skill-06-referencia-links.md) | Não |
| Skill 6 — aliases/apostilas (sob demanda) | [`skill-06-referencia-aliases.md`](skill-06-referencia-aliases.md) | Não |
| Skill 8 — suite QA | [`skill-08-testes-comportamento.md`](skill-08-testes-comportamento.md) | Não |
| Skill 8 — fixtures (sob demanda) | [`skill-08-referencia-fixtures.md`](skill-08-referencia-fixtures.md) | Não |
| Skill 9 — gate | [`skill-09-check-deterministico.md`](skill-09-check-deterministico.md) | Automático |

**Total `skill-*.md` = 10** (máximo permitido).

### Contrato operacional

1. Router escolhe o fluxo (árvore de decisão).  
2. Skills 1–4 respondem com `Evidência` / `Bases consultadas`.  
3. Skills 2/3 com código de regra: gate Skill 9 antes de publicar.  
4. Skill 6/8: carregar `*-referencia-*` **só por âncora**.  
5. Skill 8 só na manutenção do treinamento.  
6. Pedidos de conversão LSP→Java: recusa + menu 1–4.  

### Formato das skills

Baseado em [skills.sh](https://www.skills.sh/) e [agentskills.io](https://agentskills.io/home) (progressive disclosure via `skill-NN-referencia-*.md`, no estilo do projeto LSP→JAVA).

---

## Estrutura do repositório

| Arquivo | Responsabilidade |
| :--- | :--- |
| [`README.md`](README.md) | Documentação e versão |
| [`router.md`](router.md) | Regras globais (fora do teto de 10) |
| [`skill-01` … `skill-04`](skill-01-mentoria-tecnica.md) | Menu do usuário |
| [`skill-06-base-documentacao-banco.md`](skill-06-base-documentacao-banco.md) | Núcleo docs |
| [`skill-06-referencia-links.md`](skill-06-referencia-links.md) | Links oficiais |
| [`skill-06-referencia-aliases.md`](skill-06-referencia-aliases.md) | Aliases + apostilas |
| [`skill-08-testes-comportamento.md`](skill-08-testes-comportamento.md) | Suite QA |
| [`skill-08-referencia-fixtures.md`](skill-08-referencia-fixtures.md) | Fixtures |
| [`skill-09-check-deterministico.md`](skill-09-check-deterministico.md) | Gate |

---

## Diretrizes críticas

- **Proibido Senior SQL 2** em regras com SQL/cursor.  
- **Sem achismo** sem evidência verificável.  
- **Sem conversão LSP→Java**.  
- **Gate Skill 9** antes de regra gerada/corrigida.  
- **≤10** arquivos `skill-*.md`.  

---

## Versionamento

| Versão | Destaque |
| :--- | :--- |
| **v1.16** | Referências `skill-*-referencia-*` + teto de 10 arquivos skill |
| v1.15 | Referências skills.sh + agentskills.io no Router e skills |
| v1.14 | Remove conversão LSP→Java; menu 1–4; base dual skills.sh + agentskills.io |
| v1.13 | Menu com identidade; desempate 2×3×4; inventário Skill 4; ritual links; fixtures QA; métrica Skill 9; PDFs sync |
| v1.12 | Router: identidade LSPCodMind |
| v1.11 | README obrigatório a cada alteração |
| v1.10 | Skills 6–9 fronteira / gate |
| v1.0–v1.9 | Baseline e evolução inicial |
