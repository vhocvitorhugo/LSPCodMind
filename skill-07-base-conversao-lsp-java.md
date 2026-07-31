# Skill 7 | Base de Conversão LSP → Java e Exemplos Sanitizados
Versão: v1.1  
Arquivo: `skill-07-base-conversao-lsp-java.md`  
Tipo: **base interna** (não aparece no menu)

Consultada principalmente pela **Skill 5** em conversões HCM (Controle de Ponto / Refeitório / Apuração / Banco de Horas).

Aplique as **HARD CONSTRAINTS globais** do `router.md` (§1).  
**Doc oficial (Skill 6) prevalece** sobre esta base em qualquer conflito.

---

## WHEN / NOT WHEN

| | |
|---|---|
| **Usar quando** | Conversão/migração/equivalência prática LSP→Java em Ponto/HCM; padrões de classe; armadilhas; comparação com exemplos sanitizados |
| **Não usar quando** | Mentoria genérica sem conversão; substituir a Skill 6 como “prova oficial” |
| **Expor ao usuário?** | Não como “Skill 7”; fale em padrões de conversão / exemplos sanitizados |

---

## HARD CONSTRAINTS + DELIMITAÇÃO DO CATÁLOGO

1. Esta base é **complementar**. Classifique achados aqui como:  
   `Padrão observado em materiais complementares anexados` ou `inferencia` — **não** como equivalência oficial, salvo confirmação na Skill 6.  
2. **Sigilo:** nunca exponha clientes, empresas, pacotes, consultores ou caminhos. Use “exemplos sanitizados” / “materiais complementares anexados”.  
3. **Catálogo completo de centenas de variáveis/métodos NÃO está embutido neste arquivo.**  
   O que existe abaixo é o **mapeamento operacional mínimo** + esqueletos.  
4. **Regra anti-alucinação (obrigatória):**  
   Se a variável/função LSP **não** estiver nesta base **e** **não** for confirmada na documentação oficial (Skill 6) **e** **não** estiver em anexo validado do usuário →  
   `Status = validacao_manual` — **NÃO inventar** nome/assinatura de método Java.  
5. Horas em APIs de ponto = inteiros em **minutos**.  
6. SQL/cursor → priorize API semântica do módulo antes de EntitySession/SQL.  
7. Toda variável/função de contexto LSP vira chamada de método — nada “solto” no Java.

---

## WORKFLOW DE CONSULTA

```text
1. Skill 5 identifica contexto (Apuracao, FechamentoBH, etc.)
2. Buscar âncora nesta base (seção 3–4)
3. Confirmar assinatura/equivalência na Skill 6 (doc oficial)
4. Se só houver padrão aqui → evidência = padrao_anexo / inferencia
5. Se não houver em lugar nenhum → validacao_manual (não inventar)
```

---

## 1) Workflow de conversão recomendado (apoio à Skill 5)

1. **Contexto:** em qual classe a regra roda (`Apuracao`, `FechamentoBH`, …).  
2. **Inventariar:** DatPro, HorSis, ApuDiu[], HorSit, FPxMar, RetBHRDat, cursores, End, etc.  
3. **Mapear:** equivalente Java + assinatura + ordem dos parâmetros.  
4. **Mecânica:** getters/setters; horas→minutos; End→retorno; arrays→coleções/métodos.  
5. **Sintaxe:** tipagem, laços, exceções, log via contexto.

---

## 2) Padrões estruturais (esqueletos)

### Apuração de Ponto
```java
@Rule(description = "Regra de Apuracao")
public class RegraApuracao extends Apuracao {
    @Override
    public void execute() {
        ContextoGeralRH contextoGeral = getContainer().getContextoGeral();
        ContextoApuracao contextoApuracao = getContainer().getContextoApuracao();
        // Recuperar colaborador, data e contexto.
        // Aplicar regras de negócio.
        // Atualizar situações via métodos semânticos.
    }
}
```

### Fechamento de Banco de Horas
```java
@Rule(description = "Regra de Fechamento de Banco de Horas")
public class RegraFechamentoBH extends FechamentoBH {
    @Override
    public void execute() {
        ContextoGeralRH contextoGeral = getContainer().getContextoGeral();
        ContextoFechamentoBH contextoFechamentoBH = getContainer().getContextoFechamentoBH();
        // Dados de fechamento, colaborador, banco e saldo.
    }
}
```

---

## 3) Mapeamento operacional mínimo

> Âncoras práticas. Confirme na Skill 6 antes de marcar `confirmada`.

### Situações apuradas
| Intenção | Âncora Java |
|---|---|
| Ler horas da situação | `contextoApuracao.getHorSit(codigoSituacao)` |
| Definir/ajustar horas | `contextoApuracao.setHorSit(codigoSituacao, minutos)` |
| Zerar situação | `contextoApuracao.zeraHorasSituacao(codigoSituacao)` |
| Situação anterior | `contextoApuracao.getHorSitAnterior(codigoSituacao)` |
| Somar horas | `contextoApuracao.somaHorasSituacao(...)` |

### Colaborador e contexto
| Intenção | Âncora Java |
|---|---|
| Empresa / tipo / cadastro | `colaborador.getNumEmp()` / `getTipCol()` / `getNumCad()` |
| Data processada | `contextoApuracao.getData()` |
| Históricos | `getHistoricoSindicato()`, `getHistoricoVinculo()`, `getHistoricoCargo()`, `getHistoricoEscala()`, `getHistoricoCentrodeCusto()`, `getHistoricoFilial()` |

### Marcações e totais
| Intenção | Âncora Java |
|---|---|
| Marcações realizadas | `contextoApuracao.getMarcacoesRealizadas(...)` |
| Totais de situações | `contextoApuracao.getTotalSituacoes(...)` |

### Escala / horário
| Intenção | Âncora Java |
|---|---|
| Escala atual / prevista | `getEscala()` / `getEscalaPrevistaColaborador(...)` |
| Horário atual / previsto | `getHorario()` / `getHorarioPrevistoColaborador(...)` |

---

## 4) Armadilhas frequentes

| Armadilha | Ação correta |
|---|---|
| Copiar ordem dos parâmetros LSP→Java | Confirmar assinatura na doc |
| Manter hora como string/`HH:mm` em API de minutos | Converter para minutos (`14:30` → `870`) |
| Replicar cursor SQL por reflexo | Buscar API semântica primeiro |
| Inventar método “parecido” | `validacao_manual` |
| Expor nome de cliente do exemplo | Sanitizar sempre |

---

## 5) Exemplos sanitizados

Nesta versão do repositório, exemplos completos de regras reais **não** estão versionados neste arquivo (sigilo).  
Se o usuário anexar exemplos: use-os como padrão observado, sanitize identificadores e **não** os trate como doc oficial.

---

## Saída para a Skill 5 (formato interno)

```text
contexto: Apuracao | FechamentoBH | outro | indefinido
ancora_encontrada: sim | nao
metodo_ou_padrao: ...
evidencia_sugerida: padrao_anexo | inferencia | validacao_manual
requer_skill_6: sim
limite: ...
```
