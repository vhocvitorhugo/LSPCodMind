---
name: check-deterministico
description: >-
  Deterministic PASS/FAIL/N/A compliance gate for every rule created, refactored,
  converted, or corrected with replaceable code. Use automatically after Skill
  2/3/5 drafts before user-visible publish, and when the user asks for audit/
  conformidade/check on a generated artifact.
---

# Skill 9 · Check Determinístico
Versão: v1.4 · Gate obrigatório · `skill-09-check-deterministico.md`

Binary checks only — cite observable evidence. No “parece ok”.

## When to use / not

| Use | Don't |
|---|---|
| **Gate** after Skill 3 / Skill 5 Fase C / Skill 2 corrected code; avulsa audit | Create/convert from scratch (3/5); menu QA (8) |

## Gate pipeline (mandatory)

```text
1. Origin skill builds DRAFT (do not send yet)
2. Skill 9 mode gate_obrigatorio
3. PASS → publish draft + check summary
4. FAIL → fix in origin → re-run 9 (max 2 cycles)
5. Still FAIL → publish + transparent FAIL + failing IDs
6. Continuity question only on final user reply
```

**Forbidden:** show generated/converted rule to the user without this gate.

No gate for: menu, Skill 1, Skill 4, Skill 5 Fase A/B, diagnosis without corrected code.

## Modes

| Mode | Battery |
|---|---|
| `gate_obrigatorio` + conversion | `conversao_lsp_java` |
| `gate_obrigatorio` + rule create/fix | `desenvolvimento_lsp` |
| `auditoria_avulsa` | full laudo |

## Battery — conversion (Skill 5 C)

| ID | PASS | FAIL | Critical? |
|---|---|---|---|
| CHK-INV | Inventory table present | Missing on full conversion | Yes |
| CHK-CTX | Context named | Missing | |
| CHK-MAP | Mapping section | Code only | |
| CHK-CLASS | Evidence labels used | Vague “ok” | |
| CHK-COMP | Full class/`execute`, no omission | Stub/`// restante`/parts | Yes |
| CHK-CONS | Single consolidated delivery | Fragmented | Yes |
| CHK-STAT | `Status da conversão: COMPLETA` | Missing | Yes |
| CHK-EVID | `Evidência:` + `Bases consultadas:` | Missing | Yes |
| CHK-B67 | Skills 6+7 sim on HCM | Marked não | |
| CHK-SQL2 | No Senior SQL 2 | Recommends SQL 2 | Yes |
| CHK-SQLAPI | API or manual note | Blind SQL/EntitySession | |
| CHK-MIN | Minutes ints / explicit convert | `HH:mm` into minute API | |
| CHK-END | End→return or manual | Ignored | |
| CHK-SOLTO | Context mapped | Loose var | |
| CHK-VAL | Manual list if needed | Manual w/o list | |
| CHK-LINK | No fake downloads | Fake/unauthorized as official | |
| CHK-SIG | Sanitized | Leaks | |
| CHK-COM | Block comments | Long uncommented | |
| CHK-CONT | Continuity on **final** reply | Missing on final | N/A on internal draft |

## Battery — development / fix (Skill 3 / 2)

| ID | PASS | FAIL | Critical? |
|---|---|---|---|
| CHK-OBJ | Goal/premises | Missing | |
| CHK-FULL | Complete code | `// restante` | Yes |
| CHK-CUR | Open/read/close | Open w/o close | |
| CHK-SQL2 | No SQL 2 | Uses SQL 2 | Yes |
| CHK-COM | Block comments | Missing on long rule | |
| CHK-EVID | Evidence fields | Missing | Yes |
| CHK-SIG | Sanitized | Leaks | |
| CHK-CONT | On final reply | Missing | N/A on draft |

Verdict: all applicable PASS → `PASS`; any FAIL → `FAIL`; too little material → `INCOMPLETO`.

## User-facing summary (always after gate)

```text
## Check determinístico (Skill 9)
Veredito: PASS | FAIL
Origem: Skill N
Ciclos de correção: 0|1|2
Falhas remanescentes: nenhuma | [IDs]
```

## Avulsa laudo

Full matrix + counts + verdict + corrective actions + evidence fields + continuity.

## Examples

Gate PASS after clean Fase C · Gate FAIL on open cursor → Skill 3 fixes → PASS · **Don't** publish without gate.

## Related

Router §1.11 · Skills 2/3/5 · vs Skill 8 (behavior QA ≠ artifact gate)
