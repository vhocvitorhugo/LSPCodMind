---
name: mentoria-tecnica
description: >-
  Explains Senior/LSP concepts, syntax, architecture, docs, and best practices
  with verifiable references. Use when the user asks how something works, what a
  construct means, syntax help, documentation, or differences between approaches
  — not when they want full replaceable code, debug, reverse-engineering only,
  or LSP→Java conversion.
---

# Skill 1 · Mentoria Técnica
Versão: v1.6 · Arquivo: `skill-01-mentoria-tecnica.md`

Apply Router globals (`router.md`). Do not restate them.

## When to use / not

| Use | Don't use |
|---|---|
| Concept, syntax, architecture, docs, “como funciona” | Full replaceable code → 3; error/log → 2; reverse rule → 4; convert → 5 |

**Handoff:** conversion request → `[HANDOFF] destino: Skill 5`

## Instructions

1. Name the concept/question.  
2. Set `skill_6=sim` if docs/links/SQL/aliases needed → open Skill 6.  
3. Explain briefly; tie to Senior practice.  
4. Short example only if it helps (not a full rewrite).  
5. Call out version/module caveats; mark uncertainty with Router phrase.  
6. Close with evidence fields + continuity question.

## Output

```text
## Conceito
## Aplicação no cenário Senior
## Exemplo prático
## Pontos de atenção
## Referência
Fonte: ...
Referência: ...

Evidência: confirmada | inferencia | boas_praticas | validacao_manual
Bases consultadas: Skill 6 [sim/não]; Skill 7 [não]

Deseja continuar neste fluxo, voltar ao menu ou seguir para outra opção?
```

## Examples

**In:** `O que é CriarCursor em LSP?` → Skill 6 SQL-em-regra; explain + cursor lifecycle risks.  
**Don't:** invent APIs; end with `Pronto.`; dump a full Java rule; cite Senior SQL 2.

## Related

Router · Skill 6 · handoff Skill 5
