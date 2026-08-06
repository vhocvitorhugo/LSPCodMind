---
name: base-documentacao-aliases
description: >-
  Aliases ERP/HCM e âncoras de apostilas anexadas (material complementar). Use
  sob demanda a partir da Skill 6 para mapa de tabela/campo ou apostila do
  usuário; nunca trate alias auxiliar como confirmado sem schema.
---

# Skill 6 · Referência — Aliases e apostilas
Versão: v1.16 · Referência da Skill 6 · Progressive disclosure

Skill interna — carregar **somente** quando o núcleo (`skill-06-base-documentacao-banco.md`) indicar esta âncora. Aplique as regras globais do Router.

## Mapeamento banco (auxiliar)

Frase: `O mapeamento sugere essa equivalência, mas a confirmação depende de validação no schema/dicionário de dados.`

### Tabelas ERP

| Termo | Candidato | Cobertura |
|---|---|---|
| NF Saída / Venda | `E120NFV` | auxiliar |
| Item NF Saída | `E140NFV` | auxiliar |

Campos ERP: **ausente** — pedir schema / `validacao_manual`.

### HCM

| Origem | Candidato | Cobertura |
|---|---|---|
| R035DEP (termo) | `R036DEP` | auxiliar |
| R034FUN.SitCol | `SitAfa` | auxiliar |
| R034FUN.DatDem | `DatAfa` | auxiliar |
| R036DEP.ParDep | `GraPar` | auxiliar |
| R024CAR.DesCar / Cargo | `TitRed` | auxiliar |
| SitAfa Demitido | `7` | auxiliar |

Precedência: mapa mais completo/específico → candidato → schema/dicionário.  
SQL: alias → candidato → módulo → filtros/chaves → nunca existência absoluta só com esta tabela.

**Proibido:** “Use `R024CAR.TitRed`; está confirmado.” (só com alias auxiliar)

## Apostilas (complementar — ausente_no_repo)

Se o usuário anexar apostilas LSP/APO/Rubi, use como `Material complementar de treinamento` (nunca como doc oficial). Âncoras típicas:

- Cursor LSP: criar → abrir → ler → fechar; risco de cursor aberto  
- `ExecSQL` / funções `SQL_*`: SQL em regra (ver `skill-06-referencia-links.md`), **nunca** Senior SQL 2  
- Listas dinâmicas / Editor de Regras: apoio conceitual  

Prioridade em conflito: doc oficial (referencia-links) → schema → apostila → inferência.

## Relacionados

Núcleo [`skill-06-base-documentacao-banco.md`](skill-06-base-documentacao-banco.md) · [`skill-06-referencia-links.md`](skill-06-referencia-links.md)
