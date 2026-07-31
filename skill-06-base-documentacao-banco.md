# Skill 6 | Base de Documentação, Links Autorizados e Banco
Versão: v1.2  
Arquivo: `skill-06-base-documentacao-banco.md`  
Tipo: **base interna** (não aparece no menu)

Consultada pelo Router e pelas Skills 1–5 quando houver necessidade de documentação oficial Senior, links autorizados ou interpretação de aliases/tabelas/campos/domínios ERP/HCM.

Aplique as **HARD CONSTRAINTS globais** do `router.md` (§1).

---

## WHEN / NOT WHEN

| | |
|---|---|
| **Usar quando** | Precisar citar/confirmar doc oficial, link Senior, SQL em regra, WS, sintaxe LSP, equivalência HCM, alias/tabela/campo |
| **Não usar quando** | Atendimento casual sem necessidade de fonte; catálogo operacional de conversão Ponto (→ Skill 7, após esta base para doc oficial) |
| **Expor ao usuário?** | Não como “Skill 6”; cite só a fonte/link validado |

---

## HARD CONSTRAINTS

1. **Só** os links listados abaixo contam como documentação oficial Senior nesta versão.  
2. Proibido adicionar/inferir outros links como oficiais.  
3. Se o tópico não estiver coberto:  
   `Não encontrei link autorizado na base atual para validar esse ponto com segurança.`  
4. Antes de citar: página deve abrir **conteúdo específico** (não só portal/índice). Senão:  
   `Não consegui validar o conteúdo específico desse link. O endereço abriu apenas o portal/índice da documentação.`  
5. Não substitua `index.htm#...` por URLs “diretas” inventadas.  
6. Senior SQL 2 proibido em qualquer hipótese ligada a SQL/cursor em regra.  
7. Aliases desta skill são **auxiliares** (`validacao_manual` até schema/dicionário real).  
8. **Apostilas LSP/APO/Rubi:** nesta versão **não há apostilas embutidas no repositório**. Se o usuário anexar apostilas, trate como material complementar (não substituem links oficiais). Cobertura: `ausente_no_repo`.

---

## WORKFLOW DE CONSULTA (obrigatório)

```text
1. Identificar tópico (sintaxe | WS | SQL | evento | equivalência HCM | alias ERP/HCM)
2. Localizar o link/alias na seção correspondente abaixo
3. Cobertura:
   - confirmado = link listado + página específica validada
   - auxiliar   = alias desta base (não é schema oficial)
   - ausente    = não listado → usar frase de incerteza
4. Devolver à skill chamadora: achado + classificação + limite
5. Nunca inventar entrada “quase igual”
```

---

## Índice rápido → seção

| Tópico | Seção |
|---|---|
| Sintaxe/variáveis/limites LSP | § Links — Sintaxe |
| Web services / HTTP / JSON / FTP | § Links — Integração |
| SQL em regra / SP / proprietária / arquivos | § Links — Banco |
| Usuários / AD / diretórios | § Links — Acesso |
| Eventos / workflow / relatórios | § Links — Eventos |
| Equivalência LSP→Java / índice funções HCM | § Links — Conversão |
| Alias tabela/campo ERP ou HCM | § Mapeamento banco |

---

## Links autorizados — Senior 5.10.4 / HCM 6.10.4

### Sintaxe e estrutura (LSP / Tecnologia 5.10.4)
- https://documentacao.senior.com.br/tecnologia/5.10.4/index.htm#lsp/sintaxe-de-comandos-e-operadores.htm
- https://documentacao.senior.com.br/tecnologia/5.10.4/index.htm#lsp/declaracao-de-variaveis.htm
- https://documentacao.senior.com.br/tecnologia/5.10.4/index.htm#lsp/limite-das-regras.html
- https://documentacao.senior.com.br/tecnologia/5.10.4/cbds/mascara.htm

### Integração e Web Services
- https://documentacao.senior.com.br/tecnologia/5.10.4/index.htm#lsp/chamar-web-service-via-regra.htm
- https://documentacao.senior.com.br/tecnologia/5.10.4/index.htm#lsp/funcoes/requisicoes-http.htm
- https://documentacao.senior.com.br/tecnologia/5.10.4/index.htm#lsp/funcoes/criacao-json-token-web.htm
- https://documentacao.senior.com.br/tecnologia/5.10.4/index.htm#lsp/funcoes/regra-para-web-services.html
- https://documentacao.senior.com.br/tecnologia/5.10.4/index.htm#lsp/funcoes/ftp.htm

### Banco de Dados e Sistema (usar estes para SQL em regra — nunca Senior SQL 2)
- https://documentacao.senior.com.br/tecnologia/5.10.4/index.htm#lsp/funcoes/sql-em-regra.html
- https://documentacao.senior.com.br/tecnologia/5.10.4/index.htm#lsp/funcoes/execucao-de-stored-procedures-nas-regras.htm
- https://documentacao.senior.com.br/tecnologia/5.10.4/index.htm#lsp/funcoes/manipulacao-da-proprietaria.html
- https://documentacao.senior.com.br/tecnologia/5.10.4/index.htm#lsp/funcoes/manipulacao-de-arquivos-texto.htm

### Gestão de Acesso e Usuários
- https://documentacao.senior.com.br/tecnologia/5.10.4/index.htm#lsp/funcoes/manipulacao-de-usuarios-e-grupos.htm
- https://documentacao.senior.com.br/tecnologia/5.10.4/index.htm#lsp/funcoes/integracao-servidor-ad.htm
- https://documentacao.senior.com.br/tecnologia/5.10.4/index.htm#lsp/permissao-de-diretorios.htm

### Específicas e Eventos
- https://documentacao.senior.com.br/tecnologia/5.10.4/index.htm#geradores/importacao-exportacao/regras-por-evento.htm
- https://documentacao.senior.com.br/tecnologia/5.10.4/index.htm#lsp/funcoes/workflow.html
- https://documentacao.senior.com.br/tecnologia/5.10.4/index.htm#lsp/funcoes/gerador-de-relatorios.htm
- https://documentacao.senior.com.br/tecnologia/5.10.4/index.htm#lsp/funcoes/agendamento-de-compromissos.htm
- https://documentacao.senior.com.br/tecnologia/5.10.4/lsp/funcoes/gerais.html

### Conversão LSP → Java — fontes prioritárias (HCM 6.10.4)
- Equivalência das funções de regras:  
  https://documentacao.senior.com.br/gestao-de-pessoas-hcm/6.10.4/informacoes-adicionais/rotinas/gpo/integracao-controle-ponto-refeitorio/equivalencia-funcoes-regras.htm
- Índice das Funções:  
  https://documentacao.senior.com.br/gestao-de-pessoas-hcm/6.10.4/customizacoes/funcoes.htm

---

## Mapeamento de banco (auxiliar)

**Natureza:** equivalências **prováveis**. Não substituem schema/dicionário.  
Frase padrão:  
`O mapeamento sugere essa equivalência, mas a confirmação depende de validação no schema/dicionário de dados.`

### ERP — tabelas
| Termo funcional | Candidato | Cobertura |
|---|---|---|
| Nota Fiscal de Saída / NF Saída / Venda | `E120NFV` | auxiliar |
| Item NF Saída / Itens de Venda | `E140NFV` | auxiliar |

Campos ERP: **ausente** nesta base — solicitar schema ou `validacao_manual`.

### HCM — tabelas / campos / domínios
| Origem | Candidato | Cobertura |
|---|---|---|
| R035DEP (termo) | `R036DEP` (Dependentes) | auxiliar |
| R034FUN.SitCol | `SitAfa` | auxiliar |
| R034FUN.DatDem | `DatAfa` | auxiliar |
| R036DEP.ParDep | `GraPar` | auxiliar |
| R024CAR.DesCar / DescricaoCargo / Cargo | `TitRed` | auxiliar |
| R034FUN.SitAfa Demitido | `7` | auxiliar |

### Precedência SQL
1. Traduzir alias → candidato  
2. Confirmar módulo (ERP vs HCM)  
3. Validar filtros/chaves  
4. Nunca afirmar existência absoluta só com esta base  

---

## Saída para a skill chamadora (formato interno)

```text
topico: ...
cobertura: confirmado | auxiliar | ausente
achado: ...
link_ou_alias: ...
limite: ...
```
