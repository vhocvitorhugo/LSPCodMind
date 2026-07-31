---
name: base-documentacao-banco
description: >-
  Base interna de links autorizados da documentação Senior e aliases ERP/HCM.
  Use quando qualquer skill precisar citar docs oficiais, validar links de SQL
  em regra, web services, sintaxe LSP, URLs de equivalência HCM ou interpretar
  aliases de tabela/campo. Nunca trate como Senior SQL 2.
---

# Skill 6 · Base de Documentação e Banco
Versão: v1.7 · Interna · `skill-06-base-documentacao-banco.md`

Não entra no menu 1–5. Aplique as regras globais do Router (`router.md`).

## Quando usar / não usar

| Usar | Não usar |
|---|---|
| Link oficial, SQL em regra, WS, sintaxe LSP, URL de equivalência HCM, alias | Conversa casual; substituir padrões de conversão da Skill 7 |

Não exponha “Skill 6” ao usuário — cite só a fonte validada.

## Restrições absolutas

1. Somente os links listados **neste arquivo** são oficiais nesta versão do treinamento.  
2. Tópico ausente → `Não encontrei link autorizado na base atual para validar esse ponto com segurança.`  
3. Antes de citar: a página deve ter conteúdo específico, não portal/índice.  
4. Não reescreva `index.htm#...` para URLs diretas inventadas.  
5. Senior SQL 2 proibido — use só links de SQL em regra / SP / proprietária.  
6. Aliases são `auxiliar` até o schema real confirmar.  
7. Apostilas LSP/APO/Rubi: **não estão no repo** (`ausente_no_repo`); anexos do usuário são só complementares.

## Instruções

```text
1. Identificar tópico (sintaxe|WS|SQL|evento|equivalência HCM|alias)
2. Localizar seção abaixo
3. Classificar cobertura: confirmado | auxiliar | ausente
4. Devolver à skill chamadora: achado + classificação + limite
5. Nunca inventar link/alias “quase igual”
```

## Índice

| Tópico | Seção |
|---|---|
| Sintaxe / variáveis / limites LSP | Links — Sintaxe |
| Web services / HTTP / JSON / FTP | Links — Integração |
| SQL em regra / SP / proprietária / arquivos | Links — Banco |
| Usuários / AD / diretórios | Links — Acesso |
| Eventos / workflow / relatórios | Links — Eventos |
| Equivalência LSP→Java / índice de funções HCM | Links — Conversão |
| Aliases de tabela/campo | Mapeamento banco |

## Links — Sintaxe (Tecnologia 5.10.4)

- https://documentacao.senior.com.br/tecnologia/5.10.4/index.htm#lsp/sintaxe-de-comandos-e-operadores.htm
- https://documentacao.senior.com.br/tecnologia/5.10.4/index.htm#lsp/declaracao-de-variaveis.htm
- https://documentacao.senior.com.br/tecnologia/5.10.4/index.htm#lsp/limite-das-regras.html
- https://documentacao.senior.com.br/tecnologia/5.10.4/cbds/mascara.htm

## Links — Integração

- https://documentacao.senior.com.br/tecnologia/5.10.4/index.htm#lsp/chamar-web-service-via-regra.htm
- https://documentacao.senior.com.br/tecnologia/5.10.4/index.htm#lsp/funcoes/requisicoes-http.htm
- https://documentacao.senior.com.br/tecnologia/5.10.4/index.htm#lsp/funcoes/criacao-json-token-web.htm
- https://documentacao.senior.com.br/tecnologia/5.10.4/index.htm#lsp/funcoes/regra-para-web-services.html
- https://documentacao.senior.com.br/tecnologia/5.10.4/index.htm#lsp/funcoes/ftp.htm

## Links — Banco (SQL em regra — nunca Senior SQL 2)

- https://documentacao.senior.com.br/tecnologia/5.10.4/index.htm#lsp/funcoes/sql-em-regra.html
- https://documentacao.senior.com.br/tecnologia/5.10.4/index.htm#lsp/funcoes/execucao-de-stored-procedures-nas-regras.htm
- https://documentacao.senior.com.br/tecnologia/5.10.4/index.htm#lsp/funcoes/manipulacao-da-proprietaria.html
- https://documentacao.senior.com.br/tecnologia/5.10.4/index.htm#lsp/funcoes/manipulacao-de-arquivos-texto.htm

## Links — Acesso

- https://documentacao.senior.com.br/tecnologia/5.10.4/index.htm#lsp/funcoes/manipulacao-de-usuarios-e-grupos.htm
- https://documentacao.senior.com.br/tecnologia/5.10.4/index.htm#lsp/funcoes/integracao-servidor-ad.htm
- https://documentacao.senior.com.br/tecnologia/5.10.4/index.htm#lsp/permissao-de-diretorios.htm

## Links — Eventos

- https://documentacao.senior.com.br/tecnologia/5.10.4/index.htm#geradores/importacao-exportacao/regras-por-evento.htm
- https://documentacao.senior.com.br/tecnologia/5.10.4/index.htm#lsp/funcoes/workflow.html
- https://documentacao.senior.com.br/tecnologia/5.10.4/index.htm#lsp/funcoes/gerador-de-relatorios.htm
- https://documentacao.senior.com.br/tecnologia/5.10.4/index.htm#lsp/funcoes/agendamento-de-compromissos.htm
- https://documentacao.senior.com.br/tecnologia/5.10.4/lsp/funcoes/gerais.html

## Links — Conversão (HCM 6.10.4)

- Equivalência: https://documentacao.senior.com.br/gestao-de-pessoas-hcm/6.10.4/informacoes-adicionais/rotinas/gpo/integracao-controle-ponto-refeitorio/equivalencia-funcoes-regras.htm
- Índice de funções: https://documentacao.senior.com.br/gestao-de-pessoas-hcm/6.10.4/customizacoes/funcoes.htm

## Mapeamento banco (auxiliar)

Frase: `O mapeamento sugere essa equivalência, mas a confirmação depende de validação no schema/dicionário de dados.`

### Tabelas ERP

| Termo | Candidato | Cobertura |
|---|---|---|
| NF Saída / Venda | `E120NFV` | auxiliar |
| Item NF Saída | `E140NFV` | auxiliar |

Campos ERP: **ausente** — pedir schema / `validacao_manual`.

### HCM

| Origem | Candidato | Cobertura |
|---|---|---|
| R035DEP (termo) | `R036DEP` | auxiliar |
| R034FUN.SitCol | `SitAfa` | auxiliar |
| R034FUN.DatDem | `DatAfa` | auxiliar |
| R036DEP.ParDep | `GraPar` | auxiliar |
| R024CAR.DesCar / Cargo | `TitRed` | auxiliar |
| SitAfa Demitido | `7` | auxiliar |

Precedência SQL: alias → candidato → confirmar módulo → filtros/chaves → nunca existência absoluta só com esta tabela.

## Saída para a skill chamadora

```text
topico: ...
cobertura: confirmado | auxiliar | ausente
achado: ...
link_ou_alias: ...
limite: ...
```

## Relacionados

Política de evidência do Router · Skill 7 (após docs oficiais)
