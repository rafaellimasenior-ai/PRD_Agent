# Template — User Stories (Artefato Intermediário)

> Este template é a estrutura oficial do artefato gerado pela skill `features-to-user-stories`.
> O artefato é salvo em `output-files/user-stories-<nome-base>.md` e serve como contrato de revisão humana antes da publicação no Jira.

---

## Cabeçalho de Origem

```markdown
# User Stories — Breakdown

| Campo | Valor |
|-------|-------|
| **Artefato de Features** | `output-files/epics-<nome>.md` |
| **Produto / Módulo** | _[conforme metadados do Features]_ |
| **Número de Features** | _[ex: 3]_ |
| **Número de Stories Geradas** | _[ex: 8]_ |
| **Projeto Jira** | _[ex: HCMON]_ |
| **Analista Responsável** | _[nome e username]_ |
| **PO para Aprovação** | _[nome e username]_ |
| **Data de Geração** | _[AAAA-MM-DD]_ |
| **Status do Artefato** | `Estruturado` |

---

## Matriz de User Stories

| # | Feature | F# | Nº Stories | Personas | Must Have | Should Have | Could Have | Jira Story Keys |
|---|---------|---|------------|----------|-----------|-------------|------------|-----------------|
| 1 | _Nome da Feature 1_ | F012 | 3 | contador,gerente,admin | 2 | 1 | 0 | _Após publicação_ |
| 2 | _Nome da Feature 2_ | F013 | 2 | contador,admin | 2 | 0 | 0 | _Após publicação_ |

---

## User Stories Detalhadas

### Feature F012 — [RF03] Sugestão automática de transação

> **Origem no PRD:** Seção 8 — Requisitos Funcionais  
> **Contexto:** Motor de regras analisa PV e sugere transação fiscal correta  
> **Épico Jira:** E001 (Fase 1 — Motor de Regras)

#### Story S01

**Título:** [S001] As a contador I want to see the suggested transaction so that I can validate and apply it quickly

**Persona:** Contador  
**Jornada:** Receber sugestão, validar, aplicar ou descartar  
**MoSCoW:** Must Have  
**Prioridade Jira:** Alta

**Critérios de Aceite:**
- [ ] Quando contador salva um PV, modal de sugestão aparece automaticamente
- [ ] Modal exibe 3 elementos: transação sugerida (ex: "5102"), confiança % (ex: "95%"), botões "Usar" e "Descartar"
- [ ] Modal pode ser fechado com botão X (sem ação)
- [ ] Clicando "Usar", a transação sugerida é aplicada ao PV instantaneamente
- [ ] Clicando "Descartar", um Jira Comment é criado com timestamp, usuário, e campo de motivo opcional
- [ ] Se contador não agir em 3 minutos, modal desaparece (timer visível)

**Notas Técnicas:**
- Usar cache da Fase 1 Motor para evitar latência
- Considerar fallback se regra não aplicável
- Log auditável de cada ação (usar/descartar)

**Dependências:**
- ✅ Depende de: Feature F010 (Motor de Regras — deve estar pronto)
- ⚠️ Bloqueada por: nenhuma (pode começar)
- ℹ️ Bloqueia: S02, S03 (dependem de dados de S01)

**Origem Rastreável:**
```
Feature: F012 (HCMON-450)
RF: RF03 (Seção 8)
PRD: prd-sugestao-inteligente.md
Épico: E001
MoSCoW: Must Have → Jira Priority: Alta
```

**Jira Story Key:** `_Após publicação_`

---

#### Story S02

**Título:** [S002] As a gerente fiscal I want to monitor suggestion accuracy in a dashboard so that I can identify patterns and improve rules

**Persona:** Gerente Fiscal  
**Jornada:** Consultar dashboard de acurácia em tempo real  
**MoSCoW:** Must Have  
**Prioridade Jira:** Alta

**Critérios de Aceite:**
- [ ] Dashboard exibe: total de sugestões processadas, aceitas, descartadas
- [ ] Breakdown por período: múltiplos filtros (dia, semana, mês)
- [ ] Coluna de "Acurácia %" (aceitas / total)
- [ ] Tabela com últimas 20 sugestões rejeitadas (motivo, usuário, timestamp)
- [ ] Botão "Exportar relatório" gera CSV com dados do período

**Critérios de Aceite Técnicos:**
- [ ] Dashboard atualiza dados em real-time (não refresh manual)
- [ ] Performance: carregamento < 2 segundos mesmo com 100k registros
- [ ] Acessível para role "Gerente Fiscal" apenas

**Notas Técnicas:**
- Dados derivados de Jira Comments criados em S01
- Usar Power BI ou similar (definir infra)

**Dependências:**
- ✅ Depende de: S01 (histórico de dados)
- ⚠️ Depende de: Dashboard infra (versão 2+)
- ℹ️ Bloqueia: nenhuma

**Origem Rastreável:**
```
Feature: F012 (HCMON-450)
RF: RF03 (Seção 8)
PRD: prd-sugestao-inteligente.md
Épico: E001
MoSCoW: Must Have → Jira Priority: Alta
```

**Jira Story Key:** `_Após publicação_`

---

#### Story S03

**Título:** [S003] As a admin I want to register new fiscal classification rules so that the engine adapts to business changes

**Persona:** Admin Fiscal  
**Jornada:** Cadastrar, ativar/desativar regras  
**MoSCoW:** Should Have  
**Prioridade Jira:** Média

**Critérios de Aceite:**
- [ ] Tela de cadastro: campos para nome da regra, condição (ex: "CFOP=6001"), transação sugerida
- [ ] Validação: não permitir duplicação de condição
- [ ] Lista de regras ativas: cada uma pode ser ativada/desativada (soft delete)
- [ ] Ao desativar, motor deixa de usar a regra (mas histórico mantido)
- [ ] Histórico de mudanças: quem criou/editou, quando

**Critérios de Aceite Técnicos:**
- [ ] Permissão: apenas role Admin Fiscal tem acesso
- [ ] Auditoria: tudo registrado em log

**Notas Técnicas:**
- Não resetar motor — aplicar mudanças dinamicamente
- Considerar versionamento de regras

**Dependências:**
- ✅ Depende de: S01 (motor deve estar funcional)
- ⚠️ Bloqueia: Performance tuning tasks (futuro)

**Origem Rastreável:**
```
Feature: F012 (HCMON-450)
RF: RF03 (Seção 8)
PRD: prd-sugestao-inteligente.md
Épico: E001
MoSCoW: Should Have → Jira Priority: Média
```

**Jira Story Key:** `_Após publicação_`

---

## Dependências Globais

```
Story               Depende de      Tipo Dependência
────────────────────────────────────────────────────
S01                 F010 (Feature)  Bloqueia (motor deve estar pronto)
S02                 S01, Infra      Sequencial (histórico + dashboard)
S03                 S01             Sequencial (motor deve estar pronto)
S04                 S01, S02        Sequencial (depende de accuracy data)

Resumo de Ordem:
  Ordem 1 (pre-req)  → F010 (motor de regras feature)
  Ordem 2 (paralelo) → S01 + S03 (implementação do motor)
  Ordem 3 (paralelo) → S02 + testes de S01
  Ordem 4 (final)    → S04 (alertas)
```

---

## Gate de Revisão Humana

> **ANTES DE PUBLICAR:** Analista + PO devem revisar:
> 1. Cada Story é independente e entregável (ou dependência é explícita)?
> 2. AC's são testáveis (não vagos)?
> 3. Personas são distintas (não misturadas em uma Story)?
> 4. Dependencies não têm surpresas?
> 5. Rastreabilidade está completa (PRD→Feature→Story)?

| Campo | Valor |
|-------|-------|
| **Decisão** | `Estruturado` / `Aprovado` / `Ajustar` / `Cancelado` |
| **Aprovado por** | _[nome do Analista]_ |
| **PO Confirmou** | _[nome do PO e data]_ |
| **Data de aprovação** | _[AAAA-MM-DD]_ |
| **Observações** | _[ajustes solicitados, se houver]_ |

---

## Resultado da Publicação

> _Preenchido automaticamente pela skill após execução da Fase 6._

| Feature | Story | Summary | Jira Key | URL | Status |
|---------|-------|---------|----------|-----|--------|
| F012 | S01 | As a contador I want... | HCMON-461 | https://jira.senior.com.br/browse/HCMON-461 | Criado |
| F012 | S02 | As a gerente... | HCMON-462 | https://jira.senior.com.br/browse/HCMON-462 | Criado |
| F012 | S03 | As a admin... | HCMON-463 | https://jira.senior.com.br/browse/HCMON-463 | Criado |

**Total criado:** 3 stories  
**Erros:** 0

---

## Histórico do Artefato

| Data | Versão | Ação | Autor |
|------|--------|------|-------|
| _AAAA-MM-DD_ | v1 | Gerado pela skill features-to-user-stories | _[Analista]_ |
```
