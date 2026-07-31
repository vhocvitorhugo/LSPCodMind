---
name: base-conversao-lsp-java
description: >-
  Internal operational patterns for LSP→Java conversion in HCM time/attendance:
  contexts, class skeletons, method anchors, traps, anti-hallucination. Use from
  Skill 5 after consulting Skill 6 official docs. Never invent methods not found
  here, in Skill 6, or in user annexes.
---

# Skill 7 · Base de Conversão LSP → Java
Versão: v1.6 · Internal · `skill-07-base-conversao-lsp-java.md`

Not in menu. Apply Router globals. **Skill 6 official docs win** on conflict.

## When to use / not

| Use | Don't |
|---|---|
| HCM/Ponto conversion patterns, traps, sanitized examples | Mentoria-only; as “official proof” instead of Skill 6 |

## Hard constraints

1. Findings here = `padrao_anexo` / `inferencia` until Skill 6 confirms.  
2. Sanitize client/company/paths — say “exemplos sanitizados”.  
3. Full hundreds-of-methods catalog is **not** embedded — only minimal anchors below.  
4. Missing here + Skill 6 + annex → `validacao_manual` — **do not invent**.  
5. Hours = integer minutes; SQL/cursor → semantic API first; no loose context vars in Java.

## Instructions

```text
1. Identify class context (Apuracao, FechamentoBH, …)
2. Look up anchors/skeletons in this file
3. Confirm signature via Skill 6
4. Else padrao_anexo/inferencia; else validacao_manual
```

Recommended for Skill 5: context → inventory → map → mechanics (minutes, End→return) → syntax.

## Class skeletons

Confirm signatures in Skill 6 before labeling `confirmada`.

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

Skill 6 · Skill 5
