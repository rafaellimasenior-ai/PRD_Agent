# Agente de PRD — Senior Sistemas

> Guia completo para Product Owners e times de produto entenderem, usarem e evoluírem este agente de criação de PRDs.

---

## O que é isso aqui?

Este repositório é a "caixa de ferramentas" de um agente de IA configurado dentro do Kiro para ajudar times de produto da Senior Sistemas a criar PRDs (Product Requirements Documents) de forma estruturada, consistente e rápida.

Em vez de cada PO começar um PRD do zero, com formatos diferentes e seções faltando, o agente garante que todo PRD siga o mesmo padrão, faça as perguntas certas antes de escrever, e entregue um documento pronto para ser consumido por times de design, engenharia e negócio.

O agente cobre **todos os softwares da Senior Sistemas**. Pode ser usado para qualquer linha de produto: ERP, Logística, Acesso e Segurança, Agro, HCM, etc.

---

## Como o agente funciona (visão geral)

O agente segue um fluxo em três etapas:

```
1. PERGUNTAS INICIAIS  →  2. ANÁLISE E CONTEXTO  →  3. GERAÇÃO DO PRD
```

**Etapa 1 — Perguntas iniciais**
Antes de escrever qualquer coisa, o agente busca no briefing e nos materiais anexados as respostas para as perguntas obrigatórias. Só faz as perguntas cujas respostas não foram identificadas no prompt inicial. As perguntas são:
- É inovação ou melhoria/evolução de produto?
- Para qual linha de solução Senior será o PRD?
- Para qual produto específico?
- Terá IA embarcada e/ou construção de tela no sistema?
- É para mobile e/ou desktop?

**Etapa 2 — Análise e contexto**
Com as respostas em mãos, o agente:
- Analisa o briefing e identifica o problema central
- Pesquisa concorrentes (mínimo 3: Totvs, LG, Sankhya, Benner e outros relevantes)
- Monta uma análise comparativa de funcionalidades, pricing e diferenciais
- Identifica oportunidades de mercado não exploradas

**Etapa 3 — Geração do PRD**
O agente escreve o PRD completo seguindo o template padrão com 18 seções (detalhadas abaixo), revisa criticamente o próprio documento e entrega um score de qualidade.

---

## Estrutura do repositório

```
/
├── README.md                          ← você está aqui
├── .gitignore                         ← impede que prd-output/ suba ao GitHub
├── prd-guide.md                       ← guia rápido de uso (a preencher)
├── prd-rastreamento-pedidos-tempo-real.md  ← exemplo de PRD completo (Logística)
├── prd-assinatura-termo-vistoria-pvd.md   ← exemplo de PRD completo (Hypnobox PVD)
├── prd-notificacao-resposta-portal-pvd.md ← exemplo de PRD (Hypnobox PVD — Nova feature)
├── prd-output/                        ← pasta local para salvar PRDs gerados (não vai ao GitHub)
│
├── .kiro/
│   ├── steering/                      ← regras e instruções do agente
│   │   ├── prd-orchestrator.md        ← orquestrador: perguntas iniciais + análise de mercado
│   │   ├── prd-template-completo.md   ← template PRD Modelo Completo (nova feature/módulo/produto)
│   │   ├── prd-template-simples.md    ← template PRD Modelo Simples (funcionalidade em tela existente)
│   │   ├── prd-validation-rules.md    ← regras de revisão e score de qualidade
│   │   ├── product.md                 ← regras de discovery e definição de problema
│   │   ├── spac-writing-rules.md      ← regras de escrita do PRD completo
│   │   ├── market-competitors.md      ← regras de análise de concorrentes
│   │   ├── product-tree.md            ← árvore de produto: linhas, verticais, produtos e POs
│   │   ├── Guardrails.md              ← 16 guardrails de qualidade e segurança
│   │   ├── lgpd-and-compliance.md     ← regras de compliance e LGPD
│   │   ├── personas-and-users.md      ← regras de mapeamento de personas (a preencher)
│   │   ├── business-rules-hcm.md      ← regras de negócio específicas (a preencher)
│   │   ├── structure.md               ← regras de estrutura de arquivos (a preencher)
│   │   └── tech.md                    ← regras técnicas (a preencher)
│   │
│   └── skills/prd-writing/            ← skill de escrita de PRD
│       ├── SKILL.md                   ← instruções e fluxo completo do skill
│       └── references/                ← arquivos de referência usados pelo skill
│           ├── prd-template.md
│           ├── validation-checklist.md
│           ├── personas-examples.md
│           ├── functional-requirements.md
│           ├── competitor-analysis.md
│           └── compliance-lgpd.md
│
└── aidlc-docs/                        ← documentação interna do ciclo de vida do agente
    ├── aidlc-state.md                 ← estado atual do projeto
    ├── audit.md                       ← log de auditoria das execuções
    └── inception/
        ├── requirements/requirements.md
        └── plans/execution-plan.md
```

---

## O que são os Steering Files?

Steering files são arquivos `.md` dentro de `.kiro/steering/` que funcionam como **instruções permanentes para o agente**. Pense neles como o "manual de comportamento" do agente — toda vez que ele executa uma tarefa, ele lê esses arquivos e segue as regras definidas neles.

Cada arquivo tem uma responsabilidade específica:

| Arquivo | Responsabilidade |
|---------|-----------------|
| `prd-orchestrator.md` | Define as perguntas que o agente faz antes de começar + como fazer análise de mercado |
| `prd-template-completo.md` | Template de PRD **Modelo Completo** — para novas features, módulos ou produtos |
| `prd-template-simples.md` | Template de PRD **Modelo Simples** — para funcionalidades em telas existentes |
| `prd-validation-rules.md` | Como o agente revisa e pontua a qualidade do PRD gerado |
| `product.md` | Como o agente interpreta briefings e define o problema central |
| `spac-writing-rules.md` | As 18 seções obrigatórias do PRD e o que cada uma deve conter |
| `market-competitors.md` | Como identificar e comparar concorrentes (Totvs, LG, Sankhya, Benner...) |
| `product-tree.md` | Árvore de produto completa: linhas, verticais, produtos e PO designado por produto |
| `Guardrails.md` | 16 guardrails obrigatórios: foco em problema antes de solução, anti-alucinação, LGPD, controle de escopo, rastreabilidade, consistência entre seções e qualidade mínima para aprovação |
| `personas-and-users.md` | Regras para mapear personas e usuários *(vazio — a preencher)* |
| `lgpd-and-compliance.md` | Regras de LGPD e compliance |
| `business-rules-hcm.md` | Regras de negócio específicas dos produtos Senior *(vazio — a preencher)* |
| `structure.md` | Padrão de estrutura de arquivos e pastas *(vazio — a preencher)* |
| `tech.md` | Restrições e padrões técnicos *(vazio — a preencher)* |

### Como o Kiro usa os steering files

Por padrão, **todos os steering files são carregados automaticamente** em toda interação com o agente. Isso significa que as regras definidas neles estão sempre ativas — você não precisa lembrar de "ativar" nada.

É possível configurar um steering file para ser carregado apenas em situações específicas (por exemplo, só quando um arquivo `.java` é aberto), mas por ora todos estão configurados como "sempre ativos".

---

## As 18 seções do PRD

Todo PRD gerado por este agente deve conter estas seções, nesta ordem:

| # | Seção | Para que serve |
|---|-------|---------------|
| 1 | Metadados do Documento | Rastreabilidade e governança (produto, tipo, PO, versão, status) |
| 2 | Visão do Produto | Alinhamento estratégico — o quê, para quem e por quê |
| 3 | Problema e Evidências | Justificar a iniciativa com dados reais (as-is, dores, benchmark) |
| 4 | Objetivos de Negócio | Metas mensuráveis com métricas e prazos |
| 5 | Pricing | Custos identificados e modelos de precificação possíveis |
| 6 | Personas | Perfis de usuário, necessidades e valor recebido |
| 7 | Estrutura do Produto | Módulos/blocos lógicos — mapa macro da feature |
| 8 | Fluxo do Usuário | Happy path e fluxos alternativos passo a passo |
| 9 | Requisitos Funcionais | Cada RF com regras, entradas, saídas e erros |
| 10 | Requisitos Não Funcionais | Performance, segurança, acessibilidade, escalabilidade |
| 11 | Compliance, LGPD e Requisitos Legais | Dados sensíveis e obrigações regulatórias |
| 12 | Entregáveis | O que será entregue: UI, API, relatórios, docs |
| 13 | Cenários de Teste (QA) | Cenários positivos e negativos com resultado esperado |
| 14 | Dependências e Integrações | Dependências internas e integrações externas |
| 15 | Riscos e Mitigações | Riscos com impacto, probabilidade e plano de mitigação |
| 16 | Métricas de Sucesso | Baseline, meta e prazo de medição pós-release |
| 17 | Glossário e Referências | Termos padronizados e fontes |
| 18 | Histórico de Versões | Rastreabilidade do próprio documento |

---

## Como usar o agente (passo a passo)

### 1. Abra o Kiro e inicie uma conversa

Abra o chat do Kiro neste workspace. O agente já estará carregado com todas as regras dos steering files.

### 2. Forneça o briefing

Descreva a funcionalidade ou produto que você quer documentar. Pode ser um texto livre, um rascunho, uma apresentação colada no chat, ou até um arquivo anexado. Quanto mais contexto, melhor o resultado.

Exemplo:
```
Quero criar um PRD para uma funcionalidade de aprovação de férias em lote 
no módulo de Gestão de Pessoas da Senior.
```

### 3. Responda as perguntas iniciais

O agente vai fazer as perguntas antes de começar a escrever, de acordo com o arquivo `prd-orchestrator.md`. Responda com clareza — essas respostas definem o tom e o escopo de todo o PRD.

### 4. Aguarde a análise de concorrentes

O agente vai pesquisar automaticamente como Totvs, LG, Sankhya, Benner e outros resolvem o mesmo problema. Isso alimenta a seção de benchmark do PRD.

### 5. Receba e revise o PRD

O agente entrega o PRD completo e já faz uma auto-revisão com score de qualidade (0 a 10) e lista de pontos de melhoria. Você pode pedir ajustes diretamente no chat.

### 6. Salve o arquivo

O agente vai perguntar onde você quer salvar o PRD antes de gerá-lo. As opções são:

- **Opção A — recomendada**: pasta `prd-output/` dentro deste workspace. Os arquivos salvos aqui ficam apenas no seu computador e **não são enviados ao GitHub**.
- **Opção B**: informe um caminho personalizado, como `C:\Users\seu-nome\Desktop\`.

Se não souber o que escolher, confirme a Opção A. O agente vai salvar automaticamente.

O nome do arquivo segue o padrão:
```
prd-[nome-da-feature]-[data].md
```
Exemplos:
- `prd-aprovacao-ferias-lote-2026-04-09.md`
- `prd-rastreamento-pedidos-tempo-real-2026-04-07.md`

---

## Como criar ou editar um Steering File

Steering files são arquivos de texto simples em Markdown. Para criar ou editar um:

### Criando um novo steering file

1. Crie um arquivo `.md` dentro de `.kiro/steering/`
2. Escreva as instruções em linguagem natural, como se estivesse explicando para uma pessoa o que ela deve fazer
3. Seja específico: diga o que o agente deve fazer, como deve fazer, e qual o output esperado
4. Salve o arquivo — o Kiro carrega automaticamente na próxima interação

### Estrutura recomendada para um steering file

```markdown
Sua responsabilidade é:
- [O que o agente deve fazer neste contexto]

Regras:
- [Restrição ou comportamento obrigatório]
- [Outra regra]

Output esperado:
- [O que deve ser entregue]
- [Formato esperado]
```

### Editando um steering file existente

Abra o arquivo em `.kiro/steering/`, edite diretamente e salve. As mudanças entram em vigor na próxima conversa com o agente.

### Boas práticas para steering files

- **Seja direto e imperativo**: "Identifique concorrentes" é melhor que "Você pode identificar concorrentes"
- **Evite ambiguidade**: Se uma regra pode ser interpretada de duas formas, reescreva
- **Um arquivo por responsabilidade**: Não misture regras de personas com regras de compliance no mesmo arquivo
- **Documente o propósito**: Adicione uma linha no topo explicando para que serve o arquivo
- **Teste após mudanças**: Faça uma pergunta de teste ao agente para verificar se o comportamento mudou como esperado

---

## Steering files vazios (a preencher)

Os arquivos abaixo existem mas ainda estão vazios. São oportunidades de evolução do agente:

### `personas-and-users.md`
Deve conter regras para o agente mapear personas com profundidade. Sugestão de conteúdo:
- Como identificar o perfil técnico vs. perfil de negócio
- Quais perguntas fazer para entender a jornada do usuário
- Como diferenciar usuário primário de secundário
- Padrão de descrição de persona (nome fictício, cargo, dores, ganhos)

### `lgpd-and-compliance.md`
Deve conter as regras de compliance específicas da Senior. Sugestão de conteúdo:
- Quais dados são considerados sensíveis nos produtos Senior
- Checklist de LGPD para cada tipo de funcionalidade
- Quando acionar o DPO (Data Protection Officer)
- Regras de retenção e exclusão de dados
- Obrigações com eSocial, SPED, e outros sistemas regulatórios

### `business-rules-hcm.md`
Deve conter regras de negócio dos produtos Senior. Sugestão de conteúdo:
- Regras trabalhistas (CLT, eSocial, FGTS, INSS, IRRF)
- Regras específicas de cada módulo (Folha, Ponto, Benefícios, Recrutamento...)
- Tabelas e limites legais vigentes
- Integrações obrigatórias entre módulos

### `structure.md`
Deve definir o padrão de organização de arquivos. Sugestão de conteúdo:
- Convenção de nomenclatura de arquivos de PRD
- Onde salvar PRDs por linha de produto
- Como versionar documentos
- Estrutura de pastas para projetos grandes

### `tech.md`
Deve conter restrições técnicas relevantes para o PRD. Sugestão de conteúdo:
- Stack tecnológica dos produtos Senior (para o agente não sugerir algo incompatível)
- Padrões de API (REST, GraphQL, eventos)
- Restrições de infraestrutura
- Padrões de segurança e autenticação

---

## Exemplo de PRD gerado

Dois exemplos reais de PRDs gerados por este agente estão disponíveis no repositório:

- `prd-rastreamento-pedidos-tempo-real.md` — PRD para o módulo Roteirizador (Logística)
- `prd-assinatura-termo-vistoria-pvd.md` — PRD para Assinatura Digital de Termo de Vistoria (Hypnobox PVD)
- `prd-notificacao-resposta-portal-pvd.md` — PRD para Notificação de Resposta do Cliente no Portal (Hypnobox PVD — Nova feature)

Use-os como referência para entender o nível de detalhe esperado em cada seção.

---

## Direcionadores estratégicos

Ao preencher os metadados do PRD, use sempre um dos quatro direcionadores estratégicos da Senior:

| Direcionador | Quando usar |
|-------------|-------------|
| **Densidade** | Funcionalidade que aprofunda o valor de um produto existente para clientes atuais |
| **Cobertura** | Funcionalidade que expande o produto para novos segmentos ou mercados |
| **Sustentação** | Correções, melhorias de performance, débito técnico, compliance |
| **Inovação** | Funcionalidade nova que não existe no mercado ou usa tecnologia disruptiva (ex: IA) |

Um PRD pode ter mais de um direcionador, mas deve ter pelo menos um.

---

## Tipos de entrega

No campo "Tipo" dos metadados, use sempre uma destas categorias:

- **Novo produto** — produto que não existe na Senior
- **Novo módulo** — módulo novo dentro de um produto existente
- **Nova jornada** — fluxo novo dentro de um módulo existente
- **Nova feature** — funcionalidade nova dentro de uma jornada existente
- **Melhoria/Evolução** — aprimoramento de algo que já existe
- **Correção** — bug fix ou ajuste de comportamento incorreto

---

## Perguntas frequentes

**O agente substitui o trabalho do PO?**
Não. O agente acelera a documentação e garante consistência, mas o PO ainda precisa fornecer o contexto, validar o conteúdo gerado e tomar as decisões de produto. O agente é um copiloto, não um piloto automático.

**Posso usar o agente para produtos fora da Senior?**
O agente foi configurado para o contexto da Senior Sistemas, mas o template e as regras são genéricos o suficiente para funcionar em qualquer contexto de software B2B. Basta ajustar os steering files de concorrentes e regras de negócio.

**O que faço se o PRD gerado estiver incompleto?**
Peça ao agente para completar seções específicas no chat. Você pode dizer, por exemplo: "Complete a seção de Requisitos Funcionais com mais detalhes sobre validações de entrada" e o agente vai reescrever apenas aquela parte.

**Como adiciono um novo concorrente para o agente monitorar?**
Edite o arquivo `.kiro/steering/market-competitors.md` e adicione o nome e URL do concorrente na lista de exemplos. O agente vai incluí-lo nas próximas análises.

**Posso ter PRDs em subpastas por linha de produto?**
Sim. Basta criar as pastas e atualizar o `structure.md` com a convenção adotada. O agente vai seguir a estrutura definida lá.

---

## Manutenção automática deste documento

Este README é atualizado automaticamente pelo agente sempre que mudanças com impacto no seu conteúdo forem detectadas no workspace. Dois gatilhos estão configurados:

- **Edição de steering file** — quando qualquer arquivo em `.kiro/steering/` for salvo, o agente avalia se a mudança é significativa (nova regra, novo escopo, arquivo antes vazio que foi preenchido) e atualiza as seções impactadas do README de forma cirúrgica.
- **Criação de novo arquivo** — quando um novo `.md` for criado no workspace (novo PRD, novo steering file, novo guia), o agente avalia se o arquivo deve ser refletido no README (ex: estrutura do repositório, tabela de steering files) e faz a atualização necessária.

Mudanças pequenas ou cosméticas (ajustes de texto sem impacto estrutural) não disparam atualização. O agente só age quando há impacto real no conteúdo documentado aqui.

---

## Histórico deste documento

| Versão | Data | Autor | Alterações |
|--------|------|-------|-----------|
| v1.0 | 09/04/2026 | Kiro (gerado) | Criação do documento |
| v1.1 | 09/04/2026 | Kiro (gerado) | Adicionada seção de manutenção automática |
| v1.2 | 09/04/2026 | Kiro (gerado) | Guardrails.md preenchido — atualizada tabela de steering files e removido da lista de vazios |
| v1.3 | 13/04/2026 | Kiro (gerado) | Adicionada a skill hypnobox-product-knowledge ao repositório |
| v1.4 | 13/04/2026 | Kiro (gerado) | Ajustada a lógica de decisão do agente para definição do tipo de PRD |
| v1.5 | 13/04/2026 | Kiro (gerado) | Adicionado prd-assinatura-termo-vistoria-pvd.md e prd-notificacao-resposta-portal-pvd.md |
| v1.6 | 14/04/2026 | Kiro (gerado) | product-tree.md criado — árvore de produto com linhas, verticais, produtos e POs |
| v1.7 | 15/04/2026 | Kiro (gerado) | product-tree.md atualizado — POs da linha ERP detalhados (ERP XT, ERP X, ERP Mega, CRM, Marketing Intelligence, E-Docs) com nomes reais dos responsáveis |
