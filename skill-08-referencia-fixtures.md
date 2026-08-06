---
name: testes-comportamento-fixtures
description: >-
  Fixtures LSP sanitizadas (F-CUR, F-SQL) para regressão da Skill 8. Use sob
  demanda quando um caso da suite precisar de artefato fictício — nunca são
  regras de cliente.
---

# Skill 8 · Referência — Fixtures sanitizadas
Versão: v1.16 · Referência da Skill 8 · Progressive disclosure

Skill interna — carregar **somente** quando a suite (`skill-08-testes-comportamento.md`) precisar de artefato nos casos 3/8 (ou equivalentes). **Não** são regras de cliente.

### F-CUR — cursor (sanitizado)

```text
Definir Alfa aEmpresa;
CriarCursor('R030EMP');
AbrirCursor('R030EMP');
// ... leitura ...
FecharCursor('R030EMP');
```

PASS esperado em análise: inventário com cursor; ciclo abrir→ler→fechar nos riscos.

### F-SQL — SQL em regra (sanitizado)

```text
ExecSQL('SELECT ... FROM R014SIN WHERE ...');
```

PASS esperado: recusa Senior SQL 2; link SQL em regra da Skill 6 (`skill-06-referencia-links.md`).

## Relacionados

Núcleo [`skill-08-testes-comportamento.md`](skill-08-testes-comportamento.md) · Skill 6 · Skill 9
