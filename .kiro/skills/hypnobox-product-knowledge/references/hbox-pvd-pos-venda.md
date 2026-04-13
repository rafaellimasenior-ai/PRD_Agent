# PVD — Modulo de Pos-venda

## Visao Geral

O PVD e o modulo destinado ao relacionamento pos-compra com o consumidor final
(o comprador do imovel). E dividido em duas frentes:

1. **Portal do Cliente** — interface voltada ao consumidor (comprador)
2. **Backoffice** — interface voltada a equipe de atendimento da construtora/incorporadora

Stack: Angular + .NET

E um produto relativamente mais novo na Hypnobox e em evolucao acelerada
(novidades a cada 15 dias aproximadamente). Muitos recursos ainda estao sendo
adicionados (ex: atendimento via WhatsApp estava em desenvolvimento no momento
dos treinamentos — regua de cobranca ja tinha, mas atendimento reativo ainda nao).

**Importante:** A Hypnobox NAO oferece aplicativo nativo (iOS/Android) para o PVD.
O portal e um web app responsivo, acessivel via browser no celular. A estrategia
declarada e nao desenvolver app nativo neste momento — o web app responsivo pode
ser instalado como atalho na tela inicial do smartphone (PWA-like), o que atende
a maior parte dos casos de uso.

---

## Portal do Cliente (Frente do Consumidor)

### Funcionalidades

**Segunda Via de Boleto**
- Acesso aos boletos de parcelas do financiamento diretamente no portal
- Historico de pagamentos e demonstrativo de valores pagos
- O consumidor acessa sem precisar ligar para a construtora

**Documentos**
- Acesso ao contrato assinado e outros documentos da compra
- Download de documentos relevantes

**Abertura de Chamados**
- O comprador pode abrir chamados (tickets) diretamente no portal
- Acompanhamento do status do chamado em tempo real
- Canal de comunicacao direta com a equipe de atendimento da construtora

**Acompanhamento de Obra**
- Evolucao percentual da obra
- Fotos e registros de progresso (a construtora alimenta pelo backoffice)
- Transparencia para o comprador durante o periodo de construcao

**Assistencia Tecnica**
- Solicitacao de visita tecnica para reparos pos-entrega
- Acompanhamento do status da solicitacao

---

## Backoffice (Frente da Equipe Interna)

### Funcionalidades

**Gestao de Conteudo do Portal**
- A equipe configura o que aparece no portal do cliente
- Cadastro de documentos, fotos de obra, atualizacoes de progresso
- Configuracao de informacoes do empreendimento

**Gestao de Atendimentos / Chamados**
- Recepcao e triagem de chamados abertos pelos clientes
- Atribuicao de chamados a membros da equipe
- Historico de comunicacoes com o cliente

**Processo de Repasse**
- Gestao do processo de repasse de financiamento (FGTS / credito bancario)
- Controle dos documentos necessarios para o repasse
- Rastreamento do status junto a instituicoes financeiras

**Vistoria**
- Agendamento de vistorias do imovel antes da entrega
- Registro das ocorrencias encontradas durante a vistoria
- Acompanhamento da resolucao das pendencias (punch list)
- Geracao de relatorios de vistoria

**Assistencia Tecnica**
- Recepcao e gestao das solicitacoes de assistencia tecnica pos-entrega
- Fluxo de aprovacao e execucao de reparos
- Controle de garantias do imovel

**Regua de Cobranca Automatizada**
- Configuracao de regras de disparo automatico de boletos por email e/ou WhatsApp
- Acionamento conforme datas de vencimento (boleto a vencer, boleto vencido)
- Reducao drastica de inadimplencia sem trabalho manual da equipe
- Historico de disparos e status de entrega

**Integracao com ERPs**
- Integracao com Mega para sincronizacao de dados financeiros
- Integracao com UAU para sincronizacao de dados financeiros
- Dados de parcelas, saldos e status de contrato vem do ERP

---

## Fluxo de Implantacao

1. **Coleta de informacoes do cliente** — dados da construtora, empreendimentos
2. **Configuracao do portal** — customizacao visual (logo, cores), dados do empreendimento
3. **Importacao de contratos e compradores** — dados dos clientes e seus contratos
4. **Configuracao da regua de cobranca** — regras de disparo por tipo de parcela e canal
5. **Configuracao de Botmaker** — plataforma de automacao de WhatsApp (para regua via WhatsApp)
6. **Configuracao de Sendgrid** — plataforma de envio de email (para regua via email)
7. **Configuracao de vistorias** — formularios, checklists, responsaveis
8. **Configuracao de assistencia tecnica** — categorias, SLAs, responsaveis
9. **Treinamento da equipe de atendimento** no backoffice

### Ferramentas de Integracao Necessarias
- **Botmaker** — plataforma de WhatsApp Business API (equipe de implantacao precisa de acesso)
- **Sendgrid** — plataforma de envio de email transacional
- Wiki da Senior (manuais de passo a passo para importacoes)
- SharePoint interno (materiais de apoio)

---

## Dores que o PVD Resolve

| Dor do mercado | Solucao no PVD |
|---|---|
| SAC sobrecarregado com pedidos de boleto | Portal self-service para 2a via |
| Comprador sem informacao sobre obra | Acompanhamento de evolucao no portal |
| Inadimplencia por falta de lembrete | Regua de cobranca automatizada |
| Vistoria registrada em papel | Vistoria digital com registro e relatorio |
| Chamados perdidos ou sem rastreabilidade | Gestao de tickets com historico |
| Repasse sem controle de status | Gestao de repasse com documentacao |
| Assistencia tecnica descentralizada | Fluxo digital de AT com SLA |
| Reclamacoes publicas por falta de atendimento | Canal oficial de atendimento no portal |

## Dores que Ainda Pode Resolver (Oportunidades / Em Desenvolvimento)

- Atendimento via WhatsApp reativo para o comprador (solicitar boleto pelo WhatsApp) — estava em roadmap
- Aplicativo nativo (nao e prioridade declarada, mas foi demandado por clientes)
- NPS automatizado pos-entrega e pos-atendimento
- Gestao de garantia com controle de prazos por tipo de item (ABNT NBR 5674)
- Pesquisa de satisfacao automatizada no portal
- Dashboard de saude da carteira (inadimplencia, chamados abertos, etc.) para gestores

---

## Contexto de Mercado — Pos-venda Imobiliario

O pos-venda imobiliario e uma das areas mais neglenciadas do setor. Pesquisas indicam que
72% dos compradores consideram o pos-venda tao importante quanto a compra em si. Os
principais impactos de um pos-venda fraco sao:

- **Reclamacoes publicas** em redes sociais e Reclame Aqui
- **Perda de indicacoes** (clientes nao satisfeitos nao recomendam)
- **Dificuldade em vender novos lancamentos** (reputacao afetada)

Construtoras que investem em pos-venda de qualidade reduzem custos com retrabalho,
aumentam NPS e geram novas vendas por indicacao (clientes fieis representam ate 65%
das vendas segundo dados do SEBRAE).
