# Gestão de Comunicação via Produto — Guia de Prototipação

> Documento simplificado para geração de protótipos via IA.
> Contém apenas o essencial: telas, fluxos, componentes, dados e estados visuais.

---

## Contexto do Produto

Ferramenta interna da Senior usada por PMAs para criar e monitorar campanhas de banner na home page dos produtos XT.
Plataforma: Senior X (web/desktop, Angular 18, Senior Design System + PrimeNG).
Usuário principal: PMA (Product Marketing Analyst).

---

## Telas a Prototipar

### Tela 1 — Listagem de Ações de Comunicação

**Propósito:** Visão geral das campanhas de um produto selecionado.

**Componentes:**
- Header com título "Gestão de Comunicação" + botão primário "Nova Ação"
- Seletor de produto (dropdown) — campo obrigatório para carregar a listagem
- Barra de filtros: Tipo (Gratuito / Vendas), Status (Ativa / Inativa / Expirada), Período (data início–fim), Tag (Novidade / Promoção / Treinamento / Upsell / Crossell / Outro)
- Botão "Limpar filtros"
- Contador de limite: "X/5 ações gratuitas ativas" e "X/1 ação de vendas ativa"
- Tabela/lista de ações com colunas: Miniatura da imagem | Título | Tag | Tipo | Data início | Data fim | Status | Ações (Editar / Ativar-Desativar / Excluir)
- Badge de status colorido: Verde = Ativa | Cinza = Inativa | Vermelho = Expirada
- Estado vazio: ícone + texto "Nenhuma ação cadastrada para este produto. Clique em Nova Ação para começar."

**Dados de exemplo para a tabela:**

| Miniatura | Título | Tag | Tipo | Início | Fim | Status |
|---|---|---|---|---|---|---|
| [img] | Black Friday HCM XT | Promoção | Gratuito | 01/11/2026 | 30/11/2026 | Ativa |
| [img] | Novidade: Módulo Férias | Novidade | Gratuito | 15/10/2026 | 15/12/2026 | Ativa |
| [img] | Upgrade para Senior X | Upsell | Vendas | 01/10/2026 | 31/12/2026 | Ativa |
| [img] | Treinamento Online ERP XT | Treinamento | Gratuito | 01/08/2026 | 31/08/2026 | Expirada |

---

### Tela 2 — Formulário de Nova Ação / Edição

**Propósito:** Cadastrar ou editar uma campanha de comunicação.

**Componentes:**
- Título da página: "Nova Ação de Comunicação" ou "Editar Ação"
- Campo: Produto (dropdown, obrigatório) — desabilitado na edição
- Campo: Título (texto, máx. 100 caracteres, obrigatório)
- Campo: Tipo (radio button: Gratuito / Vendas, obrigatório)
  - Hint inline: "Gratuito: até 5 ativas | Vendas: até 1 ativa"
- Campo: Tag (dropdown, obrigatório)
  - Tipo Gratuito: Novidade / Promoção / Treinamento / Outro
  - Tipo Vendas: Upsell / Crossell
- Campo: Data de início (date picker, obrigatório)
- Campo: Data de fim (date picker, obrigatório, deve ser >= data início)
- Campo: Upload de imagem (drag & drop + botão "Selecionar arquivo")
  - Formatos aceitos: PNG, JPG, GIF | Tamanho máx: 2 MB
  - Preview da imagem após upload
- Campo: Link de destino (URL, obrigatório, com validação de formato)
- Botões: "Salvar" (primário) | "Cancelar" (secundário)

**Estados de erro a mostrar:**
- Limite atingido: banner de alerta no topo — "Limite de ações ativas atingido para este tipo. Desative uma ação existente para continuar."
- Campo obrigatório vazio: highlight vermelho + mensagem abaixo do campo
- Data fim < data início: "A data de fim deve ser igual ou posterior à data de início"
- Arquivo inválido: "Formato não suportado. Use PNG, JPG ou GIF com até 2 MB"

---

### Tela 3 — Painel de Monitoramento (Visão Geral)

**Propósito:** Visão consolidada de todas as campanhas por produto.

**Componentes:**
- Título "Painel de Monitoramento"
- Cards por produto com:
  - Nome do produto
  - Contadores: Ativas (verde) | Inativas (cinza) | Expiradas (vermelho)
  - Botão "Ver detalhes"
- Estado vazio: "Nenhum produto com ações cadastradas."

**Dados de exemplo para os cards:**

| Produto | Ativas | Inativas | Expiradas |
|---|---|---|---|
| HCM XT | 3 | 1 | 2 |
| ERP XT Senior | 1 | 0 | 1 |
| ERP XT Mega | 0 | 2 | 0 |
| TMS XT | 2 | 1 | 0 |
| GRS XT | 0 | 0 | 1 |

**Tela de drill-down (ao clicar em "Ver detalhes"):**
- Breadcrumb: Monitoramento > HCM
- Listagem das ações do produto com: título, tipo, tag, período, status, qtd cliques total
- Link "Ver engajamento" por ação

---

### Tela 4 — Engajamento por Campanha

**Propósito:** Análise de cliques de uma campanha específica, com visão por cliente e picos de acesso por horário.

**Componentes:**
- Breadcrumb: Monitoramento > HCM XT > Black Friday HCM XT
- Resumo da campanha: imagem miniatura | título | período | status | total de cliques
- Barra de filtros: Período (date range) | Cliente (codcli, campo de busca) | Campanha (quando acessado via visão de cliente)

**Gráfico de Picos por Horário do Dia:**
- Tipo: gráfico de barras ou área (heatmap de linha do tempo)
- Eixo X: horas do dia (00h às 23h)
- Eixo Y: quantidade de cliques
- Destaque visual nos horários de pico (barra ou ponto em cor de destaque — ex: laranja/amarelo)
- Tooltip ao passar o mouse: "14h — 47 cliques"
- Filtro de período aplicado ao gráfico (mesmo filtro da tabela)
- Legenda: "Horário de maior acesso: 14h (47 cliques)"

**Dados de exemplo para o gráfico:**

| Horário | Cliques |
|---|---|
| 08h | 12 |
| 09h | 28 |
| 10h | 35 |
| 11h | 41 |
| 12h | 18 |
| 13h | 22 |
| 14h | 47 ← pico |
| 15h | 39 |
| 16h | 31 |
| 17h | 25 |
| 18h | 10 |
| demais horas | < 5 |

- Tabela de engajamento com colunas: Tenant | Codcli | Qtd Cliques | (ícone de expandir)
- Ao clicar na linha do cliente → drilldown inline ou nova linha expandida exibindo: Usuário | Qtd Cliques daquele usuário
- Botão "Exportar CSV"
- Estado vazio: "Nenhum clique registrado para esta campanha no período selecionado."

**Dados de exemplo para a tabela (nível cliente):**

| Tenant | Codcli | Qtd Cliques |
|---|---|---|
| empresa-abc | 1001 | 8 |
| empresa-xyz | 2045 | 8 |
| empresa-beta | 3312 | 2 |

**Drilldown ao expandir cliente 1001:**

| → Usuário | Qtd Cliques |
|---|---|
| joao.silva | 5 |
| maria.souza | 3 |

**Visão por cliente (ao filtrar por codcli):**
- Título muda para: "Interações do cliente 1001 — todas as campanhas"
- Tabela exibe: Campanha | Qtd Cliques | (ícone de expandir)
- Drilldown por campanha mostra os usuários daquele cliente naquela campanha
- Exemplo:

| Campanha | Qtd Cliques |
|---|---|
| Black Friday HCM XT | 5 |
| Novidade: Módulo Férias | 2 |
| Upgrade para Senior X | 3 |

**Drilldown ao expandir "Black Friday HCM XT":**

| → Usuário | Qtd Cliques |
|---|---|
| joao.silva | 5 |

---

## Fluxo de Navegação

```
[Login Senior X]
       |
       v
[Módulo: Gestão de Comunicação]
       |
       |--- [Tela 1: Listagem] ---> [Tela 2: Nova Ação / Edição]
       |
       |--- [Tela 3: Painel de Monitoramento]
                    |
                    v
             [Drill-down por produto]
                    |
                    v
             [Tela 4: Engajamento por Campanha]
                    |
                    v
             [Filtro por cliente → visão consolidada]
```

---

## Estados Globais a Prototipar

| Estado | Descrição | Onde aparece |
|---|---|---|
| Loading | Spinner centralizado durante carregamento de dados | Todas as telas |
| Empty state — sem dados | Ícone + mensagem orientativa | Listagem, Monitoramento, Engajamento |
| Empty state — home page XT | Ícone + "Aguarde novidades" | Home page produto XT |
| Erro de limite | Banner de alerta no topo do formulário | Tela 2 |
| Erro de validação | Highlight vermelho + mensagem inline | Tela 2 |
| Confirmação de exclusão | Modal: "Tem certeza que deseja excluir esta ação? Esta operação não pode ser desfeita." + botões Confirmar / Cancelar | Tela 1 |
| Sucesso | Toast/snackbar: "Ação salva com sucesso" | Após salvar no formulário |
| Sessão expirada | Modal: "Sua sessão expirou. Faça login novamente." — formulário preservado | Qualquer tela |

---

## Regras Visuais Importantes

- Máx. 5 ações ATIVAS do tipo Gratuito por produto — contador visível na listagem
- Máx. 1 ação ATIVA do tipo Vendas por produto — contador visível na listagem
- Ação com status Expirada: linha da tabela em tom mais claro (opacidade reduzida)
- Badge de status: Verde (Ativa) | Cinza (Inativa) | Vermelho/laranja (Expirada)
- Imagem do banner: proporção recomendada 16:9 ou 3:1 (necessário validar com UX)
- Plataforma: desktop, resolução mínima 1280x768

---

## Dados Mockados para IA

### Produtos disponíveis (dropdown)
- HCM XT
- ERP XT Senior
- ERP XT Mega
- TMS XT
- GRS XT

### Tags disponíveis
- Tipo Gratuito: Novidade / Promoção / Treinamento / Outro
- Tipo Vendas: Upsell / Crossell

### Tipos de ação
- Gratuito (limite: 5 ativas por produto)
- Vendas (limite: 1 ativa por produto)

### Status possíveis
- Ativa
- Inativa
- Expirada
