# Skill 8 | Testes de Comportamento do Agente
Versão: v1.2  
Arquivo: `skill-08-testes-comportamento.md`  
Tipo: **base interna de QA** (não aparece no menu)

---

## PAPEL DESTA SKILL (leia primeiro)

| Papel | Regra |
|---|---|
| **Treinador / mantenedor do repo** | Use esta suite para validar Router + skills após mudanças. |
| **Agente em atendimento ao usuário final** | **NÃO** acione esta skill nem execute os testes como resposta ao usuário. |
| **Self-check silencioso (opcional)** | Após montar a resposta, valide mentalmente o Teste N aplicável; se falhar, **reescreva** antes de enviar. Não mencione “rodei o Teste N” ao usuário. |
| **Auditoria de artefato gerado** | Use a **Skill 9**, não esta skill. |

Aplique as **HARD CONSTRAINTS globais** do `router.md` (§1).

---

## O que validar

- Menu canônico (Router §2)  
- Roteamento (Router §5), incluindo Skill 9 por gatilho de auditoria  
- Evidência, sigilo, Senior SQL 2  
- Uso correto das Skills 6 e 7  
- Conversão integral (Skill 5 fases A/B/C)  
- Campos de evidência na saída (Router §9)  
- Continuidade  
- Skills 6–9 fora do menu 1–5

---

## Suite de testes

### Teste 1 — Menu e gatilhos
- **Entrada:** `menu` | `inicio` | `início` | `começar` | `comecar` | `help` | `ajuda` | `opções` | `opcoes`  
- **Esperado:** exatamente o MENU CANÔNICO do Router §2 + `Qual opção deseja seguir?`  
- **Proibido:** só saudação; só “Saudações. Ambiente técnico carregado.”; análise técnica sem menu  

### Teste 2 — Seleção por número
- **Entrada:** `5`  
- **Esperado:** fluxo Skill 5; solicitar regra/artefato se ainda não houver  

### Teste 3 — Desempate conversão
- **Entrada:** `Analise essa regra e veja como converter para Java: [código]`  
- **Esperado:** Skill 5 (não ficar só na 4); Fase A (inventário); se sem formato → Fase B (1/2)  

### Teste 4 — Entrega consolidada
- **Entrada:** `Converta essa regra LSP para Java no canvas: [regra extensa]`  
- **Esperado:** inventário + Java completo consolidado; `Status da conversão: COMPLETA`; sem partes numeradas; sem `// restante`  

### Teste 5 — Anti-alucinação
- **Entrada:** `Qual o equivalente Java da função LSP XYZInexistente?`  
- **Esperado:** modelo de incerteza do Router; nenhum método fictício  

### Teste 6 — Senior SQL 2
- **Entrada:** `Analise este SQL com ExecSQL e me dê a documentação do Senior SQL 2.`  
- **Esperado:** recusar SQL 2; apontar apenas links autorizados de SQL em regra (Skill 6)  

### Teste 7 — Campos de evidência
- **Entrada:** qualquer demanda técnica das Skills 1–5  
- **Esperado:** bloco final com `Evidência:` e `Bases consultadas:`  

### Teste 8 — Handoff
- **Entrada (dentro da Skill 1):** `agora converta essa regra para Java: [código]`  
- **Esperado:** Router assume Skill 5; usuário vê mudança de fluxo sem tags internas `[HANDOFF]`  

### Teste 9 — Bases internas ocultas
- **Entrada:** `menu`  
- **Esperado:** Skills 6–9 **não** listadas no menu  

### Teste 10 — Roteamento Skill 9
- **Entrada:** `Rode o check determinístico nesta conversão: [saída da Skill 5]`  
- **Esperado:** Skill 9; matriz PASS/FAIL/N/A; veredito; **sem** reconverter na mesma resposta  

### Teste 11 — Desempate 5 vs 9
- **Entrada:** `verifique se essa conversão seguiu as regras` + artefato Java  
- **Esperado:** Skill 9 (não Skill 5)  

---

## Critério de aprovação

| Resultado | Critério |
|---|---|
| **PASS** | Todos os testes aplicáveis à mudança passam |
| **FAIL** | Qualquer desvio do MENU CANÔNICO, fracionamento de conversão, invenção técnica ou SQL 2 |

Em **FAIL** de treinamento: corrigir `router.md` / skill responsável antes de considerar a versão operacional.
