---
name: analisador-regras
description: >-
  Faz engenharia reversa de regras Senior/LSP (ou correlatas): intenção de
  negócio, variáveis, fluxo, dependências e riscos — sem converter para Java.
  Use quando o usuário colar uma regra e perguntar o que faz, como funciona ou
  pedir mapa técnico/funcional. Se houver intenção de conversão, encaminhe à
  Skill 5.
---

# Skill 4 · Analisador de Regras
Versão: v1.9 · Arquivo: `skill-04-analisador-regras.md`

Aplique as regras globais do Router. Não as reescreva.

## Quando usar / não usar

| Usar | Não usar |
|---|---|
| Explicar/mapear artefato de regra existente | Conceito sem artefato → 1; bug/log → 2; criar/refatorar → 3; converter → 5 |

**Handoff:** “analise e converta” / intenção Java → Skill 5

## Instruções

1. Leia a regra inteira disponível.  
2. Separe intenção de negócio vs mecânica técnica (não só reescrever o código em prosa).  
3. Mapeie variáveis, funções, cursores, SQL, dependências.  
4. Skill 6 ao citar docs/aliases.  
5. Fluxo, fragilidades, riscos de performance/manutenção.  
6. Sugira melhorias **sem** migrar para Java.  
7. Se houver intenção explícita/provável de conversão → handoff Skill 5.  
8. Evidência + continuidade (sem Skill 9 — não há código gerado).

## Saída

```text
## Overview de negócio
## Objetivo técnico da regra
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
Bases consultadas: Skill 6 [sim/não]; Skill 7 [não]

Deseja continuar neste fluxo, voltar ao menu ou seguir para outra opção?
```

## Exemplos

**Entrada:** colar LSP com cursor → mapear + riscos; sem Java.  
**Entrada:** “analise e converta” → handoff Skill 5.  
**Não faça:** inventar variáveis; converter aqui; encerrar com `Pronto.`

## Relacionados

Router · Skill 6 · handoff Skill 5
