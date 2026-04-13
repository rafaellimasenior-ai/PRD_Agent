# TRS — Modulo de Vendas (Transacional / Secretaria de Vendas)

## Visao Geral

O TRS e o modulo de processamento de vendas imobiliarias. Entra em cena apos o lead
ter sido qualificado e decidido comprar. E onde a proposta e formalizada, a documentacao
e coletada, o credito e aprovado, o contrato e assinado digitalmente e a venda e enviada
ao ERP da construtora.

Stack: Angular + .NET

**Premissa fundamental:** O TRS so e implantado quando o CRM ja esta 100% implantado e
operacional. A sequencia e sempre CRM -> TRS -> PVD.

---

## Funcionalidades Principais

### Espelho de Vendas
- Visualizacao das unidades disponiveis (livre, reservada, vendida, bloqueada)
- Suporte a empreendimentos verticais (apartamentos, salas) e horizontais (loteamentos)
- Atualizacao em tempo real durante o processo de proposta

### Simulacao de Propostas
- Motor de calculo financeiro para simulacao de diferentes planos de pagamento
- Configuracao de: entrada, parcelas mensais, parcelas intermediarias (baloes), chaves
- Indexadores de correcao (INCC, IGP-M, IPCA, prefixado, etc.)
- Modelos de amortizacao (SAC, Tabela Price, etc.)
- Calculadora de rentabilidade por operacao
- Virada de tabela de vendas automatizada (mudanca de preco/condicao ao longo do tempo)

### Cadastro de Proponentes e Fiadores
- Registro completo de compradores: dados pessoais, CPF, estado civil, documentos
- Suporte a multiplos proponentes (casal, varios compradores)
- Logica de conjuge: o conjuge nao e tratado como proponente principal — ele tem
  vinculo especifico (estado civil casado) e tags proprias no contrato
- Cadastro de fiadores com documentacao completa

### Aprovacao de Documentos e Credito
- Fluxo de envio e aprovacao de documentacao do comprador
- Analise de credito integrada ao processo
- Status de aprovacao rastreavel

### Gestao de Contratos e Tagueamento
- Templates de contrato em formato Word com variaveis dinamicas (tags)
- Tags sao marcadas no documento Word (geralmente destacadas em amarelo pelo cliente)
- O consultor faz o tagueamento: substitui os campos variaveis pelas tags do sistema
- Tags principais: dados do proponente, dados do imovel, valores, datas, signatarios
- Logica condicional nas tags (ex: bloco de conjuge aparece apenas se estado civil = casado)
- Geracao automatica do contrato preenchido a partir dos dados da proposta
- Suporte a tabelas dinamicas (ex: quadro de parcelas) — tagueamento mais complexo

### Assinatura Digital
- Assinatura digital de contratos integrada
- Cadastro de signatarios (representantes da incorporadora) por produto/empreendimento
- Cadastro de testemunhas (assinam o contrato)
- Cadastro de observadores (recebem o contrato mas nao assinam, nao tem acao)
- Signatarios sao definidos por empreendimento (cada produto pode ter signatarios diferentes)

### Rateio de Comissao
- Configuracao de regras de comissao por empreendimento/canal de venda
- Perfis de comissionado: corretor, imobiliaria, diretor, gerente, etc.
- Calculo automatico do rateio entre os envolvidos na venda
- Configuracao de valor maximo de comissao disponivel por proposta
- Integracao com sistemas de pagadoria (Agilitas, Montagner) para pagamento aos corretores
- O consultor precisa definir o perfil de comissionado para cada usuario cadastrado no sistema

### Canais de Negocio (Canal de Contrato)
- Define como a comissao vai aparecer no contrato e como sera paga
- Configuracao por tipo de intermediario (corretor autonomo, imobiliaria, etc.)
- Reflete diretamente no campo "Receber da Comissao" na proposta

### Integracao com ERPs
- Envio da venda aprovada ao ERP da construtora (Mega ou UAU da Senior, entre outros)
- Integracao unidirecional: Hypnobox -> ERP (alteracoes no ERP nao voltam automaticamente)
- Para reenvio/correcao: cancelar a venda no ERP e reenviar da Hypnobox (gera novo codigo de venda)
- Excecao: Mega permite cancelamento direto pela Hypnobox
- De-para (depara): tabela de mapeamento de codigos entre Hypnobox e ERP do cliente
  (ex: codigo do produto no Hypnobox x codigo no Mega)
- Indices/indexadores precisam ser cadastrados tanto no Hypnobox quanto no ERP com de-para

---

## Fluxo de Implantacao

1. **Configuracao do produto/empreendimento** — nome, unidades, tipologias, valores
2. **Configuracao da tabela de vendas** — planos de pagamento, indexadores, amortizacao
3. **Regras de comissao** — percentuais, limites, perfis de comissionado
4. **Cadastro de signatarios e testemunhas** — por empreendimento, dados completos (nome, email, CPF, cargo)
5. **Tagueamento do contrato** — mapeamento das variaveis do contrato Word para as tags do sistema
6. **Configuracao de canais de negocio** — como a comissao reflete no contrato
7. **Configuracao da integracao com ERP** — de-para, credenciais, teste de envio
8. **Configuracao de perfis de comissionado** — usuario a usuario (trabalho manual)
9. **Teste ponta a ponta** — proposta simulada, aprovacao, geracao de contrato, assinatura, envio ao ERP

### Ferramentas necessarias
- Excel e Word (montagem de planilhas de importacao e templates de contrato)
- Acesso ao SharePoint interno (materiais de apoio, modelos)
- Wiki da Senior (manuais, passo a passo, artigos)
- VPN Senior (para acesso a Wiki)

---

## Dores que o TRS Resolve

| Dor do mercado | Solucao no TRS |
|---|---|
| Contrato feito manualmente em Word, com erros | Geracao automatica com tagueamento |
| Assinatura fisica com correio/cartorio | Assinatura digital integrada |
| Comissao calculada em planilha, gerando conflito | Rateio automatico e rastreavel |
| Venda registrada no ERP manualmente | Integracao automatica Hypnobox -> ERP |
| Falta de visibilidade das unidades disponíveis | Espelho de vendas em tempo real |
| Simulacoes de proposta feitas em calculadora | Motor financeiro com multiplos planos |
| Ciclo de venda longo por burocracia de documentacao | Fluxo digital integrado end-to-end |

## Dores que Ainda Pode Resolver (Oportunidades)

- Cancelamento pela Hypnobox para todos os ERPs (hoje apenas Mega tem essa funcionalidade)
- Atualizacao bidirecional com ERPs (hoje unidirecional)
- Automacao do de-para (hoje configuracao manual e trabalhosa)
- Validacao automatica de estado civil na geracao do contrato (hoje depende de tagueamento condicional correto)
- Modulo de aprovacao de credito mais robusto com bureau externo

---

## Pontos Criticos de Conhecimento

### Tagueamento de Contratos
E uma das etapas mais tecnicas e sensiveis. O contrato Word do cliente precisa ter cada
campo variavel substituido por uma tag do sistema. Erros no tagueamento resultam em:
- Campos em branco no contrato gerado
- Dados incorretos (ex: dados do conjuge onde deveria estar o proponente)
- Contrato nao sendo gerado (tag invalida)

Regra do conjuge: o conjuge nao e um "proponente" no sentido das tags — ele vem a partir
do vinculo. A validacao de estado civil = casado e necessaria para que o bloco de dados
do conjuge apareca no contrato.

### De-para com ERP
Cada cliente tem seu proprio codigo de produtos, indexadores e outros campos no ERP.
A configuracao do de-para e manual e precisa ser feita por consultor. Erros no de-para
causam falha no envio da venda ao ERP.

### Reenvio de Proposta ao ERP
Nao e possivel atualizar uma proposta ja enviada ao ERP. O fluxo e:
1. Cancelar a venda no ERP
2. Fazer o ajuste na Hypnobox
3. Reenviar — sera gerado um novo codigo de venda
