---
name: base-documentacao-banco
description: >-
  Núcleo da base interna de documentação Senior e aliases ERP/HCM. Use quando
  qualquer skill precisar citar docs oficiais, SQL em regra, WS, sintaxe LSP ou
  aliases. Carregue sob demanda skill-06-referencia-links e
  skill-06-referencia-aliases. Nunca trate como Senior SQL 2.
---

# Skill 6 · Base de Documentação e Banco
Versão: v1.16 · Interna · `skill-06-base-documentacao-banco.md`

Não entra no menu 1–4. Aplique as regras globais do Router (`router.md`).

**Fronteira:** este **núcleo** = ritual + restrições + índice + saída tipada. Detalhes em `skill-06-referencia-*` (progressive disclosure).  
**Não** leia as referências de ponta a ponta — só a âncora necessária.  
**Limite do repo:** no máximo **10** arquivos `skill-*.md` (sem contar `router.md`).

## Quando usar / não usar

| Usar | Não usar |
|---|---|
| Link oficial, SQL em regra, WS, sintaxe LSP, alias | Conversa casual; inventar URL “parecida” |

Não exponha “Skill 6” ao usuário — cite só a fonte validada.

## Como consultar (ordem)

```text
A. Restrições + ritual (neste arquivo)   ← nunca pular
B. Identificar tópico (sintaxe|WS|SQL|evento|alias|apostila)
C. Links oficiais — skill-06-referencia-links (só a seção)
D. Aliases / apostilas — skill-06-referencia-aliases (mapa ou anexo)
E. Saída tipada para a skill chamadora
```

## Ritual de revisão de links (manutenção do treinamento)

A cada bump de versão que toque docs/links **ou** a cada ciclo de manutenção da Skill 6:

1. Percorra **todos** os links em `skill-06-referencia-links.md`.  
2. Classifique cada um: `ok` | `quebrado` | `redirecionou_para_indice` | `ausente`.  
3. Link `quebrado` / índice genérico → **não citar** no atendimento; marque ou remova na próxima entrega.  
4. Tópico sem URL válida → frase de link ausente.  
5. Não adicione URL “parecida” sem validar conteúdo específico.  
6. Registre no `CHANGELOG.md` (local) se houve remoção/substituição.

## Restrições absolutas

1. Somente os links de `skill-06-referencia-links.md` são oficiais nesta versão.  
2. Tópico ausente → `Não encontrei link autorizado na base atual para validar esse ponto com segurança.`  
3. Antes de citar: a página deve ter conteúdo específico, não portal/índice.  
4. Não reescreva `index.htm#...` para URLs diretas inventadas.  
5. Senior SQL 2 proibido — use só links de SQL em regra / SP / proprietária.  
6. Aliases (referencia-aliases) são `auxiliar` até o schema real confirmar. **Nunca** diga “está confirmado” só com esta base.  
7. Apostilas: **ausente_no_repo**; anexos = `Material complementar` (seção em referencia-aliases).

## Índice rápido → referência

| Precisa de… | Vá para |
|---|---|
| URLs sintaxe / WS / SQL / acesso / eventos | [`skill-06-referencia-links.md`](skill-06-referencia-links.md) |
| Alias tabela/campo ERP/HCM ou apostila anexada | [`skill-06-referencia-aliases.md`](skill-06-referencia-aliases.md) |

## Instruções

```text
1. Identificar tópico
2. Abrir só a referência âncora (links | aliases)
3. Classificar cobertura: confirmado | auxiliar | ausente
4. Devolver à skill chamadora: achado + classificação + limite
5. Nunca inventar link/alias “quase igual”
```

## Saída para a skill chamadora

```text
topico: ...
cobertura: confirmado | auxiliar | ausente
achado: ...
link_ou_alias: ...
limite: ...
referencia_carregada: links | aliases | nenhuma
```

## Relacionados

Router · Skills 1–4 / 9 · [`skill-06-referencia-links.md`](skill-06-referencia-links.md) · [`skill-06-referencia-aliases.md`](skill-06-referencia-aliases.md)
