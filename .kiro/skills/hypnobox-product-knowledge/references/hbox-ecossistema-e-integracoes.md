# Ecossistema e Integracoes

## Posicionamento no Ecossistema Senior

A Hypnobox integra o ecossistema de solucoes da Senior Sistemas para o mercado
de construcao civil. A Senior e lider no segmento, atendendo 45+ das 100 maiores
construtoras do Brasil (segundo Ranking INTEC).

```
[Senior Sistemas - Grupo]
          |
    +-----+-----+
    |             |
[ERP Mega]    [ERP UAU] <- gestao financeira e operacional das construtoras
    |             |
    +-----+-------+
          |
     [Hypnobox]                  <- CRM, vendas e pos-venda
    [CRM | TRS | PVD]
```

A integracao Hypnobox <-> ERP e um dos principais diferenciais competitivos, pois
o cliente da incorporadora ja usa o ERP Senior e nao precisa de uma integracao
customizada.

---

## ERPs Integrados

### Mega Construcao (Senior Mega)
- ERP mais usado pelo setor de construcao civil no Brasil
- Adquirido pela Senior Sistemas em dezembro de 2018
- Funcionalidades: administracao de obras, carteira de recebiveis, securitizacao,
  financeiro, contabilidade, espelho de vendas, integracao bancaria, controle de inadimplencia
- Hypnobox -> Mega: envio de venda, proponentes, parcelas, comissoes
- Mega -> Hypnobox: sem retorno automatico (exceto cancelamento, que o Mega permite
  direto pela Hypnobox)
- De-para necessario para: produtos, indexadores, tipos de pagamento



### Outros ERPs
- A Hypnobox pode ter integracoes com outros ERPs do mercado (ex: UAU, Sienge)
- Cada integracao tem suas especificidades de de-para e configuracao

---

## Canais de Captacao de Leads (Integracoes CRM)

### Facebook / Meta Leads Ads
- Principal canal de captacao de leads para o mercado imobiliario brasileiro
- Integracao via Business Manager (BM) do cliente
- Requer acesso de administrador ao BM do cliente para configurar
- Leads chegam em tempo real no CRM
- Formularios do Facebook preenchidos pelo lead no proprio anuncio

### Portais Imobiliarios
- ZAP Imoveis — maior portal imobiliario do Brasil
- Viva Real
- OLX Imoveis
- Imovelweb
- Outros portais regionais
- Integracao geralmente via Zapier ou API direta do portal

### Zapier
- Plataforma de automacao que conecta a Hypnobox a centenas de outras fontes
- Permite receber leads de qualquer fonte que tenha integracao com Zapier
- Ex: formularios do site proprio, Google Forms, Typeform, etc.

### WhatsApp Business API
- Atendimento receptivo: lead manda mensagem e e direcionado para fila do CRM
- WhatsApp ativo: corretor inicia conversa pelo CRM
- Bot de WhatsApp: qualificacao automatica sem corretor (24/7)
- Plataforma utilizada: Botmaker

### Google Ads / Outros
- Via Zapier ou formularios do site proprio

---

## Plataformas de Apoio

### Botmaker
- Plataforma de automacao de WhatsApp Business (chatbot e atendimento)
- Usada tanto no CRM (bot de qualificacao de leads) quanto no PVD (regua de cobranca)
- A equipe de implantacao precisa ter acesso ao Botmaker para configurar fluxos

### Sendgrid
- Plataforma de envio de email transacional (Twilio Sendgrid)
- Usada no PVD para envio da regua de cobranca por email
- Configuracao necessaria durante implantacao do PVD

### Uselink / Zacaratto (Agencia de Performance)
- Agencia do proprio grupo Hypnobox/Senior
- Responsavel por gestao de campanhas digitais (Facebook Ads, Google Ads)
- Alternativa ao cliente que nao tem agencia propria
- Gerencia o BM do cliente e as campanhas, entregando leads ja no CRM

### Pagadorias
- **Agilitas** — sistema de pagamento de comissoes a corretores
- **Montagner** — sistema de pagamento de comissoes a corretores
- O perfil de comissionado do usuario no TRS define qual pagadoria ele usa

---

## Arquitetura de Implantacao

A implantacao da Hypnobox segue uma sequencia obrigatoria:

```
1. CRM (pre-venda)     <- sempre primeiro
2. TRS (vendas)        <- apenas quando CRM esta 100% implantado
3. PVD (pos-venda)     <- pode ser paralelo ao TRS, mas geralmente vem depois
```

### Ambientes
- Cada cliente tem seu proprio ambiente (instancia) da Hypnobox
- Ambientes de homologacao/staging para testes antes de producao
- Acesso via SharePoint (materiais) e Wiki Senior (manuais) — Wiki requer VPN Senior

### Ferramentas do Consultor de Implantacao
- Postman — chamadas de API durante configuracao
- Excel — planilhas de importacao, mapeamento de dados, de-para
- Word — tagueamento de contratos
- Acesso ao SharePoint interno Hypnobox
- Acesso a Wiki Senior (VPN Senior obrigatoria)
- Acesso ao Botmaker (para PVD)
- Acesso ao Sendgrid (para PVD)

---

## Competidores por Modulo

| Modulo | Competidores Diretos |
|---|---|
| CRM / Pre-venda | CV CRM, Facilita, Anapro, Jetimob |
| Vendas / Transacional | CV CRM (CV Vender), Vimob (Senior Mega), Facilita |
| Pos-venda | CV CRM (CV Relacionar), sistemas de helpdesk adaptados |

**Diferencial estrategico da Hypnobox:**
- Unica plataforma de CRM + Vendas + Pos-venda nativa para o mercado imobiliario
  integrada ao ecossistema Senior (ERPs Mega)
- Especialidade de 13+ anos no segmento
- Agencia de performance propria (Uselink) integrada ao produto
