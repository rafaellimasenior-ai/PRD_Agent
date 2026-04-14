# PRD — API de Chamados em Aberto | Hypnobox PVD

---

## Metadados do Documento

| Campo | Valor |
|---|---|
| Produto / Módulo | Hypnobox PVD — Pós-venda |
| Funcionalidade | API de Chamados em Aberto |
| Tipo | Nova feature |
| Direcionador Estratégico | Cobertura (expansão de integrações e ecossistema) |
| Status | Em Definição |
| Product Owner | Não informado — necessário validar |
| Stakeholders | Time de Produto PVD, Engenharia (.NET), CS, Clientes integradores |
| Data de criação | 14/04/2026 |
| Última atualização | 14/04/2026 |
| Versão | v0.1 |

---

## 1. Visão do Produto

**O que é?**
Uma API REST que expõe os chamados em aberto do módulo PVD da Hypnobox, permitindo que sistemas externos (ERPs, dashboards, ferramentas de BI, plataformas de atendimento) consumam em tempo real os tickets abertos pelos compradores.

**Para quem?**
Equipes de TI e integradores das construtoras/incorporadoras clientes da Hypnobox, e internamente para o backoffice de atendimento pós-venda.

**Qual o valor entregue?**
Elimina a necessidade de acesso manual ao backoffice para consultar chamados, viabiliza integrações com sistemas de gestão externos e permite automações de atendimento (ex: notificações, SLA tracking, dashboards gerenciais).

**Resumo executivo:**
A API de Chamados em Aberto é uma nova feature do PVD que permite que sistemas externos consultem, em tempo real, todos os chamados abertos pelos compradores de imóveis. Esta funcionalidade é estratégica porque viabiliza integrações com ERPs (Mega, UAU) e ferramentas de BI, reduz o trabalho manual das equipes de atendimento e posiciona a Hypnobox como uma plataforma aberta e integrável — diferencial competitivo crescente no mercado imobiliário.

---

## 2. Problema e Evidências

### 2.1 Estado Atual (As-Is)

Hoje, os chamados abertos pelos compradores no Portal do Cliente ficam disponíveis apenas dentro do backoffice do PVD. Não existe endpoint público ou integração nativa que permita a consulta desses dados por sistemas externos.

Workarounds adotados pelos clientes:
- Exportação manual de relatórios em CSV/Excel
- Acesso direto ao backoffice por múltiplos usuários para monitorar chamados
- Uso de ferramentas de scraping ou automações frágeis sobre a interface web

### 2.2 Evidências de Dor

| Fonte da Evidência | Descrição |
|---|---|
| Feedback de clientes | Solicitações recorrentes de integração do PVD com sistemas de CRM e ERP externos |
| Time de CS | Relatos de construtoras que gerenciam chamados em planilhas paralelas por falta de API |
| Time de Vendas | Perda de RFPs de clientes enterprise que exigem API aberta como requisito de contratação |
| Suporte / Tickets | Volume de chamados internos pedindo exportação de dados de atendimento — necessário validar volume exato |

> ⚠️ **Necessário validar:** Levantar volume real de solicitações de integração junto ao CS e ao time de suporte.

---

## 3. Objetivos de Negócio

| # | Objetivo |
|---|---|
| O1 | Viabilizar integrações de clientes enterprise com sistemas externos (ERP, BI, CRM) |
| O2 | Reduzir trabalho manual das equipes de atendimento na consulta de chamados |
| O3 | Aumentar a percepção de plataforma aberta e integrável da Hypnobox |
| O4 | Reduzir churn de clientes que exigem API como requisito técnico |

> ⚠️ **Necessário validar:** Definir métricas e metas mensuráveis com o time de produto (ex: % de clientes usando a API em 6 meses, redução de tickets de exportação manual).

---

## 4. Pricing

**Custos de implementação:**
- Desenvolvimento de endpoint .NET (backend PVD)
- Infraestrutura de autenticação (API Key ou OAuth2)
- Documentação técnica (Swagger/OpenAPI)

**Modelo de precificação sugerido:**
- Incluído no plano PVD existente (sem custo adicional) — recomendado para adoção rápida
- Ou como add-on de "Integrações API" para planos enterprise — a validar com time comercial

> ⚠️ **Necessário validar:** Decisão de pricing com time comercial e produto.

---

## 5. Personas

| Persona | Perfil | Necessidade Principal | Valor Recebido |
|---|---|---|---|
| Desenvolvedor / Integrador da Construtora | Profissional de TI responsável por integrar sistemas da construtora | Consumir dados de chamados em tempo real via API padronizada | Elimina scraping e exportações manuais; integração confiável e documentada |
| Gestor de Atendimento Pós-venda | Responsável pela equipe de SAC da construtora | Visibilidade centralizada dos chamados em aberto em seu dashboard próprio | Monitora SLA e volume de chamados sem precisar acessar o backoffice Hypnobox |
| Analista de BI / Dados | Profissional que constrói relatórios gerenciais | Fonte de dados estruturada e atualizada sobre atendimento | Alimenta dashboards e relatórios sem depender de exportações manuais |
| Equipe de Produto Hypnobox | Time interno que consome dados do PVD | Expor dados de chamados para integrações futuras (ex: WhatsApp, notificações) | Base técnica para evoluções do produto |

---

## 6. Estrutura do Produto (Módulos / Blocos)

**Módulo 1 — Endpoint de Consulta de Chamados em Aberto**
Funcionalidades:
- `GET /chamados/abertos` — retorna lista paginada de chamados em aberto
- Filtros opcionais: por empreendimento, por responsável, por data de abertura, por cliente
- Ordenação por data de abertura (mais recente / mais antigo)

**Módulo 2 — Autenticação e Autorização**
Funcionalidades:
- Autenticação via API Key por tenant (construtora)
- Controle de escopo: cada construtora acessa apenas seus próprios chamados
- Rate limiting para evitar abuso

**Módulo 3 — Documentação e Contrato de API**
Funcionalidades:
- Documentação Swagger/OpenAPI disponível
- Exemplos de request/response
- Changelog de versões da API

---

## 7. Requisitos Funcionais

### RF01 — Listagem de Chamados em Aberto

| Campo | Descrição |
|---|---|
| Descrição | O sistema deve expor um endpoint REST que retorna todos os chamados com status "em aberto" do tenant autenticado |
| Regras de Negócio | Retornar apenas chamados com status = "aberto" (não resolvidos, não cancelados). Respeitar o escopo do tenant autenticado (isolamento de dados por construtora). Paginação obrigatória (máximo 100 registros por página). |
| Dados de Entrada | API Key no header (`Authorization: Bearer {api_key}`). Parâmetros opcionais: `page`, `per_page`, `empreendimento_id`, `responsavel_id`, `data_abertura_inicio`, `data_abertura_fim`, `cliente_id` |
| Dados de Saída | Array de objetos de chamado contendo: `id`, `assunto`, `conteudo` (texto do chamado), `texto_resposta` (última resposta), `responsavel` (nome e id), `cliente` (nome, id, CPF mascarado), `empreendimento` (nome e id), `data_abertura` (ISO 8601), `status`, `prioridade` (se disponível). Metadados de paginação: `total`, `page`, `per_page`, `total_pages`. |
| Comportamento de Erro | 401 Unauthorized — API Key inválida ou ausente. 403 Forbidden — tentativa de acesso a dados de outro tenant. 422 Unprocessable Entity — parâmetros de filtro inválidos. 500 Internal Server Error — erro interno com mensagem genérica (sem expor stack trace). |
| Dependências | Base de dados de chamados do PVD (backoffice). Sistema de autenticação por API Key. |
| Prioridade | Must |

---

### RF02 — Autenticação por API Key

| Campo | Descrição |
|---|---|
| Descrição | O sistema deve autenticar as requisições via API Key única por tenant (construtora) |
| Regras de Negócio | Cada construtora possui uma API Key única. A API Key deve ser gerada e gerenciada pelo backoffice do PVD (pelo administrador da construtora). API Keys podem ser revogadas e regeneradas. |
| Dados de Entrada | Header HTTP: `Authorization: Bearer {api_key}` |
| Dados de Saída | Acesso concedido (200) ou negado (401/403) |
| Comportamento de Erro | 401 para API Key ausente ou inválida. 403 para API Key válida mas sem permissão no recurso solicitado. |
| Dependências | RF01 |
| Prioridade | Must |

---

### RF03 — Filtros de Consulta

| Campo | Descrição |
|---|---|
| Descrição | O endpoint deve aceitar parâmetros opcionais de filtro para refinar os resultados retornados |
| Regras de Negócio | Todos os filtros são opcionais. Filtros combinados aplicam lógica AND. Datas devem seguir formato ISO 8601 (YYYY-MM-DD). IDs devem ser inteiros positivos. |
| Dados de Entrada | `empreendimento_id` (integer), `responsavel_id` (integer), `cliente_id` (integer), `data_abertura_inicio` (date), `data_abertura_fim` (date), `page` (integer, default: 1), `per_page` (integer, default: 20, max: 100) |
| Dados de Saída | Lista filtrada de chamados conforme parâmetros informados |
| Comportamento de Erro | 422 com mensagem descritiva para parâmetros com formato inválido |
| Dependências | RF01, RF02 |
| Prioridade | Should |

---

### RF04 — Gerenciamento de API Keys no Backoffice

| Campo | Descrição |
|---|---|
| Descrição | O administrador da construtora deve conseguir gerar, visualizar e revogar API Keys diretamente no backoffice do PVD |
| Regras de Negócio | Apenas usuários com perfil "Administrador" podem gerenciar API Keys. A API Key é exibida apenas uma vez no momento da criação (não recuperável depois). Revogação é imediata. |
| Dados de Entrada | Ação do usuário no backoffice (gerar / revogar) |
| Dados de Saída | API Key gerada (exibida uma única vez) ou confirmação de revogação |
| Comportamento de Erro | Exibir alerta de confirmação antes de revogar. Mensagem de erro se falha na geração. |
| Dependências | Sistema de permissões do backoffice PVD |
| Prioridade | Must |

---

## 8. Requisitos Não Funcionais

| ID | Categoria | Requisito |
|---|---|---|
| RNF01 | Performance | Tempo de resposta < 1s para listagens com até 100 registros |
| RNF02 | Segurança | API Key transmitida apenas via HTTPS. Nunca exposta em logs. |
| RNF03 | Isolamento de dados | Cada tenant acessa exclusivamente seus próprios dados (row-level security) |
| RNF04 | Auditoria | Log de todas as requisições com: tenant_id, endpoint, timestamp, status HTTP |
| RNF05 | Rate Limiting | Máximo de 100 requisições por minuto por API Key |
| RNF06 | Disponibilidade | SLA de 99,5% de uptime — necessário validar com infraestrutura |
| RNF07 | Versionamento | API versionada via path (`/v1/chamados/abertos`) para garantir backward compatibility |
| RNF08 | Documentação | Swagger/OpenAPI disponível e atualizado a cada release |

---

## 9. Entregáveis

| Componente | Descrição da Entrega |
|---|---|
| Backend / API | Endpoint `GET /v1/chamados/abertos` em .NET com autenticação, filtros e paginação |
| Gerenciamento de API Keys | Tela no backoffice PVD para geração e revogação de API Keys |
| Documentação técnica | Swagger/OpenAPI com exemplos de request/response e guia de autenticação |
| Logs de auditoria | Registro de todas as chamadas à API com rastreabilidade por tenant |

---

## 10. Dependências e Integrações

### 10.1 Dependências Internas

| Dependência | Tipo | Descrição |
|---|---|---|
| Base de dados de chamados PVD | Dados | Fonte dos chamados em aberto |
| Sistema de autenticação do backoffice | Serviço | Gerenciamento de usuários e permissões para API Keys |
| Sistema de permissões por perfil | Serviço | Controle de quem pode gerar/revogar API Keys |

### 10.2 Integrações Externas

| Sistema / API | Tipo | Descrição |
|---|---|---|
| ERPs dos clientes (Mega, UAU, outros) | Consumidor | Sistemas externos que consumirão a API |
| Ferramentas de BI (Power BI, Tableau, etc.) | Consumidor | Dashboards externos que consumirão os dados |
| Plataformas de atendimento (Zendesk, Freshdesk) | Consumidor | Possíveis integradores da API |

---

## 11. Riscos e Mitigações

| # | Risco | Impacto | Probabilidade | Mitigação |
|---|---|---|---|---|
| R1 | Exposição indevida de dados de outro tenant | Crítico | Baixa | Implementar row-level security rigoroso + testes de isolamento obrigatórios |
| R2 | Performance degradada em construtoras com alto volume de chamados | Alto | Média | Paginação obrigatória + índices no banco + cache de curta duração (TTL 30s) |
| R3 | API Key comprometida por cliente | Alto | Média | Mecanismo de revogação imediata + alertas de uso anômalo |
| R4 | Escopo crescente (pressão para adicionar chamados fechados, histórico, etc.) | Médio | Alta | Definir claramente o escopo v1 e criar roadmap de versões futuras |
| R5 | Falta de adoção por documentação insuficiente | Médio | Média | Swagger completo + guia de integração + suporte ao onboarding dos primeiros clientes |

---

## 12. Compliance, LGPD e Requisitos Legais

### 12.1 Dados Sensíveis Envolvidos

A API expõe dados pessoais dos compradores de imóveis:
- Nome do cliente
- CPF (deve ser mascarado — ex: `***.456.789-**`)
- Conteúdo dos chamados (pode conter dados sensíveis relatados pelo comprador)

### 12.2 Requisitos de Conformidade

| Requisito | Descrição |
|---|---|
| Mascaramento de CPF | CPF nunca deve ser retornado completo na API — aplicar máscara obrigatória |
| Trilha de auditoria (LGPD) | Log de todas as requisições com tenant_id, endpoint, timestamp e IP de origem |
| Controle de acesso | Apenas sistemas autorizados (API Key válida) acessam dados pessoais |
| Finalidade declarada | Uso restrito à gestão de atendimento — não permitir uso para fins de marketing ou perfilamento |
| Retenção de logs | Logs de acesso à API devem ser retidos por mínimo 6 meses — validar política interna |
| Direitos do titular | Dados retornados pela API devem ser consistentes com o que o comprador pode ver no portal |

> ⚠️ **Classificação de risco LGPD: MÉDIO** — A API expõe dados pessoais de compradores. O risco é controlável com mascaramento de CPF, autenticação robusta e logs de auditoria. Recomenda-se revisão jurídica antes do lançamento.

---

## 13. Cenários de Teste (QA)

### 13.1 Cenários Positivos (Happy Path)

| # | Cenário | Condições | Resultado Esperado |
|---|---|---|---|
| C1 | Listagem padrão sem filtros | API Key válida, tenant com 5 chamados abertos | Retorna 5 chamados com todos os campos obrigatórios, paginação correta |
| C2 | Listagem com filtro por empreendimento | API Key válida, filtro `empreendimento_id=10` | Retorna apenas chamados do empreendimento 10 |
| C3 | Listagem com filtro por data | API Key válida, `data_abertura_inicio=2026-01-01&data_abertura_fim=2026-03-31` | Retorna apenas chamados abertos no período informado |
| C4 | Paginação | API Key válida, tenant com 150 chamados, `per_page=50&page=2` | Retorna registros 51-100, metadados de paginação corretos |
| C5 | Geração de API Key no backoffice | Usuário administrador gera nova API Key | API Key exibida uma única vez, funcional para autenticação |

### 13.2 Cenários Negativos (Edge Cases)

| # | Cenário | Condições | Resultado Esperado |
|---|---|---|---|
| C6 | API Key inválida | Header com API Key inexistente | 401 Unauthorized |
| C7 | Tentativa de acesso a outro tenant | API Key do tenant A com `empreendimento_id` do tenant B | 403 Forbidden ou resultado vazio (sem vazar dados) |
| C8 | Parâmetro de data inválido | `data_abertura_inicio=31-13-2026` | 422 com mensagem de erro descritiva |
| C9 | `per_page` acima do limite | `per_page=500` | 422 ou retorno com máximo de 100 registros |
| C10 | Tenant sem chamados abertos | API Key válida, nenhum chamado em aberto | 200 com array vazio e metadados de paginação zerados |
| C11 | Rate limit excedido | Mais de 100 requisições/minuto com a mesma API Key | 429 Too Many Requests |
| C12 | CPF exposto sem máscara | Qualquer requisição válida | CPF sempre retornado mascarado (`***.456.789-**`) |

---

## 14. Métricas de Sucesso

| Métrica | Baseline (Atual) | Meta | Prazo de Medição |
|---|---|---|---|
| Clientes usando a API | 0 | Necessário validar com time comercial | 3 meses após release |
| Redução de exportações manuais de chamados | Necessário validar baseline | -50% de solicitações de exportação manual | 3 meses após release |
| Tickets de suporte sobre acesso a chamados | Necessário validar baseline | -30% | 6 meses após release |
| Tempo médio de integração por cliente | Não medido | < 1 dia de trabalho técnico | Primeiros 5 clientes integradores |

> ⚠️ **Necessário validar:** Todos os baselines precisam ser levantados com CS e suporte antes do release.

---

## 15. Glossário e Referências

| Termo / Sigla | Definição |
|---|---|
| Chamado | Ticket de atendimento aberto pelo comprador no Portal do Cliente PVD |
| Tenant | Construtora/incorporadora cliente da Hypnobox — unidade de isolamento de dados |
| API Key | Chave de autenticação única por tenant para acesso à API |
| PVD | Módulo de Pós-venda da Hypnobox |
| Backoffice | Interface interna da Hypnobox usada pela equipe da construtora |
| Portal do Cliente | Interface do comprador do imóvel no PVD |
| Row-level security | Controle de acesso a dados no nível de linha do banco de dados |
| Rate limiting | Controle de quantidade máxima de requisições por período |
| ISO 8601 | Padrão internacional de formatação de datas (ex: 2026-04-14) |
| LGPD | Lei Geral de Proteção de Dados — Lei nº 13.709/2018 |

**Referências:**
- Base de conhecimento Hypnobox PVD — `.kiro/skills/hypnobox-product-knowledge/references/hbox-pvd-pos-venda.md`
- LGPD — Lei nº 13.709/2018: https://www.planalto.gov.br/ccivil_03/_ato2015-2018/2018/lei/l13709.htm

---

## Histórico de Versões

| Versão | Data | Autor | Alterações |
|---|---|---|---|
| v0.1 | 14/04/2026 | Kiro (IA) | Criação do documento |

---

> **Nota:** Este PRD foi gerado com base no briefing fornecido e na base de conhecimento Hypnobox PVD. Campos marcados com ⚠️ **"Necessário validar"** requerem confirmação com stakeholders antes de avançar para desenvolvimento. Não foram inventados dados de mercado, métricas ou baselines — esses itens estão sinalizados para preenchimento pelo time.
