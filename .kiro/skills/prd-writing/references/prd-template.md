# Template PRD Completo

Use este template como base para estruturar seu PRD. Adapte conforme necessário.

## Metadados do Documento

| Campo | Valor |
|-------|-------|
| Produto / Módulo | [Nome do produto ou módulo] |
| Funcionalidade | [Nome da feature] |
| Tipo | Nova funcionalidade / Melhoria / Correção |
| Status | Em Definição / Em Desenvolvimento / Em Homologação / Entregue |
| Product Owner | [Nome] |
| Stakeholders | [Lista de envolvidos] |
| Data de criação | [DD/MM/AAAA] |
| Última atualização | [DD/MM/AAAA] |
| Versão | v0.1 |

---

## 1. Visão do Produto

### O que é?
[Definição em uma frase clara e objetiva]

### Para quem?
[Público-alvo primário e secundário]

### Qual o valor entregue?
[Benefício central para o negócio e o usuário]

### Resumo Executivo
[Parágrafo curto contextualizando importância estratégica: competitividade, experiência, compliance, receita]

**Exemplo de estrutura:**
"[Nome] é uma [tipo] que permite [ação] para [persona], gerando [valor]. Esta funcionalidade é estratégica porque [razão de negócio]."

---

## 2. Problema e Evidências

### 2.1 Estado Atual (As-Is)
[Descrição de como o processo funciona hoje, sem a funcionalidade proposta. Incluir workarounds que os usuários adotam.]

### 2.2 Evidências de Dor

| Fonte da Evidência | Descrição |
|-------------------|-----------|
| Feedback de clientes | [Ex: Volume alto de solicitações no portal] |
| Dados internos | [Ex: % de retrabalho ou registros excluídos] |
| Time de Vendas / CS | [Ex: Perda de RFPs ou churn por falta da feature] |
| Suporte / Tickets | [Ex: Volume de chamados relacionados] |

### 2.3 Benchmark (Concorrência)

| Concorrente | Funcionalidade Observada |
|-------------|-------------------------|
| [Concorrente A] | [Como resolve o mesmo problema] |
| [Concorrente B] | [Como resolve o mesmo problema] |
| [Concorrente C] | [Como resolve o mesmo problema] |

---

## 3. Objetivos de Negócio

| # | Objetivo | Métrica Alvo |
|---|----------|-------------|
| O1 | [Ex: Reduzir tempo de aprovação] | [Ex: -30% em 3 meses] |
| O2 | [Ex: Aumentar adoção da feature] | [Ex: 30% da base ativa] |
| O3 | [Ex: Reduzir tickets de suporte] | [Ex: -40% em chamados] |

---

## 4. Pricing

### Custos Identificados
- [Custo 1]
- [Custo 2]
- [Custo 3]

### Modelos de Precificação Possíveis
- [Modelo 1]
- [Modelo 2]
- [Modelo 3]

---

## 5. Personas

| Persona | Perfil | Necessidade Principal | Valor Recebido |
|---------|--------|----------------------|-----------------|
| [Ex: Analista de RH] | [Descrição breve do papel] | [O que precisa resolver] | [Como a feature ajuda] |
| [Ex: Gestor] | [Descrição breve do papel] | [O que precisa resolver] | [Como a feature ajuda] |
| [Ex: Colaborador] | [Descrição breve do papel] | [O que precisa resolver] | [Como a feature ajuda] |

---

## 6. Estrutura do Produto (Módulos / Blocos)

### Módulo 1 — [Nome] ([Propósito])
Funcionalidades:
- [Funcionalidade 1]
- [Funcionalidade 2]
- [Funcionalidade 3]

### Módulo 2 — [Nome] ([Propósito])
Funcionalidades:
- [Funcionalidade 1]
- [Funcionalidade 2]

---

## 7. Jornada do Usuário

### 7.1 Fluxo Principal (Happy Path)
1. [Passo 1 — Ex: Usuário acessa a tela de simulação]
2. [Passo 2 — Ex: Seleciona o colaborador]
3. [Passo 3 — Ex: Preenche parâmetros]
4. [Passo 4 — Ex: Clica em "Simular"]
5. [Passo 5 — Ex: Visualiza resultado]

### 7.2 Fluxos Alternativos / Inteligentes
- [Fluxo alternativo 1 — Descrição]
- [Fluxo alternativo 2 — Descrição]

---

## 8. Requisitos Funcionais

### RF01 — [Nome do Requisito]

| Campo | Descrição |
|-------|-----------|
| Descrição | [O que o sistema deve fazer] |
| Regras de Negócio | [Condições, validações, limites] |
| Dados de Entrada | [Campos, parâmetros, seleções do usuário] |
| Dados de Saída | [O que o sistema retorna/exibe] |
| Comportamento de Erro | [Mensagens, bloqueios, fallback] |
| Dependências | [Outros RFs, APIs, módulos] |
| Prioridade | Must / Should / Could / Won't |

### RF02 — [Nome do Requisito]
[Repetir estrutura acima]

---

## 9. Requisitos Não Funcionais

| ID | Categoria | Requisito |
|----|-----------|-----------|
| RNF01 | Performance | [Ex: Tempo de resposta < 1s para listagens] |
| RNF02 | Responsividade | [Ex: Compatível com desktop e mobile] |
| RNF03 | Segurança | [Ex: Controle de permissões por perfil] |
| RNF04 | Auditoria | [Ex: Log de todas as ações com user_id e timestamp] |
| RNF05 | Escalabilidade | [Ex: Suportar processamento em lote de N registros] |
| RNF06 | Acessibilidade | [Ex: Conformidade com WCAG 2.1 nível AA] |

---

## 10. Compliance, LGPD e Requisitos Legais

### 10.1 Dados Sensíveis Envolvidos
- [Dado sensível 1 — Ex: Salário]
- [Dado sensível 2 — Ex: CPF]
- [Dado sensível 3 — Ex: Dependentes]

### 10.2 Requisitos de Conformidade

| Requisito | Descrição |
|-----------|-----------|
| Trilha de auditoria (LGPD) | [Ex: Logs com user_id, employee_id, timestamp] |
| Matriz de segurança | [Ex: Respeitar permissões já configuradas no sistema] |
| Fidelidade legal | [Ex: Cálculos devem reproduzir 100% das regras fiscais] |
| Marca d'água / Disclaimers | [Ex: Documento gerado com "SEM VALOR LEGAL"] |
| Integrações regulatórias | [Ex: Não gerar eventos no eSocial para simulações] |

---

## 11. Entregáveis

| Componente | Descrição da Entrega |
|-----------|----------------------|
| Interface (UI) | [Ex: Nova tela em Módulo > Sub > Funcionalidade] |
| Backend / API | [Ex: Endpoint ou motor de cálculo com flag específica] |
| Relatórios / PDFs | [Ex: Relatório de simulação com marca d'água] |
| Integrações | [Ex: Webhook, notificação, export] |
| Documentação | [Ex: Help online, release notes, material de treinamento] |

---

## 12. Cenários de Teste (QA)

### 12.1 Cenários Positivos (Happy Path)

| # | Cenário | Descrição / Condições | Resultado Esperado |
|---|---------|----------------------|-------------------|
| C1 | [Ex: Simulação padrão] | [Ex: 30 dias, saldo total disponível] | [Cálculo exibido corretamente] |
| C2 | [Ex: Com abono pecuniário] | [Ex: 20 dias gozo + 10 abono] | [Valores separados] |

### 12.2 Cenários Negativos (Edge Cases)

| # | Cenário | Descrição / Condições | Resultado Esperado |
|---|---------|----------------------|-------------------|
| C5 | [Ex: Saldo insuficiente] | [Ex: Simular 30 dias com saldo 15] | [Mensagem de erro] |
| C6 | [Ex: Acesso não autorizado] | [Ex: Colaborador fora do escopo LGPD] | [Bloqueio de acesso] |

---

## 13. Dependências e Integrações

### 13.1 Dependências Internas

| Dependência | Tipo | Descrição |
|-------------|------|-----------|
| [Ex: Cadastro de Colaborador] | Dados | [Necessário para buscar informações base] |
| [Ex: Motor de cálculo existente] | Serviço | [Reutilizar lógica já implementada] |

### 13.2 Integrações Externas

| Sistema / API | Tipo | Descrição |
|---------------|------|-----------|
| [Ex: Tabelas INSS/IRRF] | Dados | [Tabelas atualizadas pelo governo] |
| [Ex: eSocial] | Regulatório | [Não deve gerar eventos para simulação] |

---

## 14. Riscos e Mitigações

| # | Risco | Impacto | Probabilidade | Mitigação |
|---|-------|---------|---------------|-----------|
| R1 | [Ex: Performance em lote] | Alto | Média | [Ex: Processamento assíncrono + paginação] |
| R2 | [Ex: Divergência de cálculo] | Crítico | Baixa | [Ex: Usar o mesmo motor do processo oficial] |
| R3 | [Ex: Escopo crescente] | Médio | Alta | [Ex: Fases bem definidas com gates] |

---

## 15. Métricas de Sucesso

| Métrica | Baseline (Atual) | Meta | Prazo de Medição |
|---------|-----------------|------|------------------|
| [Ex: Adoção da feature] | [0%] | [30% da base] | [3 meses após release] |
| [Ex: Redução de retrabalho] | [X exclusões/mês] | [-60%] | [3 meses após release] |
| [Ex: Tickets de suporte] | [X/mês] | [-40%] | [6 meses após release] |

---

## 16. Plano de Execução (Roadmap)

### Fase 1 — Discovery e Definição
- [Entregável 1 — Ex: PRD finalizado]
- [Entregável 2 — Ex: Protótipo de alta fidelidade]
- Duração estimada: [X sprints]

### Fase 2 — Desenvolvimento
- [Entregável 1 — Ex: Backend/API]
- [Entregável 2 — Ex: Frontend/UI]
- Duração estimada: [X sprints]

### Fase 3 — QA e Homologação
- [Entregável 1 — Ex: Execução dos cenários de teste]
- [Entregável 2 — Ex: Testes de estresse/performance]
- Duração estimada: [X sprints]

### Fase 4 — Release e Acompanhamento
- [Entregável 1 — Ex: Deploy em produção]
- [Entregável 2 — Ex: Monitoramento de métricas]
- Duração estimada: [X sprints]

---

## 17. Glossário e Referências

| Termo / Sigla | Definição |
|---------------|-----------|
| [Ex: CLT] | [Consolidação das Leis do Trabalho] |
| [Ex: SLA] | [Service Level Agreement] |

### Referências
- [Link ou documento de referência 1]
- [Link ou documento de referência 2]

---

## 18. Histórico de Versões

| Versão | Data | Autor | Alterações |
|--------|------|-------|-----------|
| v0.1 | DD/MM/AAAA | [Nome] | Criação do documento |
| v0.2 | DD/MM/AAAA | [Nome] | [Descrição da alteração] |
