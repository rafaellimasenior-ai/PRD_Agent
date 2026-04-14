---
name: hypnobox-product-knowledge
description: >
  Conhecimento profundo sobre os produtos da Hypnobox (empresa do Grupo Senior Sistemas),
  plataforma B2B para o mercado imobiliário brasileiro. Use esta skill SEMPRE que o usuario
  mencionar Hypnobox, CRM imobiliario, pre-venda, TRS, PVD, pos-venda imobiliario,
  construtoras, incorporadoras, corretor de imoveis, espelho de vendas, plantao de vendas,
  proposta imobiliaria, assinatura digital de contrato, boleto de imovel, vistoria, assistencia
  tecnica, regua de cobranca, portal do cliente, integracao com ERP, Mega,
  ou qualquer combinacao desses termos. Tambem use ao escrever tarefas (jiratxt), historias de
  usuario, roadmap, analise de persona, analise competitiva ou qualquer documento de produto
  relacionado ao mercado imobiliario.
---

# Hypnobox — Base de Conhecimento Completa de Produto

## Contexto Corporativo

A Hypnobox e uma empresa do **Grupo Senior Sistemas**, sediada em Sao Paulo, Brasil.
A Senior Sistemas e uma das maiores empresas de tecnologia de gestao empresarial do Brasil,
com mais de 12 mil empresas no portfolio e lider em solucoes ERP para construcao civil
(ERPs Mega e UAU). A Hypnobox representa a verticalizacao da Senior no CRM e
gestao comercial imobiliaria, complementando o ecossistema de ERPs de construcao.

A Hypnobox atua exclusivamente no mercado imobiliario brasileiro — especificamente
para incorporadoras, construtoras e imobiliarias de lancamento. Nao atende outros
verticais de mercado por possuir regras de negocio proprietarias do setor.

A plataforma possui mais de 13 anos de expertise no mercado imobiliario.

---

## Os Tres Produtos (Modulos)

### 1. CRM — Pre-venda
- **Sigla interna:** CRM
- **Stack:** PHP + jQuery (legado, frontend nao-SPA)
- **Foco:** Gestao de leads, marketing, atendimento comercial e performance de campanhas

### 2. TRS — Vendas (Transacional)
- **Sigla interna:** TRS (Transacional) ou "Secretaria de Vendas"
- **Stack:** Angular + .NET
- **Foco:** Processamento de propostas, contratos, assinatura digital e integracao com ERPs

### 3. PVD — Pos-venda
- **Sigla interna:** PVD
- **Stack:** Angular + .NET
- **Foco:** Relacionamento pos-compra com o consumidor final (comprador do imovel)

> Para detalhes profundos de cada modulo, leia os arquivos em `references/`:
> - `/references/hbox-crm-pre-venda.md` — funcionalidades, fluxos e dores do CRM
> - `/references/hbox-trs-vendas.md` — funcionalidades, fluxos e dores do TRS
> - `/references/hbox-pvd-pos-venda.md` — funcionalidades, fluxos e dores do PVD
> - `/references/hbox-personas-e-mercado.md` — personas, dores e contexto do mercado imobiliario
> - `/references/hbox-ecossistema-e-integracoes.md` — ERPs, portais, canais e ecossistema tecnico

---

## Mapa Rapido de Personas

| Persona | Produto Principal | Dor Central |
|---|---|---|
| Corretor de imoveis | CRM + TRS | Perder lead por lentidao no atendimento |
| Gerente comercial / SDR | CRM | Nao saber de onde vem os melhores leads |
| Diretor de incorporadora | CRM + TRS | Falta de visibilidade do funil e performance |
| Backoffice de vendas | TRS | Processo manual e lento de contrato |
| Equipe de atendimento pos-venda | PVD (backoffice) | Volume alto de chamados sem gestao |
| Comprador do imovel | PVD (portal) | Dificuldade de obter boleto e informacoes |
| Gestor de marketing | CRM | ROI de campanhas opaco |

---

## Glossario Essencial

- **Lead:** Potencial comprador captado por algum canal (Facebook, portal, WhatsApp, etc.)
- **Fila de atendimento:** Mecanismo do CRM que distribui leads para corretores de forma ordenada
- **Plantao de vendas:** Evento presencial de vendas em decorados / stands de imoveis
- **Espelho de vendas:** Mapa visual de disponibilidade de unidades (vertical ou horizontal/loteamentos)
- **Proposta:** Simulacao financeira de compra de uma unidade com condicoes de pagamento
- **Proponente:** Comprador ou co-comprador de um imovel dentro de uma proposta
- **Signatario:** Representante da incorporadora que assina o contrato
- **Testemunha:** Pessoa que participa da assinatura do contrato sem acao direta
- **Observador:** Recebe o contrato por email mas nao assina nem tem acao sobre ele
- **Tagueamento:** Processo de marcar variaveis dinamicas no template do contrato Word para geracao automatica
- **Regua de cobranca:** Fluxo automatizado de envio de boletos por email/WhatsApp conforme datas de vencimento
- **Chamado:** Ticket de atendimento aberto pelo comprador no portal do cliente
- **Vistoria:** Inspecao do imovel entregue, registrada no sistema
- **Assistencia tecnica:** Processo de reparos pos-entrega solicitados pelo comprador
- **Repasse:** Processo de transferencia de financiamento (FGTS/bancario) para quitacao junto a incorporadora
- **Indexador:** Indice de correcao monetaria das parcelas (INCC, IGP-M, IPCA, etc.)
- **Amortizacao:** Forma de calculo das parcelas (SAC, Tabela Price, etc.)
- **BM (Business Manager):** Plataforma Meta para gestao de anuncios — necessaria para integracao Facebook Leads
- **Pagadoria:** Sistema de pagamento de comissoes a corretores (ex: Agilitas, Montagner)
- **ERP:** Sistema de gestao financeira/operacional da construtora (Mega)
- **De-para:** Tabela de mapeamento de codigos entre Hypnobox e ERP do cliente

---

## Principios de Negocio Criticos

1. **A Hypnobox NAO gera leads** — ela gerencia leads gerados por outros canais (Facebook Ads, portais, WhatsApp, Zapier, etc.)
2. **O CRM sempre vem antes do TRS** — o transacional so e implantado quando o CRM ja esta 100% configurado
3. **A integracao com ERP e unidirecional na pratica** — Hypnobox envia venda ao ERP; alteracoes no ERP nao voltam para a Hypnobox automaticamente (exceto o Mega, que tem cancelamento direto)
4. **O produto NAO atende corretores autonomos diretamente** — e vendido para incorporadoras/construtoras, que dao acesso aos corretores
5. **Ciclo de venda imobiliario e longo** — multiplos stakeholders, documentacao complexa, aprovacao de credito, assinatura digital
6. **Atualizacoes a cada 15 dias** — produto em ritmo acelerado de evolucao

---

## Comando jiratxt — Estrutura de Tarefa

Ao receber o comando `jiratxt`, sempre usar esta estrutura:

```
TITULO: [verbo de acao + objeto + contexto]

CONTEXTO:
[Explicar o problema/oportunidade que motiva a tarefa, referenciando o modulo
(CRM/TRS/PVD), a persona afetada e o impacto no negocio]

ESCOPO:
[O que deve ser feito — listar comportamentos esperados, nao solucoes tecnicas]
[O que NAO faz parte do escopo desta tarefa]

CRITERIOS DE ACEITE:
- [ ] [Criterio verificavel e objetivo]
- [ ] [Criterio verificavel e objetivo]
...

CRITERIOS DE PRONTO (DoR):
- [ ] Mockup ou prototipo aprovado (se aplicavel)
- [ ] Regras de negocio documentadas
- [ ] Dependencias mapeadas (integracao com ERP, canais, etc.)
- [ ] Casos de borda identificados

LINKS UTEIS:
- [documentacao, API, referencia tecnica relevante]
```
