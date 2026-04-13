# CRM — Modulo de Pre-venda

## Visao Geral

O CRM e o ponto de entrada de toda a jornada comercial da Hypnobox. E onde o relacionamento
com o potencial comprador (lead) comeca, e gerenciado e convertido em oportunidade de venda.
E usado principalmente por corretores de imoveis, SDRs e gestores comerciais de
incorporadoras, construtoras e imobiliarias de lancamento.

Stack: PHP + jQuery (frontend nao-SPA, legado)

---

## Funcionalidades Principais

### Gestao de Leads
- Captura de leads de multiplos canais (Facebook Leads, portais imobiliarios, WhatsApp, Zapier, formularios proprios)
- Fila de atendimento: distribuicao automatizada de leads entre corretores por ordem, regra de negocio ou disponibilidade
- Identificacao da origem de todos os leads (UTMs, canal, campanha)
- Cadastro automatico do lead no CRM sem intervencao manual (via bot/integracao)
- Historico completo de interacoes por lead

### Atendimento
- Atendimento via WhatsApp receptivo (mensagem recebida entra no CRM)
- WhatsApp ativo (corretor inicia conversa pelo CRM)
- Bot de WhatsApp para qualificacao automatica de leads (24/7) — modulo adicional
- Registro de todas as conversas no CRM para gestao e auditoria
- Atendimento multicanal: chat, e-mail, telefone, WhatsApp

### Oferta Ativa
- Funcionalidade que permite ao corretor prospectar ativamente dentro da base de leads do CRM
- Selecao de perfil de cliente por criterios (renda, regiao, interesse, estagio no funil)
- Envio de comunicacoes e ofertas personalizadas

### Plantao de Vendas
- Controle de presenca e fluxo de visitantes em stands e decorados
- Registro de visitas agendadas e walk-ins
- Atribuicao automatica de corretor ao visitante conforme regra de fila presencial

### Espelho de Vendas
- Mapa visual de disponibilidade de unidades em tempo real
- Suporte a empreendimentos verticais (apartamentos) e horizontais (loteamentos)
- Previne reservas duplicadas — dor classica do mercado imobiliario

### Marketing e Campanhas
- Integracao nativa com Facebook Business Manager (Meta Leads Ads)
- Integracao com portais imobiliarios (ZAP Imoveis, Viva Real, OLX, etc.) via Zapier ou API direta
- Rastreamento de origem de lead (UTM, canal, campanha especifica)
- Mais de 20 relatorios: ranking de vendas, previsao de receita, NPS, funil de conversao, performance por campanha, origem de leads

### Relatorios e Insights
- Dashboard de performance comercial
- Ranking de corretores
- Funil de vendas por estagio
- Taxa de conversao por origem de lead
- Velocidade de atendimento (tempo de primeiro contato)
- ROI por campanha de marketing

---

## Fluxo de Implantacao (o que o consultor precisa fazer)

1. **Configuracao de produtos** (empreendimentos) — nome, tipologia, preco, unidades
2. **Configuracao de usuarios** — corretores, gerentes, diretores, backoffice
3. **Configuracao de clientes** (incorporadoras/imobiliarias) — hierarquia comercial
4. **Regras de negocio** — fila de atendimento, comissao, SLA de resposta
5. **Integracao com Facebook Leads** — requer acesso de administrador ao Business Manager (BM) do cliente
6. **Integracao com outros canais** — Zapier, portais, API

### Ferramentas necessarias para implantacao
- Postman (para chamadas de API durante configuracao)
- Excel (montagem de planilhas de importacao e mapeamento)
- Acesso ao SharePoint interno da Hypnobox (materiais de apoio)
- Acesso a Wiki interna (manuais, artigos, passo a passo) — requer VPN Senior

### Ponto critico na integracao com Facebook
O consultor precisa de **acesso de administrador** ao Business Manager (BM) do cliente.
Acesso parcial (ex: apenas a pagina, ou perfil de visualizador) nao permite configurar a
integracao. Se o cliente nao concordar em conceder acesso de admin, a integracao nao pode
ser realizada.

---

## Dores que o CRM Resolve

| Dor do mercado | Solucao no CRM |
|---|---|
| Lead cai no email e ninguem responde | Fila de atendimento automatica com SLA |
| Reserva duplicada de unidade | Espelho de vendas em tempo real |
| Nao sabe de onde vem os melhores leads | Identificacao de origem + relatorios de ROI |
| Planilhas e ferramentas desconexas | Plataforma unica integrando marketing e vendas |
| Corretor perde lead por demora | Bot de WhatsApp que responde em segundos (24/7) |
| Gestao nao sabe performance da equipe | Ranking e funil de vendas em tempo real |
| Leads frios sem acao | Oferta ativa para reengajar base |

## Dores que Ainda Pode Resolver (Roadmap / Oportunidades)

- Automacao de partes tecnicas da implantacao (hoje muito manual via Postman)
- Ferramenta interna para importacao sem necessidade de API externa
- IA para qualificacao automatica de leads com base em historico de conversao
- Integracao com mais plataformas de anuncio (TikTok Ads, Google Ads nativo)
- Precificacao dinamica com IA (em estudo no mercado)

---

## Competidores Diretos

- CV CRM (Construtor de Vendas) — maior do mercado, 1000+ incorporadoras
- Facilita CRM — foco em mobilidade
- Anapro
- Jetimob (foco em imobiliarias)
- Loft CRM

**Diferencial declarado da Hypnobox:** 13+ anos de especialidade imobiliaria,
integracao nativa com ecossistema Senior (Mega) ou (UAU), agencia de performance
propria (Uselink), Customer Success com 90% de aprovacao.
