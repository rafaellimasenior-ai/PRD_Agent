Template PRD — Modelo Simples
Quando usar: nova funcionalidade ou ação em tela existente.
Propósito: Modelo padronizado de PRD que unifica visão de negócio, detalhamento funcional (para quebra de tarefas) e base para documentação e prototipação. Projetado para ser consumido por agentes de IA na geração automatizada de PRDs.
 
Metadados do Documento
Campo	Valor
Produto / Módulo	[Nome do produto ou módulo]
Funcionalidade	[Nome da feature]
Tipo	[Nova funcionalidade / Melhoria / Correção]
Status	[Em Definição / Em Desenvolvimento / Em Homologação / Entregue]
Product Owner	[Nome]
Stakeholders	[Lista de envolvidos]
Data de criação	[DD/MM/AAAA]
Última atualização	[DD/MM/AAAA]
Versão	[v0.1]

 
1. Visão do Produto
Descrição de alto nível do produto/funcionalidade, respondendo:
•	O que é? — Definição em uma frase.
•	Para quem? — Público-alvo primário.
•	Qual o valor entregue? — Benefício central para o negócio e o usuário.
•	Resumo executivo — Parágrafo curto que contextualiza a importância estratégica (competitividade, experiência, compliance, receita).
Exemplo de estrutura:
"[Nome] é uma [tipo] que permite [ação] para [persona], gerando [valor]. Esta funcionalidade é estratégica porque [razão de negócio]."
 
2. Problema e Evidências
2.1 Estado Atual (As-Is)
Descrição de como o processo funciona hoje, sem a funcionalidade proposta. Incluir workarounds que os usuários adotam.
2.2 Evidências de Dor
Fonte da Evidência	Descrição
Feedback de clientes	[Ex: Volume alto de solicitações no portal]
Dados internos	[Ex: % de retrabalho ou registros excluídos]
Time de Vendas / CS	[Ex: Perda de RFPs ou churn por falta da feature]
Suporte / Tickets	[Ex: Volume de chamados relacionados]

 
3. Objetivos de Negócio
Lista dos objetivos mensuráveis que a funcionalidade busca atingir.
#	Objetivo	
O1	[Ex: Reduzir tempo de aprovação]	
O2	[Ex: Aumentar adoção da feature]	
O3	[Ex: Reduzir tickets de suporte]

 
4. Personas
Para cada persona, descrever: perfil, necessidade principal, como a funcionalidade a atende.
Persona	Perfil	Necessidade Principal	Valor Recebido
[Ex: Analista de RH]	[Descrição breve do papel]	[O que precisa resolver]	[Como a feature ajuda]
[Ex: Gestor]	[Descrição breve do papel]	[O que precisa resolver]	[Como a feature ajuda]
[Ex: Colaborador]	[Descrição breve do papel]	[O que precisa resolver]	[Como a feature ajuda]

 
5. Estrutura do Produto (Módulos / Blocos)
Visão macro de como a funcionalidade se organiza em módulos ou blocos lógicos. Cada módulo é um agrupamento coeso de funcionalidades.
Módulo [N] — [Nome] ([Propósito])
Funcionalidades:
•	[Funcionalidade 1]
•	[Funcionalidade 2]
•	[Funcionalidade 3]
Repetir para cada módulo. Esta seção serve como "mapa" do produto para alinhar times e orientar a navegação do PRD.
 
6. Fluxo do Usuário
6.1 Fluxo Principal (Happy Path)
Descrição passo-a-passo do caminho típico do usuário:
1.	[Passo 1 — Ex: Usuário acessa a tela de simulação]
2.	[Passo 2 — Ex: Seleciona o colaborador]
3.	[Passo 3 — Ex: Preenche parâmetros]
4.	[Passo 4 — Ex: Clica em "Simular"]
5.	[Passo 5 — Ex: Visualiza resultado]
6.2 Fluxos Alternativos / Inteligentes
Caminhos derivados que agregam valor (ex: drill-down de KPI para ação, atalhos contextuais).
•	[Fluxo alternativo 1 — Descrição]
•	[Fluxo alternativo 2 — Descrição]
 
7. Requisitos Funcionais
Cada requisito funcional deve ser detalhado o suficiente para permitir a quebra em tarefas de desenvolvimento e a criação de testes.
RF[XX] — [Nome do Requisito]
Campo	Descrição
Descrição	[O que o sistema deve fazer]
Regras de Negócio	[Condições, validações, limites — ex: CLT, tabelas INSS/IRRF]
Dados de Entrada	[Campos, parâmetros, seleções do usuário]
Dados de Saída	[O que o sistema retorna/exibe]
Comportamento de Erro	[Mensagens, bloqueios, fallback]
Dependências	[Outros RFs, APIs, módulos]
Prioridade	[Must / Should / Could / Won't] (MoSCoW)

Repetir para cada requisito funcional.
 
8. Requisitos Não Funcionais
ID	Categoria	Requisito
RNF01	Performance	[Ex: Tempo de resposta < 1s para listagens]
RNF02	Responsividade	[Ex: Compatível com desktop e mobile]
RNF03	Segurança	[Ex: Controle de permissões por perfil]
RNF04	Auditoria	[Ex: Log de todas as ações com user_id e timestamp]
RNF05	Escalabilidade	[Ex: Suportar processamento em lote de N registros]
RNF06	Acessibilidade	[Ex: Conformidade com WCAG 2.1 nível AA]

9. Entregáveis
Componente	Descrição da Entrega
Interface (UI)	[Ex: Nova tela em Módulo > Sub > Funcionalidade]
Backend / API	[Ex: Endpoint ou motor de cálculo com flag específica]
Relatórios / PDFs	[Ex: Relatório de simulação com marca d'água]
Integrações	[Ex: Webhook, notificação, export]
Documentação	[Ex: Help online, release notes, material de treinamento]

 
10. Dependências e Integrações
10.1 Dependências Internas
Dependência	Tipo	Descrição
[Ex: Cadastro de Colaborador]	Dados	[Necessário para buscar informações base]
[Ex: Motor de cálculo existente]	Serviço	[Reutilizar lógica já implementada]

10.2 Integrações Externas
Sistema / API	Tipo	Descrição
[Ex: Tabelas INSS/IRRF]	Dados	[Tabelas atualizadas pelo governo]
[Ex: eSocial]	Regulatório	[Não deve gerar eventos para simulação]

 
11. Riscos e Mitigações
#	Risco	Impacto	Probabilidade	Mitigação
R1	[Ex: Performance em lote]	Alto	Média	[Ex: Processamento assíncrono + paginação]
R2	[Ex: Divergência de cálculo]	Crítico	Baixa	[Ex: Usar o mesmo motor do processo oficial]
R3	[Ex: Escopo crescente]	Médio	Alta	[Ex: Fases bem definidas com gates]

Nota para o agente de IA: Ao preencher este template, garanta que:
- Não invente dados, sugira e deixe claro ao usuário pra validar e buscar dados reais