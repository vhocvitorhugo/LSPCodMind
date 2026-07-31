---
name: diagnostico-debug
description: >-
  Diagnoses Senior/LSP errors, logs, exceptions, integration failures, and
  performance issues; delivers partial useful diagnosis and complete corrected
  rules when possible. Use when the user sends errors, logs, unexpected
  behavior, or broken rules. Always run Skill 9 gate before publishing a
  replaceable corrected rule.
---

# Skill 2 · Diagnóstico e Debug
Versão: v1.6 · Arquivo: `skill-02-diagnostico-debug.md`

Apply Router globals. Do not restate them.

## When to use / not

| Use | Don't use |
|---|---|
| Error, log, exception, unexpected behavior, bad performance | Concept-only → 1; greenfield build → 3; healthy-rule analysis → 4; convert → 5 |

**Handoff:** conversion → Skill 5; broad rewrite without bug focus → Router may pick Skill 3

## Instructions

1. Read material already provided.  
2. Name primary symptom; probable cause + alternatives.  
3. Skill 6 if confirming syntax/behavior/aliases.  
4. How to validate each hypothesis.  
5. If enough code: build **complete** corrected draft (cursor open→read→close risks called out).  
6. If publishing corrected rule → **Skill 9 gate** (`desenvolvimento_lsp`); fix ≤2 cycles.  
7. Publish diagnosis (+ code) + Check 9 summary (or N/A) + evidence + continuity.  
8. Ask for more input only if blocked.

Never answer only “Preciso do código completo” — give partial useful diagnosis first.

## Output

```text
## Problema identificado
## Causa provável
## Hipóteses alternativas
## Como validar
## Correção sugerida
## Versão corrigida comentada
## Riscos e impactos
## Referência

Evidência: ...
Bases consultadas: Skill 6 [sim/não]; Skill 7 [não]

## Check determinístico (Skill 9)
Veredito: PASS | FAIL | N/A
Origem: Skill 2
Ciclos de correção: 0|1|2
Falhas remanescentes: ...

Deseja continuar neste fluxo, voltar ao menu ou seguir para outra opção?
```

## Examples

**In:** log shows cursor never closed → diagnose + full fix + gate 9.  
**Don't:** publish corrected rule without Skill 9; invent APIs; Senior SQL 2.

## Related

Router · Skill 6 · Skill 9 gate · handoff Skill 5
