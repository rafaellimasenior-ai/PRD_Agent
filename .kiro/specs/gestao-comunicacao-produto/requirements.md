# Documento de Requisitos — Gestão de Comunicação via Produto

## Introdução

Este documento descreve os requisitos funcionais e de qualidade para o módulo de **Gestão de Comunicação via Produto**, um produto novo a ser construído na plataforma **Senior X**. O módulo permitirá que PMAs (Product Marketing Analysts) cadastrem, gerenciem e monitorem campanhas de comunicação visual (banners/imagens com links) diretamente pela interface do produto, eliminando a dependência de alterações no código-fonte do workspace.

---

## Glossário

- **PMA**: Product Marketing Analyst — profissional responsável por criar e gerenciar campanhas de comunicação de produto.
- **Campanha**: Conjunto de uma ou mais ações de comunicação (imagens com links) associadas a um produto, período e tema.
- **Ação de Comunicação**: Unidade mínima de campanha — uma imagem com link, data de início, data de fim, tag de tema e tipo (gratuito ou upsell).
- **Produto Gratuito**: Produto disponível sem custo adicional ao cliente; permite até 5 ações ativas simultaneamente.
- **Upsell**: Produto ou funcionalidade paga/premium; permite apenas 1 ação ativa simultaneamente.
- **Tag de Tema**: Classificação temática da ação de comunicação (ex: "Novidade", "Promoção", "Treinamento").
- **Engajamento**: Registro de cliques realizados pelos usuários finais nos links das ações de comunicação.
- **Senior X**: Plataforma web/desktop da Senior Sistemas, base tecnológica deste produto.
- **Workspace**: Ambiente configurado na plataforma Senior X para um cliente específico.
- **Sistema**: O módulo de Gestão de Comunicação via Produto na plataforma Senior X.
- **Painel de Monitoramento**: Tela de visão geral com métricas e status das campanhas por produto.

---

## Requisitos

### Requisito 1 — Cadastro de Ação de Comunicação

**User Story:** Como PMA, quero cadastrar ações de comunicação (imagens com links) por produto, para que eu possa veicular campanhas visuais sem depender de alterações no código-fonte.

#### Critérios de Aceitação

1. WHEN um PMA acessa o módulo de Gestão de Comunicação, THE Sistema SHALL exibir um formulário de cadastro de ação de comunicação com os campos: imagem, URL do link, data de início, data de fim, tag de tema e tipo (gratuito ou upsell).
2. WHEN um PMA submete o formulário com todos os campos obrigatórios preenchidos corretamente, THE Sistema SHALL criar a ação de comunicação e associá-la ao produto selecionado.
3. WHEN um PMA tenta cadastrar uma ação do tipo "produto gratuito" e já existem 5 ações ativas para aquele produto, THE Sistema SHALL bloquear o cadastro e exibir a mensagem: "Limite de 5 ações ativas para produto gratuito atingido."
4. WHEN um PMA tenta cadastrar uma ação do tipo "upsell" e já existe 1 ação ativa para aquele produto, THE Sistema SHALL bloquear o cadastro e exibir a mensagem: "Limite de 1 ação ativa para upsell atingido."
5. WHEN um PMA submete o formulário com campos obrigatórios ausentes ou inválidos, THE Sistema SHALL destacar os campos com erro e exibir mensagens de validação descritivas sem submeter o formulário.
6. WHEN a data de fim informada é anterior à data de início, THE Sistema SHALL rejeitar o formulário e exibir a mensagem: "A data de fim deve ser posterior à data de início."
7. WHEN um PMA faz upload de uma imagem, THE Sistema SHALL aceitar apenas arquivos nos formatos PNG, JPG e GIF com tamanho máximo de 2 MB.
8. IF o upload de imagem falhar por erro de rede ou servidor, THEN THE Sistema SHALL exibir mensagem de erro descritiva e permitir nova tentativa sem perda dos demais dados preenchidos.

---

### Requisito 2 — Gerenciamento de Ações de Comunicação

**User Story:** Como PMA, quero editar, ativar, desativar e excluir ações de comunicação cadastradas, para que eu possa manter as campanhas atualizadas e relevantes.

#### Critérios de Aceitação

1. WHEN um PMA acessa a listagem de ações de comunicação de um produto, THE Sistema SHALL exibir todas as ações cadastradas com status (ativa, inativa, expirada), imagem em miniatura, link, período e tag.
2. WHEN um PMA seleciona uma ação para editar, THE Sistema SHALL carregar o formulário preenchido com os dados atuais da ação e permitir alteração de todos os campos.
3. WHEN um PMA salva a edição de uma ação, THE Sistema SHALL validar as regras de limite de ações ativas antes de persistir as alterações.
4. WHEN um PMA desativa uma ação ativa, THE Sistema SHALL alterar o status da ação para "inativa" imediatamente e liberar a vaga no limite de ações ativas do produto.
5. WHEN um PMA exclui uma ação de comunicação, THE Sistema SHALL solicitar confirmação antes de remover permanentemente o registro.
6. WHEN a data de fim de uma ação é atingida, THE Sistema SHALL alterar automaticamente o status da ação para "expirada" sem intervenção manual.
7. WHILE uma ação está com status "expirada", THE Sistema SHALL impedir sua reativação direta e exigir atualização da data de fim para uma data futura antes de reativar.

---

### Requisito 3 — Monitoramento de Ações por Produto (Visão Geral)

**User Story:** Como PMA, quero visualizar um painel de monitoramento com visão geral das ações por produto, para que eu possa acompanhar o desempenho das campanhas em andamento.

#### Critérios de Aceitação

1. WHEN um PMA acessa o Painel de Monitoramento, THE Sistema SHALL exibir uma listagem consolidada de todos os produtos com o número de ações ativas, inativas e expiradas por produto.
2. WHEN um PMA seleciona um produto no painel, THE Sistema SHALL exibir o detalhamento das ações daquele produto com status, período, tag e total de cliques.
3. THE Sistema SHALL atualizar os dados do Painel de Monitoramento com frequência máxima de 1 hora em relação aos dados de engajamento.
4. WHEN não há ações cadastradas para um produto, THE Sistema SHALL exibir o estado vazio com mensagem orientativa para cadastrar a primeira ação.

---

### Requisito 4 — Dados de Engajamento (Cliques)

**User Story:** Como PMA, quero visualizar dados de engajamento de cliques nos links das ações de comunicação, para que eu possa medir a efetividade das campanhas.

#### Critérios de Aceitação

1. WHEN um usuário final clica no link de uma ação de comunicação ativa, THE Sistema SHALL registrar o evento de clique com timestamp, identificador da ação e identificador do produto.
2. WHEN um PMA acessa os dados de engajamento de uma ação, THE Sistema SHALL exibir o total de cliques, a série temporal de cliques por dia e a taxa de cliques em relação ao período ativo da ação.
3. THE Sistema SHALL armazenar os dados de engajamento por no mínimo 12 meses após a expiração da ação.
4. IF o registro de clique falhar por indisponibilidade temporária, THEN THE Sistema SHALL armazenar o evento em fila de reprocessamento e garantir a persistência sem perda de dados.
5. WHEN um PMA exporta os dados de engajamento de uma ação, THE Sistema SHALL gerar um arquivo CSV com as colunas: data, total de cliques do dia, acumulado.

---

### Requisito 5 — Filtros e Busca

**User Story:** Como PMA, quero filtrar as ações de comunicação por produto, tipo de ação, período e tag, para que eu possa localizar e analisar campanhas específicas com agilidade.

#### Critérios de Aceitação

1. WHEN um PMA aplica filtro por produto, THE Sistema SHALL exibir apenas as ações associadas ao produto selecionado.
2. WHEN um PMA aplica filtro por tipo de ação (gratuito ou upsell), THE Sistema SHALL exibir apenas as ações do tipo selecionado.
3. WHEN um PMA aplica filtro por período (data de início e/ou data de fim), THE Sistema SHALL exibir apenas as ações cujo período de vigência intersecta o intervalo informado.
4. WHEN um PMA aplica filtro por tag de tema, THE Sistema SHALL exibir apenas as ações que possuem a tag selecionada.
5. WHEN múltiplos filtros são aplicados simultaneamente, THE Sistema SHALL combinar os critérios com operador AND e exibir apenas as ações que atendem a todos os filtros.
6. WHEN um PMA limpa todos os filtros, THE Sistema SHALL restaurar a listagem completa de ações sem recarregar a página.
7. IF nenhuma ação corresponder aos filtros aplicados, THEN THE Sistema SHALL exibir mensagem informativa: "Nenhuma ação encontrada para os filtros selecionados."

---

### Requisito 6 — Controle de Acesso e Permissões

**User Story:** Como administrador da plataforma, quero controlar quem pode criar e gerenciar campanhas de comunicação, para que apenas usuários autorizados (PMAs) realizem essas operações.

#### Critérios de Aceitação

1. WHEN um usuário sem perfil PMA tenta acessar o módulo de Gestão de Comunicação, THE Sistema SHALL bloquear o acesso e exibir mensagem de permissão insuficiente.
2. THE Sistema SHALL registrar em log de auditoria todas as operações de criação, edição, desativação e exclusão de ações, incluindo identificador do usuário, timestamp e dados alterados.
3. WHEN um PMA realiza qualquer operação de escrita no módulo, THE Sistema SHALL validar a sessão ativa do usuário antes de processar a requisição.
4. IF a sessão do PMA expirar durante o preenchimento do formulário, THEN THE Sistema SHALL preservar os dados preenchidos no formulário e redirecionar para autenticação, restaurando o formulário após login bem-sucedido.
