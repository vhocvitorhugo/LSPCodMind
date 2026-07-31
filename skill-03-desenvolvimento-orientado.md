---
name: desenvolvimento-orientado
description: >-
  Creates or refactors Senior/LSP rules, routines, integrations, and validations
  as complete commented code. Use when the user asks to build, structure, or
  refactor a rule without LSP→Java conversion. Always run Skill 9 gate before
  publishing the rule to the user.
---

# Skill 3 · Desenvolvimento Orientado
Versão: v1.4 · Arquivo: `skill-03-desenvolvimento-orientado.md`

Apply Router globals. Do not restate them.

## When to use / not

| Use | Don't use |
|---|---|
| Create/refactor LSP rule, routine, WS, automation | Concept → 1; debug-only → 2; reverse-only → 4; convert → 5 |

**Handoff:** conversion → Skill 5

## Instructions

1. State functional goal + premises.  
2. Skill 6 for syntax/aliases/SQL.  
3. Choose safest strategy; implement with block comments.  
4. List risks + manual validation.  
5. Build **complete** draft (no `// restante`).  
6. **Skill 9 gate** (`desenvolvimento_lsp`); fix ≤2 cycles on FAIL.  
7. Publish code + Check 9 summary + evidence + continuity.

## Output

```text
## Objetivo da implementação
## Premissas adotadas
## Estratégia técnica
## Código completo comentado
## Riscos / impactos
## Pontos de validação manual
## Referência

Evidência: ...
Bases consultadas: Skill 6 [sim/não]; Skill 7 [não]

## Check determinístico (Skill 9)
Veredito: PASS | FAIL
Origem: Skill 3
Ciclos de correção: 0|1|2
Falhas remanescentes: ...

Deseja continuar neste fluxo, voltar ao menu ou seguir para outra opção?
```

## Examples

**In:** `Crie regra LSP que valide colaborador ativo` → draft → gate 9 → publish.  
**Don't:** publish without Skill 9; omit code via comments; deliver HCM Java (Skill 5).

## Related

Router · Skill 6 · Skill 9 gate · handoff Skill 5
