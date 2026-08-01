---
name: check-deterministico
description: >-
  Gate determinístico PASS/FAIL/N/A de conformidade para toda regra criada,
  refatorada, convertida ou corrigida com código substituível. Use
  automaticamente após rascunhos das Skills 2/3/5 antes de publicar ao usuário,
  e quando o usuário pedir auditoria/conformidade/check de um artefato gerado.
---

# Skill 9 · Check Determinístico
Versão: v1.9 · Gate obrigatório · `skill-09-check-deterministico.md`

Checks binários apenas — cite evidência observável. Proibido “parece ok”.

## Quando usar / não usar

| Usar | Não usar |
|---|---|
| **Gate** após Skill 3 / Skill 5 Fase C / código corrigido da Skill 2; auditoria avulsa | Criar/converter do zero (3/5); QA de menu (8) |

## Pipeline do gate (obrigatório)

```text
1. Skill origem monta RASCUNHO (ainda não envia)
2. Skill 9 no modo gate_obrigatorio
3. PASS → publica rascunho + resumo do check
4. FAIL → corrige na origem → reexecuta 9 (máx. 2 ciclos)
5. Ainda FAIL → publica + FAIL transparente + IDs que falharam
6. Pergunta de continuidade só na resposta final ao usuário
```

**Proibido:** mostrar regra gerada/convertida ao usuário sem este gate.

Sem gate para: menu, Skill 1, Skill 4, Skill 5 Fase A/B, diagnóstico sem código corrigido.

## Modos

| Modo | Bateria |
|---|---|
| `gate_obrigatorio` + conversão | `conversao_lsp_java` |
| `gate_obrigatorio` + criar/corrigir regra | `desenvolvimento_lsp` |
| `auditoria_avulsa` | laudo completo |

## Bateria — conversão (Skill 5 C)

| ID | PASS | FAIL | Crítico? |
|---|---|---|---|
| CHK-INV | Tabela de inventário presente | Ausente na conversão completa | Sim |
| CHK-CTX | Contexto nomeado | Ausente | |
| CHK-MAP | Seção de mapeamento | Só código | |
| CHK-CLASS | Rótulos de evidência usados | “ok” vago | |
| CHK-COMP | Classe/`execute` completo, sem omissão | Stub/`// restante`/partes | Sim |
| CHK-CONS | Entrega única consolidada | Fragmentada | Sim |
| CHK-STAT | `Status da conversão: COMPLETA` | Ausente | Sim |
| CHK-EVID | `Evidência:` + `Bases consultadas:` | Ausente | Sim |
| CHK-B67 | Skills 6+7 sim no HCM | Marcado não | |
| CHK-SQL2 | Sem Senior SQL 2 | Recomenda SQL 2 | Sim |
| CHK-SQLAPI | API ou nota manual | SQL/EntitySession cego | |
| CHK-SITAPI | Usa `getHorSit`/`setHorSit`/`zeraHorasSituacao` | Usa `getSituacao().get/setMinutos` | Sim (se manipula situações) |
| CHK-ORDEM | Ordem de parâmetros confirmada ou marcada manual | Cópia cega da ordem LSP | |
| CHK-TIPO | Tipos Java explícitos coerentes | `Numero` solto / tipagem fraca | |
| CHK-FIN | Cursor/`EntitySession` com `finally`/close | Abre sem fechar | Sim (se usa cursor) |
| CHK-CTXOK | Métodos do contexto correto da regra | Getter de apuração em contexto errado | |
| CHK-MIN | Minutos inteiros / conversão explícita | `HH:mm` em API de minutos | |
| CHK-END | End→retorno ou manual | Ignorado | |
| CHK-SOLTO | Contexto mapeado | Variável solta | |
| CHK-VAL | Lista manual se necessário | Manual sem lista | |
| CHK-LINK | Sem downloads falsos | Link falso/não autorizado como oficial | |
| CHK-SIG | Sanitizado | Vazamento | |
| CHK-COM | Comentários por bloco | Código longo sem comentário | |
| CHK-CONT | Continuidade na resposta **final** | Ausente no final | N/A no rascunho interno |

## Bateria — desenvolvimento / correção (Skill 3 / 2)

| ID | PASS | FAIL | Crítico? |
|---|---|---|---|
| CHK-OBJ | Objetivo/premissas | Ausente | |
| CHK-FULL | Código completo | `// restante` | Sim |
| CHK-CUR | Abrir/ler/fechar | Abre sem fechar | |
| CHK-SQL2 | Sem SQL 2 | Usa SQL 2 | Sim |
| CHK-COM | Comentários por bloco | Ausente em regra longa | |
| CHK-EVID | Campos de evidência | Ausente | Sim |
| CHK-SIG | Sanitizado | Vazamento | |
| CHK-CONT | Na resposta final | Ausente | N/A no rascunho |

Veredito: todos aplicáveis PASS → `PASS`; qualquer FAIL → `FAIL`; material insuficiente → `INCOMPLETO`.

## Resumo ao usuário (sempre após o gate)

```text
## Check determinístico (Skill 9)
Veredito: PASS | FAIL
Origem: Skill N
Ciclos de correção: 0|1|2
Falhas remanescentes: nenhuma | [IDs]
```

## Laudo avulso

Matriz completa + contagens + veredito + ações corretivas + evidência + continuidade.

## Exemplos

Gate PASS após Fase C limpa · Gate FAIL por cursor aberto → Skill 3 corrige → PASS · **Não** publicar sem gate.

## Relacionados

Router (gate §11) · Skills 2/3/5 · vs Skill 8 (QA de comportamento ≠ gate de artefato)
