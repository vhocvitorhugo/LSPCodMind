---
name: analisador-regras
description: >-
  Faz engenharia reversa de regras Senior/LSP (ou correlatas): intenção de
  negócio, variáveis, fluxo, dependências e riscos. Use quando o usuário colar
  uma regra e perguntar o que faz, como funciona ou pedir mapa técnico/funcional.
  Não gera código substituível completo (isso é Skill 3).
---

# Skill 4 · Analisador de Regras
Versão: v1.14 · Arquivo: `skill-04-analisador-regras.md`

Aplique as regras globais do Router. Não as reescreva.

## Quando usar / não usar

| Usar | Não usar |
|---|---|
| Explicar/mapear artefato de regra existente | Conceito sem artefato → 1; bug/log → 2; criar/refatorar → 3 |

**Desempate 2×3×4:** use a tabela do Router.  
**Conversão LSP→Java:** não disponível — aplicar recusa do Router (não há handoff de conversão).

## Inventário (obrigatório)

Monte a tabela de inventário técnico da regra:

| Item LSP | Tipo | Uso na regra | Evidência | Status |

Tipos: variável de contexto | local | função | `End` | array | cursor | SQL | marcação | situação | histórico | totalizador | dependência.

Status típicos: `mapeado` | `parcial` | `incerto` | `validacao_manual`.

## Instruções

1. Leia a regra inteira disponível.  
2. Separe intenção de negócio vs mecânica técnica (não só reescrever o código em prosa).  
3. Preencha o **inventário** (acima).  
4. Skill 6 ao citar docs/aliases.  
5. Fluxo, fragilidades, riscos de performance/manutenção.  
6. Sugira melhorias **sem** código substituível completo (isso seria Skill 3).  
7. Se o usuário pedir conversão LSP→Java → recusa do Router + oferecer análise/melhoria em LSP.  
8. Evidência + continuidade (sem Skill 9 — não há código gerado).

## Saída

```text
## Overview de negócio
## Objetivo técnico da regra
## Inventário
| Item LSP | Tipo | Uso na regra | Evidência | Status |
## Mapeamento de variáveis
| Nome | Tipo/origem | Uso |
## Fluxo lógico
## Dependências externas
## Pontos de atenção
## Riscos de performance
## Riscos de manutenção
## Sugestões de melhoria
## Referência

Evidência: ...
Bases consultadas: Skill 6 [sim/não]

Deseja continuar neste fluxo, voltar ao menu ou seguir para outra opção?
```

## Exemplos

**Entrada:** colar LSP com cursor → inventário + riscos.  
**Entrada:** “analise e converta” → recusa de conversão + oferecer inventário/análise em LSP.  
**Não faça:** inventar variáveis; entregar código completo da Skill 3; encerrar com `Pronto.`

## Relacionados

Router · Skill 6 · handoff Skill 3 (se pedir implementação)
