---
name: testes-comportamento
description: >-
  Suite interna de QA do comportamento do LSPCodMind (menu, roteamento, gate).
  Use somente ao manter ou validar o treinamento — nunca no atendimento ao
  usuário final. Para conformidade de artefato use a Skill 9.
disable-model-invocation: true
---

# Skill 8 · Testes de Comportamento
Versão: v1.8 · QA interno · `skill-08-testes-comportamento.md`

| Papel | Regra |
|---|---|
| Mantenedor | Executar após mudanças no treinamento |
| Atendimento ao usuário | **Não** acionar |
| Auditoria de artefato | Skill 9, não este arquivo |

Aplique as regras globais do Router.

## Suite

| # | Entrada | Esperado |
|---|---|---|
| 1 | `menu`/`inicio`/`ajuda`… | Somente o menu canônico |
| 2 | `5` | Skill 5; pedir artefato se faltar |
| 3 | “analise e converta: [código]” | Skill 5 (não só 4); Fase A; B se sem formato |
| 4 | Converter regra completa no canvas | Inventário + Java completo + `Status COMPLETA` + **resumo Skill 9** |
| 5 | Equivalente Java de `XYZInexistente` | Frase de incerteza; sem método inventado |
| 6 | Pedir docs Senior SQL 2 para ExecSQL | Recusar SQL 2; só SQL em regra da Skill 6 |
| 7 | Qualquer resposta técnica 1–5 | `Evidência:` + `Bases consultadas:` |
| 8 | No meio da Skill 1: “agora converta” | Router → Skill 5 (sem `[HANDOFF]` cru ao usuário) |
| 9 | `menu` | Skills 6–9 ausentes do menu |
| 10 | Converter no canvas | Gate 9 antes de publicar |
| 11 | Criar regra LSP | Gate 9 antes de publicar |
| 12 | — | Publicar regra/Java sem Skill 9 = **FAIL** |
| 13 | “rode o check nesta conversão: […]” | Skill 9 `auditoria_avulsa` |

**PASS** = testes aplicáveis ok · **FAIL** = menu errado, gate ausente, invenção ou SQL 2.
