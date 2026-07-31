---
name: analisador-regras
description: >-
  Reverse-engineers existing Senior/LSP (or related) rules: business intent,
  variables, flow, dependencies, and risks — without converting to Java. Use
  when the user pastes a rule and asks what it does, how it works, or for a
  technical/functional map. If conversion is intended, hand off to Skill 5.
---

# Skill 4 · Analisador de Regras
Versão: v1.4 · Arquivo: `skill-04-analisador-regras.md`

Apply Router globals. Do not restate them.

## When to use / not

| Use | Don't use |
|---|---|
| Explain/map existing rule artifact | Concept w/o artifact → 1; bug/log → 2; create/refactor → 3; convert → 5 |

**Handoff:** “analise e converta” / Java intent → Skill 5

## Instructions

1. Read full available rule.  
2. Separate business intent vs technical mechanics.  
3. Map variables, functions, cursors, SQL, dependencies.  
4. Skill 6 when citing docs/aliases.  
5. Flow, fragility, performance/maintenance risks.  
6. Suggest improvements **without** Java migration.  
7. Evidence + continuity (no Skill 9 — no generated code).

## Output

```text
## Overview de negócio
## Objetivo técnico da regra
## Mapeamento de variáveis
| Nome | Tipo/origem | Uso |
## Fluxo lógico
## Dependências externas
## Pontos de atenção
## Riscos de performance
## Riscos de manutenção
## Sugestões de melhoria
## Referência

Evidência: ...
Bases consultadas: Skill 6 [sim/não]; Skill 7 [não]

Deseja continuar neste fluxo, voltar ao menu ou seguir para outra opção?
```

## Examples

**In:** paste LSP with cursor → map + risks; no Java.  
**In:** “analise e converta” → handoff Skill 5.  
**Don't:** invent variables; convert here; end with `Pronto.`

## Related

Router · Skill 6 · handoff Skill 5
