# PRD — Sugestão Inteligente de Transação em Pedido de Venda e Emissão de Notas Fiscais

---

## Metadados do Documento

| Campo | Valor |
|-------|-------|
| **Produto / Módulo** | ERP Senior X SaaS — Venda e Faturamento |
| **Funcionalidade** | Sugestão Inteligente de Transação |
| **Tipo** | Melhoria / Evolução |
| **Direcionadores Estratégicos** | Sustentação, Inovação |
| **Status** | Em Definição |
| **Product Owner** | [Nome do PO] |
| **Stakeholders** | Equipe Fiscal, Equipe Comercial, Equipe de Desenvolvimento, Compliance, Suporte |
| **Data de criação** | 10/04/2026 |
| **Última atualização** | 10/04/2026 |
| **Versão** | v0.1 |

---

## 1. Visão do Produto

**O que é?**
Uma melhoria no módulo de Venda e Faturamento do ERP Senior X SaaS que sugere de forma inteligente e automatizada a transação correta durante a emissão de pedidos de venda e notas fiscais.

**Para quem?**
- Analistas fiscais e faturistas
- Equipe comercial que emite pedidos de venda
- Gestores financeiros e fiscais

**Qual o valor entregue?**
Redução drástica de erros fiscais causados pela seleção incorreta de transações, diminuição de retrabalho, mitigação de riscos tributários e aumento da produtividade operacional.

**Resumo executivo**
A seleção manual de transações em pedidos de venda e notas fiscais é uma das maiores fontes de erro operacional em ERPs. No ERP Senior X, o uso incorreto de transações gera retrabalho fiscal, cancelamentos de NF-e, retificações e potenciais autuações. Esta melhoria introduz um motor de sugestão inteligente que analisa o contexto da operação (tipo de cliente, UF de origem/destino, natureza da operação, CFOP, regime tributário, histórico) e sugere automaticamente a transação mais adequada, reduzindo erros e acelerando o processo de emissão.

---

## 2. Problema e Evidências

### 2.1 Estado Atual (As-Is)

Hoje, ao emitir um pedido de venda ou nota fiscal no módulo de Venda e Faturamento do ERP Senior X, o usuário precisa selecionar manualmente a transação fiscal. Este processo apresenta os seguintes problemas:

- O campo de transação exibe uma lista extensa sem filtro contextual
- Não há orientação sobre qual transação é adequada para cada cenário
- Usuários menos experientes frequentemente selecionam transações incorretas
- Erros são detectados tardiamente (na validação da SEFAZ ou em auditorias)
- Correções exigem cancelamento de NF-e, reemissão e ajustes contábeis
- Workarounds incluem: planilhas de "de-para" mantidas manualmente, consultas frequentes ao setor fiscal, e treinamentos recorrentes que não eliminam o problema

### 2.2 Evidências de Dor

> ⚠️ **Atenção**: A evidência coletada até o momento é limitada (1 fonte, baixo volume de votos). Recomenda-se fortemente buscar evidências complementares antes de priorizar esta iniciativa.

| Fonte da Evidência | Descrição | Status |
|--------------------|-----------|--------|
| **Fórum de Produto** | Solicitação registrada com 2 votos pedindo sugestão inteligente de transação em pedido de venda e NF-e | ✅ Validado (evidência fraca) |
| **Dados internos (erros de transação)** | Necessário levantar: volume de PVs e NF-es com transação corrigida após emissão, cancelamentos de NF-e por erro de transação | 🔴 Não validado |
| **Suporte / Tickets** | Necessário levantar: volume de chamados relacionados a "transação incorreta", "CFOP errado", "rejeição de NF-e" | 🔴 Não validado |
| **Feedback qualitativo de clientes** | Necessário levantar: entrevistas ou pesquisas com faturistas e analistas fiscais sobre dificuldade na seleção de transações | 🔴 Não validado |

**Avaliação da força da evidência**: A demanda existe no fórum de produto, mas com apenas 2 votos a evidência é fraca para justificar priorização. É recomendável cruzar com dados de suporte (tickets), dados internos (taxa de erro/cancelamento de NF-e) e feedback qualitativo antes de avançar para desenvolvimento.

### 2.3 Benchmark (Concorrência)

| Concorrente | Funcionalidade Observada |
|-------------|--------------------------|
| **Totvs (Protheus)** | Possui regras de determinação fiscal por TES (Tipo de Entrada/Saída) com amarração automática por natureza de operação. Permite configuração de regras por combinação de parâmetros, mas exige setup complexo e não utiliza IA preditiva |
| **Sankhya** | Oferece "Regras de Negócio" configuráveis que automatizam a seleção de natureza de operação com base em parâmetros do pedido. Possui motor de regras, mas sem aprendizado de máquina |
| **SAP Business One** | Determinação automática de impostos e transações via "Tax Determination" com regras hierárquicas. Robusto, mas rígido e dependente de parametrização manual extensiva |
| **Benner** | Configuração de transações por tipo de operação e regime tributário. Abordagem baseada em cadastro, sem sugestão inteligente contextual |

**Oportunidade identificada**: Nenhum concorrente direto no mercado brasileiro de ERP oferece sugestão inteligente baseada em contexto + histórico + aprendizado contínuo. A maioria depende de parametrização estática. Há uma oportunidade clara de diferenciação ao combinar regras de negócio com inteligência contextual.

---

## 3. Objetivos de Negócio

> ⚠️ **Atenção**: As métricas alvo abaixo são **placeholders hipotéticos** e devem ser definidas com base em dados reais (baseline atual) durante a fase de Discovery. Sem baseline, não é possível definir metas concretas.

| # | Objetivo | Métrica Alvo | Status |
|---|----------|--------------|--------|
| **O1** | Reduzir erros na seleção de transações em pedidos de venda | A definir após levantamento de baseline | 🔴 Não validado |
| **O2** | Reduzir erros na seleção de transações em notas fiscais | A definir após levantamento de baseline | 🔴 Não validado |
| **O3** | Reduzir tickets de suporte relacionados a transação incorreta | A definir após levantamento de baseline | 🔴 Não validado |
| **O4** | Reduzir tempo médio de emissão de pedido de venda | A definir após levantamento de baseline | 🔴 Não validado |
| **O5** | Aumentar adoção da sugestão inteligente | A definir (sugestão: >70% de aceitação) | 🔴 Não validado |
| **O6** | Reduzir cancelamentos de NF-e por erro de transação | A definir após levantamento de baseline | 🔴 Não validado |

---

## 4. Pricing

### 4.1 Custos Identificados

| Item | Custo Estimado |
|------|----------------|
| Desenvolvimento (motor de regras + IA + UI) | Necessário validar com engenharia |
| Infraestrutura (processamento de sugestões, modelo de ML) | Necessário validar |
| Treinamento de equipes internas e clientes | Necessário validar |

### 4.2 Modelos de Precificação Possíveis

1. **Incluso no módulo**: Funcionalidade nativa do módulo Venda e Faturamento, sem custo adicional — fortalece proposta de valor do ERP Senior X
2. **Add-on premium**: Módulo de IA como complemento pago para clientes que desejam sugestão inteligente avançada
3. **Freemium**: Sugestão baseada em regras gratuita; sugestão com IA/aprendizado como premium

**Recomendação**: Modelo 1 (incluso) para sugestão baseada em regras. Modelo 2 (add-on) para funcionalidades avançadas de IA com aprendizado contínuo. Isso diferencia o produto sem onerar clientes menores.

---

## 5. Personas

| Persona | Perfil | Necessidade Principal | Valor Recebido |
|---------|--------|----------------------|----------------|
| **Faturista / Analista Fiscal** | Profissional responsável pela emissão de NF-e e conferência fiscal. Lida diariamente com dezenas de transações diferentes | Selecionar a transação correta rapidamente, sem precisar consultar tabelas ou colegas | Redução de erros, agilidade, menos retrabalho e menor risco de autuação |
| **Vendedor / Analista Comercial** | Profissional que emite pedidos de venda. Conhecimento fiscal limitado | Emitir pedidos sem se preocupar com complexidade fiscal | Autonomia na emissão, menos dependência do setor fiscal, produtividade |
| **Gestor Fiscal / Controller** | Responsável pela conformidade fiscal da empresa. Audita operações e responde por inconsistências | Garantir que transações estejam corretas antes da emissão, reduzir retrabalho da equipe | Conformidade fiscal, redução de riscos tributários, visibilidade sobre erros |
| **Administrador do Sistema** | Profissional de TI ou consultor que configura o ERP | Configurar regras de sugestão de forma simples e manutenível | Facilidade de parametrização, menos chamados de suporte, regras centralizadas |

---

## 6. Estrutura do Produto (Módulos / Blocos)

### Módulo 1 — Motor de Regras de Sugestão (Propósito: Lógica de determinação)
Funcionalidades:
- Cadastro de regras de sugestão por combinação de parâmetros (UF origem/destino, tipo de cliente, natureza da operação, regime tributário, tipo de produto/serviço)
- Hierarquia de prioridade entre regras
- Regras padrão pré-configuradas (templates por segmento)
- Validação de conflitos entre regras

### Módulo 2 — Sugestão Contextual em Pedido de Venda (Propósito: Automação na emissão de PV)
Funcionalidades:
- Sugestão automática de transação ao preencher dados do pedido
- Exibição de justificativa da sugestão (por que esta transação?)
- Possibilidade de aceitar, alterar ou ignorar a sugestão
- Indicador visual de confiança da sugestão

### Módulo 3 — Sugestão Contextual em Emissão de NF-e (Propósito: Automação no faturamento)
Funcionalidades:
- Sugestão automática de transação ao iniciar emissão de NF-e
- Herança da transação do pedido de venda (quando aplicável)
- Validação cruzada entre transação sugerida e dados fiscais (CFOP, CST, alíquotas)
- Alerta de inconsistência antes da transmissão à SEFAZ

### Módulo 4 — Painel de Gestão e Auditoria (Propósito: Visibilidade e controle)
Funcionalidades:
- Dashboard de aceitação/rejeição de sugestões
- Relatório de transações alteradas manualmente
- Log de auditoria de sugestões aceitas e rejeitadas
- Indicadores de acurácia do motor de sugestão

---

## 7. Fluxo do Usuário

### 7.1 Fluxo Principal (Happy Path) — Emissão de Pedido de Venda

1. Usuário acessa a tela de emissão de pedido de venda
2. Preenche dados do cliente (CNPJ/CPF, UF, regime tributário)
3. Seleciona os itens do pedido (produtos/serviços)
4. Sistema analisa o contexto: tipo de operação, UF origem/destino, tipo de cliente, natureza dos itens, regime tributário
5. Sistema sugere automaticamente a transação mais adequada com indicador de confiança (ex: "Transação 5102 — Venda de mercadoria para contribuinte dentro do estado — Confiança: Alta")
6. Usuário visualiza a justificativa e aceita a sugestão com um clique
7. Transação é preenchida automaticamente no pedido
8. Usuário finaliza o pedido normalmente

### 7.2 Fluxo Principal (Happy Path) — Emissão de Nota Fiscal

1. Usuário inicia a emissão de NF-e a partir de um pedido de venda
2. Sistema herda a transação do pedido de venda
3. Sistema valida se a transação continua adequada para o contexto da NF-e (pode haver mudanças entre PV e NF)
4. Se adequada, exibe confirmação: "Transação herdada do PV — Validação OK"
5. Se houver divergência, sugere nova transação com justificativa
6. Usuário confirma e prossegue com a emissão
7. Sistema realiza validação fiscal final antes da transmissão à SEFAZ

### 7.3 Fluxos Alternativos

**Fluxo A — Usuário rejeita a sugestão**
1. Sistema sugere transação
2. Usuário discorda e seleciona outra transação manualmente
3. Sistema exibe alerta: "A transação selecionada difere da sugestão. Deseja continuar?"
4. Se o usuário confirmar, sistema registra a rejeição no log de auditoria
5. Gestor pode revisar rejeições no painel de gestão

**Fluxo B — Múltiplas transações possíveis**
1. Sistema identifica mais de uma transação válida para o contexto
2. Exibe lista ranqueada com justificativa para cada opção
3. Usuário seleciona a mais adequada
4. Sistema registra a escolha

**Fluxo C — Nenhuma regra aplicável**
1. Sistema não encontra regra que cubra o cenário
2. Exibe mensagem: "Não foi possível sugerir uma transação para este cenário. Selecione manualmente."
3. Sistema registra o cenário como "gap de regra" para análise futura
4. Administrador pode criar nova regra para cobrir o cenário

**Fluxo D — Emissão de NF-e sem pedido de venda (avulsa)**
1. Usuário inicia emissão de NF-e diretamente (sem PV vinculado)
2. Sistema solicita dados mínimos para contexto (tipo de operação, cliente, itens)
3. Motor de sugestão analisa e sugere transação
4. Fluxo segue normalmente

---

## 8. Requisitos Funcionais

### RF01 — Motor de Regras de Sugestão de Transação

| Campo | Descrição |
|-------|-----------|
| **Descrição** | O sistema deve possuir um motor de regras configurável que determine a transação mais adequada com base em parâmetros contextuais da operação |
| **Regras de Negócio** | As regras devem considerar: UF de origem, UF de destino, tipo de cliente (contribuinte/não contribuinte/consumidor final), regime tributário (Simples Nacional, Lucro Presumido, Lucro Real), natureza da operação (venda, devolução, remessa, transferência, bonificação), tipo de produto (mercadoria, serviço, ativo imobilizado), finalidade da operação. Regras devem ter prioridade configurável. Em caso de conflito, a regra de maior prioridade prevalece |
| **Dados de Entrada** | Parâmetros do pedido/NF: CNPJ/CPF do cliente, UF origem/destino, itens (NCM, tipo), natureza da operação, regime tributário do emitente e destinatário |
| **Dados de Saída** | Transação sugerida com: código, descrição, CFOP associado, nível de confiança (Alta/Média/Baixa), justificativa textual |
| **Comportamento de Erro** | Se nenhuma regra for aplicável: exibir mensagem informativa e permitir seleção manual. Se houver conflito de regras: aplicar prioridade e registrar log |
| **Dependências** | Cadastro de transações existente, cadastro de clientes, cadastro de produtos |
| **Prioridade** | Must |

### RF02 — Sugestão Automática em Pedido de Venda

| Campo | Descrição |
|-------|-----------|
| **Descrição** | Ao preencher os dados essenciais de um pedido de venda (cliente + itens), o sistema deve sugerir automaticamente a transação adequada |
| **Regras de Negócio** | A sugestão deve ser disparada automaticamente após o preenchimento do cliente e pelo menos um item. A sugestão deve ser atualizada se o usuário alterar dados relevantes (ex: trocar o cliente). O usuário pode aceitar ou rejeitar a sugestão. Se rejeitada, o sistema deve solicitar confirmação e registrar no log |
| **Dados de Entrada** | Dados do pedido de venda em preenchimento |
| **Dados de Saída** | Campo de transação preenchido automaticamente com indicador visual de sugestão (ícone + tooltip com justificativa) |
| **Comportamento de Erro** | Se dados insuficientes para sugestão: campo permanece vazio com tooltip "Preencha cliente e itens para receber sugestão". Se API do motor de regras indisponível: permitir seleção manual normalmente |
| **Dependências** | RF01 (Motor de Regras) |
| **Prioridade** | Must |

### RF03 — Sugestão Automática em Emissão de Nota Fiscal

| Campo | Descrição |
|-------|-----------|
| **Descrição** | Ao iniciar a emissão de uma nota fiscal, o sistema deve sugerir automaticamente a transação adequada, considerando se há pedido de venda vinculado |
| **Regras de Negócio** | Se NF-e vinculada a PV: herdar transação do PV e validar se continua adequada. Se NF-e avulsa (sem PV): aplicar motor de regras normalmente. Validar consistência entre transação e dados fiscais (CFOP, CST, alíquotas). Alertar se a transação sugerida gerar inconsistência fiscal antes da transmissão à SEFAZ |
| **Dados de Entrada** | Dados da NF-e (cliente, itens, operação) + dados do PV vinculado (quando existir) |
| **Dados de Saída** | Transação sugerida/herdada com validação fiscal. Alertas de inconsistência quando aplicável |
| **Comportamento de Erro** | Se transação herdada do PV for inconsistente com contexto da NF-e: exibir alerta com sugestão alternativa. Se validação fiscal falhar: bloquear emissão e exibir detalhes do erro |
| **Dependências** | RF01 (Motor de Regras), RF02 (Sugestão em PV) |
| **Prioridade** | Must |

### RF04 — Cadastro e Gestão de Regras de Sugestão

| Campo | Descrição |
|-------|-----------|
| **Descrição** | O sistema deve oferecer uma interface para cadastro, edição, ativação/desativação e exclusão de regras de sugestão de transação |
| **Regras de Negócio** | Cada regra deve conter: nome, descrição, condições (combinação de parâmetros), transação resultante, prioridade (numérica), status (ativa/inativa). O sistema deve validar conflitos ao salvar uma nova regra. Deve ser possível importar/exportar regras. Deve haver regras padrão (templates) pré-configuradas por segmento |
| **Dados de Entrada** | Parâmetros da regra: condições, transação resultante, prioridade |
| **Dados de Saída** | Regra salva e ativa no motor de sugestão |
| **Comportamento de Erro** | Se conflito detectado: exibir regras conflitantes e solicitar resolução. Se transação referenciada não existir: bloquear salvamento |
| **Dependências** | Cadastro de transações |
| **Prioridade** | Must |

### RF05 — Indicador Visual de Confiança da Sugestão

| Campo | Descrição |
|-------|-----------|
| **Descrição** | O sistema deve exibir um indicador visual do nível de confiança da sugestão (Alta, Média, Baixa) junto à transação sugerida |
| **Regras de Negócio** | Alta: regra específica encontrada com match exato de todos os parâmetros. Média: regra encontrada com match parcial (alguns parâmetros genéricos). Baixa: sugestão baseada em regra genérica ou histórico. O indicador deve ser acompanhado de tooltip explicativo |
| **Dados de Entrada** | Resultado do motor de regras |
| **Dados de Saída** | Ícone colorido (verde/amarelo/vermelho) + texto de confiança + tooltip com justificativa |
| **Comportamento de Erro** | Se não for possível calcular confiança: exibir como "Não determinado" |
| **Dependências** | RF01 (Motor de Regras) |
| **Prioridade** | Should |

### RF06 — Validação Cruzada Transação x Dados Fiscais

| Campo | Descrição |
|-------|-----------|
| **Descrição** | O sistema deve validar a consistência entre a transação selecionada (sugerida ou manual) e os dados fiscais da operação antes da emissão |
| **Regras de Negócio** | Validar: CFOP compatível com UF origem/destino, CST compatível com regime tributário, alíquotas compatíveis com a operação, finalidade da NF-e compatível com a transação. Exibir alertas classificados por severidade (Erro bloqueante / Aviso / Informativo) |
| **Dados de Entrada** | Transação selecionada + dados fiscais da operação |
| **Dados de Saída** | Lista de validações com status (OK / Aviso / Erro) e descrição |
| **Comportamento de Erro** | Erros bloqueantes: impedir emissão até correção. Avisos: permitir emissão com confirmação do usuário |
| **Dependências** | RF01, RF03 |
| **Prioridade** | Must |

### RF07 — Log de Auditoria de Sugestões

| Campo | Descrição |
|-------|-----------|
| **Descrição** | O sistema deve registrar todas as sugestões realizadas, incluindo aceitações, rejeições e alterações manuais |
| **Regras de Negócio** | Registrar: data/hora, usuário, documento (PV ou NF), transação sugerida, transação efetivamente utilizada, ação (aceita/rejeitada/alterada), justificativa (quando rejeitada). Dados devem ser consultáveis por período, usuário, documento e tipo de ação |
| **Dados de Entrada** | Eventos de sugestão durante emissão de PV e NF |
| **Dados de Saída** | Registros de auditoria consultáveis |
| **Comportamento de Erro** | Se falha no registro: não bloquear operação, mas gerar alerta para administrador |
| **Dependências** | RF02, RF03 |
| **Prioridade** | Must |

### RF08 — Dashboard de Acurácia e Adoção

| Campo | Descrição |
|-------|-----------|
| **Descrição** | O sistema deve oferecer um painel com indicadores de performance do motor de sugestão |
| **Regras de Negócio** | Indicadores: taxa de aceitação de sugestões (%), taxa de rejeição (%), transações mais rejeitadas, cenários sem cobertura de regras, evolução temporal da acurácia. Filtros por período, filial, usuário, tipo de operação |
| **Dados de Entrada** | Dados do log de auditoria (RF07) |
| **Dados de Saída** | Gráficos e tabelas com KPIs |
| **Comportamento de Erro** | Se dados insuficientes: exibir mensagem informativa |
| **Dependências** | RF07 (Log de Auditoria) |
| **Prioridade** | Should |

### RF09 — Templates de Regras por Segmento

| Campo | Descrição |
|-------|-----------|
| **Descrição** | O sistema deve oferecer conjuntos pré-configurados de regras de sugestão para os cenários fiscais mais comuns do mercado brasileiro |
| **Regras de Negócio** | Templates disponíveis para: Venda de mercadoria (dentro do estado, interestadual, para consumidor final), Devolução de venda, Remessa para demonstração/consignação, Transferência entre filiais, Venda de serviço, Bonificação. Templates devem ser importáveis e editáveis. Não devem sobrescrever regras customizadas existentes |
| **Dados de Entrada** | Seleção do template pelo administrador |
| **Dados de Saída** | Regras importadas e ativas no motor |
| **Comportamento de Erro** | Se conflito com regras existentes: exibir comparativo e solicitar resolução |
| **Dependências** | RF04 (Cadastro de Regras) |
| **Prioridade** | Should |

### RF10 — Alerta Proativo de Inconsistência Pré-SEFAZ

| Campo | Descrição |
|-------|-----------|
| **Descrição** | Antes da transmissão da NF-e à SEFAZ, o sistema deve realizar uma validação final e alertar sobre possíveis inconsistências relacionadas à transação |
| **Regras de Negócio** | Validar: transação x CFOP, transação x CST/CSOSN, transação x tipo de operação na NF-e, transação x dados do destinatário. Classificar alertas: Bloqueante (impede transmissão), Aviso (permite com confirmação), Informativo. Exibir resumo de validação antes do envio |
| **Dados de Entrada** | NF-e completa pronta para transmissão |
| **Dados de Saída** | Relatório de validação com status por item verificado |
| **Comportamento de Erro** | Alertas bloqueantes impedem transmissão. Usuário deve corrigir antes de prosseguir |
| **Dependências** | RF03, RF06 |
| **Prioridade** | Must |

---

## 9. Requisitos Não Funcionais

| ID | Categoria | Requisito |
|----|-----------|-----------|
| **RNF01** | Performance | A sugestão de transação deve ser retornada em menos de 500ms após o preenchimento dos dados contextuais |
| **RNF02** | Performance | A validação cruzada pré-SEFAZ deve ser concluída em menos de 2 segundos para NF-e com até 100 itens |
| **RNF03** | Disponibilidade | O motor de sugestão deve ter disponibilidade de 99,5%. Em caso de indisponibilidade, o fluxo manual deve funcionar normalmente |
| **RNF04** | Escalabilidade | O motor de regras deve suportar até 10.000 regras ativas sem degradação de performance |
| **RNF05** | Segurança | O cadastro de regras deve respeitar a matriz de permissões do ERP (somente administradores e perfis autorizados) |
| **RNF06** | Segurança | Logs de auditoria devem ser imutáveis e protegidos contra alteração |
| **RNF07** | Responsividade | A interface de sugestão deve funcionar em desktop (resolução mínima 1366x768) |
| **RNF08** | Auditoria | Todas as ações de sugestão (aceite, rejeição, alteração) devem ser registradas com user_id, timestamp e contexto |
| **RNF09** | Acessibilidade | Indicadores visuais de confiança devem ter alternativas textuais (não depender apenas de cor). Conformidade com diretrizes de acessibilidade |
| **RNF10** | Manutenibilidade | Regras de sugestão devem ser configuráveis sem necessidade de deploy ou alteração de código |
| **RNF11** | Compatibilidade | A funcionalidade deve ser compatível com todos os navegadores suportados pelo ERP Senior X SaaS |

---

## 10. Compliance, LGPD e Requisitos Legais

### 10.1 Dados Sensíveis Envolvidos

| Dado | Classificação | Justificativa |
|------|---------------|---------------|
| CNPJ/CPF de clientes | Dado pessoal | Utilizado como parâmetro para determinação de regime tributário e tipo de cliente |
| Razão social / Nome | Dado pessoal | Exibido na interface durante a sugestão |
| Dados fiscais (CFOP, CST, alíquotas) | Dado empresarial | Não são dados pessoais, mas são sensíveis do ponto de vista comercial |
| Histórico de operações | Dado empresarial | Utilizado para aprendizado e sugestões baseadas em histórico |

### 10.2 Requisitos de Conformidade

| Requisito | Descrição |
|-----------|-----------|
| **Trilha de auditoria (LGPD)** | Logs com user_id, timestamp, ação realizada e contexto. Retenção mínima de 5 anos (exigência fiscal) |
| **Matriz de segurança** | Respeitar permissões já configuradas no ERP Senior X. Acesso ao cadastro de regras restrito a perfis autorizados |
| **Fidelidade fiscal** | Sugestões devem estar 100% aderentes à legislação fiscal vigente (CFOP, CST, CSOSN, alíquotas). Atualizações legislativas devem ser refletidas nas regras |
| **Minimização de dados** | O motor de sugestão deve utilizar apenas os dados estritamente necessários para a determinação da transação |
| **Transparência** | O usuário deve ter visibilidade sobre por que uma transação foi sugerida (justificativa explícita) |
| **Não geração de obrigações acessórias** | A sugestão em si não deve gerar eventos fiscais. Apenas a confirmação/emissão efetiva gera obrigações |

### 10.3 Classificação Geral de Risco LGPD

**Risco: Baixo**

Justificativa: A funcionalidade utiliza predominantemente dados empresariais (transações, CFOP, regimes tributários) e dados cadastrais já existentes no ERP. Não há coleta de novos dados pessoais. O tratamento de CNPJ/CPF é limitado à consulta para determinação de parâmetros fiscais, com base legal de execução de contrato e cumprimento de obrigação legal (legislação fiscal).

---

## 11. Entregáveis

| Componente | Descrição da Entrega |
|------------|---------------------|
| **Interface (UI) — Motor de Regras** | Tela de cadastro, edição e gestão de regras de sugestão em Configurações > Venda e Faturamento > Regras de Sugestão |
| **Interface (UI) — Sugestão em PV** | Componente de sugestão integrado à tela de emissão de pedido de venda (indicador visual + tooltip + ação de aceite/rejeição) |
| **Interface (UI) — Sugestão em NF-e** | Componente de sugestão integrado à tela de emissão de nota fiscal (herança de PV + validação + alertas) |
| **Interface (UI) — Dashboard** | Painel de gestão com KPIs de acurácia e adoção em Relatórios > Venda e Faturamento > Sugestão de Transação |
| **Backend / API** | API do motor de regras (avaliação de contexto, retorno de sugestão, validação cruzada) |
| **Backend / API** | API de gestão de regras (CRUD + importação/exportação + templates) |
| **Backend / API** | API de auditoria (registro e consulta de logs de sugestão) |
| **Templates** | Conjunto de regras pré-configuradas para cenários fiscais comuns (venda interna, interestadual, devolução, remessa, transferência, serviço) |
| **Documentação** | Help online integrado ao sistema, release notes, guia de configuração de regras |

---

## 12. Cenários de Teste (QA)

### 12.1 Cenários Positivos (Happy Path)

| # | Cenário | Descrição / Condições | Resultado Esperado |
|---|---------|----------------------|-------------------|
| C01 | Sugestão em PV — Venda interna para contribuinte | PV para cliente contribuinte ICMS, mesma UF, mercadoria | Transação de venda interna sugerida (ex: 5102), confiança Alta |
| C02 | Sugestão em PV — Venda interestadual | PV para cliente em outra UF, contribuinte | Transação interestadual sugerida (ex: 6102), confiança Alta |
| C03 | Sugestão em PV — Venda para consumidor final | PV para pessoa física, mesma UF | Transação para consumidor final sugerida (ex: 5101), confiança Alta |
| C04 | Sugestão em NF-e herdada de PV | NF-e gerada a partir de PV com transação já definida | Transação herdada do PV, validação OK exibida |
| C05 | Sugestão em NF-e avulsa | NF-e sem PV vinculado, dados preenchidos manualmente | Motor de regras sugere transação adequada |
| C06 | Aceitação de sugestão | Usuário aceita sugestão com um clique | Transação preenchida, log de auditoria registrado como "aceita" |
| C07 | Validação cruzada OK | Transação compatível com CFOP, CST e alíquotas | Validação retorna "OK" para todos os itens |

### 12.2 Cenários Negativos (Edge Cases)

| # | Cenário | Descrição / Condições | Resultado Esperado |
|---|---------|----------------------|-------------------|
| C08 | Rejeição de sugestão | Usuário rejeita sugestão e seleciona outra transação | Alerta de divergência exibido, log registrado como "rejeitada" |
| C09 | Nenhuma regra aplicável | Cenário fiscal não coberto por nenhuma regra | Mensagem "Não foi possível sugerir" exibida, seleção manual habilitada, gap registrado |
| C10 | Conflito de regras | Duas regras com mesma condição e prioridade | Sistema aplica regra mais recente e registra conflito no log |
| C11 | Inconsistência transação x CFOP | Transação selecionada manualmente incompatível com CFOP | Alerta bloqueante exibido, emissão impedida até correção |
| C12 | Motor de regras indisponível | API do motor fora do ar | Fluxo manual funciona normalmente, mensagem informativa exibida |
| C13 | Alteração de cliente após sugestão | Usuário altera cliente no PV após receber sugestão | Sugestão recalculada automaticamente para novo contexto |
| C14 | Regra com transação inexistente | Administrador tenta salvar regra referenciando transação inativa | Erro de validação, salvamento bloqueado |
| C15 | Importação de template com conflito | Template importado conflita com regras existentes | Comparativo exibido, usuário decide resolução |

---

## 13. Dependências e Integrações

### 13.1 Dependências Internas

| Dependência | Tipo | Descrição |
|-------------|------|-----------|
| Cadastro de Transações | Dados | Base de transações fiscais configuradas no ERP — fonte primária para sugestões |
| Cadastro de Clientes | Dados | Dados de CNPJ/CPF, UF, regime tributário, tipo de contribuinte |
| Cadastro de Produtos | Dados | NCM, tipo de produto (mercadoria/serviço/ativo), classificação fiscal |
| Módulo de Pedido de Venda | Serviço | Tela de emissão de PV onde a sugestão será integrada |
| Módulo de Faturamento/NF-e | Serviço | Tela de emissão de NF-e onde a sugestão será integrada |
| Motor Fiscal existente | Serviço | Regras de cálculo de impostos (ICMS, IPI, PIS, COFINS) para validação cruzada |
| Infraestrutura de Auditoria | Serviço | Framework de logs do ERP Senior X para registro de eventos |

### 13.2 Integrações Externas

| Sistema / API | Tipo | Descrição |
|---------------|------|-----------|
| SEFAZ (NF-e) | Regulatório | A sugestão não interage diretamente com a SEFAZ, mas a validação pré-SEFAZ garante consistência antes da transmissão |
| Tabelas fiscais (CFOP, CST, CSOSN, NCM) | Dados | Tabelas atualizadas pela Receita Federal — necessárias para validação cruzada e templates de regras |

---

## 14. Riscos e Mitigações

| # | Risco | Impacto | Probabilidade | Mitigação |
|---|-------|---------|---------------|-----------|
| **R1** | Sugestão incorreta gera emissão de NF-e com transação errada | Crítico | Baixa | Validação cruzada obrigatória pré-SEFAZ (RF06/RF10). Indicador de confiança para alertar o usuário. Log de auditoria para rastreabilidade |
| **R2** | Baixa adoção por desconfiança dos usuários | Alto | Média | Exibir justificativa transparente para cada sugestão. Indicador de confiança. Dashboard de acurácia para gestores. Treinamento e comunicação |
| **R3** | Complexidade de configuração de regras | Médio | Média | Templates pré-configurados por segmento. Interface intuitiva de cadastro. Documentação e help online |
| **R4** | Mudanças na legislação fiscal invalidam regras | Alto | Alta | Processo de atualização de templates vinculado a atualizações fiscais do ERP. Alertas para administradores quando regras podem estar desatualizadas |
| **R5** | Performance degradada com volume alto de regras | Médio | Baixa | Otimização do motor de regras com indexação. Limite de 10.000 regras com monitoramento. Cache de regras mais utilizadas |
| **R6** | Escopo crescente (pedidos de inclusão de IA avançada, ML) | Médio | Alta | Fases bem definidas: Fase 1 = motor de regras; Fase 2 = IA/ML como evolução futura. Gates claros entre fases |

---

## 15. Métricas de Sucesso

> ⚠️ **Atenção**: Todas as metas abaixo dependem do levantamento de baseline real durante a fase de Discovery. Sem dados concretos da operação atual, as metas não podem ser definidas com responsabilidade. Os prazos de medição são sugestões iniciais.

| Métrica | Baseline (Atual) | Meta | Prazo de Medição |
|---------|-------------------|------|-----------------|
| Taxa de erro em seleção de transação (PV) | 🔴 Necessário levantar | A definir com base no baseline | 6 meses após release |
| Taxa de erro em seleção de transação (NF-e) | 🔴 Necessário levantar | A definir com base no baseline | 6 meses após release |
| Taxa de aceitação de sugestões | 0% (funcionalidade não existe) | A definir | 6 meses após release |
| Cancelamentos de NF-e por erro de transação | 🔴 Necessário levantar | A definir com base no baseline | 6 meses após release |
| Tickets de suporte sobre transação incorreta | 🔴 Necessário levantar | A definir com base no baseline | 6 meses após release |
| Tempo médio de emissão de PV | 🔴 Necessário levantar | A definir com base no baseline | 3 meses após release |
| Cobertura de cenários por regras | 0% (funcionalidade não existe) | A definir | 3 meses após release |

---

## 16. Plano de Execução (Roadmap)

### Fase 1 — Discovery e Definição
- PRD finalizado e validado com stakeholders
- Mapeamento completo de cenários fiscais mais comuns (top 20 transações)
- Protótipo de alta fidelidade da interface de sugestão
- Duração estimada: 2 sprints

### Fase 2 — Desenvolvimento do Motor de Regras
- Backend: API do motor de regras (RF01)
- Backend: API de gestão de regras (RF04)
- Frontend: Tela de cadastro de regras
- Templates de regras para cenários comuns (RF09)
- Duração estimada: 3 sprints

### Fase 3 — Integração com PV e NF-e
- Frontend: Componente de sugestão em Pedido de Venda (RF02)
- Frontend: Componente de sugestão em Emissão de NF-e (RF03)
- Backend: Validação cruzada pré-SEFAZ (RF06, RF10)
- Backend: Log de auditoria (RF07)
- Duração estimada: 3 sprints

### Fase 4 — Dashboard e Refinamentos
- Frontend: Dashboard de acurácia e adoção (RF08)
- Indicador de confiança (RF05)
- Ajustes de UX baseados em feedback interno
- Duração estimada: 2 sprints

### Fase 5 — QA e Homologação
- Execução dos cenários de teste (C01 a C15)
- Testes de performance com volume de regras
- Homologação com clientes piloto
- Duração estimada: 2 sprints

### Fase 6 — Release e Acompanhamento
- Deploy em produção (rollout gradual)
- Monitoramento de métricas de adoção e acurácia
- Coleta de feedback para evolução (Fase futura: IA/ML)
- Duração estimada: 1 sprint + acompanhamento contínuo

---

## 17. Glossário e Referências

| Termo / Sigla | Definição |
|----------------|-----------|
| **Transação** | Configuração fiscal no ERP que define o comportamento tributário de uma operação (CFOP, CST, alíquotas, natureza da operação) |
| **CFOP** | Código Fiscal de Operações e Prestações — identifica a natureza de circulação de mercadoria ou prestação de serviço |
| **CST** | Código de Situação Tributária — identifica a tributação do ICMS para empresas do regime normal |
| **CSOSN** | Código de Situação da Operação do Simples Nacional — equivalente ao CST para empresas do Simples Nacional |
| **NCM** | Nomenclatura Comum do Mercosul — classificação fiscal de mercadorias |
| **NF-e** | Nota Fiscal Eletrônica — documento fiscal digital autorizado pela SEFAZ |
| **PV** | Pedido de Venda — documento comercial que origina o faturamento |
| **SEFAZ** | Secretaria da Fazenda — órgão estadual responsável pela autorização de NF-e |
| **MoSCoW** | Método de priorização: Must, Should, Could, Won't |
| **SaaS** | Software as a Service — modelo de entrega de software via nuvem |
| **ERP** | Enterprise Resource Planning — sistema integrado de gestão empresarial |
| **LGPD** | Lei Geral de Proteção de Dados (Lei nº 13.709/2018) |

**Referências:**
- Documentação do módulo Venda e Faturamento — ERP Senior X
- Legislação fiscal brasileira (CFOP, CST, CSOSN) — Receita Federal
- LGPD — Lei nº 13.709/2018

---

## Histórico de Versões

| Versão | Data | Autor | Alterações |
|--------|------|-------|------------|
| v0.1 | 10/04/2026 | [Nome] | Criação do documento |

---

> **Nota**: Itens marcados como "Necessário validar" devem ser preenchidos com dados reais durante a fase de Discovery, antes do início do desenvolvimento. Recomenda-se levantar métricas de baseline com a equipe de suporte e dados do sistema em produção.
