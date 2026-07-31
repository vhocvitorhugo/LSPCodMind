---
name: conversao-lsp-java
description: >-
  Converte regras LSP Senior para Java (HCM/Gestão do Ponto) com inventário,
  mapeamento, fases A/B/C e entrega consolidada. Use ao converter, migrar ou
  mapear LSP→Java. Sempre execute o gate da Skill 9 antes de publicar a Fase C.
  Prefira documentação oficial (Skill 6) aos padrões da Skill 7.
---

# Skill 5 · Conversão LSP → Java
Versão: v1.8 · Arquivo: `skill-05-conversao-lsp-java.md`

Aplique as regras globais do Router. Preserve a **intenção funcional**, não a sintaxe literal.

## Quando usar / não usar

| Usar | Não usar |
|---|---|
| Converter/migrar/mapear LSP→Java / HCM Ponto | Conceito → 1; debug → 2; só criar LSP → 3; só engenharia reversa → 4 |

**Handoff:** só explicar → 4; gate FAIL → corrigir aqui e reexecutar 9; auditoria avulsa → 9

## Restrições locais

1. Fases A→B→C; sem Java final antes do inventário (salvo formato já pedido e A+C na mesma resposta transparente).  
2. Java só consolidado; sem pedaços / `// restante`.  
3. Nunca invente assinaturas; desconhecido → `validacao_manual`.  
4. Ordem de parâmetros não se presume igual à LSP.  
5. SQL/cursor → API semântica antes de EntitySession.  
6. Skill 6 obrigatória para docs; Skill 7 obrigatória em HCM/Ponto; **6 prevalece** em conflito.  
7. **Fase C:** rascunho → **gate Skill 9** → publicar com resumo do check.  
8. Sem links de download inventados.

## Fases

```text
A  Inventário + mapeamento + plano   (sem Java final)
   → se o usuário já pediu canvas|doc|código inteiro → pular B e ir à C após A
B  Perguntar 1=canvas / 2=documento  (sem Java final)
C  Rascunho Java completo → gate Skill 9 → publicar
```

### Tabela de inventário (A)

| Item LSP | Tipo | Uso na regra | Equivalente Java / padrão | Evidência | Status |

Regras: End → candidato a retorno; arrays → coleções/métodos; horas → minutos (`14:30`→`870`).

## Instruções

1. Leia a LSP inteira; defina contexto: `apuracao|consistencia|bloqueio|fechamento_bh|geral|indefinido`.  
2. Consulte Skill 6 (links) e Skill 7 (**catálogo oficial de equivalência** + exemplos).  
3. Monte inventário; mapeie com rótulos `confirmada|adaptacao_arquitetural|padrao_anexo|inferencia|validacao_manual`. Item achado no catálogo oficial da Skill 7 → preferir `confirmada`.  
4. Mecânica antes da sintaxe.  
5. Execute A/B/C; gate na C.

Âncoras: Skill 7 — catálogo oficial Senior + `getHorSit`/`setHorSit`/`zeraHorasSituacao`/`getDefinicaoSituacoes`.  
**Não** usar `getSituacao(...).getMinutos()/setMinutos(...)`.  
Cursor `R014SIN`/`R030EMP` para `CodDsi` → `getDefinicaoSituacoes().getCodigo()` (Skill 7).  
Fontes: [equivalência](https://documentacao.senior.com.br/gestao-de-pessoas-hcm/6.10.4/informacoes-adicionais/rotinas/gpo/integracao-controle-ponto-refeitorio/equivalencia-funcoes-regras.htm) · [índice de funções](https://documentacao.senior.com.br/gestao-de-pessoas-hcm/6.10.4/customizacoes/funcoes.htm).

## Saída — Fase A

```text
## Objetivo da regra original
## Resumo da lógica de negócio
## Contexto de execução
## Inventário de conversão
(tabela)
## Mapeamento LSP → Java (plano)
## Itens sem equivalência direta

Evidência: ...
Bases consultadas: Skill 6 [sim]; Skill 7 [sim]
[pergunta Fase B, se necessário]
+ continuidade
```

## Saída — Fase C (após o gate)

```text
## Objetivo / Inventário / Mapeamento
## Código Java convertido   [completo]
## Comentários técnicos
## Itens sem equivalência / validação manual
## Referência documental
Status da conversão: COMPLETA
Formato de entrega: ...

Evidência: ...
Bases consultadas: Skill 6 [sim]; Skill 7 [sim]

## Check determinístico (Skill 9)
Veredito: PASS | FAIL
Origem: Skill 5
Ciclos de correção: 0|1|2
Falhas remanescentes: ...

+ continuidade
```

## Exemplos

**A→B:** converter sem formato → inventário + perguntar 1/2.  
**Pular B + gate:** “no canvas, regra toda” → rascunho A+C → Skill 9 → publicar.  
**Não faça:** publicar C sem Skill 9; inventar `XYZInexistente`; entregar em partes.

## Relacionados

Router · Skills 6 e 7 · gate Skill 9
