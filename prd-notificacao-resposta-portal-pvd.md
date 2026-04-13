# PRD — Notificação de Resposta do Cliente no Portal (PVD)

---

## Metadados do Documento

| Campo              | Valor                                                                 |
|--------------------|-----------------------------------------------------------------------|
| Produto / Módulo   | Hypnobox PVD — Backoffice                                             |
| Funcionalidade     | Notificação de resposta do cliente no portal (push + email)           |
| Tipo               | Nova feature                                                          |
| Direcionador       | Cobertura / Experiência do usuário interno                            |
| Status             | Em Definição                                                          |
| Product Owner      | Necessário validar                                                    |
| Stakeholders       | Time de Produto PVD, Engenharia Frontend (Angular), Engenharia Backend (.NET), QA, CS/Implantação |
| Data de criação    | 13/04/2026                                                            |
| Última atualização | 13/04/2026                                                            |
| Versão             | v0.1                                                                  |

---

## 1. Visão do Produto

**O que é?**
Um fluxo de notificação automática que alerta os usuários internos (equipe da construtora/incorporadora) envolvidos em uma vistoria ou atendimento sempre que o cliente responder um chamado pelo Portal do Cliente.

**Para quem?**
Equipe de atendimento pós-venda (backoffice) — analistas, responsáveis por vistoria e assistência técnica.

**Qual o valor entregue?**
Elimina a necessidade de o atendente monitorar manualmente o sistema para verificar novas respostas, reduzindo o tempo de resposta ao cliente e evitando chamados esquecidos ou em atraso.

**Resumo executivo:**
Hoje, quando um comprador responde um chamado no Portal do Cliente, os usuários internos só tomam conhecimento se acessarem ativamente o backoffice. Isso gera atrasos no atendimento, chamados sem resposta e insatisfação do cliente — impactando diretamente o NPS e a reputação da construtora. Esta feature entrega notificações em tempo real via push (Web Push API do navegador) e email, garantindo que nenhuma resposta do cliente passe despercebida.

---

## 2. Problema e Evidências

### 2.1 Estado Atual (As-Is)

- O cliente responde um chamado no Portal do Cliente (vistoria ou atendimento/assistência técnica).
- O sistema **não emite nenhum alerta** para os usuários internos envolvidos.
- O atendente precisa acessar o backoffice e navegar até o chamado para verificar se houve resposta.
- Em equipes com alto volume de chamados, respostas ficam sem retorno por horas ou dias.
- Não há diferenciação entre chamados com e sem resposta pendente na listagem do backoffice.

**Workaround atual:** Atendentes verificam periodicamente a fila de chamados ou dependem do cliente ligar/enviar WhatsApp para avisar que respondeu.

### 2.2 Evidências de Dor

| Fonte da Evidência       | Descrição                                                                                   |
|--------------------------|---------------------------------------------------------------------------------------------|
| Feedback de clientes     | Compradores relatam que respondem chamados e não recebem retorno — levando a reclamações no Reclame Aqui |
| Time de CS / Implantação | Construtoras solicitam algum mecanismo de alerta para não perder respostas dos clientes     |
| Contexto do produto      | O PVD já possui régua de cobrança automatizada, mas não possui notificação reativa para atendentes |
| Suporte / Tickets        | Necessário validar volume de chamados relacionados a "resposta sem retorno" — **dado a coletar** |

---

## 3. Objetivos de Negócio

| # | Objetivo                                                        | Métrica Alvo                                      |
|---|-----------------------------------------------------------------|---------------------------------------------------|
| O1 | Reduzir o tempo médio de primeira resposta da equipe interna   | Meta a definir após coleta de baseline — **validar** |
| O2 | Reduzir chamados sem resposta por mais de 24h                  | Meta a definir após coleta de baseline — **validar** |
| O3 | Aumentar NPS pós-atendimento das construtoras usuárias do PVD  | Meta a definir — **validar com CS**               |
| O4 | Reduzir reclamações públicas relacionadas a falta de retorno   | Redução de menções negativas no Reclame Aqui — **validar** |

> ⚠️ Os baselines precisam ser coletados antes do release para viabilizar medição de sucesso.

---

## 4. Personas

| Persona                        | Perfil                                                                 | Necessidade Principal                                              | Valor Recebido                                                              |
|-------------------------------|------------------------------------------------------------------------|--------------------------------------------------------------------|-----------------------------------------------------------------------------|
| Analista de Atendimento PVD   | Usuário do backoffice responsável por responder chamados de clientes   | Saber imediatamente quando o cliente respondeu um chamado          | Recebe push no navegador e email — age sem precisar monitorar o sistema     |
| Responsável por Vistoria      | Usuário do backoffice que conduz e acompanha o processo de vistoria    | Ser alertado quando o cliente interage com chamados de vistoria    | Não perde interações críticas do cliente durante o processo de vistoria     |
| Responsável por Assistência Técnica | Usuário do backoffice que gerencia solicitações de AT pós-entrega | Acompanhar respostas do cliente sem acessar o sistema constantemente | Recebe notificação contextualizada com link direto para o chamado          |
| Gestor de Pós-venda           | Supervisor da equipe de atendimento                                    | Garantir SLA de resposta da equipe                                 | Visibilidade indireta via métricas de tempo de resposta (futuro)            |

---

## 5. Estrutura do Produto (Módulos / Blocos)

**Módulo 1 — Motor de Detecção de Resposta**
Responsável por identificar quando um cliente registra uma nova mensagem/resposta em um chamado ativo.
- Detecção de nova mensagem do cliente em chamados de Vistoria
- Detecção de nova mensagem do cliente em chamados de Atendimento / Assistência Técnica
- Identificação dos usuários internos vinculados ao chamado (responsável + envolvidos)

**Módulo 2 — Notificação Push (Web Push API)**
Responsável por disparar notificações push via API nativa do navegador web.
- Solicitação de permissão de notificação ao usuário no primeiro acesso ao backoffice
- Armazenamento do token/subscription de push por usuário
- Disparo da notificação push com título, corpo e link direto ao chamado
- Suporte a múltiplos dispositivos/navegadores por usuário

**Módulo 3 — Notificação por Email**
Responsável por enviar email transacional aos usuários envolvidos.
- Template de email com dados do chamado (tipo, empreendimento, cliente, trecho da mensagem)
- Envio via SendGrid (já utilizado no PVD para régua de cobrança)
- Link direto para o chamado no backoffice
- Controle de deduplicação (não enviar múltiplos emails para a mesma resposta)

**Módulo 4 — Configuração de Preferências de Notificação**
Permite ao usuário controlar quais notificações deseja receber.
- Ativar/desativar notificação push por tipo de chamado (vistoria / atendimento)
- Ativar/desativar notificação por email por tipo de chamado
- Configuração acessível nas preferências do perfil do usuário no backoffice

---

## 6. Fluxo do Usuário

### 6.1 Fluxo Principal (Happy Path)

1. Cliente acessa o Portal do Cliente e abre um chamado existente (vistoria ou atendimento).
2. Cliente digita e envia uma resposta/mensagem no chamado.
3. O backend do PVD detecta a nova mensagem e identifica os usuários internos vinculados ao chamado.
4. O sistema dispara simultaneamente:
   - **Push notification** via Web Push API para todos os usuários vinculados que concederam permissão e estão com o navegador aberto (ou com service worker ativo).
   - **Email transacional** via SendGrid para todos os usuários vinculados com email cadastrado.
5. O usuário interno recebe a notificação push no navegador com: título ("Nova resposta no chamado #XXXX"), nome do cliente e empreendimento.
6. O usuário clica na notificação e é redirecionado diretamente para o chamado no backoffice.
7. O usuário visualiza a mensagem do cliente e responde.

### 6.2 Fluxos Alternativos

- **Usuário sem permissão de push concedida:** Recebe apenas o email. O sistema exibe um banner no backoffice sugerindo habilitar notificações push.
- **Usuário com navegador fechado:** O service worker entrega a notificação push quando o navegador for reaberto (comportamento nativo da Web Push API). O email é entregue normalmente.
- **Múltiplas respostas em sequência rápida:** O sistema aplica debounce/agrupamento — envia uma única notificação consolidada por janela de tempo (ex: 2 minutos), evitando spam.
- **Chamado sem usuário responsável atribuído:** Notifica todos os usuários com perfil de atendimento do empreendimento vinculado ao chamado. **Regra a validar com o time.**
- **Usuário com notificações desativadas nas preferências:** Não recebe push nem email para o tipo de chamado desativado.

---

## 7. Requisitos Funcionais

---

### RF01 — Detecção de Nova Resposta do Cliente

| Campo               | Descrição                                                                                                   |
|---------------------|-------------------------------------------------------------------------------------------------------------|
| Descrição           | O sistema deve detectar quando um cliente registra uma nova mensagem em um chamado ativo no Portal do Cliente |
| Regras de Negócio   | Apenas mensagens originadas pelo cliente (comprador) disparam notificação. Mensagens da equipe interna não disparam. O chamado deve estar com status ativo (não encerrado/cancelado). |
| Dados de Entrada    | ID do chamado, ID do usuário autor da mensagem, tipo do autor (cliente / interno), timestamp                |
| Dados de Saída      | Evento de notificação com: ID do chamado, tipo do chamado (vistoria / atendimento), lista de usuários internos a notificar |
| Comportamento de Erro | Se a identificação dos usuários vinculados falhar, registrar log de erro e não disparar notificação. Não bloquear o envio da mensagem pelo cliente. |
| Dependências        | Módulo de Chamados (Vistoria e Atendimento), cadastro de usuários internos vinculados ao chamado            |
| Prioridade          | Must                                                                                                        |

---

### RF02 — Solicitação de Permissão de Push ao Usuário

| Campo               | Descrição                                                                                                   |
|---------------------|-------------------------------------------------------------------------------------------------------------|
| Descrição           | O sistema deve solicitar permissão de notificação push ao usuário interno na primeira vez que acessar o backoffice após a feature ser ativada |
| Regras de Negócio   | A solicitação deve seguir o fluxo nativo da Web Push API (Notification.requestPermission()). Deve ser exibida apenas uma vez por navegador/dispositivo. Se o usuário negar, o sistema não deve solicitar novamente de forma automática — apenas exibir um banner informativo opcional. |
| Dados de Entrada    | Ação do usuário (permitir / bloquear / ignorar)                                                             |
| Dados de Saída      | PushSubscription salvo no backend vinculado ao user_id; status de permissão registrado                      |
| Comportamento de Erro | Se o navegador não suportar Web Push API, exibir mensagem informativa e operar apenas via email.           |
| Dependências        | RF03 (armazenamento de subscription), compatibilidade com navegadores modernos (Chrome, Edge, Firefox, Safari 16.4+) |
| Prioridade          | Must                                                                                                        |

---

### RF03 — Armazenamento e Gestão de Push Subscriptions

| Campo               | Descrição                                                                                                   |
|---------------------|-------------------------------------------------------------------------------------------------------------|
| Descrição           | O backend deve armazenar e gerenciar os tokens de push subscription de cada usuário interno                 |
| Regras de Negócio   | Um usuário pode ter múltiplas subscriptions (diferentes navegadores/dispositivos). Subscriptions expiradas ou inválidas devem ser removidas automaticamente após falha de entrega. |
| Dados de Entrada    | user_id, endpoint da subscription, chaves p256dh e auth (padrão Web Push)                                  |
| Dados de Saída      | Subscription persistida no banco; subscriptions inválidas removidas                                         |
| Comportamento de Erro | Falha ao salvar subscription: registrar log, não bloquear o usuário. Subscription inválida no disparo: remover do banco e continuar para as demais. |
| Dependências        | RF02, banco de dados do PVD                                                                                 |
| Prioridade          | Must                                                                                                        |

---

### RF04 — Disparo de Notificação Push via Web Push API

| Campo               | Descrição                                                                                                   |
|---------------------|-------------------------------------------------------------------------------------------------------------|
| Descrição           | O backend deve disparar notificações push para todos os usuários internos vinculados ao chamado que possuam subscription ativa |
| Regras de Negócio   | O payload da notificação deve conter: título (ex: "Nova resposta — Chamado #XXXX"), corpo (nome do cliente + empreendimento + trecho da mensagem, máx. 100 caracteres), URL de redirecionamento para o chamado no backoffice, ícone da Hypnobox/construtora. Aplicar debounce de 2 minutos para múltiplas respostas consecutivas do mesmo cliente no mesmo chamado. |
| Dados de Entrada    | Lista de push subscriptions, payload da notificação                                                         |
| Dados de Saída      | Notificação entregue ao navegador do usuário; log de disparo com status (entregue / falhou / subscription inválida) |
| Comportamento de Erro | Falha de entrega: registrar log com motivo. Não retentar automaticamente (evitar spam). Subscription inválida: remover e continuar. |
| Dependências        | RF01, RF03, biblioteca de Web Push no backend (.NET — ex: WebPush NuGet package)                            |
| Prioridade          | Must                                                                                                        |

---

### RF05 — Service Worker para Recebimento de Push

| Campo               | Descrição                                                                                                   |
|---------------------|-------------------------------------------------------------------------------------------------------------|
| Descrição           | O frontend Angular deve registrar um Service Worker capaz de receber e exibir notificações push mesmo com o backoffice fechado |
| Regras de Negócio   | O Service Worker deve tratar o evento `push`, exibir a notificação com os dados do payload e tratar o evento `notificationclick` redirecionando para a URL do chamado. Deve funcionar em HTTPS (obrigatório para Web Push). |
| Dados de Entrada    | Evento push recebido pelo Service Worker com payload JSON                                                   |
| Dados de Saída      | Notificação exibida no sistema operacional do usuário; redirecionamento ao clicar                           |
| Comportamento de Erro | Se o Service Worker não estiver registrado, a notificação não é exibida — o usuário recebe apenas o email. Registrar falha de registro no log do frontend. |
| Dependências        | RF02, RF04, Angular Service Worker ou SW customizado, HTTPS obrigatório                                     |
| Prioridade          | Must                                                                                                        |

---

### RF06 — Disparo de Email Transacional

| Campo               | Descrição                                                                                                   |
|---------------------|-------------------------------------------------------------------------------------------------------------|
| Descrição           | O sistema deve enviar email transacional via SendGrid para os usuários internos vinculados ao chamado quando o cliente responder |
| Regras de Negócio   | O email deve conter: assunto (ex: "Nova resposta do cliente — Chamado #XXXX"), nome do cliente, empreendimento, tipo do chamado (vistoria / atendimento), trecho da mensagem (máx. 200 caracteres), botão/link "Ver chamado" com URL direta ao backoffice. Aplicar deduplicação: não enviar mais de 1 email por chamado por janela de 2 minutos. |
| Dados de Entrada    | Lista de emails dos usuários vinculados, dados do chamado e da mensagem                                     |
| Dados de Saída      | Email enviado via SendGrid; log de envio com status (enviado / falhou / bounced)                            |
| Comportamento de Erro | Falha no SendGrid: registrar log, não retentar automaticamente na mesma janela. Email inválido ou bounced: registrar e não reenviar. |
| Dependências        | RF01, integração SendGrid já existente no PVD, template de email a ser criado                               |
| Prioridade          | Must                                                                                                        |

---

### RF07 — Preferências de Notificação por Usuário

| Campo               | Descrição                                                                                                   |
|---------------------|-------------------------------------------------------------------------------------------------------------|
| Descrição           | O usuário interno deve poder configurar suas preferências de notificação no perfil do backoffice            |
| Regras de Negócio   | Configurações disponíveis: ativar/desativar push por tipo (vistoria / atendimento); ativar/desativar email por tipo (vistoria / atendimento). Padrão inicial: ambos ativos para ambos os tipos. |
| Dados de Entrada    | Seleção do usuário nas preferências de perfil                                                               |
| Dados de Saída      | Preferências salvas no banco vinculadas ao user_id; respeitadas nos disparos de RF04 e RF06                 |
| Comportamento de Erro | Falha ao salvar preferências: exibir mensagem de erro e manter configuração anterior.                      |
| Dependências        | RF04, RF06, tela de perfil do usuário no backoffice                                                         |
| Prioridade          | Should                                                                                                      |

---

### RF08 — Banner de Ativação de Push no Backoffice

| Campo               | Descrição                                                                                                   |
|---------------------|-------------------------------------------------------------------------------------------------------------|
| Descrição           | Exibir um banner não intrusivo no backoffice para usuários que ainda não concederam permissão de push, incentivando a ativação |
| Regras de Negócio   | Exibir apenas para usuários com permissão pendente ou negada. Permitir fechar/dispensar o banner. Não exibir novamente por 7 dias após ser dispensado. Incluir botão "Ativar notificações" que aciona o fluxo de permissão. |
| Dados de Entrada    | Status de permissão do navegador (Notification.permission)                                                  |
| Dados de Saída      | Banner exibido ou ocultado conforme estado; ação de ativação dispara RF02                                   |
| Comportamento de Erro | Se o navegador não suportar push, não exibir o banner.                                                     |
| Dependências        | RF02, frontend Angular                                                                                      |
| Prioridade          | Should                                                                                                      |

---

### RF09 — Log de Notificações Disparadas

| Campo               | Descrição                                                                                                   |
|---------------------|-------------------------------------------------------------------------------------------------------------|
| Descrição           | O sistema deve registrar um log de todas as notificações disparadas (push e email) para fins de auditoria e diagnóstico |
| Regras de Negócio   | Registrar: tipo de notificação (push / email), user_id destinatário, chamado_id, timestamp do disparo, status (sucesso / falha), motivo da falha (se houver). Logs devem ser acessíveis para o time de suporte/engenharia. Retenção mínima: 90 dias. |
| Dados de Entrada    | Resultado do disparo de RF04 e RF06                                                                         |
| Dados de Saída      | Registro persistido no banco de logs                                                                        |
| Comportamento de Erro | Falha ao registrar log: não bloquear o disparo da notificação. Registrar falha do log em sistema de monitoramento. |
| Dependências        | RF04, RF06                                                                                                  |
| Prioridade          | Must                                                                                                        |

---

## 8. Requisitos Não Funcionais

| ID     | Categoria       | Requisito                                                                                                   |
|--------|-----------------|-------------------------------------------------------------------------------------------------------------|
| RNF01  | Performance     | O disparo de notificações deve ocorrer em até 5 segundos após o registro da resposta do cliente no portal   |
| RNF02  | Disponibilidade | O serviço de notificação não deve bloquear o fluxo de envio de mensagem do cliente em caso de falha         |
| RNF03  | Compatibilidade | Web Push API deve funcionar nos navegadores: Chrome 50+, Edge 17+, Firefox 44+, Safari 16.4+. Fallback para email em navegadores sem suporte. |
| RNF04  | Segurança       | Comunicação com Web Push API deve usar VAPID (Voluntary Application Server Identification). Tokens de subscription armazenados com controle de acesso por user_id. |
| RNF05  | Segurança       | O link de redirecionamento na notificação deve exigir autenticação — usuário não autenticado é redirecionado para login antes de acessar o chamado |
| RNF06  | Escalabilidade  | O serviço de disparo deve suportar envio assíncrono (fila/background job) para não impactar a performance do backend em picos de volume |
| RNF07  | Auditoria       | Todos os disparos devem ser logados com user_id, chamado_id, tipo e timestamp (RF09)                        |
| RNF08  | Responsividade  | As preferências de notificação devem ser acessíveis em desktop e mobile (web responsivo)                    |
| RNF09  | HTTPS           | Web Push API exige HTTPS obrigatoriamente — o backoffice deve estar servido em HTTPS                        |

---

## 9. Compliance, LGPD e Requisitos Legais

### 9.1 Dados Pessoais Envolvidos

| Dado                        | Titular       | Finalidade no Fluxo                                      |
|-----------------------------|---------------|----------------------------------------------------------|
| Email do usuário interno    | Funcionário da construtora | Envio de notificação de resposta do cliente |
| Nome do cliente (comprador) | Comprador     | Exibido no corpo da notificação push e email             |
| Trecho da mensagem do cliente | Comprador   | Exibido no corpo da notificação (máx. 200 chars)         |
| Push subscription token     | Usuário interno | Identificação do dispositivo para entrega de push      |
| Logs de disparo             | Usuário interno + Comprador | Auditoria e diagnóstico                   |

### 9.2 Classificação de Risco LGPD

**Risco geral: Baixo** — os dados tratados são operacionais, com finalidade clara e base legal de execução de contrato/legítimo interesse.

### 9.3 Requisitos de Conformidade

| Requisito                  | Descrição                                                                                                   |
|----------------------------|-------------------------------------------------------------------------------------------------------------|
| Base legal                 | Execução de contrato (Art. 7º, V, LGPD) — notificação é parte do serviço contratado pela construtora       |
| Minimização de dados       | Exibir apenas trecho da mensagem (não a mensagem completa) na notificação push e email                      |
| Trilha de auditoria        | Log de todos os disparos com user_id, chamado_id e timestamp (RF09)                                         |
| Controle de acesso         | Push subscriptions acessíveis apenas pelo próprio usuário e pelo sistema — não expostas a outros usuários   |
| Retenção de logs           | Logs de notificação retidos por 90 dias, após isso podem ser descartados ou anonimizados                    |
| Direito de opt-out         | Usuário pode desativar notificações nas preferências de perfil (RF07) e revogar permissão push no navegador |
| Dados de terceiros (SendGrid) | SendGrid já é utilizado no PVD — verificar se o DPA (Data Processing Agreement) com a SendGrid já cobre este novo fluxo de dados |

---

## 10. Entregáveis

| Componente         | Descrição da Entrega                                                                                        |
|--------------------|-------------------------------------------------------------------------------------------------------------|
| Backend / API      | Endpoint de detecção de resposta + serviço de disparo assíncrono (fila) + armazenamento de subscriptions + integração Web Push (VAPID) + integração SendGrid |
| Frontend (Angular) | Service Worker para recebimento de push + fluxo de solicitação de permissão + banner de ativação + tela de preferências de notificação no perfil |
| Template de Email  | Template HTML transacional no SendGrid para notificação de resposta do cliente                              |
| Banco de Dados     | Tabelas: push_subscriptions (user_id, endpoint, keys, created_at, updated_at) + notification_logs (tipo, user_id, chamado_id, status, timestamp) |
| Documentação       | Release notes para clientes + guia de ativação de push para usuários do backoffice + documentação técnica do Service Worker |

---

## 11. Cenários de Teste (QA)

### 11.1 Cenários Positivos (Happy Path)

| # | Cenário                                          | Condições                                                                 | Resultado Esperado                                                          |
|---|--------------------------------------------------|---------------------------------------------------------------------------|-----------------------------------------------------------------------------|
| C1 | Cliente responde chamado de atendimento          | Usuário interno com push ativo e email cadastrado, chamado ativo          | Push exibido no navegador + email recebido em até 5s                        |
| C2 | Cliente responde chamado de vistoria             | Usuário responsável pela vistoria com push ativo                          | Push exibido com título correto e link para o chamado de vistoria           |
| C3 | Usuário clica na notificação push                | Usuário autenticado no backoffice                                         | Redirecionado diretamente para o chamado correspondente                     |
| C4 | Usuário não autenticado clica na notificação push | Sessão expirada                                                           | Redirecionado para tela de login; após login, vai para o chamado            |
| C5 | Usuário desativa notificação push nas preferências | Preferência de push desativada para "atendimento"                        | Push não é disparado; email continua sendo enviado                          |
| C6 | Múltiplos usuários vinculados ao chamado         | 3 usuários internos vinculados ao chamado                                 | Todos os 3 recebem push e email                                             |
| C7 | Usuário com múltiplos dispositivos               | Mesmo usuário logado em Chrome e Edge                                     | Push entregue em ambos os dispositivos                                      |

### 11.2 Cenários Negativos (Edge Cases)

| # | Cenário                                          | Condições                                                                 | Resultado Esperado                                                          |
|---|--------------------------------------------------|---------------------------------------------------------------------------|-----------------------------------------------------------------------------|
| C8 | Navegador sem suporte a Web Push                 | Internet Explorer ou Safari < 16.4                                        | Apenas email é enviado; nenhum erro exibido ao usuário                      |
| C9 | Usuário negou permissão de push                  | Permissão bloqueada no navegador                                          | Apenas email é enviado; banner de ativação não é exibido novamente por 7 dias |
| C10 | Cliente envia 5 respostas em 1 minuto            | Múltiplas mensagens consecutivas no mesmo chamado                         | Apenas 1 notificação push e 1 email enviados (debounce de 2 minutos)        |
| C11 | Chamado encerrado/cancelado                      | Cliente tenta responder chamado com status "encerrado"                    | Notificação não é disparada; ação bloqueada ou ignorada                     |
| C12 | Usuário interno sem email cadastrado             | Campo email vazio no cadastro do usuário                                  | Push é enviado normalmente; email não é enviado; log registra ausência de email |
| C13 | Falha no SendGrid                                | SendGrid retorna erro 500                                                 | Log de falha registrado; push é enviado normalmente; não há retry automático |
| C14 | Push subscription expirada                       | Token de subscription inválido no banco                                   | Subscription removida do banco; log registrado; email enviado normalmente   |
| C15 | Usuário interno responde o chamado (não o cliente) | Mensagem originada por usuário interno                                   | Nenhuma notificação é disparada                                             |

---

## 12. Dependências e Integrações

### 12.1 Dependências Internas

| Dependência                          | Tipo    | Descrição                                                                 |
|--------------------------------------|---------|---------------------------------------------------------------------------|
| Módulo de Chamados — Vistoria        | Serviço | Fonte dos eventos de nova mensagem do cliente em chamados de vistoria     |
| Módulo de Chamados — Atendimento/AT  | Serviço | Fonte dos eventos de nova mensagem do cliente em chamados de atendimento  |
| Cadastro de usuários internos        | Dados   | Necessário para identificar responsáveis e envolvidos no chamado          |
| Tela de perfil do usuário (backoffice) | UI    | Ponto de entrada para as preferências de notificação (RF07)               |
| Infraestrutura HTTPS do backoffice   | Infra   | Obrigatório para Web Push API funcionar                                   |

### 12.2 Integrações Externas

| Sistema / API       | Tipo       | Descrição                                                                                   |
|---------------------|------------|---------------------------------------------------------------------------------------------|
| Web Push API (browser) | API nativa | API nativa dos navegadores para entrega de notificações push — sem custo adicional        |
| VAPID               | Protocolo  | Padrão de autenticação para servidores de push — geração de chaves VAPID no backend        |
| SendGrid            | Email      | Já integrado no P
