---
name: base-conversao-lsp-java
description: >-
  Padrões e catálogo oficial de equivalência LSP→Java (HCM 6.10.4 / Gestão do
  Ponto): variáveis, funções, âncoras, armadilhas e exemplos. Use a partir da
  Skill 5 após Skill 6. Fonte prioritária: documentação Senior de equivalência
  das funções de regras. Nunca invente método ausente neste catálogo e na Skill 6.
---

# Skill 7 · Base de Conversão LSP → Java
Versão: v1.8 · Interna · `skill-07-base-conversao-lsp-java.md`

Não entra no menu. Aplique as regras globais do Router. Em conflito de assinatura, **revalide na Skill 6 / página oficial**.

## Fontes oficiais (consultar / citar)

| Fonte | URL | Uso |
|---|---|---|
| **Equivalência das funções de regras** (mapa LSP→Java) | https://documentacao.senior.com.br/gestao-de-pessoas-hcm/6.10.4/informacoes-adicionais/rotinas/gpo/integracao-controle-ponto-refeitorio/equivalencia-funcoes-regras.htm | Mapeamento oficial Controle de Ponto → Gestão do Ponto |
| **Índice das Funções** HCM 6.10.4 | https://documentacao.senior.com.br/gestao-de-pessoas-hcm/6.10.4/customizacoes/funcoes.htm | Detalhe/assinatura das funções Java/HCM |

Evidência dos itens do **Catálogo de equivalência** abaixo: `confirmada` (doc oficial Senior 6.10.4), salvo nota em contrário.

## Quando usar / não usar

| Usar | Não usar |
|---|---|
| Converter/mapear variáveis e funções de apuração LSP→Java | Só mentoria genérica; inventar método fora do catálogo |

## Restrições absolutas

1. Preferir o catálogo oficial deste arquivo; se faltar item → Skill 6 → `validacao_manual` (não inventar).  
2. Horas em APIs de ponto = **minutos inteiros**.  
3. SQL/cursor → API semântica do catálogo antes de EntitySession.  
4. **Proibido** `getSituacao(...).getMinutos()` / `setMinutos(...)` — use `getHorSit` / `setHorSit` / `zeraHorasSituacao`.  
5. Sanitize nomes de cliente em exemplos anexados.

## Instruções

```text
1. Identificar contexto (Apuracao, FechamentoBH, …)
2. Buscar item LSP no Catálogo de equivalência abaixo
3. Se precisar de detalhe de assinatura → Índice das Funções (Skill 6 / URL acima)
4. Aplicar mecânica (minutos, End→retorno, arrays→métodos)
5. Ausente no catálogo → validacao_manual
```

## Esqueletos de classe

### Apuração

```java
@Rule(description = "Regra de Apuracao")
public class RegraApuracao extends Apuracao {
    @Override
    public void execute() {
        ContextoGeralRH contextoGeral = getContainer().getContextoGeral();
        ContextoApuracao contextoApuracao = getContainer().getContextoApuracao();
    }
}
```

### Fechamento BH

```java
@Rule(description = "Regra de Fechamento de Banco de Horas")
public class RegraFechamentoBH extends FechamentoBH {
    @Override
    public void execute() {
        ContextoGeralRH contextoGeral = getContainer().getContextoGeral();
        ContextoFechamentoBH contextoFechamentoBH = getContainer().getContextoFechamentoBH();
    }
}
```

---

## Catálogo de equivalência (oficial Senior 6.10.4)

Fonte: [Equivalência das funções de regras](https://documentacao.senior.com.br/gestao-de-pessoas-hcm/6.10.4/informacoes-adicionais/rotinas/gpo/integracao-controle-ponto-refeitorio/equivalencia-funcoes-regras.htm).  
Coluna Java = equivalência no Gestão do Ponto. Métodos ficam tipicamente no `contextoApuracao` / container (confirmar assinatura no Índice das Funções).

### Data / sistema

| LSP (Controle de Ponto) | Java (Gestão do Ponto) |
|---|---|
| `DatPro` (implícito via Ano/Dia/MesPro) | `getData()` |
| `AnoPro` | `getAnoData(Date data)` / `getData()` |
| `MesPro` | `getMesData(Date data)` |
| `DiaPro` | `getDiaData(Date data)` |
| `AnoSis` / `MesSis` / `DiaSis` | `getAnoData` / `getMesData` / `getDiaData` |
| `HorSis` / `ExtSis` | Nativo em Java |
| `DatIni` / `Datfim` | `getDataInicial()` / `getDataFinal()` |
| `DiaSem`, `DiaDom`…`DiaSab` | `getDiaSem(Date data)` |
| `MesAtu` | `getMesData(Date data)` |
| `RetornaAnoData` / `RetornaDiaData` / `RetornaMesData` | `getAnoData` / `getDiaData` / `getMesData` |

### Situações / HorSit

| LSP | Java |
|---|---|
| `HorSit[]` | `getHorSit(...)`, `setHorSit(int codSit, int horas)`, `somaHorasSituacao(...)`, `zeraHorasSituacao(...)`, `zeraHorasSituacaoFaixa(...)`, `getHorSitFaixa(...)`, `getHorSitAnterior(int codSit)` |
| `SitAnt[]` | `getHorSitAnterior(int codSit)` |
| `TotSit[]` / `BuscaTotalizadoresSituacoes` | `getTotalSituacoes(int codigoTotalizador, date data)` (e overload com intervalo) |
| `MotSit` | `getMotivoAcerto(int situacao)` |

### Apuração diurna/noturna / trabalhadas / previstas

| LSP | Java |
|---|---|
| `ApuDiu[]` / `ApuNot[]` | `getHorasSeparadas(...)` / `getHoras(Marcacao, Marcacao, ...)` |
| `HrtRaD[]` / `HrtRan[]` / `TraDiu` / `TraNot` | `getHorasTrabalhadas(int parte)` |
| `MinPvd[]` / `MinPvn[]` / `PrvTra[]` / `PrvTrd` / `PrvTrn` / `VprVho` / `VprVin` / `VprVtr` | `getTotalMinutosPrevisto(...)` / `getHorasPrevistas(...)` / `getTotalMinutosPrevistoProrrogado(...)` |
| `FatRed` | `getHorarioPrevistoColaborador(...)` |
| `ExtrasIntervalo` | `getExtrasIntervalo` / `getExtrasIntervaloAnterior` / `getExtrasIntervaloPosterior` |
| `MinExD[]` / `MinExn[]` / `MsaInd[]` / `MsaInn[]` / `IniExt` / `FimExt` / `PerExt` / `PriExt` / `QtdExt` / `TipExt` / `DiaExt` | `getIntervalosCalculados()` / `getIntervaloCalculado(int indice)` |

### Marcações

| LSP | Java |
|---|---|
| `FPxMar` / `FLeMar` / `ConGer` / `DatMar` / `HorMar` / `FncMar` / `OriMar` / `RlgMar` / `UsoMar` | `getMarcacoesRealizadas(boolean conger)` |
| `QtdMar` / `TotMar` | `getQtdMarcacoesRealizadas(boolean conger)` |
| `DulMar` / `HulMar` | `getMarcacaoAnterior()` |
| `MinJor` | `getHorasInterjornadaRealizada()` |
| `MinMJo` | `getHorasInterjornadaPrevista()` |

### Escala / horário / filial / feriado

| LSP | Java |
|---|---|
| `EscAtu` | `getEscala()` |
| `EscEmp` / `RetEscEmp` | `getHistoricoEscala()` |
| `EscTrf` | `getEscalaHistorico()` |
| `TemTes` | `getTrocaEscala(Date data)` |
| `TemThr` | `getTrocaHorario(Date data)` |
| `RetornaEscala` | `getEscalaPrevistaColaborador(...)` |
| `CodHor` / `RetornaHorarioApurado` | `getHorario()` |
| `HorEsc` / `HorTrf` | `getHorarioEscala()` |
| `HorDFe` | `getHorarioOriginalEscala()` |
| `HorFol` | `getCodigoHorarioFolga()` / `getHorarioFolga()` |
| `HorPfo` | `getHorarioProjecaoFolga()` |
| `RetornaHorario` / `RetornaBatidaHorario` | `getHorarioPrevistoColaborador(...)` |
| `NumPer` | `getNumeroPeriodos(int codHor)` |
| `NumInt` | `getNumeroIntervalos()` |
| `NinRef` | `getNumeroIntervaloRefeicao()` |
| `TurInt` | `getTurmaIntervalo()` |
| `RetMinRefHTr` | `getMinutosRefeicaoPrevisto()` |
| `FilEmp` / `RetFilEmp` / `DatAltFil` / `EmpAltFil` | `getHistoricoFilial()` |
| `FerFil` | `getFeriadoFilial(Date data)` |
| `VerDatFer` | `getFeriado(Date data)` |

### Históricos colaborador / usuário

| LSP | Java |
|---|---|
| `CarEmp` / `EstCarEmp` / `RetCarEmp` | `getHistoricoCargo()` |
| `CcuEmp` / `DatAltCcu` / `RetCcuEmp` | `getHistoricoCentrodeCusto()` |
| `CodSinEmp` / `RetSinEmp` | `getHistoricoSindicato()` |
| `CodVinEmp` / `RetVinEmp` | `getHistoricoVinculo()` |
| `LocEmp` / `RetLocEmp` | `getHistoricoLocal(...)` |
| `CodAfs` / `IniAfs` / `FimAfs` / `TemAfs` / `QtdAfs[]` | `getHistoricosAfastamento()` |
| `BusCraTit` | `getHistoricosCracha()` / `getHistoricosCrachaProvisorio()` |
| `RetApuPon` | `getHistoricoApuracao(colaborador, data)` |
| `CodUsu` | `getUsuarioAtivo()` |
| `NomUsu` | `getUsuario(long codigoUsuario)` |
| `RetornaDesGrupo` / `RetornaQtdGrupos` | `getGrupos(long codigoUsuario)` |
| `AssociaUsuColab` | `associarUsuarioColaborador(...)` |
| `RetColabPorCodUsu` | `getUsuarioColaborador(...)` |

### Compensação / banco de horas / cálculo

| LSP | Java |
|---|---|
| `TemCmp[]` / `DtICmp[]` / `DtFCmp[]` / `PerCmp[]` / `QtdCmp[]` / `SitCmD[]` / `SitCmN[]` / `TipCmp[]` | `getCompensacoes()` / `getCompensacoes(LocalDate data)` |
| `LimBa1` / `LimBa2` | `getEscala()` |
| `RetBHRDat` | `getSaldoBanco(int banco, int empresa, int tipo, int cadastro, LocalDate data)` |
| `TipCal` | `getTipoCalculo()` |
| `MensagemLog` | `mensagemLog(String mensagem)` |
| `VerificaAbrangenciaNumero` | `getAbrangencia(string abrangencia, int numero)` |
| `RetornaCodLoc` / `RetornaNumLoc` / `RetNivLoc` | `getCodigoLocal` / `getNumeroLocal` / `getQtdNiveisLocal` |

### Definição de situações (padrão complementar observado)

Quando a LSP busca `CodDsi` via cursor em `R014SIN`/`R030EMP`, preferir API (evidência `padrao_anexo` até confirmar na doc):

```java
int codDsi = contextoApuracao.getDefinicaoSituacoes().getCodigo();
```

---

## Armadilhas práticas

| Armadilha | Correção |
|---|---|
| Copiar ordem de parâmetros LSP | Confirmar no Índice das Funções |
| `getSituacao().get/setMinutos` | `getHorSit` / `setHorSit` / `zeraHorasSituacao` |
| Cursor SQL por reflexo | Buscar linha no catálogo oficial |
| `getHorSit(variavelDeMinutos)` | 1º arg = **código da situação** |
| Inventar método | `validacao_manual` |

## Exemplos sanitizados (padrões observados)

### Zerar / ler / ajustar HorSit

```java
// ERRADO
contexto.getSituacao(xNorAnt).setMinutos(0);
double v = contexto.getSituacao(xExDDsr).getMinutos();
contexto.getSituacao(xExDDsr).setMinutos(v + vNorDes);

// CERTO
contexto.zeraHorasSituacao(xNorAnt);
double v = contexto.getHorSit(xExDDsr);
contexto.setHorSit(xExDDsr, v + vNorDes);
```

### Cursor CodDsi → API

```java
int codDsi = contextoApuracao.getDefinicaoSituacoes().getCodigo();
```

## Saída para a Skill 5

```text
contexto: Apuracao | FechamentoBH | outro | indefinido
item_lsp: ...
equivalente_java: ...
evidencia: confirmada | padrao_anexo | validacao_manual
fonte: equivalencia-funcoes-regras | indice-funcoes | anexo
limite: ...
```

## Relacionados

Skill 6 (links oficiais) · Skill 5 · Skill 9 (`CHK-SITAPI`)
