<h1 align="center">LSPCodMind</h1>

<p align="center">
  <b>O Framework Definitivo de Agente de IA para Senior Sistemas: LSP, Engenharia Reversa e Conversão LSP → Java</b>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/SENIOR_SISTEMAS-HCM_%7C_ERP-blue?style=for-the-badge" alt="Senior Sistemas" />
  <img src="https://img.shields.io/badge/LSP-5.10.4-orange?style=for-the-badge" alt="LSP 5.10.4" />
  <img src="https://img.shields.io/badge/JAVA-17%2B-red?style=for-the-badge" alt="Java 17+" />
  <img src="https://img.shields.io/badge/LSPCodMind-v13.0-success?style=for-the-badge" alt="LSPCodMind v13.0" />
</p>

---

O **LSPCodMind** é um framework avançado de agente de IA arquitetado em formato modular de *Router + Skills*, projetado especificamente para a plataforma **Senior Sistemas**. Atuando com postura técnica de nível Senior, o sistema é focado no diagnóstico de regras, engenharia reversa de código legado, desenvolvimento orientado e conversão assistida de regras LSP para o novo Editor de Regras Java do **Senior HCM** (Controle de Ponto e Refeitório).

---

## 🚀 Principais Funcionalidades

- **🎓 Mentoria Técnica**: Explicação didática e aplicável de conceitos, sintaxe LSP, boas práticas de desenvolvimento, arquitetura Senior e navegação de recursos.
- **🔍 Diagnóstico e Debug**: Análise profunda de erros, exceções, logs de execução, falhas de integração, vazamento de cursores e gargalos de performance.
- **🛠️ Desenvolvimento Orientado**: Criação, estruturação e refatoração de regras LSP e rotinas Senior com validações de segurança e comentários por blocos lógicos.
- **🧬 Analisador de Regras**: Engenharia reversa de regras legadas, mapeamento completo de variáveis, identificação de dependências e análise do fluxo de negócio.
- **🔄 Conversão LSP para Java**: Migração assistida e integral de regras LSP para Java (HCM 6.10.4 / Gestão do Ponto), com inventário prévio de variáveis, mapeamento de métodos do `ContextoApuracao` e entrega consolidada sem fracionamento.

---

## 🛠️ Arquitetura do Agente & Referências Técnicas

O projeto é guiado pelo **Prompt Router** central (`router.md`) que controla as interações e roteia os pedidos do usuário para as skills técnicas corretas:

- **Router Central (`router.md`)**: Autoridade de menu principal, desempate de fluxos, política de evidência e controle de continuidade.
- **Base de Documentação e Banco (`skill-06-base-documentacao-banco.md`)**: Centralizador de links oficiais autorizados Senior, apostilas complementares de treinamento (LSP, APO, Rubi) e dicionário de dados (aliases/domínios ERP e HCM).
- **Base de Conversão LSP → Java (`skill-07-base-conversao-lsp-java.md`)**: Catálogo operacional de 224 variáveis/métodos do contexto de apuração e repositório de exemplos sanitizados de conversão real.
- **Testes de Comportamento (`skill-08-testes-comportamento.md`)**: Suite interna de testes de QA para validação do comportamento do agente.

---

## 📁 Estrutura de Arquivos do Repositório

| Arquivo | Função / Responsabilidade |
| :--- | :--- |
| [`README.md`](file:///Users/vitorhugo/Meu%20Drive/Projetos/Agent%20StartSe/README.md) | Documentação oficial e apresentação do repositório |
| [`router.md`](file:///Users/vitorhugo/Meu%20Drive/Projetos/Agent%20StartSe/router.md) | Router central de controle, menu e direcionamento de fluxos |
| [`skill-01-mentoria-tecnica.md`](file:///Users/vitorhugo/Meu%20Drive/Projetos/Agent%20StartSe/skill-01-mentoria-tecnica.md) | Skill 1 — Mentoria Técnica e Boas Práticas |
| [`skill-02-diagnostico-debug.md`](file:///Users/vitorhugo/Meu%20Drive/Projetos/Agent%20StartSe/skill-02-diagnostico-debug.md) | Skill 2 — Diagnóstico, Logs e Debugging |
| [`skill-03-desenvolvimento-orientado.md`](file:///Users/vitorhugo/Meu%20Drive/Projetos/Agent%20StartSe/skill-03-desenvolvimento-orientado.md) | Skill 3 — Criação e Refatoração de Regras LSP |
| [`skill-04-analisador-regras.md`](file:///Users/vitorhugo/Meu%20Drive/Projetos/Agent%20StartSe/skill-04-analisador-regras.md) | Skill 4 — Engenharia Reversa e Análise de Regras |
| [`skill-05-conversao-lsp-java.md`](file:///Users/vitorhugo/Meu%20Drive/Projetos/Agent%20StartSe/skill-05-conversao-lsp-java.md) | Skill 5 — Conversão Assistida LSP para Java |
| [`skill-06-base-documentacao-banco.md`](file:///Users/vitorhugo/Meu%20Drive/Projetos/Agent%20StartSe/skill-06-base-documentacao-banco.md) | Base Interna 6 — Links Autorizados, Apostilas e Banco de Dados |
| [`skill-07-base-conversao-lsp-java.md`](file:///Users/vitorhugo/Meu%20Drive/Projetos/Agent%20StartSe/skill-07-base-conversao-lsp-java.md) | Base Interna 7 — Catálogo Operacional de Conversão + Exemplos |
| [`skill-08-testes-comportamento.md`](file:///Users/vitorhugo/Meu%20Drive/Projetos/Agent%20StartSe/skill-08-testes-comportamento.md) | Base Interna 8 — Suite de Testes de Comportamento |

---

## 🔒 Diretrizes Críticas e Políticas Globais

- **Proibição de Senior SQL 2**: É terminantemente proibido o uso de Senior SQL 2 em regras com queries SQL ou conversões.
- **Política de Evidência**: Nenhuma função, tabela ou equivalência técnica é inventada; incertezas são sinalizadas com limites claros de evidência.
- **Entrega Consolidada de Código**: Conversões LSP → Java são entregues de forma integral (em Canvas, Documento completo ou bloco único consolidado).