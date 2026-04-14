# PRD — API de Vistorias Agendadas (PVD)

## Metadados do Documento

| Campo | Valor |
|---|---|
| Produto / Módulo | Hypnobox PVD — Pós-venda |
| Funcionalidade | API de Vistorias Agendadas |
| Tipo | Nova feature |
| Status | Em Definição |
| Product Owner | [Nome — necessário validar] |
| Stakeholders | Time PVD, Time de Integrações, Clientes com integração via API |
| Data de criação | 14/04/2026 |
| Última atualização | 14/04/2026 |
| Versão | v0.1 |

---

## 1. Visão do Produto

**O que é?**
Uma API REST no módulo PVD da Hypnobox que expõe as vistorias agendadas de empreendimentos, permitindo consulta por técnico responsável, cliente (comprador) ou unidade.

**Para quem?**
Times de integração de construtoras/incorporadoras que precisam consumir dados de vistoria em sistemas externos (ERPs, dashboards, apps próprios, ferramentas de field service).

**Qual o valor entregue?**
Elimina a necessidade de acesso manual ao backoffice PVD para consultar agenda de vistorias, permitindo que sistemas externos se integrem de forma programática e automatizem fluxos operacionais.

**Resumo executivo:**
A API de Vistorias Agendadas é uma nova feature do PVD que permite que construtoras e incorporadoras integrem a agenda de vistorias da Hypnobox com seus sistemas internos. Esta funcionalidade é estratégica porque o processo de vistoria envolve múltiplos atores (técnicos, clientes, equipe interna) e hoje não existe forma programática de consultar esses dados fora do backoffice — o que gera retrabalho, falta de visibilidade e dificuldade de escalar operações de entrega de imóveis.

---

## 2. Problema e Evidências

### 2.1 Estado Atual (As-Is)

Hoje, as vistorias agendadas no PVD só podem ser consultadas manualmente pelo backoffice da Hypnobox. Não existe endpoint público ou privado que exponha esses dados de forma estruturada.

Workarounds adotados pelos clientes:
- Exportação manual de relatórios de vistoria em PDF/Excel
- Replicação manual de agendamentos em planilhas ou sistemas de field service
- Ligações/WhatsApp para confirmar agenda com técnicos

### 2.2 Evidências de Dor

| Fonte da Evidência | Descrição |
|---|---|
| Feedback de clientes | [Necessário validar — construtoras com operações de entrega em escala relatam dificuldade de sincronizar agenda de técnicos] |
| Time de Vendas / CS | [Necessário validar — verificar se há RFPs ou churn relacionados à ausência de API de vistoria] |
| Suporte / Tickets | [Necessário validar — volume de chamados pedindo exportação ou integração de vistorias] |
| Dados internos | [Necessário validar — % de clientes que usam o módulo de vistoria ativamente] |

> ⚠️ **Nota:** As evidências acima precisam ser validadas com dados reais antes da aprovação do PRD.

---

## 3. Objetivos de Negócio

| # | Objetivo |
|---|---|
| O1 | Habilitar integração programática de vistorias com sistemas externos (ERPs, field service, dashboards) |
| O2 | Reduzir retrabalho operacional de equipes de entrega de imóveis |
| O3 | Aumentar adoção do módulo de vistoria do PVD por clientes com operações em escala |
| O4 | Posicionar a Hypnobox como plataforma aberta e integrável no ecossistema imobiliário |

> ⚠️ Métricas-alvo (baseline e meta) precisam ser definidas com o time de produto e CS.

---

## 4. Personas

| Persona | Perfil | Necessidade Principal | Valor Recebido |
|---|---|---|---|
| Desenvolvedor / Integrador da construtora | Profissional técnico responsável por integrações entre sistemas da incorporadora | Consumir dados de vistoria de forma estruturada e automatizada | API documentada, estável e com filtros úteis |
| Gestor de Pós-venda | Responsável pela operação de entrega e vistoria de imóveis | Visibilidade da agenda de técnicos e status de vistorias em tempo real | Dados disponíveis em dashboards e ferramentas próprias |
| Técnico de Vistoria | Profissional de campo que realiza as inspeções | Receber agenda atualizada sem depender do backoffice | Integração com apps de field service via API |
| Equipe de Atendimento PVD (backoffice) | Operadores que gerenciam vistorias no sistema | Reduzir perguntas e retrabalho manual | Menos demandas de exportação e consulta manual |

---

## 5. Estrutura do Produto (Módulos / Blocos)

**Módulo 1 — Endpoint de Listagem de Vistorias Agendadas**
Propósito: Retornar todas as vistorias agendadas com suporte a paginação e filtros.

Funcionalidades:
- `GET /vistorias` — lista todas as vistorias agendadas
- Suporte a paginação (`page`, `pageSize`)
- Suporte a filtros via query params
- Retorno em JSON estruturado

**Módulo 2 — Filtros de Busca**
Propósito: Permitir consultas segmentadas por diferentes dimensões operacionais.

Funcionalidades:
- Filtro por técnico responsável (`tecnicoId` ou `tecnicoNome`)
- Filtro por cliente/comprador (`clienteId`, `clienteNome` ou `cpf`)
- Filtro por unidade (`unidadeId`, `bloco`, `numero`)
- Filtro por período (`dataInicio`, `dataFim`)
- Filtro por status da vistoria (`agendada`, `realizada`, `cancelada`, `reagendada`)

**Módulo 3 — Autenticação e Segurança**
Propósito: Garantir que apenas sistemas autorizados acessem os dados.

Funcionalidades:
- Autenticação via API Key ou OAuth 2.0 (a definir conforme padrão da plataforma)
- Controle de acesso por empreendimento/empresa
- Rate limiting para evitar abuso

---

## 6. Fluxo do Usuário

### 6.1 Fluxo Principal (Happy Path)

1. Sistema externo realiza autenticação com credenciais válidas
2. Sistema envia `GET /vistorias` com os filtros desejados (ex: `?tecnicoId=123&dataInicio=2026-04-01&dataFim=2026-04-30`)
3. API valida autenticação e parâmetros
4. API consulta base de dados do PVD
5. API retorna lista paginada de vistorias no formato JSON
6. Sistema externo processa e exibe os dados conforme sua necessidade

### 6.2 Fluxos Alternativos

- **Sem filtros:** Retorna todas as vistorias agendadas da empresa autenticada (com paginação obrigatória)
- **Filtro combinado:** Técnico + período — retorna agenda do técnico em um intervalo de datas
- **Busca por cliente:** Retorna todas as vistorias associadas a um comprador específico (útil para atendimento)
- **Busca por unidade:** Retorna histórico de vistorias de uma unidade específica

---

## 7. Requisitos Funcionais

### RF01 — Listagem de Vistorias Agendadas

| Campo | Descrição |
|---|---|
| Descrição | A API deve retornar todas as vistorias agendadas da empresa autenticada |
| Regras de Negócio | Retornar apenas vistorias do empreendimento/empresa vinculada à credencial de acesso; respeitar isolamento multi-tenant |
| Dados de Entrada | Credencial de autenticação (header); parâmetros opcionais de paginação (`page`, `pageSize`, default: 20) |
| Dados de Saída | Array de objetos de vistoria com: id, dataAgendada, horaAgendada, status, unidade (bloco, número, empreendimento), técnico (id, nome), cliente (id, nome, CPF mascarado), observações |
| Comportamento de Erro | 401 — credencial inválida; 403 — sem permissão para o recurso; 500 — erro interno com mensagem genérica |
| Dependências | Módulo de vistoria do PVD (backoffice); cadastro de técnicos; cadastro de unidades; cadastro de clientes |
| Prioridade | Must |

---

### RF02 — Filtro por Técnico Responsável

| Campo | Descrição |
|---|---|
| Descrição | A API deve permitir filtrar vistorias pelo técnico responsável |
| Regras de Negócio | Aceitar `tecnicoId` (inteiro) ou `tecnicoNome` (string, busca parcial case-insensitive); se ambos informados, `tecnicoId` tem precedência |
| Dados de Entrada | Query params: `tecnicoId` (opcional) ou `tecnicoNome` (opcional) |
| Dados de Saída | Lista filtrada de vistorias do técnico informado |
| Comportamento de Erro | 404 — técnico não encontrado; 400 — parâmetro inválido |
| Dependências | RF01; cadastro de técnicos no PVD |
| Prioridade | Must |

---

### RF03 — Filtro por Cliente (Comprador)

| Campo | Descrição |
|---|---|
| Descrição | A API deve permitir filtrar vistorias pelo cliente/comprador do imóvel |
| Regras de Negócio | Aceitar `clienteId` (inteiro) ou `cpf` (string, apenas dígitos); busca por nome (`clienteNome`) deve ser parcial e case-insensitive; CPF deve ser validado no formato antes da consulta |
| Dados de Entrada | Query params: `clienteId` (opcional), `cpf` (opcional) ou `clienteNome` (opcional) |
| Dados de Saída | Lista de vistorias associadas ao cliente informado |
| Comportamento de Erro | 404 — cliente não encontrado; 400 — CPF em formato inválido |
| Dependências | RF01; cadastro de compradores/contratos do PVD |
| Prioridade | Must |

---

### RF04 — Filtro por Unidade

| Campo | Descrição |
|---|---|
| Descrição | A API deve permitir filtrar vistorias por unidade do empreendimento |
| Regras de Negócio | Aceitar `unidadeId` (inteiro) ou combinação de `empreendimentoId` + `bloco` + `numero`; unidade deve pertencer à empresa autenticada |
| Dados de Entrada | Query params: `unidadeId` (opcional) ou `empreendimentoId` + `bloco` + `numero` (opcionais, mas devem ser usados em conjunto) |
| Dados de Saída | Lista de vistorias da unidade informada (incluindo histórico se houver múltiplas vistorias) |
| Comportamento de Erro | 404 — unidade não encontrada; 400 — combinação de parâmetros inválida; 403 — unidade não pertence à empresa autenticada |
| Dependências | RF01; cadastro de empreendimentos e unidades do PVD |
| Prioridade | Must |

---

### RF05 — Filtro por Período

| Campo | Descrição |
|---|---|
| Descrição | A API deve permitir filtrar vistorias por intervalo de datas |
| Regras de Negócio | Aceitar `dataInicio` e `dataFim` no formato ISO 8601 (YYYY-MM-DD); `dataFim` não pode ser anterior a `dataInicio`; intervalo máximo de consulta: [necessário definir — sugestão: 90 dias] |
| Dados de Entrada | Query params: `dataInicio` (opcional), `dataFim` (opcional) |
| Dados de Saída | Lista de vistorias dentro do período informado |
| Comportamento de Erro | 400 — formato de data inválido; 400 — `dataFim` anterior a `dataInicio`; 400 — intervalo excede o limite máximo |
| Dependências | RF01 |
| Prioridade | Should |

---

### RF06 — Filtro por Status da Vistoria

| Campo | Descrição |
|---|---|
| Descrição | A API deve permitir filtrar vistorias pelo status atual |
| Regras de Negócio | Valores aceitos: `agendada`, `realizada`, `cancelada`, `reagendada`; valores inválidos devem retornar erro 400 com lista de valores aceitos |
| Dados de Entrada | Query param: `status` (opcional, aceita múltiplos valores separados por vírgula) |
| Dados de Saída | Lista de vistorias com o(s) status informado(s) |
| Comportamento de Erro | 400 — status inválido com mensagem indicando valores aceitos |
| Dependências | RF01 |
| Prioridade | Should |

---

### RF07 — Paginação

| Campo | Descrição |
|---|---|
| Descrição | A API deve suportar paginação em todos os endpoints de listagem |
| Regras de Negócio | Parâmetros: `page` (default: 1) e `pageSize` (default: 20, máximo: 100); resposta deve incluir metadados de paginação: `totalItems`, `totalPages`, `currentPage`, `pageSize` |
| Dados de Entrada | Query params: `page` (opcional), `pageSize` (opcional) |
| Dados de Saída | Objeto com `data` (array de vistorias) e `pagination` (metadados) |
| Comportamento de Erro | 400 — `pageSize` acima do limite máximo; 400 — `page` menor que 1 |
| Dependências | RF01 |
| Prioridade | Must |

---

### RF08 — Autenticação e Autorização

| Campo | Descrição |
|---|---|
| Descrição | A API deve exigir autenticação válida e garantir isolamento de dados por empresa |
| Regras de Negócio | [Necessário definir padrão: API Key no header `X-API-Key` ou Bearer Token OAuth 2.0 — alinhar com padrão atual da plataforma Hypnobox]; cada credencial deve estar vinculada a uma empresa específica; não é permitido acessar dados de outra empresa |
| Dados de Entrada | Header de autenticação em todas as requisições |
| Dados de Saída | 401 se não autenticado; 403 se autenticado mas sem permissão |
| Comportamento de Erro | 401 — credencial ausente ou inválida; 403 — acesso negado ao recurso |
| Dependências | Sistema de autenticação da plataforma Hypnobox |
| Prioridade | Must |

---

## 8. Requisitos Não Funcionais

| ID | Categoria | Requisito |
|---|---|---|
| RNF01 | Performance | Tempo de resposta < 1s para listagens com até 100 registros; < 3s para consultas sem filtro com paginação |
| RNF02 | Disponibilidade | SLA de [necessário definir — sugestão: 99,5%] em horário comercial |
| RNF03 | Segurança | Autenticação obrigatória em todos os endpoints; isolamento multi-tenant rigoroso; CPF retornado mascarado (ex: `***.456.789-**`) |
| RNF04 | Auditoria | Log de todas as requisições com: credencial utilizada, IP de origem, endpoint, parâmetros, timestamp e status de resposta |
| RNF05 | Escalabilidade | Suportar [necessário definir — sugestão: N requisições/minuto por credencial] com rate limiting configurável |
| RNF06 | Documentação | API documentada em OpenAPI 3.0 (Swagger) com exemplos de request/response para cada endpoint e filtro |
| RNF07 | Versionamento | API versionada via path (`/v1/vistorias`) para garantir retrocompatibilidade em evoluções futuras |
| RNF08 | Formato | Respostas exclusivamente em JSON; datas no formato ISO 8601; encoding UTF-8 |

---

## 9. Entregáveis

| Componente | Descrição da Entrega |
|---|---|
| Backend / API | Endpoint `GET /v1/vistorias` com todos os filtros documentados nos RFs |
| Documentação OpenAPI | Especificação Swagger completa com exemplos de uso, autenticação e códigos de erro |
| Credenciais de acesso | Mecanismo de geração/gestão de API Keys (ou integração com OAuth existente) |
| Ambiente de sandbox | Ambiente de testes com dados fictícios para que integradores possam desenvolver sem afetar produção |
| Release notes | Comunicado para clientes com integração ativa sobre o novo endpoint disponível |

---

## 10. Dependências e Integrações

### 10.1 Dependências Internas

| Dependência | Tipo | Descrição |
|---|---|---|
| Módulo de Vistoria PVD (backoffice) | Dados | Fonte primária dos dados de vistorias agendadas |
| Cadastro de Técnicos | Dados | Necessário para filtro por técnico responsável |
| Cadastro de Unidades / Empreendimentos | Dados | Necessário para filtro por unidade |
| Cadastro de Clientes / Compradores | Dados | Necessário para filtro por cliente |
| Sistema de Autenticação da Hypnobox | Serviço | Validação de credenciais e controle de acesso |
| Infraestrutura de API Gateway | Serviço | Rate limiting, logging e roteamento |

### 10.2 Integrações Externas

| Sistema / API | Tipo | Descrição |
|---|---|---|
| ERPs dos clientes (Mega, UAU, outros) | Consumidor | Sistemas que irão consumir a API para sincronizar agenda de vistorias |
| Ferramentas de field service | Consumidor | Apps de gestão de técnicos em campo que podem integrar com a API |
| Dashboards e BI dos clientes | Consumidor | Ferramentas de visualização que podem consumir os dados via API |

---

## 11. Riscos e Mitigações

| # | Risco | Impacto | Probabilidade | Mitigação |
|---|---|---|---|---|
| R1 | Exposição indevida de dados de clientes (CPF, dados pessoais) | Crítico | Média | Mascaramento de CPF na resposta; autenticação obrigatória; isolamento multi-tenant; auditoria de acesso |
| R2 | Performance degradada em consultas sem filtro em bases grandes | Alto | Média | Paginação obrigatória; índices no banco para campos de filtro; cache de curta duração para consultas frequentes |
| R3 | Inconsistência entre dados da API e backoffice PVD | Alto | Baixa | API deve consultar a mesma fonte de dados do backoffice; sem camada de cache que possa desatualizar |
| R4 | Abuso da API por clientes (scraping, sobrecarga) | Médio | Média | Rate limiting por credencial; monitoramento de uso anômalo; alertas automáticos |
| R5 | Escopo crescente (clientes pedindo endpoints adicionais) | Médio | Alta | Definir claramente o escopo v1; criar processo de roadmap para versões futuras |
| R6 | Padrão de autenticação não definido na plataforma | Alto | Média | Alinhar com time de plataforma antes do início do desenvolvimento; não iniciar sem decisão tomada |

---

## Glossário e Referências

| Termo / Sigla | Definição |
|---|---|
| PVD | Pós-venda — módulo da Hypnobox para gestão do relacionamento pós-compra |
| Vistoria | Inspeção do imóvel antes ou após a entrega, registrada no sistema PVD |
| Técnico de Vistoria | Profissional responsável por realizar a inspeção física do imóvel |
| Unidade | Apartamento, casa ou lote dentro de um empreendimento |
| Empreendimento | Conjunto de unidades (condomínio, loteamento) gerenciado pela construtora |
| Multi-tenant | Arquitetura onde múltiplos clientes (construtoras) compartilham a mesma infraestrutura com isolamento de dados |
| API Key | Chave de autenticação para acesso programático à API |
| ISO 8601 | Padrão internacional de representação de datas e horas (ex: 2026-04-14) |
| OpenAPI / Swagger | Especificação padrão para documentação de APIs REST |
| Rate Limiting | Controle de quantidade máxima de requisições por período para evitar abuso |
| Field Service | Gestão de equipes técnicas em campo (técnicos de vistoria, assistência técnica) |

**Referências:**
- Base de conhecimento PVD — Hypnobox (`.kiro/skills/hypnobox-product-knowledge/references/hbox-pvd-pos-venda.md`)
- Padrão de autenticação atual da plataforma Hypnobox — [necessário consultar time de plataforma]
- Documentação de API existente da Hypnobox — [necessário consultar time de engenharia]

---

## Histórico de Versões

| Versão | Data | Autor | Alterações |
|---|---|---|---|
| v0.1 | 14/04/2026 | Kiro (IA) | Criação do documento |

---

> **⚠️ Itens que precisam de validação antes de avançar para desenvolvimento:**
> 1. Padrão de autenticação (API Key vs OAuth 2.0) — alinhar com time de plataforma
> 2. Intervalo máximo de consulta por período (sugestão: 90 dias)
> 3. Rate limiting — definir limite de requisições por credencial/minuto
> 4. SLA de disponibilidade da API
> 5. Evidências de dor (seção 2.2) — validar com CS e time de vendas
> 6. Métricas de sucesso — definir baseline e metas com time de produto
> 7. Status possíveis de vistoria — confirmar com time de produto se há outros além dos listados
