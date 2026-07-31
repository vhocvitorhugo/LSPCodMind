---
name: base-documentacao-banco-reference
description: >-
  Reference catalog of authorized Senior 5.10.4 / HCM 6.10.4 documentation URLs
  and auxiliary ERP/HCM aliases for Skill 6. Read when Skill 6 needs a concrete
  link or alias row. Not a menu skill.
---

# Skill 6 Reference · Links e aliases
Versão: v1.4 · Progressive disclosure for Skill 6

## Index

| Topic | Section |
|---|---|
| LSP syntax / variables / limits | Sintaxe |
| Web services / HTTP / JSON / FTP | Integração |
| SQL em regra / SP / proprietária / files | Banco |
| Users / AD / directories | Acesso |
| Events / workflow / reports | Eventos |
| LSP→Java equivalence / HCM function index | Conversão |
| Table/field aliases | Mapeamento |

---

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

## Links — Banco (SQL em regra — never Senior SQL 2)

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

---

## Mapeamento banco (auxiliar)

Phrase: `O mapeamento sugere essa equivalência, mas a confirmação depende de validação no schema/dicionário de dados.`

### ERP tables

| Term | Candidate | Coverage |
|---|---|---|
| NF Saída / Venda | `E120NFV` | auxiliar |
| Item NF Saída | `E140NFV` | auxiliar |

ERP fields: **ausente** — ask schema / `validacao_manual`.

### HCM

| Origin | Candidate | Coverage |
|---|---|---|
| R035DEP (term) | `R036DEP` | auxiliar |
| R034FUN.SitCol | `SitAfa` | auxiliar |
| R034FUN.DatDem | `DatAfa` | auxiliar |
| R036DEP.ParDep | `GraPar` | auxiliar |
| R024CAR.DesCar / Cargo | `TitRed` | auxiliar |
| SitAfa Demitido | `7` | auxiliar |

SQL precedence: alias → candidate → confirm module → filters/keys → never absolute existence from this table alone.
