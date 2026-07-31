---
name: base-conversao-lsp-java
description: >-
  Internal operational patterns for LSP→Java conversion in HCM time/attendance
  (contexts, anti-hallucination, traps). Use from Skill 5 after consulting Skill
  6 official docs. Read skill-07-reference.md for class skeletons and method
  anchors. Never invent methods not found here, in Skill 6, or in user annexes.
---

# Skill 7 · Base de Conversão LSP → Java
Versão: v1.4 · Internal · `skill-07-base-conversao-lsp-java.md`

Not in menu. Apply Router globals. **Skill 6 official docs win** on conflict.  
Catalogs/skeletons: [`skill-07-reference.md`](skill-07-reference.md).

## When to use / not

| Use | Don't |
|---|---|
| HCM/Ponto conversion patterns, traps, sanitized examples | Mentoria-only; as “official proof” instead of Skill 6 |

## Hard constraints

1. Findings here = `padrao_anexo` / `inferencia` until Skill 6 confirms.  
2. Sanitize client/company/paths — say “exemplos sanitizados”.  
3. Full hundreds-of-methods catalog is **not** embedded — only minimal anchors in reference.  
4. Missing in reference + Skill 6 + annex → `validacao_manual` — **do not invent**.  
5. Hours = integer minutes; SQL/cursor → semantic API first; no loose context vars in Java.

## Instructions

```text
1. Identify class context (Apuracao, FechamentoBH, …)
2. Look up anchors in skill-07-reference.md
3. Confirm signature via Skill 6
4. Else padrao_anexo/inferencia; else validacao_manual
```

Recommended conversion steps for Skill 5: context → inventory → map → mechanics (minutes, End→return) → syntax.

## Output to Skill 5

```text
contexto: Apuracao | FechamentoBH | outro | indefinido
ancora_encontrada: sim | nao
metodo_ou_padrao: ...
evidencia_sugerida: padrao_anexo | inferencia | validacao_manual
requer_skill_6: sim
limite: ...
```

## Related

`skill-07-reference.md` · Skill 6 · Skill 5
