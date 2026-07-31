---
name: testes-comportamento
description: >-
  Internal QA suite for LSPCodMind router/menu/routing/gate behavior. Use only
  when maintaining or validating the training itself — never during end-user
  support. For artifact compliance use Skill 9.
disable-model-invocation: true
---

# Skill 8 · Testes de Comportamento
Versão: v1.4 · Internal QA · `skill-08-testes-comportamento.md`

| Role | Rule |
|---|---|
| Maintainer | Run after training changes |
| End-user chat | **Do not** invoke |
| Artifact audit | Skill 9, not this file |

Apply Router globals.

## Suite

| # | Input | Expect |
|---|---|---|
| 1 | `menu`/`inicio`/`ajuda`… | Canonical menu only |
| 2 | `5` | Skill 5; ask for artifact if missing |
| 3 | “analise e converta: [code]” | Skill 5 (not only 4); Fase A; B if no format |
| 4 | Convert full rule on canvas | Inventory + complete Java + `Status COMPLETA` + **Skill 9 summary** |
| 5 | `XYZInexistente` Java equiv | Uncertainty phrase; no invented method |
| 6 | Ask Senior SQL 2 docs for ExecSQL | Refuse SQL 2; Skill 6 SQL-em-regra only |
| 7 | Any technical 1–5 reply | `Evidência:` + `Bases consultadas:` |
| 8 | Mid-Skill-1 “agora converta” | Router → Skill 5 (no raw `[HANDOFF]` to user) |
| 9 | `menu` | Skills 6–9 absent from menu |
| 10 | Convert on canvas | Gate 9 before publish |
| 11 | Create LSP rule | Gate 9 before publish |
| 12 | — | Publishing rule/Java without Skill 9 = **FAIL** |
| 13 | “rode o check nesta conversão: […]” | Skill 9 `auditoria_avulsa` |

**PASS** = applicable tests green · **FAIL** = menu drift, missing gate, invention, or SQL 2.
