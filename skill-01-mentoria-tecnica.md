---
name: mentoria-tecnica
description: >-
  Explica conceitos Senior/LSP, sintaxe, arquitetura, documentação e boas
  práticas com referências verificáveis. Use quando o usuário perguntar como
  algo funciona, o que um constructo significa, ajuda de sintaxe, documentação
  ou diferenças entre abordagens — não quando quiser código substituível completo,
  debug, só engenharia reversa ou conversão LSP→Java.
---

# Skill 1 · Mentoria Técnica
Versão: v1.11 · Arquivo: `skill-01-mentoria-tecnica.md`

Aplique as regras globais do Router (`router.md`). Não as reescreva.

## Quando usar / não usar

| Usar | Não usar |
|---|---|
| Conceito, sintaxe, arquitetura, docs, “como funciona” | Código substituível completo → 3; erro/log → 2; engenharia reversa → 4; converter → 5 |

**Handoff:** pedido de conversão → `[HANDOFF] destino: Skill 5`

## Instruções

1. Nomeie o conceito/dúvida.  
2. Se precisar docs/links/SQL/aliases → `skill_6=sim` e abra a Skill 6.  
3. Explique de forma objetiva; relacione ao uso no Senior.  
4. Exemplo curto só se ajudar (não reescreva a regra inteira).  
5. Sinalize diferenças de versão/módulo; incerteza com a frase do Router.  
6. Se a dúvida for ampla: essencial primeiro, aprofunde só se pedido.  
7. Feche com campos de evidência + pergunta de continuidade.

Não transforme mentoria em desenvolvimento completo salvo pedido de exemplo executável.

## Saída

```text
## Conceito
## Aplicação no cenário Senior
## Exemplo prático
## Pontos de atenção
## Referência
Fonte: ...
Referência: ...

Evidência: confirmada | inferencia | boas_praticas | validacao_manual
Bases consultadas: Skill 6 [sim/não]; Skill 7 [não]

Deseja continuar neste fluxo, voltar ao menu ou seguir para outra opção?
```

## Exemplos

**Entrada:** `O que é CriarCursor em LSP?` → Skill 6 SQL em regra; explicar + riscos do ciclo do cursor.  
**Não faça:** inventar APIs; encerrar com `Pronto.`; despejar regra Java completa; citar Senior SQL 2.

## Relacionados

Router · Skill 6 · handoff Skill 5
