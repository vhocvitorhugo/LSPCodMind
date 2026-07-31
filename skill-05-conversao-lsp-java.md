---
name: conversao-lsp-java
description: >-
  Converts Senior LSP rules to Java (HCM/Gestão do Ponto) with inventory,
  mapping, phases A/B/C, and consolidated delivery. Use when converting,
  migrating, or mapping LSP→Java. Always run Skill 9 gate before publishing
  Fase C. Prefer official docs (Skill 6) over Skill 7 patterns.
---

# Skill 5 · Conversão LSP → Java
Versão: v1.5 · Arquivo: `skill-05-conversao-lsp-java.md`

Apply Router globals. Preserve **functional intent**, not literal syntax.

## When to use / not

| Use | Don't use |
|---|---|
| Convert/migrate/map LSP→Java / HCM Ponto | Concept → 1; debug → 2; new LSP only → 3; reverse-only → 4 |

**Handoff:** explain-only → 4; gate FAIL → fix here + re-run 9; avulsa audit → 9

## Hard constraints (local)

1. Phases A→B→C; no final Java before inventory (unless format already chosen and A+C fit one transparent reply).  
2. Consolidated Java only; no chunks / `// restante`.  
3. Never invent signatures; unknown → `validacao_manual`.  
4. Parameter order not assumed equal to LSP.  
5. SQL/cursor → semantic API before EntitySession.  
6. Skill 6 required for docs; Skill 7 required for HCM/Ponto; **6 wins** on conflict.  
7. **Fase C:** draft → **Skill 9 gate** → publish with check summary.  
8. No fake download links.

## Phases

```text
A  Inventory + mapping + plan   (no final Java)
   → if user already asked canvas|doc|full code → skip B to C after A
B  Ask 1=canvas / 2=document     (no final Java)
C  Draft complete Java → Skill 9 gate → publish
```

### Inventory table (A)

| Item LSP | Tipo | Uso na regra | Equivalente Java / padrão | Evidência | Status |

Rules: End → return candidate; arrays → collections/methods; hours → minutes (`14:30`→`870`).

## Instructions

1. Read full LSP; set context: `apuracao|consistencia|bloqueio|fechamento_bh|geral|indefinido`.  
2. Consult Skill 6 + `skill-06-reference.md`; Skill 7 + `skill-07-reference.md`.  
3. Build inventory; map with labels `confirmada|adaptacao_arquitetural|padrao_anexo|inferencia|validacao_manual`.  
4. Mechanics before syntax.  
5. Run A/B/C; gate on C.

Quick method anchors: see Skill 7 reference (`getHorSit`, históricos, marcações…).

## Output — Fase A

```text
## Objetivo da regra original
## Resumo da lógica de negócio
## Contexto de execução
## Inventário de conversão
(tabela)
## Mapeamento LSP → Java (plano)
## Itens sem equivalência direta

Evidência: ...
Bases consultadas: Skill 6 [sim]; Skill 7 [sim]
[Fase B question if needed]
+ continuity
```

## Output — Fase C (after gate)

```text
## Objetivo / Inventário / Mapeamento
## Código Java convertido   [complete]
## Comentários técnicos
## Itens sem equivalência / validação manual
## Referência documental
Status da conversão: COMPLETA
Formato de entrega: ...

Evidência: ...
Bases consultadas: Skill 6 [sim]; Skill 7 [sim]

## Check determinístico (Skill 9)
Veredito: PASS | FAIL
Origem: Skill 5
Ciclos de correção: 0|1|2
Falhas remanescentes: ...

+ continuity
```

## Examples

**A→B:** convert without format → inventory + ask 1/2.  
**Skip B + gate:** “no canvas, regra toda” → A+C draft → Skill 9 → publish.  
**Don't:** publish C without Skill 9; invent `XYZInexistente`; partial parts.

## Related

Router · Skill 6/7 (+ references) · Skill 9 gate
