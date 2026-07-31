---
name: base-conversao-lsp-java
description: >-
  Padrões operacionais internos de conversão LSP→Java em HCM/ponto: contextos,
  esqueletos de classe, âncoras de métodos, armadilhas e anti-alucinação. Use a
  partir da Skill 5 após consultar a documentação oficial da Skill 6. Nunca
  invente métodos que não estejam aqui, na Skill 6 ou em anexos do usuário.
---

# Skill 7 · Base de Conversão LSP → Java
Versão: v1.7 · Interna · `skill-07-base-conversao-lsp-java.md`

Não entra no menu. Aplique as regras globais do Router. Em conflito, **docs oficiais da Skill 6 prevalecem**.

## Quando usar / não usar

| Usar | Não usar |
|---|---|
| Padrões de conversão HCM/Ponto, armadilhas, exemplos sanitizados | Só mentoria; como “prova oficial” no lugar da Skill 6 |

## Restrições absolutas

1. Achados aqui = `padrao_anexo` / `inferencia` até a Skill 6 confirmar.  
2. Sanitize cliente/empresa/caminhos — diga “exemplos sanitizados”.  
3. Catálogo completo de centenas de métodos **não** está embutido — só âncoras mínimas abaixo.  
4. Ausente aqui + Skill 6 + anexo → `validacao_manual` — **não invente**.  
5. Horas = minutos inteiros; SQL/cursor → API semântica primeiro; sem variáveis de contexto soltas no Java.

## Instruções

```text
1. Identificar contexto de classe (Apuracao, FechamentoBH, …)
2. Buscar âncoras/esqueletos neste arquivo
3. Confirmar assinatura via Skill 6
4. Senão padrao_anexo/inferencia; senão validacao_manual
```

Recomendado para Skill 5: contexto → inventário → mapear → mecânica (minutos, End→retorno) → sintaxe.

## Esqueletos de classe

Confirme assinaturas na Skill 6 antes de marcar `confirmada`.

### Apuração

```java
@Rule(description = "Regra de Apuracao")
public class RegraApuracao extends Apuracao {
    @Override
    public void execute() {
        ContextoGeralRH contextoGeral = getContainer().getContextoGeral();
        ContextoApuracao contextoApuracao = getContainer().getContextoApuracao();
        // colaborador, data, regras, situações via API semântica
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

## Âncoras de métodos

### Situações

| Intenção | Âncora |
|---|---|
| Ler | `contextoApuracao.getHorSit(codigoSituacao)` |
| Definir | `contextoApuracao.setHorSit(codigoSituacao, minutos)` |
| Zerar | `contextoApuracao.zeraHorasSituacao(codigoSituacao)` |
| Anterior | `contextoApuracao.getHorSitAnterior(codigoSituacao)` |
| Somar | `contextoApuracao.somaHorasSituacao(...)` |

### Colaborador / contexto

| Intenção | Âncora |
|---|---|
| Emp/Tip/Cad | `getNumEmp()` / `getTipCol()` / `getNumCad()` |
| Data | `contextoApuracao.getData()` |
| Históricos | `getHistoricoSindicato()`, `getHistoricoVinculo()`, `getHistoricoCargo()`, `getHistoricoEscala()`, `getHistoricoCentrodeCusto()`, `getHistoricoFilial()` |

### Marcações / totais / escala

| Intenção | Âncora |
|---|---|
| Marcações | `getMarcacoesRealizadas(...)` |
| Totais | `getTotalSituacoes(...)` |
| Escala | `getEscala()` / `getEscalaPrevistaColaborador(...)` |
| Horário | `getHorario()` / `getHorarioPrevistoColaborador(...)` |

## Armadilhas

| Armadilha | Correção |
|---|---|
| Copiar ordem de parâmetros da LSP | Confirmar assinatura Java |
| Passar `HH:mm` em APIs de minutos | Converter (`14:30` → `870`) |
| Portar SQL/cursor no automático | Preferir API semântica |
| Inventar método parecido | `validacao_manual` |
| Vazar nomes de cliente dos exemplos | Sanitizar |

## Exemplos sanitizados

Regras reais completas não estão versionadas aqui. Anexos do usuário = padrão observado, nunca doc oficial.

## Saída para a Skill 5

```text
contexto: Apuracao | FechamentoBH | outro | indefinido
ancora_encontrada: sim | nao
metodo_ou_padrao: ...
evidencia_sugerida: padrao_anexo | inferencia | validacao_manual
requer_skill_6: sim
limite: ...
```

## Relacionados

Skill 6 · Skill 5
