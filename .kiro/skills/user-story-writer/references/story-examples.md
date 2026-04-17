# Exemplos de Stories — Referência

Exemplos práticos baseados nos PRDs existentes no repositório.
Use como referência de qualidade e formato ao gerar novas stories.

---

## Exemplo 1 — Story completa (origem: RF05 do PRD Assinatura de Vistoria PVD)

```
TIPO: Story
PRIORIDADE: Must
MÓDULO: Hypnobox PVD — Pós-venda
RF ORIGEM: RF05

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

TÍTULO: Enviar documento de vistoria para assinatura digital do comprador

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

HISTÓRIA DO USUÁRIO:
*Como* coordenador de vistoria,
*quero* enviar o termo de vistoria gerado para assinatura digital do comprador diretamente
pelo PVD,
*para* que o processo de entrega de chaves seja formalizado sem sair do sistema e com
rastreabilidade completa.

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

CONTEXTO:
Hoje, após registrar a vistoria no PVD, o coordenador precisa enviar o termo de vistoria
manualmente por email ou WhatsApp, sem rastreabilidade no sistema. Isso gera risco jurídico
para a construtora em casos de disputa. A integração com plataformas de assinatura digital
fecha essa lacuna e centraliza o processo no PVD.

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

ESCOPO:

✅ Inclui:
- Botão de envio para assinatura no fluxo de conclusão de vistoria
- Seleção da plataforma de assinatura configurada para o empreendimento
- Configuração automática do comprador como signatário obrigatório
- Envio do envelope com notificação por email ao comprador
- Registro do ID do envelope vinculado à vistoria

❌ Não inclui:
- Configuração das credenciais da plataforma de assinatura (coberto em task técnica separada)
- Envio por WhatsApp (escopo de story separada — Should)
- Suporte a múltiplas plataformas simultâneas no mesmo empreendimento

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

CRITÉRIOS DE ACEITE:
- [ ] Ao acionar "Concluir Vistoria", o sistema exibe modal para seleção de template antes do envio
- [ ] Após confirmar, o sistema cria e envia o envelope via API da plataforma configurada
- [ ] O comprador recebe email de notificação com link para assinatura
- [ ] O status da vistoria muda para "Aguardando Assinatura" após o envio com sucesso
- [ ] Se a API da plataforma retornar erro, o sistema exibe mensagem de erro e mantém o status anterior da vistoria
- [ ] Se o comprador não tiver email cadastrado, o sistema bloqueia o envio e exibe alerta ao operador

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

CRITÉRIOS DE PRONTO (DoR):
- [ ] História revisada pelo PO
- [ ] Mockup do modal de envio aprovado
- [ ] Regras de signatários por empreendimento documentadas
- [ ] Credenciais de sandbox da plataforma de assinatura disponíveis para dev
- [ ] Casos de borda documentados nos critérios de aceite

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

LINKS E REFERÊNCIAS:
- PRD: prd-assinatura-termo-vistoria-pvd.md
- Protótipo: ⚠️ Necessário validar com Design
- Docs Clicksign API: https://developers.clicksign.com/
```

---

## Exemplo 2 — Task Técnica

```
TIPO: Task
PRIORIDADE: Must
MÓDULO: Hypnobox PVD — Pós-venda

TÍTULO: Configurar endpoint de webhook para receber eventos de assinatura da Clicksign

DESCRIÇÃO:
Criar endpoint no backend do PVD para receber notificações de eventos da Clicksign
(assinatura concluída, cancelamento, expiração). O endpoint deve validar a autenticidade
da requisição (HMAC), processar o evento e atualizar o status do envelope e da vistoria
correspondente no banco de dados.

CRITÉRIOS DE PRONTO:
- [ ] Endpoint criado e documentado (rota, método, payload esperado)
- [ ] Validação de autenticidade implementada (HMAC ou token de segurança da Clicksign)
- [ ] Atualização de status do envelope funcionando para os eventos: assinado, cancelado, expirado
- [ ] Fallback de polling implementado para casos de webhook não recebido
- [ ] Logs de todos os eventos recebidos com timestamp e payload

DEPENDÊNCIAS:
- Story: "Enviar documento de vistoria para assinatura digital" deve estar em andamento
- Credenciais de sandbox da Clicksign disponíveis
```

---

## Exemplo 3 — Story com estimativa

```
TIPO: Story
PRIORIDADE: Must
MÓDULO: Logística — Rastreamento de Pedidos
RF ORIGEM: RF01
ESTIMATIVA: 5 pontos

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

TÍTULO: Exibir mapa interativo com localização em tempo real do pedido

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

HISTÓRIA DO USUÁRIO:
Como cliente final,
quero visualizar no mapa onde está o meu pedido em tempo real,
para que eu possa planejar meu dia sem precisar ligar para o atendimento.

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

CONTEXTO:
Hoje o cliente não tem visibilidade sobre a localização do pedido em trânsito, gerando
~450 tickets/mês de "onde está meu pedido". A exibição do mapa em tempo real elimina
a principal causa de contato com o suporte.

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

ESCOPO:

✅ Inclui:
- Mapa com pin da localização atual do pedido (atualizado a cada 60 segundos)
- Indicador visual do destino final (endereço de entrega)
- ETA dinâmico exibido acima do mapa

❌ Não inclui:
- Histórico de rota percorrida (escopo de melhoria futura)
- Mapa offline / modo sem conexão
- Notificações push (coberto em módulo separado)

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

CRITÉRIOS DE ACEITE:
- [ ] O mapa exibe o pin de localização do pedido na posição correta ao carregar a página
- [ ] A posição do pin é atualizada automaticamente a cada 60 segundos sem recarregar a página
- [ ] O ETA é exibido no formato "Hoje, HH:mm" e atualizado junto com a posição
- [ ] Se o pedido ainda não saiu para entrega, o mapa exibe o armazém de origem com status "Em preparação"
- [ ] Se a API de geolocalização estiver indisponível, o sistema exibe mensagem "Localização temporariamente indisponível" sem quebrar a página

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

CRITÉRIOS DE PRONTO (DoR):
- [ ] História revisada pelo PO
- [ ] Mockup do componente de mapa aprovado
- [ ] API de geolocalização definida (Google Maps, Mapbox, ou outra)
- [ ] Frequência de atualização validada com engenharia (custo vs. UX)

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

LINKS E REFERÊNCIAS:
- PRD: prd-rastreamento-pedidos-tempo-real.md
- Protótipo: ⚠️ Necessário validar com Design
```

---

## Exemplo 4 — Bug

```
TIPO: Bug
MÓDULO: Hypnobox PVD — Pós-venda
SEVERIDADE: Alto

TÍTULO: Status da vistoria permanece "Aguardando Assinatura" após assinatura confirmada pela Clicksign

COMPORTAMENTO ATUAL:
Após o comprador assinar o termo via Clicksign, o webhook é recebido corretamente
(confirmado em logs), mas o status da vistoria não é atualizado no PVD. O operador
precisa atualizar manualmente.

COMPORTAMENTO ESPERADO:
Ao receber o webhook de assinatura completa, o sistema deve atualizar automaticamente
o status da vistoria para "Concluída".

PASSOS PARA REPRODUZIR:
1. Criar vistoria e enviar envelope via Clicksign (sandbox)
2. Assinar o documento como comprador
3. Verificar o status da vistoria no PVD
4. Status permanece "Aguardando Assinatura" — não atualiza

AMBIENTE:
- Versão: [necessário preencher]
- Navegador: Chrome 124

EVIDÊNCIAS:
- Log do webhook recebido: [anexar]
- Screenshot do status incorreto: [anexar]
```
