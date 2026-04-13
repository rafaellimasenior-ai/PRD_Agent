# PRD — Score Financeiro Inteligente

## Metadados do Documento

| Campo | Valor |
|---|---|
| Produto / Módulo | ERP Senior X — Gestão de Cobrança |
| Funcionalidade | Score Financeiro Inteligente |
| Tipo | Melhoria / Evolução de funcionalidade existente |
| Status | Em Definição |
| Product Owner | Necessário validar |
| Stakeholders | Time de Produto, Engenharia, UX, Comercial, CS |
| Data de criação | Necessário validar |
| Última atualização | Necessário validar |
| Versão | v0.1 |

---

## 1. Visão do Produto

O **Score Financeiro Inteligente** é uma evolução do módulo de Score de Crédito existente no ERP Senior X — Gestão de Cobrança, que incorpora análise preditiva de comportamento de carteira para antecipar riscos de inadimplência antes que eles se concretizem.

**Para quem:** Analistas de crédito, gestores financeiros e equipes de cobrança que utilizam o ERP Senior X.

**Valor entregue:** Capacidade de agir proativamente sobre clientes com tendência de deterioração financeira, reduzindo perdas por inadimplência e aumentando a eficiência das ações de cobrança.

**Resumo executivo:** Atualmente o score é calculado a cada 15 dias com base em dados históricos estáticos. Isso significa que a empresa só percebe o risco quando ele já se materializou. A evolução proposta adiciona uma camada preditiva que analisa tendências de comportamento ao longo do tempo, sinalizando clientes em trajetória de declínio antes que atinjam classificações críticas. Isso é estratégico para redução de inadimplência, priorização de cobrança e proteção da receita.

---

## 2. Problema e Evidências

### 2.1 Estado Atual (As-Is)

O Score de Crédito atual do ERP Senior X calcula uma pontuação estática a cada 15 dias com base em 4 dimensões: Comportamento de Pagamento, Severidade da Inadimplência, Concentração e Exposição, e Representatividade. O resultado é uma fotografia do momento, sem análise de tendência ou trajetória.

Workarounds atuais dos usuários:
- Análise manual de histórico de pagamentos em planilhas externas
- Revisão periódica manual de clientes com score "Regular" para identificar piora
- Sem alertas automáticos — a equipe só age quando o cliente já está inadimplente

### 2.2 Evidências de Dor

| Fonte da Evidência | Descrição |
|---|---|
| Feedback de clientes | Necessário validar — coletar junto ao CS e time comercial |
| Dados internos | Necessário validar — levantar % de clientes que passaram de "Bom" para "Baixo" sem alerta prévio |
| Time de Vendas / CS | Necessário validar — identificar perdas de contrato por inadimplência não prevista |
| Suporte / Tickets | Necessário validar — volume de solicitações relacionadas a análise de risco de carteira |

### 2.3 Benchmark (Concorrência)

O benchmark foi estruturado em três camadas: ERPs nacionais concorrentes diretos, plataformas especializadas em crédito/cobrança no Brasil, e referências globais de mercado com análise preditiva avançada.

#### Concorrentes Diretos — ERPs Nacionais

| Concorrente | Score / Análise de Crédito | Análise de Tendência / Preditivo | Alertas Proativos | Integração Bureau | Modelo de Pricing |
|---|---|---|---|---|---|
| **TOTVS (Protheus / Fluig)** | Score estático com histórico de pagamentos e limite de crédito configurável | Não possui — análise pontual sem trajetória temporal | Não possui alertas automáticos de deterioração | Integração com Serasa/SPC disponível | Licença por módulo; pricing sob consulta |
| **Sankhya** | Análise de risco com consulta a bureaus externos (Serasa, SPC) e score baseado em dados externos | Não possui motor preditivo interno de tendência de carteira | Régua de cobrança automatizada, mas sem alerta de tendência de score | Integração nativa com Serasa/SPC | Licença por usuário/módulo; pricing sob consulta |
| **Benner** | Gestão de cobrança com régua automatizada e classificação de risco básica | Não possui análise preditiva de score | Alertas de vencimento e cobrança, sem sinalização de tendência | Integração com bureaus disponível | Pricing sob consulta |
| **LG Sistemas** | Módulo financeiro com score de crédito básico baseado em histórico interno | Não possui análise comportamental preditiva | Sem alertas de tendência | Integração com bureaus disponível | Pricing sob consulta |

#### Concorrentes Indiretos — Plataformas Especializadas em Crédito/Cobrança (Brasil)

| Plataforma | Proposta de Valor | Score / Análise de Risco | Análise Preditiva | Diferencial |
|---|---|---|---|---|
| **Serasa Experian (B2B)** | Bureau de crédito com soluções para empresas — consulta de score, monitoramento de carteira e alertas de mudança de perfil | Score baseado em dados externos (histórico nacional de crédito, protestos, ações judiciais) | Monitoramento contínuo com alertas de mudança de score do cliente no bureau | Maior base de dados do Brasil; score externo com visão de mercado ampla — mas não analisa comportamento interno da carteira da empresa |
| **Credits Brasil (SPC Brasil)** | Plataforma de análise de crédito, antifraude e recuperação de crédito com régua de cobrança | Score baseado em dados do SPC Brasil; consultas PF/PJ com relatórios de risco | Automação de regras de crédito com políticas configuráveis | Integração com negativação estratégica via SPC; foco em decisão de crédito na concessão, não em monitoramento contínuo da carteira |
| **Quod** | Bureau de crédito com Cadastro Positivo — score baseado em comportamento de pagamento positivo | Score com dados de Cadastro Positivo (comportamento de pagamento histórico) | Não possui análise preditiva de tendência interna | Único bureau com foco em Cadastro Positivo no Brasil; dados complementares ao Serasa/SPC |
| **iugu** | Plataforma de gestão financeira e cobrança recorrente para SaaS e empresas digitais | Análise de inadimplência e métricas de cobrança recorrente | Relatórios de comportamento de pagamento e churn financeiro | Foco em cobrança recorrente/assinaturas; sem score de crédito estruturado para carteiras B2B tradicionais |

#### Referências Globais — Plataformas com Análise Preditiva Avançada

| Plataforma | Proposta de Valor | Análise Preditiva | Diferencial vs. Senior X |
|---|---|---|---|
| **HighRadius (EUA/Global)** | Plataforma de AR (Accounts Receivable) com IA — líder no Gartner Magic Quadrant 2025 para Invoice-to-Cash | Análise de comportamento de pagamento com 20+ parâmetros; previsão de contas em atraso; priorização de cobrança por IA com 13+ agentes de IA | Análise preditiva madura com ML; integração com 35+ bureaus globais; foco em grandes empresas enterprise — alto custo e complexidade de implantação |
| **Sidetrade (França/Global)** | Plataforma O2C (Order-to-Cash) com IA para gestão de crédito e cobrança | Monitoramento contínuo orientado a eventos — detecta deterioração de pagamento e mudanças externas antes que escalem; alertas em tempo real | Monitoramento event-driven (não apenas por ciclo); visão unificada de dados internos + bureaus; foco em enterprise com operações globais |
| **Emagia (EUA/Global)** | Plataforma de AR automation com IA preditiva para crédito e cobrança | Score de risco dinâmico por cliente com dados internos e externos; previsão de inadimplência com ML; priorização inteligente de cobrança | Score dinâmico (não estático por ciclo); análise 360° do cliente; integrado a ERPs como SAP e NetSuite — sem versão para mercado brasileiro |

#### Análise Comparativa — Capacidades-Chave

| Capacidade | Senior X (Atual) | Senior X (Proposto) | TOTVS | Sankhya | HighRadius | Sidetrade |
|---|---|---|---|---|---|---|
| Score interno por ciclo | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ |
| Histórico de score (série temporal) | ❌ | ✅ | ❌ | ❌ | ✅ | ✅ |
| Análise de tendência de score | ❌ | ✅ | ❌ | ❌ | ✅ | ✅ |
| Alertas proativos de deterioração | ❌ | ✅ | ❌ | ❌ | ✅ | ✅ |
| Dashboard de carteira com tendências | ❌ | ✅ | ❌ | ❌ | ✅ | ✅ |
| Baseado em dados internos (sem bureau) | ✅ | ✅ | Parcial | ❌ | Parcial | Parcial |
| Integração com bureaus externos | ❌ | ❌ (v1) | ✅ | ✅ | ✅ | ✅ |
| Disponível em português / mercado BR | ✅ | ✅ | ✅ | ✅ | ❌ | ❌ |

#### Oportunidades de Diferenciação Identificadas

1. **Gap no mercado nacional de ERPs:** Nenhum ERP nacional concorrente (TOTVS, Sankhya, Benner, LG) oferece análise preditiva de tendência de score baseada no comportamento interno da carteira. A Senior X pode ser pioneira nesse segmento.

2. **Independência de bureaus externos como diferencial:** Soluções como Serasa e Credits Brasil dependem de dados externos para análise de risco. A proposta da Senior X usa exclusivamente dados internos da carteira — mais relevante para o contexto de relacionamento comercial já estabelecido.

3. **Custo-benefício vs. soluções globais:** HighRadius e Sidetrade oferecem análise preditiva avançada, mas são soluções enterprise de alto custo, em inglês, sem adaptação ao mercado brasileiro. A Senior X pode entregar capacidade preditiva similar com menor complexidade e custo, integrada ao ERP já utilizado pelo cliente.

4. **Integração nativa ao fluxo de cobrança:** Diferente de plataformas standalone de score (Serasa, Quod), a análise preditiva da Senior X estará integrada diretamente ao módulo de cobrança — permitindo ação imediata a partir do alerta, sem troca de sistema.

> ⚠️ Necessário validar: pricing dos concorrentes nacionais (TOTVS, Sankhya, Benner, LG) junto ao time comercial para análise competitiva de posicionamento de preço.

---

## 3. Objetivos de Negócio

| # | Objetivo | Métrica Alvo |
|---|---|---|
| O1 | Reduzir inadimplência por falta de antecipação de risco | Necessário validar — sugestão: redução de X% em clientes que transitam de "Bom" para "Baixo" sem ação prévia |
| O2 | Aumentar eficiência da equipe de cobrança com priorização inteligente | Necessário validar — sugestão: redução de Y% no tempo médio de acionamento de clientes em risco |
| O3 | Aumentar adoção do módulo de score | Necessário validar — sugestão: 40% da base ativa utilizando alertas de tendência em 3 meses |
| O4 | Reduzir perdas financeiras por inadimplência não prevista | Necessário validar — sugestão: redução de Z% no valor de títulos vencidos sem ação prévia |

---

## 4. Pricing

**Modelo atual:** Necessário validar — identificar se o módulo de score atual é cobrado separadamente ou está incluso no ERP Senior X.

**Modelos possíveis para a evolução:**
- Inclusão na licença existente do módulo de Gestão de Cobrança (sem custo adicional — estratégia de retenção e diferenciação)
- Módulo adicional com cobrança por volume de clientes analisados (modelo SaaS por faixa)
- Feature premium dentro do módulo de Gestão de Cobrança (upsell)

**Custos a considerar:** Infraestrutura de processamento para algoritmos preditivos (recálculo de tendências), armazenamento de histórico de scores para análise temporal.

> ⚠️ Necessário validar com time comercial e financeiro qual modelo se aplica.

---

## 5. Personas

| Persona | Perfil | Necessidade Principal | Valor Recebido |
|---|---|---|---|
| Analista de Crédito | Profissional responsável por avaliar e liberar crédito para clientes | Identificar clientes com risco crescente antes de liberar novos créditos | Recebe alertas de tendência de declínio antes de tomar decisões de crédito |
| Gestor Financeiro | Responsável pela saúde financeira da carteira de recebíveis | Visão macro da carteira com indicadores de risco preditivo | Dashboard com tendências da carteira, permitindo ações estratégicas antecipadas |
| Analista de Cobrança | Responsável por acionar clientes inadimplentes ou em risco | Priorizar quais clientes acionar primeiro com base em risco real | Lista priorizada de clientes com maior probabilidade de inadimplência futura |
| Diretor / CFO | Tomador de decisão estratégica sobre crédito e cobrança | Visão consolidada de risco da carteira com tendências | Relatórios executivos com projeção de risco e impacto financeiro potencial |

---

## 6. Estrutura do Produto (Módulos / Blocos)

### Módulo 1 — Motor de Tendência Preditiva (Backend)
Responsável por calcular a trajetória do score ao longo do tempo e identificar padrões de declínio.

Funcionalidades:
- Armazenamento do histórico de scores por cliente (série temporal)
- Algoritmo de detecção de tendência de declínio (ex: regressão linear simples sobre os últimos N ciclos)
- Classificação de tendência: Estável, Atenção, Declínio, Recuperação
- Recálculo de tendência a cada ciclo de score (a cada 15 dias)

### Módulo 2 — Alertas e Sinalizações
Responsável por notificar usuários sobre clientes com risco crescente.

Funcionalidades:
- Geração de alertas automáticos para clientes com tendência de declínio
- Configuração de limiar de alerta (ex: queda de X pontos em N ciclos)
- Fila de clientes priorizados por risco de deterioração
- Indicador visual de tendência na ficha do cliente (ícone/badge)

### Módulo 3 — Dashboard de Carteira Inteligente
Visão consolidada da saúde da carteira com perspectiva preditiva.

Funcionalidades:
- Painel com distribuição de clientes por tendência (Estável / Atenção / Declínio / Recuperação)
- Gráfico de evolução do score médio da carteira ao longo do tempo
- Filtros por segmento, faixa de score, tendência e período
- Exportação de relatório de clientes em risco

### Módulo 4 — Configurações do Score Inteligente
Permite que o administrador ajuste parâmetros do motor preditivo.

Funcionalidades:
- Configuração do número de ciclos usados para cálculo de tendência
- Configuração dos limiares de alerta por classificação de risco
- Ativação/desativação de alertas por perfil de usuário

---

## 7. Fluxo do Usuário

### 7.1 Fluxo Principal — Analista de Cobrança identifica clientes em risco

1. Analista acessa o módulo de Gestão de Cobrança no ERP Senior X
2. Acessa o Dashboard de Carteira Inteligente
3. Visualiza painel com clientes classificados por tendência de score
4. Filtra por "Declínio" para ver clientes com trajetória negativa
5. Seleciona um cliente da lista para ver detalhes
6. Visualiza gráfico de evolução do score do cliente nos últimos ciclos
7. Visualiza indicador de tendência e projeção de risco
8. Registra ação de cobrança preventiva diretamente na ficha do cliente

### 7.2 Fluxos Alternativos

- Fluxo de alerta proativo: Sistema gera notificação automática quando cliente atinge limiar de declínio configurado — analista recebe alerta na tela inicial e acessa diretamente a ficha do cliente
- Fluxo de configuração: Administrador acessa configurações do score inteligente, ajusta número de ciclos e limiares de alerta, salva configuração — motor recalcula tendências no próximo ciclo
- Fluxo de exportação: Gestor filtra carteira por tendência "Declínio", exporta relatório em CSV/PDF para análise externa ou reunião de gestão

---

## 8. Requisitos Funcionais

### RF01 — Armazenamento de Histórico de Score

| Campo | Descrição |
|---|---|
| Descrição | O sistema deve armazenar o score calculado de cada cliente a cada ciclo de recálculo, formando uma série temporal |
| Regras de Negócio | Manter histórico mínimo de 12 ciclos (6 meses) para cálculo de tendência; histórico completo para análise; não sobrescrever registros anteriores |
| Dados de Entrada | Score calculado, data do cálculo, identificador do cliente |
| Dados de Saída | Série histórica de scores por cliente com data de cada registro |
| Comportamento de Erro | Se o cálculo do ciclo falhar, manter último score válido e registrar falha no log |
| Dependências | Motor de cálculo de score existente |
| Prioridade | Must |

### RF02 — Cálculo de Tendência de Score

| Campo | Descrição |
|---|---|
| Descrição | O sistema deve calcular a tendência do score de cada cliente com base na série histórica, classificando-a em: Estável, Atenção, Declínio ou Recuperação |
| Regras de Negócio | Tendência calculada sobre os últimos N ciclos (configurável, padrão: 6 ciclos); Declínio = queda consistente acima do limiar configurado; Atenção = queda moderada ou volatilidade; Recuperação = alta consistente após período de declínio; Estável = variação dentro da margem de tolerância |
| Dados de Entrada | Série histórica de scores do cliente, parâmetros de configuração (N ciclos, limiares) |
| Dados de Saída | Classificação de tendência, variação absoluta e percentual no período, projeção do próximo ciclo |
| Comportamento de Erro | Se histórico insuficiente (menos de 3 ciclos), exibir "Dados insuficientes" sem classificar tendência |
| Dependências | RF01 |
| Prioridade | Must |

### RF03 — Indicador Visual de Tendência na Ficha do Cliente

| Campo | Descrição |
|---|---|
| Descrição | O sistema deve exibir um indicador visual de tendência na ficha do cliente dentro do módulo de Gestão de Cobrança |
| Regras de Negócio | Ícone/badge colorido: verde (Estável/Recuperação), amarelo (Atenção), vermelho (Declínio); exibir variação do score no período; exibir classificação textual |
| Dados de Entrada | Tendência calculada pelo RF02 |
| Dados de Saída | Indicador visual com cor, ícone, texto de classificação e variação numérica |
| Comportamento de Erro | Se tendência não calculada, exibir "Sem dados de tendência" sem ícone colorido |
| Dependências | RF02 |
| Prioridade | Must |

### RF04 — Gráfico de Evolução do Score do Cliente

| Campo | Descrição |
|---|---|
| Descrição | O sistema deve exibir um gráfico de linha com a evolução do score do cliente ao longo dos ciclos históricos na ficha do cliente |
| Regras de Negócio | Exibir mínimo dos últimos 6 ciclos; exibir linha de tendência projetada para o próximo ciclo; marcar visualmente os limiares de classificação de risco (Excelente/Bom/Regular/Baixo) |
| Dados de Entrada | Série histórica de scores (RF01), tendência calculada (RF02) |
| Dados de Saída | Gráfico de linha interativo com pontos de score por data, linha de tendência e faixas de classificação |
| Comportamento de Erro | Se menos de 2 pontos históricos, exibir mensagem "Histórico insuficiente para exibir gráfico" |
| Dependências | RF01, RF02 |
| Prioridade | Must |

### RF05 — Dashboard de Carteira Inteligente

| Campo | Descrição |
|---|---|
| Descrição | O sistema deve disponibilizar um painel consolidado com a visão da carteira de clientes segmentada por tendência de score |
| Regras de Negócio | Exibir contagem e percentual de clientes por classificação de tendência; exibir gráfico de evolução do score médio da carteira; permitir filtros por: tendência, faixa de score atual, segmento de cliente, período; ordenação padrão por risco (Declínio primeiro) |
| Dados de Entrada | Tendências calculadas de todos os clientes ativos (RF02), filtros selecionados pelo usuário |
| Dados de Saída | Painel com cards de resumo, lista de clientes filtrada e ordenada, gráfico de carteira |
| Comportamento de Erro | Se nenhum cliente com dados suficientes, exibir estado vazio com orientação ao usuário |
| Dependências | RF02 |
| Prioridade | Must |

### RF06 — Alertas Automáticos de Declínio

| Campo | Descrição |
|---|---|
| Descrição | O sistema deve gerar alertas automáticos para usuários quando clientes atingirem o limiar de declínio configurado |
| Regras de Negócio | Alerta gerado no ciclo em que o cliente atinge classificação "Declínio" pela primeira vez ou após período de estabilidade; não gerar alerta duplicado no mesmo ciclo; alerta deve conter: nome do cliente, score atual, variação, classificação de tendência |
| Dados de Entrada | Resultado do cálculo de tendência (RF02), configuração de limiares (RF08) |
| Dados de Saída | Notificação na interface do ERP para usuários com permissão de visualização de cobrança |
| Comportamento de Erro | Se falha no envio de alerta, registrar em log e tentar reenvio no próximo ciclo |
| Dependências | RF02, RF08 |
| Prioridade | Should |

### RF07 — Exportação de Relatório de Clientes em Risco

| Campo | Descrição |
|---|---|
| Descrição | O sistema deve permitir a exportação da lista de clientes filtrada no Dashboard de Carteira Inteligente |
| Regras de Negócio | Formatos: CSV e PDF; incluir campos: nome do cliente, CNPJ/CPF, score atual, tendência, variação no período, data do último cálculo; respeitar filtros aplicados no dashboard |
| Dados de Entrada | Lista filtrada de clientes (RF05), seleção de formato pelo usuário |
| Dados de Saída | Arquivo CSV ou PDF para download |
| Comportamento de Erro | Se lista vazia, desabilitar botão de exportação com tooltip explicativo |
| Dependências | RF05 |
| Prioridade | Should |

### RF08 — Configurações do Motor Preditivo

| Campo | Descrição |
|---|---|
| Descrição | O sistema deve permitir que administradores configurem os parâmetros do motor de tendência preditiva |
| Regras de Negócio | Parâmetros configuráveis: número de ciclos para cálculo de tendência (mínimo 3, máximo 12); limiar de queda para classificação "Declínio" (em pontos); limiar para "Atenção"; ativação/desativação de alertas por perfil; alterações aplicadas no próximo ciclo de recálculo |
| Dados de Entrada | Valores configurados pelo administrador |
| Dados de Saída | Configuração salva, confirmação de aplicação no próximo ciclo |
| Comportamento de Erro | Validar limites mínimos e máximos; exibir erro descritivo se valor inválido |
| Dependências | Módulo de configurações do ERP Senior X |
| Prioridade | Could |

---

## 9. Requisitos Não Funcionais

| ID | Categoria | Requisito |
|---|---|---|
| RNF01 | Performance | Cálculo de tendência para toda a carteira deve ser concluído dentro da janela do ciclo de recálculo (15 dias); processamento assíncrono para carteiras grandes |
| RNF02 | Performance | Dashboard de Carteira Inteligente deve carregar em menos de 3 segundos para carteiras de até 10.000 clientes ativos |
| RNF03 | Responsividade | Interface desktop — compatível com resoluções a partir de 1280x768; não requer suporte mobile nesta versão |
| RNF04 | Segurança | Acesso ao dashboard e alertas restrito a perfis com permissão de visualização do módulo de Gestão de Cobrança |
| RNF05 | Segurança | Dados de score e tendência não devem ser expostos via API sem autenticação e autorização adequadas |
| RNF06 | Auditoria | Log de todas as ações de configuração do motor preditivo com user_id, timestamp e valores alterados |
| RNF07 | Escalabilidade | Motor de tendência deve suportar processamento de carteiras com até 50.000 clientes ativos sem degradação de performance (Necessário validar capacidade atual do ambiente) |
| RNF08 | Disponibilidade | Falha no cálculo de tendência não deve impactar o cálculo do score principal existente |
| RNF09 | Acessibilidade | Indicadores visuais de tendência não devem depender exclusivamente de cor — incluir ícone e texto para conformidade com acessibilidade |
| RNF10 | Manutenibilidade | Algoritmo de tendência deve ser modular e substituível sem impacto nas demais funcionalidades |

---

## 10. Compliance, LGPD e Requisitos Legais

### 10.1 Classificação Geral de Risco LGPD: **MÉDIO**

### 10.2 Dados Pessoais Envolvidos

| Dado | Tipo | Sensível? | Necessário? |
|---|---|---|---|
| Nome do cliente (PJ/PF) | Pessoal | Não | Sim — identificação |
| CNPJ / CPF | Pessoal | Não (CPF é dado pessoal) | Sim — identificação |
| Histórico de pagamentos | Financeiro | Não (mas é dado de comportamento econômico) | Sim — base do cálculo |
| Score de crédito calculado | Derivado / Financeiro | Não formalmente, mas impacta decisões sobre o titular | Sim — produto da funcionalidade |
| Tendência de score | Derivado / Preditivo | Não formalmente, mas é dado inferido sobre comportamento futuro | Sim — produto da evolução |

> ⚠️ **Atenção:** Dados de score e tendência são dados derivados que podem impactar decisões de crédito sobre pessoas físicas (CPF). Isso os aproxima de dados com impacto significativo sobre o titular, exigindo cuidado especial.

### 10.3 Análise por Princípio LGPD

| Princípio | Avaliação | Risco | Mitigação |
|---|---|---|---|
| Finalidade | Uso dos dados para análise de risco de crédito — finalidade legítima e compatível com a relação contratual | Baixo | Documentar finalidade na política de privacidade |
| Base Legal | Legítimo interesse (análise de risco de crédito no contexto de relação comercial) ou execução de contrato | Baixo | Validar com jurídico qual base legal se aplica ao contexto do cliente do ERP |
| Minimização | Score e histórico de pagamentos são os dados mínimos necessários — não há coleta excessiva | Baixo | Garantir que o motor preditivo não acesse dados além do necessário |
| Transparência | Clientes PF cujo score é calculado podem não saber que dados preditivos são gerados sobre eles | Médio | Verificar se a política de privacidade do cliente do ERP cobre esse uso; não é responsabilidade direta do ERP Senior X, mas deve ser orientado |
| Segurança | Dados de score armazenados em série temporal aumentam o volume de dados sensíveis armazenados | Médio | Criptografia em repouso para tabelas de histórico de score; controle de acesso por perfil |
| Direitos do Titular | Titular (cliente PF) pode solicitar acesso, correção ou exclusão dos dados de score | Médio | Prever fluxo de atendimento a direitos do titular no módulo; documentar como o cliente do ERP deve responder a essas solicitações |
| Retenção | Histórico de scores armazenado indefinidamente sem política de descarte | Alto | Definir política de retenção (sugestão: manter histórico por 5 anos, alinhado com prescrição de dívidas) |

### 10.4 Requisitos de Conformidade

| Requisito | Descrição |
|---|---|
| Trilha de auditoria | Log de acesso ao dashboard e exportações com user_id, timestamp e filtros aplicados |
| Controle de acesso | Dados de score e tendência visíveis apenas para perfis autorizados no módulo de cobrança |
| Política de retenção | Definir e implementar política de retenção do histórico de scores — Necessário validar prazo com jurídico |
| Orientação ao cliente do ERP | Documentar que o cliente do ERP (empresa usuária) é o controlador dos dados e deve garantir transparência ao titular final |
| Exportação de dados | Relatórios exportados devem conter apenas dados necessários; evitar exportação de dados sensíveis desnecessários |

> ⚠️ **Item crítico:** A política de retenção do histórico de scores não está definida. Isso representa risco alto de não conformidade com o Art. 15 da LGPD (término do tratamento). Necessário definir antes do desenvolvimento.

---

## 11. Entregáveis

| Componente | Descrição da Entrega |
|---|---|
| Backend / Motor | Serviço de cálculo de tendência preditiva com armazenamento de histórico de scores |
| Backend / API | Endpoints para consulta de tendência por cliente, listagem de carteira com filtros, configurações do motor |
| Interface (UI) | Indicador visual de tendência na ficha do cliente (evolução da tela existente) |
| Interface (UI) | Gráfico de evolução do score na ficha do cliente |
| Interface (UI) | Dashboard de Carteira Inteligente (nova tela no módulo de Gestão de Cobrança) |
| Interface (UI) | Tela de configurações do motor preditivo (evolução das configurações existentes) |
| Interface (UI) | Sistema de alertas/notificações na interface do ERP |
| Relatórios | Exportação de lista de clientes em risco (CSV e PDF) |
| Documentação | Help online atualizado com as novas funcionalidades |
| Documentação | Release notes para comunicação ao cliente |

---

## 12. Cenários de Teste (QA)

### 12.1 Cenários Positivos (Happy Path)

| # | Cenário | Condições | Resultado Esperado |
|---|---|---|---|
| C1 | Cálculo de tendência — Declínio | Cliente com 6 ciclos de score: 800, 750, 700, 650, 600, 550 | Tendência classificada como "Declínio", variação de -250 pontos, indicador vermelho |
| C2 | Cálculo de tendência — Estável | Cliente com 6 ciclos de score: 700, 710, 695, 705, 700, 698 | Tendência classificada como "Estável", indicador verde |
| C3 | Cálculo de tendência — Recuperação | Cliente com 6 ciclos: 400, 350, 300, 350, 400, 450 | Tendência classificada como "Recuperação", indicador verde |
| C4 | Dashboard com filtro de Declínio | Carteira com 100 clientes, 20 em declínio | Lista exibe apenas os 20 clientes em declínio, ordenados por maior queda |
| C5 | Alerta automático gerado | Cliente atinge limiar de declínio no ciclo atual | Alerta exibido na interface para usuários com permissão |
| C6 | Exportação CSV | Filtro aplicado: tendência = Declínio, 20 clientes | Arquivo CSV gerado com 20 linhas e todos os campos obrigatórios |
| C7 | Gráfico de evolução | Cliente com 8 ciclos de histórico | Gráfico exibe 8 pontos, linha de tendência e faixas de classificação |

### 12.2 Cenários Negativos (Edge Cases)

| # | Cenário | Condições | Resultado Esperado |
|---|---|---|---|
| C8 | Histórico insuficiente | Cliente com apenas 1 ciclo de score | Exibir "Dados insuficientes para calcular tendência", sem indicador colorido |
| C9 | Carteira sem clientes em declínio | Filtro aplicado: tendência = Declínio, nenhum cliente | Estado vazio com mensagem "Nenhum cliente em declínio no período selecionado" |
| C10 | Configuração inválida | Administrador tenta configurar N ciclos = 1 (abaixo do mínimo) | Erro de validação: "Número mínimo de ciclos é 3" |
| C11 | Acesso não autorizado | Usuário sem permissão de cobrança tenta acessar dashboard | Bloqueio de acesso com mensagem de permissão insuficiente |
| C12 | Falha no cálculo de tendência | Erro no processamento do ciclo | Score principal não é afetado; log de erro registrado; tendência mantém último valor válido |
| C13 | Exportação com lista vazia | Nenhum cliente no filtro aplicado | Botão de exportação desabilitado com tooltip "Nenhum cliente para exportar" |

---

## 13. Dependências e Integrações

### 13.1 Dependências Internas

| Dependência | Tipo | Descrição |
|---|---|---|
| Motor de cálculo de score existente | Serviço | O score calculado a cada 15 dias é a entrada principal do motor de tendência |
| Módulo de Gestão de Cobrança | Interface | As novas telas são evoluções dentro do módulo existente |
| Cadastro de Clientes | Dados | Necessário para identificação e segmentação dos clientes na carteira |
| Sistema de permissões do ERP Senior X | Segurança | Controle de acesso às novas funcionalidades baseado nos perfis existentes |
| Módulo de configurações do ERP | Interface | Tela de configurações do motor preditivo integrada às configurações existentes |

### 13.2 Integrações Externas

| Sistema / API | Tipo | Descrição |
|---|---|---|
| Bureaus de crédito (Serasa, SPC) | Não aplicável nesta versão | O motor preditivo usa apenas dados internos — integração externa não está no escopo desta evolução |

> ℹ️ A ausência de integração com bureaus externos é um diferencial desta solução — análise preditiva baseada exclusivamente no comportamento interno da carteira.

---

## 14. Riscos e Mitigações

| # | Risco | Impacto | Probabilidade | Mitigação |
|---|---|---|---|---|
| R1 | Performance degradada em carteiras muito grandes no recálculo de tendência | Alto | Média | Processamento assíncrono e em lote; indexação adequada nas tabelas de histórico; monitorar tempo de processamento nos primeiros ciclos |
| R2 | Algoritmo de tendência gera falsos positivos (alertas desnecessários) | Médio | Alta | Configuração de limiares ajustáveis; período de calibração com dados reais antes do go-live; feedback loop para ajuste dos parâmetros |
| R3 | Resistência dos usuários à mudança de processo (confiança no score preditivo) | Médio | Média | Treinamento e material de apoio; exibir dados históricos que embasam a tendência para aumentar confiança |
| R4 | Escopo crescente — pressão para incluir integração com bureaus externos | Médio | Alta | Fatiamento claro: v1 com dados internos; integração externa como roadmap futuro documentado |
| R5 | Política de retenção de dados não definida antes do desenvolvimento | Alto | Alta | Bloquear início do desenvolvimento até definição da política com jurídico — item crítico de LGPD |
| R6 | Histórico de scores insuficiente nos primeiros meses após implantação | Médio | Alta | Comunicar limitação ao usuário; tendência disponível apenas após N ciclos mínimos; planejar migração de dados históricos se disponíveis |
| R7 | Divergência entre tendência calculada e comportamento real do cliente | Alto | Baixa | Documentar claramente que a tendência é indicativa, não determinística; incluir disclaimer na interface |

---

## 15. Métricas de Sucesso

| Métrica | Baseline (Atual) | Meta | Prazo de Medição |
|---|---|---|---|
| % de clientes que transitam de "Bom" para "Baixo" sem ação prévia registrada | Necessário validar | Redução de X% | 3 meses após release |
| Tempo médio entre identificação de risco e primeiro contato de cobrança | Necessário validar | Redução de Y dias | 3 meses após release |
| Adoção do Dashboard de Carteira Inteligente | 0% (feature nova) | 50% dos usuários do módulo de cobrança acessando semanalmente | 3 meses após release |
| Volume de alertas gerados vs. acionados | 0 (feature nova) | Taxa de acionamento > 60% dos alertas gerados | 3 meses após release |
| Satisfação dos usuários com a funcionalidade | Necessário validar (NPS/CSAT) | NPS > 7 para a feature | 3 meses após release |

> ⚠️ Todos os baselines marcados como "Necessário validar" devem ser levantados com o time de CS e dados internos antes do go-live para permitir medição real de impacto.

---

## 16. Plano de Execução (Roadmap)

### Fase 1 — Discovery e Definição
- PRD finalizado e aprovado
- Levantamento de dados históricos disponíveis para calibração do algoritmo
- Protótipo de alta fidelidade das novas telas
- Definição da política de retenção de dados (LGPD)
- Duração estimada: Necessário validar

### Fase 2 — Desenvolvimento
- Backend: tabela de histórico de scores e motor de tendência
- Backend: API de consulta de tendência e carteira
- Frontend: indicador visual na ficha do cliente e gráfico de evolução
- Frontend: Dashboard de Carteira Inteligente
- Frontend: sistema de alertas e configurações
- Duração estimada: Necessário validar

### Fase 3 — QA e Homologação
- Execução dos cenários de teste (positivos e negativos)
- Testes de performance com volume real de carteira
- Calibração dos limiares de tendência com dados reais
- Duração estimada: Necessário validar

### Fase 4 — Release e Acompanhamento
- Deploy em produção
- Monitoramento das métricas de sucesso
- Coleta de feedback dos primeiros usuários
- Ajuste de parâmetros do algoritmo se necessário
- Duração estimada: Necessário validar

---

## 17. Glossário e Referências

| Termo / Sigla | Definição |
|---|---|
| Score de Crédito | Pontuação calculada automaticamente para cada cliente ativo, avaliando risco de crédito com base em histórico de pagamentos e relação financeira |
| Tendência de Score | Classificação da trajetória do score ao longo do tempo: Estável, Atenção, Declínio ou Recuperação |
| Ciclo de Recálculo | Período de 15 dias entre cada recálculo automático do score |
| Série Temporal | Sequência de valores de score registrados ao longo dos ciclos, usada como base para cálculo de tendência |
| Motor Preditivo | Componente de software responsável por calcular tendências e gerar sinalizações de risco |
| Carteira | Conjunto de clientes ativos com score calculado |
| Limiar de Alerta | Valor configurável que define a partir de qual variação de score um alerta é gerado |
| LGPD | Lei Geral de Proteção de Dados — Lei nº 13.709/2018 |
| PJ | Pessoa Jurídica |
| PF | Pessoa Física |
| ERP | Enterprise Resource Planning — sistema integrado de gestão empresarial |
| HCM | Human Capital Management |
| MVP | Minimum Viable Product — versão mínima viável do produto |

Referências:
- Documentação interna do Score de Crédito — ERP Senior X (fornecida no briefing)
- Lei nº 13.709/2018 — LGPD
- TOTVS: https://www.totvs.com/
- Sankhya: https://www.sankhya.com.br/
- Benner: https://benner.com.br/
- LG Sistemas: https://www.lg.com.br/

---

## 18. Histórico de Versões

| Versão | Data | Autor | Alterações |
|---|---|---|---|
| v0.1 | Necessário validar | Necessário validar | Criação do documento |
