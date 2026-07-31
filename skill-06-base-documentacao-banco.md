---
name: base-documentacao-banco
description: >-
  Internal knowledge base of authorized Senior documentation links and ERP/HCM
  alias hints. Use when any skill must cite official docs, validate SQL-in-rule
  links, web services, LSP syntax pages, HCM function equivalence URLs, or
  interpret table/field aliases. Read skill-06-reference.md for the full link
  and alias catalogs. Never treat as Senior SQL 2.
---

# Skill 6 · Base de Documentação e Banco
Versão: v1.5 · Internal · `skill-06-base-documentacao-banco.md`

Not in menu 1–5. Apply Router globals. Full catalogs: [`skill-06-reference.md`](skill-06-reference.md).

## When to use / not

| Use | Don't |
|---|---|
| Official link, SQL-em-regra, WS, LSP syntax, HCM equivalence URL, alias | Casual chat; replace Skill 7 conversion patterns |

Do not expose “Skill 6” to the user — cite the validated source only.

## Hard constraints

1. Only links in `skill-06-reference.md` are official in this training version.  
2. Missing topic → `Não encontrei link autorizado na base atual para validar esse ponto com segurança.`  
3. Before citing: page must be specific content, not portal/index.  
4. Do not rewrite `index.htm#...` to invented direct URLs.  
5. Senior SQL 2 banned — use SQL-em-regra / SP / proprietária links only.  
6. Aliases are `auxiliar` until real schema confirms.  
7. Apostilas LSP/APO/Rubi: **not in repo** (`ausente_no_repo`); user attachments are complementary only.

## Instructions

```text
1. Identify topic (syntax|WS|SQL|event|HCM equivalence|alias)
2. Open skill-06-reference.md → matching section
3. Classify coverage: confirmado | auxiliar | ausente
4. Return to caller: achado + class + limite
5. Never invent a “close enough” link/alias
```

## Output to caller

```text
topico: ...
cobertura: confirmado | auxiliar | ausente
achado: ...
link_ou_alias: ...
limite: ...
```

## Related

`skill-06-reference.md` · Router evidence policy · Skill 7 (after official docs)
