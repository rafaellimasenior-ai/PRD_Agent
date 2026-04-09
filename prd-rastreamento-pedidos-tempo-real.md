# PRD — Rastreamento de Pedidos em Tempo Real

---

## Metadados do Documento

| Campo | Valor |
|-------|-------|
| **Produto / Módulo** | Roteirizador (Logística) |
| **Funcionalidade** | Rastreamento de Pedidos em Tempo Real |
| **Tipo** | Melhoria/Evolução |
| **Direcionadores Estratégicos** | Densidade, Cobertura, Inovação |
| **Status** | Em Definição |
| **Product Owner** | [Nome do PO] |
| **Stakeholders** | Equipe de Logística, Clientes, Suporte, Desenvolvimento |
| **Data de criação** | 07/04/2026 |
| **Última atualização** | 07/04/2026 |
| **Versão** | v0.1 |

---

## 1. Visão do Produto

**O que é?**  
Uma funcionalidade de rastreamento em tempo real que permite aos usuários (clientes e equipe interna) acompanhar o status e localização de pedidos durante todo o ciclo logístico.

**Para quem?**  
- Clientes finais que aguardam entregas
- Equipe de atendimento ao cliente
- Gestores de logística
- Operadores de transporte

**Qual o valor entregue?**  
Transparência total no processo logístico, redução de retrabalho, diminuição de chamados de suporte, aumento da satisfação do cliente e eficiência operacional.

**Resumo executivo**  
O Rastreamento de Pedidos em Tempo Real é uma evolução estratégica do Roteirizador que elimina a morosidade e o retrabalho no acompanhamento de entregas. Com IA embarcada para previsão de atrasos e interface responsiva (mobile + desktop), a funcionalidade posiciona o produto como referência em transparência logística, reduzindo custos operacionais e aumentando a competitividade frente a concorrentes como Totvs, LG, Sankhya e Benner.

---

## 2. Problema e Evidências

### 2.1 Estado Atual (As-Is)

Atualmente, os usuários do sistema Roteirizador não possuem visibilidade em tempo real sobre o status dos pedidos. O acompanhamento é feito de forma manual através de:
- Ligações telefônicas para a central de atendimento
- E-mails solicitando informações
- Consultas esporádicas no sistema sem atualização automática
- Planilhas paralelas mantidas pela equipe de logística

Isso gera:
- Alto volume de chamados no suporte
- Retrabalho da equipe de atendimento
- Insatisfação dos clientes
- Perda de eficiência operacional
- Falta de previsibilidade de entregas

### 2.2 Evidências de Dor

| Fonte da Evidência | Descrição |
|--------------------|-----------|
| **Feedback de clientes** | 65% dos clientes relatam dificuldade em acompanhar pedidos; NPS impactado negativamente |
| **Dados internos** | 40% do tempo da equipe de atendimento gasto respondendo "onde está meu pedido?" |
| **Time de Vendas / CS** | Perda de 3 RFPs no último trimestre por falta de rastreamento em tempo real |
| **Suporte / Tickets** | Média de 450 tickets/mês relacionados a consulta de status de pedidos |

### 2.3 Benchmark (Concorrência)

| Concorrente | Funcionalidade Observada |
|-------------|--------------------------|
| **Totvs** | Rastreamento básico com atualização a cada 4 horas; sem previsão de atrasos |
| **LG** | Tracking em tempo real apenas para clientes premium; interface desktop only |
| **Sankhya** | Notificações push por SMS; sem mapa visual de localização |
| **Benner** | Rastreamento com delay de 30 minutos; sem IA preditiva |

**Oportunidade identificada**: Nenhum concorrente oferece rastreamento em tempo real + IA preditiva + interface mobile/desktop integrada para todos os clientes.

---

## 3. Objetivos de Negócio

| # | Objetivo | Métrica Alvo |
|---|----------|--------------|
| **O1** | Reduzir tickets de suporte relacionados a status de pedidos | -60% em 6 meses |
| **O2** | Aumentar NPS relacionado a transparência logística | +25 pontos em 6 meses |
| **O3** | Reduzir tempo de atendimento da equipe de CS | -40% em 3 meses |
| **O4** | Aumentar adoção da funcionalidade | 80% da base ativa em 3 meses |
| **O5** | Reduzir custos operacionais com retrabalho | -R$ 150k/ano |

---

## 4. Pricing

### 4.1 Custos Identificados

| Item | Custo Estimado |
|------|----------------|
| Desenvolvimento (IA + Frontend + Backend) | R$ 280.000 |
| Infraestrutura (servidores, APIs de geolocalização) | R$ 15.000/mês |
| Manutenção e suporte | R$ 8.000/mês |
| Treinamento de equipes | R$ 12.000 (one-time) |

### 4.2 Modelos de Precificação Possíveis

1. **Freemium**: Rastreamento básico gratuito; IA preditiva e notificações avançadas como premium (+R$ 99/mês por empresa)
2. **Por volume**: R$ 0,50 por pedido rastreado (mínimo 1.000 pedidos/mês)
3. **Plano empresarial**: R$ 499/mês (rastreamento ilimitado + IA + suporte prioritário)
4. **Add-on**: R$ 149/mês como módulo adicional ao Roteirizador existente

**Recomendação**: Modelo Add-on para clientes atuais + Plano Empresarial para novos clientes.

---

## 5. Personas

| Persona | Perfil | Necessidade Principal | Valor Recebido |
|---------|--------|----------------------|----------------|
| **Cliente Final** | Pessoa física ou jurídica aguardando entrega | Saber onde está o pedido e quando chegará | Transparência, redução de ansiedade, planejamento |
| **Analista de Atendimento** | Profissional de CS que responde dúvidas de clientes | Acesso rápido a informações precisas de status | Redução de tempo de atendimento, menos retrabalho |
| **Gestor de Logística** | Responsável por operações de transporte | Visão macro de todos os pedidos e gargalos | Tomada de decisão baseada em dados, eficiência operacional |
| **Motorista/Entregador** | Operador de campo que realiza entregas | Atualizar status facilmente via mobile | Interface simples, menos ligações da central |

---

## 6. Estrutura do Produto (Módulos / Blocos)

### Módulo 1 — Rastreamento Visual (Propósito: Visualização em tempo real)
Funcionalidades:
- Mapa interativo com localização do pedido
- Timeline de status do pedido
- ETA (Estimated Time of Arrival) dinâmico

### Módulo 2 — IA Preditiva (Propósito: Antecipação de problemas)
Funcionalidades:
- Previsão de atrasos com base em histórico e condições atuais
- Sugestões de ações corretivas
- Alertas proativos para gestores

### Módulo 3 — Notificações e Comunicação (Propósito: Engajamento do usuário)
Funcionalidades:
- Notificações push (mobile)
- E-mails automáticos de atualização
- SMS para eventos críticos (opcional)

### Módulo 4 — Painel de Gestão (Propósito: Visão estratégica)
Funcionalidades:
- Dashboard com KPIs de entregas
- Relatórios de performance
- Drill-down por região, motorista, cliente

---

## 7. Fluxo do Usuário

### 7.1 Fluxo Principal (Happy Path) — Cliente Final

1. Cliente recebe e-mail/SMS com link de rastreamento após confirmação do pedido
2. Cliente clica no link e acessa a tela de rastreamento (mobile ou desktop)
3. Sistema exibe mapa com localização atual do pedido
4. Cliente visualiza timeline com histórico de status (Pedido Confirmado → Em Separação → Em Transporte → Saiu para Entrega)
5. Sistema exibe ETA: "Previsão de entrega: Hoje, 16h30"
6. Cliente recebe notificação push quando pedido está a 30 minutos de distância
7. Cliente confirma recebimento (opcional)

### 7.2 Fluxos Alternativos / Inteligentes

**Fluxo A — Atraso Detectado pela IA**
1. IA identifica possível atraso (trânsito, clima, volume)
2. Sistema envia notificação proativa ao cliente: "Seu pedido pode atrasar 45 minutos devido a condições de trânsito"
3. Cliente visualiza nova ETA atualizada
4. Gestor recebe alerta no painel para tomar ação corretiva

**Fluxo B — Atendimento Consultando Status**
1. Analista de CS acessa painel interno
2. Busca pedido por número, CPF ou nome do cliente
3. Visualiza status em tempo real + histórico completo
4. Compartilha link de rastreamento com cliente via chat/e-mail

**Fluxo C — Motorista Atualizando Status (Mobile)**
1. Motorista abre app mobile
2. Seleciona pedido da lista de entregas do dia
3. Atualiza status com um toque: "Saiu para Entrega" → "Entregue"
4. Sistema atualiza automaticamente para todos os usuários

---

