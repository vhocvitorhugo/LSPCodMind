---
name: base-conversao-lsp-java-reference
description: >-
  Reference skeletons and minimum Java method anchors for HCM time-attendance
  conversion (Skill 7). Read when Skill 5/7 need concrete getHorSit-style
  patterns or Apuracao/FechamentoBH class shapes.
---

# Skill 7 Reference · Esqueletos e âncoras
Versão: v1.4 · Progressive disclosure for Skill 7

Confirm signatures in Skill 6 before labeling `confirmada`.

## Class skeletons

### Apuração

```java
@Rule(description = "Regra de Apuracao")
public class RegraApuracao extends Apuracao {
    @Override
    public void execute() {
        ContextoGeralRH contextoGeral = getContainer().getContextoGeral();
        ContextoApuracao contextoApuracao = getContainer().getContextoApuracao();
        // colaborador, data, regras, situações via API semântica
    }
}
```

### Fechamento BH

```java
@Rule(description = "Regra de Fechamento de Banco de Horas")
public class RegraFechamentoBH extends FechamentoBH {
    @Override
    public void execute() {
        ContextoGeralRH contextoGeral = getContainer().getContextoGeral();
        ContextoFechamentoBH contextoFechamentoBH = getContainer().getContextoFechamentoBH();
    }
}
```

## Method anchors

### Situações

| Intent | Anchor |
|---|---|
| Read | `contextoApuracao.getHorSit(codigoSituacao)` |
| Set | `contextoApuracao.setHorSit(codigoSituacao, minutos)` |
| Zero | `contextoApuracao.zeraHorasSituacao(codigoSituacao)` |
| Previous | `contextoApuracao.getHorSitAnterior(codigoSituacao)` |
| Sum | `contextoApuracao.somaHorasSituacao(...)` |

### Colaborador / contexto

| Intent | Anchor |
|---|---|
| Emp/Tip/Cad | `getNumEmp()` / `getTipCol()` / `getNumCad()` |
| Date | `contextoApuracao.getData()` |
| Histories | `getHistoricoSindicato()`, `getHistoricoVinculo()`, `getHistoricoCargo()`, `getHistoricoEscala()`, `getHistoricoCentrodeCusto()`, `getHistoricoFilial()` |

### Marcações / totais / escala

| Intent | Anchor |
|---|---|
| Marcações | `getMarcacoesRealizadas(...)` |
| Totais | `getTotalSituacoes(...)` |
| Escala | `getEscala()` / `getEscalaPrevistaColaborador(...)` |
| Horário | `getHorario()` / `getHorarioPrevistoColaborador(...)` |

## Traps

| Trap | Fix |
|---|---|
| Copy LSP param order | Confirm Java signature |
| Pass `HH:mm` into minute APIs | Convert (`14:30` → `870`) |
| Blind SQL/cursor port | Prefer semantic API |
| Invent similar method | `validacao_manual` |
| Leak client names from examples | Sanitize |

## Sanitized examples

Full real rules are not versioned here. User annexes = observed pattern only, never official docs.
