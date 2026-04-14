# PRD — Assinatura Digital de Termo de Vistoria

## Metadados do Documento

| Campo | Valor |
|---|---|
| Produto / Módulo | Hypnobox PVD — Pós-venda |
| Funcionalidade | Assinatura Digital de Termo de Vistoria |
| Tipo | Nova Jornada |
| Direcionador Estratégico | Cobertura + Sustentação |
| Status | Em Definição |
| Product Owner | Necessário validar |
| Stakeholders | Time de Produto PVD, Engenharia, CS, Implantação, Jurídico |
| Data de criação | 13/04/2026 |
| Última atualização | 13/04/2026 |
| Versão | v0.1 |

---

## 1. Visão do Produto

**O que é?**
Um fluxo integrado ao módulo de Vistoria do PVD que permite ao administrador cadastrar templates de termos tagueados, gerar documentos preenchidos automaticamente com dados da vistoria e do cliente, e enviá-los para assinatura digital via plataformas como Clicksign, DocuSign ou D4Sign — tornando a assinatura do comprador um requisito obrigatório para a conclusão da vistoria.

**Para quem?**
Equipe de backoffice de construtoras/incorporadoras (gestores de vistoria, coordenadores de entrega de chaves) e compradores de imóveis (clientes finais).

**Qual o valor entregue?**
Elimina o processo manual e em papel de coleta de assinatura no termo de vistoria, garantindo validade jurídica, rastreabilidade e agilidade na entrega de chaves. Reduz retrabalho, litígios e custos operacionais da construtora.

**Resumo executivo:**
Hoje, o processo de vistoria no PVD registra ocorrências digitalmente, mas a formalização do aceite do comprador ainda depende de documentos físicos ou processos externos à plataforma. Isso gera risco jurídico, perda de rastreabilidade e fricção operacional. A integração de assinatura digital ao fluxo de vistoria fecha essa lacuna crítica, posicionando o PVD como solução end-to-end para entrega de imóveis — diferencial competitivo relevante frente a concorrentes do setor.

---

## 2. Problema e Evidências

### 2.1 Estado Atual (As-Is)

O módulo de Vistoria do PVD permite agendar vistorias, registrar ocorrências (punch list) e gerar relatórios. Porém, ao concluir a vistoria, não existe um fluxo nativo para:
- Geração automática do termo de vistoria preenchido com dados do cliente e da vistoria
- Envio do documento para assinatura digital do comprador
- Bloqueio da conclusão da vistoria até que a assinatura seja obtida

O workaround atual das construtoras é: imprimir o termo, coletar assinatura física no ato da vistoria ou enviar por email/WhatsApp de forma manual, sem rastreabilidade no sistema.

### 2.2 Evidências de Dor

| Fonte da Evidência | Descrição |
|---|---|
| Feedback de clientes | Construtoras relatam dificuldade em comprovar aceite do comprador em casos de disputa jurídica pós-entrega |
| Time de CS / Implantação | Processo de coleta de assinatura é citado como gap recorrente durante onboarding de clientes PVD |
| Time de Vendas | Feature de assinatura digital é demandada em RFPs e comparações com concorrentes |
| Suporte / Tickets | ⚠️ Necessário validar volume de chamados relacionados a este tema com o time de suporte |

### 2.3 Benchmark (Concorrência)

| Concorrente | Funcionalidade Observada |
|---|---|
| Sienge (Softplan) | Módulo de entrega de chaves com geração de termo e integração com assinatura digital (D4Sign) |
| Facilita (CRM imobiliário) | Geração de documentos com variáveis dinâmicas e envio para assinatura via Clicksign |
| Construtor de Vendas | Fluxo de vistoria com checklist digital e termo de entrega, sem assinatura digital nativa (gap identificado) |
| Loft / Plataformas PropTech | Assinatura digital integrada ao processo de entrega, com notificação automática ao comprador |

> ⚠️ Dados de benchmark baseados em informações públicas disponíveis. Necessário validar com time de Produto e Vendas.

---

## 3. Objetivos de Negócio

| # | Objetivo | Métrica Alvo |
|---|---|---|
| O1 | Eliminar o processo manual de coleta de assinatura no termo de vistoria | 100% das vistorias concluídas com termo assinado digitalmente (meta pós-adoção) |
| O2 | Reduzir risco jurídico das construtoras na entrega de imóveis | Necessário validar baseline com time jurídico / CS |
| O3 | Aumentar adoção do módulo de Vistoria do PVD | +X% de construtoras ativas no módulo de vistoria (necessário validar baseline) |
| O4 | Reduzir chamados e retrabalho relacionados a termos de vistoria | -40% em chamados sobre documentação de vistoria (necessário validar baseline) |
| O5 | Posicionar o PVD como solução end-to-end de entrega de imóveis | Menção em RFPs ganhos como diferencial competitivo |

---

## 4. Pricing

### Custos Envolvidos

| Item | Descrição | Modelo |
|---|---|---|
| Clicksign | Plataforma de assinatura digital — cobra por envelope enviado | Pay-per-use ou pacote mensal |
| DocuSign | Plataforma de assinatura digital — cobra por envelope ou por usuário/mês | Pay-per-use ou licença |
| D4Sign | Plataforma brasileira de assinatura digital — cobra por documento ou pacote | Pay-per-use ou pacote |
| Infraestrutura de armazenamento | Templates e documentos gerados precisam ser armazenados | Custo de storage (S3 ou equivalente) |

### Modelos de Precificação Possíveis para o Cliente

- **Incluso no plano PVD:** absorver custo de envelopes até um limite mensal por cliente
- **Add-on pago:** cobrar por volume de envelopes enviados (repasse do custo da plataforma + margem)
- **Integração bring-your-own:** cliente usa sua própria conta na plataforma de assinatura (Hypnobox apenas integra via API)

> ⚠️ Necessário validar com time de Produto, Comercial e Financeiro qual modelo adotar. A opção "bring-your-own" reduz custo operacional da Hypnobox e é comum em integrações B2B.

---

## 5. Personas

| Persona | Perfil | Necessidade Principal | Valor Recebido |
|---|---|---|---|
| Administrador do Sistema (Construtora) | Gestor de TI ou coordenador de implantação da construtora | Cadastrar e gerenciar templates de termos de vistoria com variáveis dinâmicas | Autonomia para configurar documentos sem depender de suporte técnico |
| Coordenador de Vistoria / Entrega | Responsável pela operação de vistorias e entrega de chaves | Enviar o termo correto para assinatura ao finalizar a vistoria, sem sair do sistema | Fluxo unificado, sem troca de ferramentas, com rastreabilidade completa |
| Comprador do Imóvel (Cliente Final) | Pessoa física que adquiriu o imóvel e está recebendo as chaves | Assinar o termo de forma simples, de qualquer dispositivo, sem burocracia | Experiência digital, sem necessidade de comparecer fisicamente para assinar |
| Gestor de Pós-venda | Diretor ou gerente responsável pela operação de pós-venda | Acompanhar status de assinaturas pendentes e garantir que nenhuma vistoria fique em aberto | Visibilidade e controle do processo sem depender de planilhas externas |

---

## 5. Estrutura do Produto (Módulos / Blocos)

### Módulo 1 — Gestão de Templates (Administrador)
Permite ao administrador cadastrar, versionar e gerenciar os templates de termos de vistoria com tags dinâmicas.

Funcionalidades:
- Upload de template em formato DOCX com tags no padrão `{{variavel}}`
- Listagem de templates cadastrados com status (ativo/inativo)
- Visualização prévia do template com dados fictícios
- Ativação/desativação de templates
- Vínculo de template a empreendimento específico ou uso global
- Documentação das tags disponíveis (dicionário de variáveis)

### Módulo 2 — Geração e Seleção de Documento
Ao concluir uma vistoria, o operador seleciona o template desejado e o sistema gera o documento preenchido automaticamente.

Funcionalidades:
- Seleção do template disponível para aquela vistoria/empreendimento
- Preenchimento automático das tags com dados da vistoria, cliente e imóvel
- Pré-visualização do documento gerado antes do envio
- Geração do PDF final para envio

### Módulo 3 — Envio para Assinatura Digital
Integração com plataformas de assinatura digital para envio do envelope ao comprador.

Funcionalidades:
- Seleção da plataforma de assinatura (Clicksign, DocuSign ou D4Sign)
- Configuração dos signatários (comprador obrigatório + opcionais: representante da construtora, testemunhas)
- Envio do envelope com notificação por email e/ou WhatsApp ao comprador
- Registro do envelope enviado vinculado à vistoria

### Módulo 4 — Acompanhamento e Gestão do Envelope
Permite ao operador monitorar o status da assinatura e tomar ações sobre o envelope.

Funcionalidades:
- Painel de status do envelope (aguardando assinatura, assinado, cancelado, expirado)
- Cancelamento do envelope ativo
- Reenvio de notificação ao signatário
- Envio de novo envelope (após cancelamento)
- Download do documento assinado

### Módulo 5 — Bloqueio de Conclusão da Vistoria
Regra de negócio que impede a marcação da vistoria como "concluída" sem assinatura do comprador.

Funcionalidades:
- Validação de assinatura obrigatória antes de permitir status "Concluída"
- Exibição de alerta/bloqueio com status atual da assinatura
- Liberação automática do status ao receber confirmação de assinatura da plataforma (webhook)

---

## 6. Fluxo do Usuário

### 6.1 Fluxo Principal (Happy Path)

1. Administrador acessa **Configurações > Templates de Vistoria** e faz upload de um arquivo DOCX tagueado
2. Sistema valida as tags do documento e exibe dicionário de variáveis reconhecidas
3. Administrador ativa o template e vincula ao empreendimento
4. Coordenador de vistoria realiza a vistoria normalmente no PVD (checklist, ocorrências, fotos)
5. Ao acionar "Concluir Vistoria", o sistema exibe modal de seleção de template
6. Coordenador seleciona o template desejado entre os disponíveis para aquele empreendimento
7. Sistema gera preview do documento preenchido com dados da vistoria e do cliente
8. Coordenador confirma e seleciona a plataforma de assinatura (se houver mais de uma configurada)
9. Sistema envia o envelope para o comprador via email/WhatsApp com link de assinatura
10. Status da vistoria muda para **"Aguardando Assinatura"** — não pode ser marcada como concluída
11. Comprador recebe notificação, acessa o link e assina o documento digitalmente
12. Plataforma de assinatura notifica o PVD via webhook
13. Status da vistoria muda automaticamente para **"Concluída"**
14. Documento assinado fica disponível para download no backoffice e no Portal do Cliente

### 6.2 Fluxos Alternativos

- **Comprador não assina dentro do prazo:** sistema exibe alerta no painel; operador pode reenviar notificação ou cancelar o envelope e enviar novo
- **Cancelamento de envelope:** operador cancela o envelope ativo, seleciona novo template (ou o mesmo) e reenvia
- **Vistoria com múltiplos compradores (co-proprietários):** todos os compradores cadastrados devem assinar (configurável)
- **Plataforma de assinatura indisponível:** sistema exibe erro e permite tentar novamente; vistoria permanece em "Aguardando Assinatura"
- **Template sem tags reconhecidas:** sistema alerta o administrador no momento do upload e não permite ativação

---

## 7. Requisitos Funcionais

---

### RF01 — Upload e Gestão de Templates

| Campo | Descrição |
|---|---|
| Descrição | O sistema deve permitir que o administrador faça upload de templates DOCX com tags dinâmicas no formato `{{nome_da_variavel}}` |
| Regras de Negócio | Apenas arquivos .docx são aceitos; tamanho máximo: necessário validar (sugestão: 10MB); o sistema deve validar e listar as tags encontradas no documento; templates inativos não aparecem na seleção durante a vistoria |
| Dados de Entrada | Arquivo DOCX, nome do template, empreendimento(s) vinculado(s), status (ativo/inativo) |
| Dados de Saída | Template cadastrado com ID, lista de tags reconhecidas, preview com dados fictícios |
| Comportamento de Erro | Arquivo inválido: mensagem "Formato não suportado. Envie um arquivo .docx"; tags não reconhecidas: alerta com lista de tags desconhecidas |
| Dependências | Dicionário de variáveis disponíveis (RF02) |
| Prioridade | Must |

---

### RF02 — Dicionário de Variáveis (Tags)

| Campo | Descrição |
|---|---|
| Descrição | O sistema deve manter um dicionário de tags disponíveis para uso nos templates, mapeando cada tag ao dado correspondente no sistema |
| Regras de Negócio | Tags devem cobrir dados de: cliente (nome, CPF, email, telefone), imóvel (bloco, unidade, endereço), vistoria (data, responsável, ocorrências, status), empreendimento (nome, CNPJ da construtora); novas tags podem ser adicionadas por configuração interna |
| Dados de Entrada | N/A (configuração interna do sistema) |
| Dados de Saída | Lista de tags com nome, descrição e exemplo de valor |
| Comportamento de Erro | Tag não mapeada: exibir aviso no upload do template |
| Dependências | Módulo de Vistoria, Cadastro de Clientes, Cadastro de Empreendimentos |
| Prioridade | Must |

---

### RF03 — Geração Automática do Documento

| Campo | Descrição |
|---|---|
| Descrição | Ao selecionar um template durante o fluxo de conclusão de vistoria, o sistema deve gerar automaticamente o documento PDF com todas as tags substituídas pelos dados reais |
| Regras de Negócio | Todas as tags mapeadas devem ser substituídas; tags sem valor disponível devem ser substituídas por campo em branco ou valor padrão configurável; o PDF gerado deve ser idêntico ao DOCX em layout |
| Dados de Entrada | ID do template selecionado, ID da vistoria, ID do cliente |
| Dados de Saída | PDF gerado com dados preenchidos, disponível para preview antes do envio |
| Comportamento de Erro | Falha na geração: mensagem de erro com opção de tentar novamente; log do erro para diagnóstico |
| Dependências | RF01, RF02, Módulo de Vistoria |
| Prioridade | Must |

---

### RF04 — Seleção de Template pelo Operador

| Campo | Descrição |
|---|---|
| Descrição | Ao acionar a conclusão de uma vistoria, o sistema deve exibir modal para seleção do template de termo a ser enviado |
| Regras de Negócio | Exibir apenas templates ativos vinculados ao empreendimento da vistoria (ou templates globais); se houver apenas um template disponível, pré-selecionar automaticamente mas permitir confirmação; se não houver template cadastrado, exibir alerta e bloquear o envio |
| Dados de Entrada | Seleção do template pelo operador |
| Dados de Saída | Template selecionado, preview do documento gerado |
| Comportamento de Erro | Nenhum template disponível: "Nenhum template de termo cadastrado para este empreendimento. Contate o administrador." |
| Dependências | RF01, RF03 |
| Prioridade | Must |

---

### RF05 — Envio para Assinatura Digital

| Campo | Descrição |
|---|---|
| Descrição | O sistema deve enviar o documento gerado para assinatura digital via Clicksign, DocuSign ou D4Sign, configurando os signatários e disparando notificação ao comprador |
| Regras de Negócio | O comprador é sempre signatário obrigatório; outros signatários (representante da construtora, testemunhas) são configuráveis por empreendimento; a plataforma de assinatura é configurada pelo administrador (uma por vez por empreendimento, ou selecionável pelo operador); o envelope deve ter prazo de expiração configurável (sugestão: 30 dias) |
| Dados de Entrada | PDF gerado, lista de signatários com email, plataforma selecionada, prazo de expiração |
| Dados de Saída | ID do envelope na plataforma, status inicial "Aguardando Assinatura", link de acompanhamento |
| Comportamento de Erro | Falha na API da plataforma: mensagem de erro, vistoria permanece em status anterior, possibilidade de retentar |
| Dependências | RF03, RF04, Integração com Clicksign/DocuSign/D4Sign |
| Prioridade | Must |

---

### RF06 — Acompanhamento do Status do Envelope

| Campo | Descrição |
|---|---|
| Descrição | O sistema deve exibir o status atual do envelope de assinatura vinculado à vistoria, atualizado em tempo real via webhook das plataformas |
| Regras de Negócio | Status possíveis: Aguardando Assinatura, Parcialmente Assinado (quando há múltiplos signatários), Assinado, Cancelado, Expirado; atualização via webhook (push) com fallback de polling periódico |
| Dados de Entrada | Webhook da plataforma de assinatura com evento de atualização |
| Dados de Saída | Status atualizado na tela de vistoria, histórico de eventos do envelope |
| Comportamento de Erro | Webhook não recebido: polling a cada X minutos como fallback (necessário definir intervalo) |
| Dependências | RF05, Integração com webhooks das plataformas |
| Prioridade | Must |

---

### RF07 — Cancelamento de Envelope e Reenvio

| Campo | Descrição |
|---|---|
| Descrição | O operador deve poder cancelar um envelope ativo e enviar um novo documento para assinatura |
| Regras de Negócio | Apenas envelopes com status "Aguardando Assinatura" ou "Parcialmente Assinado" podem ser cancelados; ao cancelar, o sistema deve registrar motivo (campo obrigatório); após cancelamento, o operador pode selecionar novo template e reenviar; histórico de envelopes cancelados deve ser mantido |
| Dados de Entrada | Confirmação de cancelamento, motivo do cancelamento |
| Dados de Saída | Envelope cancelado na plataforma, status atualizado, histórico registrado |
| Comportamento de Erro | Falha no cancelamento via API: mensagem de erro, envelope permanece ativo |
| Dependências | RF05, RF06 |
| Prioridade | Must |

---

### RF08 — Bloqueio de Conclusão sem Assinatura

| Campo | Descrição |
|---|---|
| Descrição | O sistema deve impedir que a vistoria seja marcada como "Concluída" enquanto o termo não estiver assinado pelo comprador |
| Regras de Negócio | Status "Concluída" só é liberado após recebimento de confirmação de assinatura de todos os signatários obrigatórios; o botão/ação de conclusão deve estar desabilitado com tooltip explicativo enquanto a assinatura estiver pendente; a liberação deve ocorrer automaticamente via webhook |
| Dados de Entrada | Evento de assinatura completa recebido via webhook |
| Dados de Saída | Status da vistoria atualizado para "Concluída" automaticamente |
| Comportamento de Erro | Webhook não recebido: operador pode acionar atualização manual de status (com log de auditoria) |
| Dependências | RF05, RF06 |
| Prioridade | Must |

---

### RF09 — Disponibilização do Documento Assinado

| Campo | Descrição |
|---|---|
| Descrição | Após a assinatura completa, o documento assinado deve estar disponível para download no backoffice e no Portal do Cliente |
| Regras de Negócio | O documento assinado deve ser armazenado no sistema (não apenas link externo para a plataforma); deve aparecer na seção de Documentos do Portal do Cliente vinculado à vistoria; o backoffice deve permitir download a qualquer momento após a assinatura |
| Dados de Entrada | Documento assinado recebido da plataforma (via webhook ou download após assinatura) |
| Dados de Saída | PDF assinado disponível para download no backoffice e no Portal do Cliente |
| Comportamento de Erro | Falha no download do documento assinado: retry automático; alerta para o operador se falhar após X tentativas |
| Dependências | RF06, Portal do Cliente (módulo de Documentos) |
| Prioridade | Must |

---

### RF10 — Reenvio de Notificação ao Signatário

| Campo | Descrição |
|---|---|
| Descrição | O operador deve poder reenviar a notificação de assinatura ao comprador sem cancelar o envelope |
| Regras de Negócio | Disponível apenas para envelopes com status "Aguardando Assinatura"; limite de reenvios por envelope: necessário validar (sugestão: sem limite, mas com log de cada reenvio); reenvio via email e/ou WhatsApp conforme configuração |
| Dados de Entrada | Ação do operador de reenvio |
| Dados de Saída | Notificação reenviada ao comprador, log registrado |
| Comportamento de Erro | Falha no reenvio: mensagem de erro com opção de tentar novamente |
| Dependências | RF05 |
| Prioridade | Should |

---

## 8. Requisitos Não Funcionais

| ID | Categoria | Requisito |
|---|---|---|
| RNF01 | Performance | Geração do PDF a partir do template deve ocorrer em até 5 segundos para documentos de até 10 páginas |
| RNF02 | Performance | Atualização de status via webhook deve ser processada em até 10 segundos após o evento na plataforma de assinatura |
| RNF03 | Responsividade | Interface do backoffice compatível com desktop (resolução mínima 1280px); Portal do Cliente responsivo para mobile |
| RNF04 | Segurança | Acesso à gestão de templates restrito ao perfil Administrador; acesso ao envio de envelopes restrito a perfis com permissão de gestão de vistoria |
| RNF05 | Segurança | Documentos armazenados com controle de acesso por tenant (isolamento entre construtoras) |
| RNF06 | Auditoria | Log de todas as ações sobre envelopes (envio, cancelamento, reenvio, download) com user_id, timestamp e IP |
| RNF07 | Disponibilidade | Indisponibilidade da plataforma de assinatura não deve bloquear o uso do restante do módulo de vistoria |
| RNF08 | Escalabilidade | Suportar envio simultâneo de envelopes para múltiplas vistorias sem degradação de performance |
| RNF09 | Armazenamento | Documentos assinados devem ser armazenados por no mínimo 5 anos (necessário validar com jurídico) |
| RNF10 | Compatibilidade | Integração com no mínimo uma plataforma de assinatura no MVP (sugestão: Clicksign por ser a mais adotada no mercado imobiliário brasileiro) |

---

## 9. Compliance, LGPD e Requisitos Legais

### 9.1 Dados Sensíveis Envolvidos

| Dado | Classificação | Finalidade |
|---|---|---|
| Nome completo do comprador | Dado pessoal | Preenchimento do termo |
| CPF do comprador | Dado pessoal | Identificação no termo e na plataforma de assinatura |
| Email do comprador | Dado pessoal | Envio da notificação de assinatura |
| Telefone do comprador | Dado pessoal | Envio via WhatsApp (se configurado) |
| Dados do imóvel | Dado não pessoal | Preenchimento do termo |
| Documento assinado (PDF) | Dado pessoal (contém dados do comprador) | Comprovação de aceite da vistoria |

### 9.2 Requisitos de Conformidade

| Requisito | Descrição |
|---|---|
| Base legal (LGPD) | Execução de contrato (Art. 7º, V) — o comprador já possui relação contratual com a construtora; o termo de vistoria é parte da execução desse contrato |
| Trilha de auditoria | Log completo de todas as ações sobre o envelope com user_id, timestamp e IP |
| Compartilhamento com terceiros | Dados do comprador são enviados à plataforma de assinatura (Clicksign/DocuSign/D4Sign) — necessário garantir que essas plataformas possuem DPA (Data Processing Agreement) e estão em conformidade com LGPD |
| Retenção de dados | Documentos assinados devem ser retidos pelo prazo legal (mínimo 5 anos — validar com jurídico) |
| Direitos do titular | O comprador deve poder acessar o documento assinado via Portal do Cliente; exclusão de dados deve respeitar prazo de retenção legal |
| Segurança | Documentos armazenados com criptografia em repouso e em trânsito (TLS 1.2+) |
| Validade jurídica | Assinatura digital via plataformas certificadas (ICP-Brasil ou equivalente aceito) garante validade jurídica conforme MP 2.200-2/2001 e Lei 14.063/2020 |

> ⚠️ Classificação de risco LGPD: **MÉDIO** — dados pessoais são compartilhados com plataformas terceiras. Mitigação: exigir DPA assinado com cada plataforma de assinatura integrada.

---

## 10. Entregáveis

| Componente | Descrição da Entrega |
|---|---|
| Interface (UI) — Backoffice | Tela de gestão de templates (upload, listagem, ativação); modal de seleção de template no fluxo de vistoria; painel de status do envelope na tela de vistoria; ações de cancelamento, reenvio e download |
| Interface (UI) — Portal do Cliente | Documento assinado disponível na seção de Documentos do portal |
| Backend / API | Serviço de geração de PDF a partir de DOCX tagueado; integração com APIs de Clicksign, DocuSign e D4Sign (envio, cancelamento, reenvio, webhook); armazenamento de documentos; lógica de bloqueio de status de vistoria |
| Webhooks | Endpoints para recebimento de eventos das plataformas de assinatura |
| Dicionário de Tags | Documentação interna das variáveis disponíveis para uso nos templates |
| Documentação | Help online para administradores (como criar templates tagueados); release notes; material de treinamento para implantação |

---

## 11. Cenários de Teste (QA)

### 11.1 Cenários Positivos (Happy Path)

| # | Cenário | Condições | Resultado Esperado |
|---|---|---|---|
| C01 | Upload de template válido | DOCX com tags reconhecidas, tamanho dentro do limite | Template cadastrado com sucesso, tags listadas, preview disponível |
| C02 | Geração de documento | Template ativo, vistoria com todos os dados preenchidos | PDF gerado com todas as tags substituídas corretamente |
| C03 | Envio de envelope | Template selecionado, comprador com email cadastrado, plataforma configurada | Envelope enviado, status "Aguardando Assinatura", notificação recebida pelo comprador |
| C04 | Assinatura pelo comprador | Comprador acessa link e assina | Status atualizado para "Assinado", vistoria marcada como "Concluída" automaticamente, documento disponível para download |
| C05 | Cancelamento e reenvio | Envelope ativo, operador cancela e seleciona novo template | Envelope cancelado, novo envelope enviado com sucesso |
| C06 | Reenvio de notificação | Envelope aguardando assinatura | Notificação reenviada ao comprador, log registrado |
| C07 | Download do documento assinado | Vistoria concluída com assinatura | PDF assinado disponível para download no backoffice e no Portal do Cliente |

### 11.2 Cenários Negativos (Edge Cases)

| # | Cenário | Condições | Resultado Esperado |
|---|---|---|---|
| C08 | Upload de arquivo inválido | Arquivo .pdf ou .xlsx enviado | Mensagem de erro: "Formato não suportado. Envie um arquivo .docx" |
| C09 | Template com tags desconhecidas | DOCX com `{{campo_inexistente}}` | Alerta com lista de tags não reconhecidas; template não pode ser ativado |
| C10 | Tentativa de concluir vistoria sem as
