---
name: prd-writing
description: Skill completo para escrita de PRD (Product Requirements Document) estruturado, alinhado com melhores práticas de product management. Cobre discovery, análise de concorrentes, definição de personas, requisitos funcionais/não-funcionais, compliance LGPD, cenários de teste e métricas de sucesso. Use quando precisar criar, refinar ou validar um PRD completo.
license: MIT
compatibility: Requer acesso a web para análise de concorrentes. Ideal para produtos SaaS, plataformas e soluções empresariais.
metadata:
  category: product-management
  version: 1.0.0
  language: pt-BR
  use-cases: "novo-produto, feature, modulo, jornada, melhoria"
allowed-tools: readFile readMultipleFiles fsWrite strReplace remote_web_search webFetch
---

# PRD Writing Skill

Skill especializado para criação de PRDs (Product Requirements Documents) estruturados, completos e prontos para desenvolvimento.

## Quando Usar Este Skill

- Criar um novo PRD do zero
- Refinar ou validar um PRD existente
- Estruturar descobertas de produto em documento executável
- Documentar features, módulos ou jornadas de usuário
- Preparar PRD para homologação com stakeholders

## Fluxo de Trabalho Recomendado

### Fase 1: Discovery e Orquestração
1. **Fazer perguntas de contexto** (se não fornecidas):
   - É inovação ou melhoria/evolução?
   - Qual a linha de solução?
   - Qual produto será construído?
   - Terá IA embarcada e/ou construção de tela?
   - É para mobile e/ou desktop?

2. **Analisar o briefing fornecido**:
   - Identificar problema principal
   - Mapear dores do usuário
   - Entender contexto de negócio
   - Validar hipótese de solução

### Fase 2: Análise de Mercado
1. **Identificar concorrentes** (mínimo 3):
   - Diretos e indiretos
   - Buscar informações públicas
   - Documentar funcionalidades principais

2. **Análise comparativa**:
   - Funcionalidades
   - Modelo de pricing
   - Pontos fortes e fracos
   - Oportunidades de diferenciação

### Fase 3: Estruturação do PRD
Seguir o template padrão com 18 seções:

1. **Metadados do Documento** — Rastreabilidade e governança
2. **Visão do Produto** — O que é, para quem, por que importa
3. **Problema e Evidências** — Estado atual, dores, benchmark
4. **Objetivos de Negócio** — Metas mensuráveis vinculadas a métricas
5. **Pricing** — Custos e modelos de precificação
6. **Personas** — Perfis de usuário, necessidades, valor
7. **Estrutura do Produto** — Módulos/blocos lógicos
8. **Jornada do Usuário** — Happy path e fluxos alternativos
9. **Requisitos Funcionais** — Detalhamento com regras, entrada, saída, erros
10. **Requisitos Não Funcionais** — Performance, segurança, acessibilidade, escalabilidade
11. **Compliance, LGPD e Requisitos Legais** — Dados sensíveis, conformidade
12. **Entregáveis** — UI, API, relatórios, docs
13. **Cenários de Teste (QA)** — Positivos e negativos
14. **Dependências e Integrações** — Internas e externas
15. **Riscos e Mitigações** — Impacto, probabilidade, plano
16. **Métricas de Sucesso** — Baseline, meta, prazo
17. **Plano de Execução** — Roadmap em fases
18. **Glossário e Referências** — Termos padronizados
19. **Histórico de Versões** — Rastreabilidade de alterações

### Fase 4: Validação
1. **Revisar criticamente**:
   - Clareza e completude
   - Consistência
   - Ausência de ambiguidades
   - Qualidade dos requisitos

2. **Gerar score de qualidade** (0-10)
3. **Listar problemas** com severidade
4. **Sugerir melhorias** acionáveis

## Regras Essenciais

### Escrita
- Seja claro, estruturado e sem ambiguidades
- Escreva para que times de produto, design e engenharia consigam executar
- Evite lacunas de informação (ou sinalize explicitamente)
- Use linguagem objetiva e direta

### Requisitos Funcionais
- Cada RF deve ter: descrição, regras de negócio, dados de entrada/saída, comportamento de erro, dependências, prioridade (MoSCoW)
- Suficientemente detalhado para quebra em tarefas de desenvolvimento
- Vinculado a personas e jornadas

### Compliance e LGPD
- Mapear dados sensíveis (salário, CPF, dependentes, etc.)
- Definir trilha de auditoria com user_id e timestamp
- Respeitar matriz de segurança existente
- Incluir disclaimers e marcas d'água quando necessário
- Não gerar eventos em sistemas regulatórios para simulações

### Personas
- Mínimo 3 personas com perfil, necessidade principal e valor recebido
- Conectar cada persona aos requisitos funcionais
- Descrever como a feature resolve o problema de cada uma

### Cenários de Teste
- Mínimo 5 cenários positivos (happy path)
- Mínimo 5 cenários negativos (edge cases)
- Cada cenário com: descrição, condições, resultado esperado
- Cobrir validações, permissões, limites, erros

## Estrutura de Arquivo

```
prd-[nome-produto]-[data].md
```

Exemplo: `prd-rastreamento-pedidos-tempo-real-2026-04-07.md`

## Checklist de Completude

- [ ] Metadados preenchidos (produto, tipo, status, PO, stakeholders, versão)
- [ ] Visão clara em uma frase + resumo executivo
- [ ] Problema e evidências com fontes (feedback, dados, tickets)
- [ ] Mínimo 3 concorrentes analisados
- [ ] Objetivos de negócio com métricas mensuráveis
- [ ] Mínimo 3 personas definidas
- [ ] Estrutura de produto com módulos claros
- [ ] Happy path descrito passo-a-passo
- [ ] Mínimo 10 requisitos funcionais detalhados
- [ ] Requisitos não funcionais (performance, segurança, acessibilidade, escalabilidade)
- [ ] Dados sensíveis mapeados e compliance definido
- [ ] Entregáveis concretos listados
- [ ] Mínimo 10 cenários de teste (5+ positivos, 5+ negativos)
- [ ] Dependências e integrações mapeadas
- [ ] Riscos identificados com mitigações
- [ ] Métricas de sucesso com baseline e meta
- [ ] Roadmap em fases com durações estimadas
- [ ] Glossário com termos-chave
- [ ] Histórico de versões iniciado

## Dicas Práticas

1. **Comece pelo problema**: Não pule a fase de discovery. Um PRD bem fundamentado economiza semanas de desenvolvimento.

2. **Valide com stakeholders**: Antes de finalizar, circule o PRD com PO, design, engenharia e compliance.

3. **Use templates**: Reutilize estruturas de PRDs anteriores para manter consistência.

4. **Seja específico**: Evite "melhorar experiência do usuário". Diga "reduzir tempo de aprovação de 5 dias para 1 dia".

5. **Documente incertezas**: Se não souber algo, sinalize como "TBD" (To Be Determined) e defina quem vai resolver.

6. **Vincule a métricas**: Cada objetivo deve ter uma métrica mensurável e um prazo de medição.

7. **Considere LGPD desde o início**: Não deixe compliance para o final. Mapear dados sensíveis desde a discovery.

8. **Cenários de teste desde o início**: Escrever testes enquanto define requisitos melhora a qualidade.

## Referências

- [Template PRD Padrão](references/prd-template.md)
- [Checklist de Validação](references/validation-checklist.md)
- [Exemplos de Personas](references/personas-examples.md)
- [Análise de Concorrentes](references/competitor-analysis.md)
- [Requisitos Funcionais - Padrão](references/functional-requirements.md)
- [Compliance e LGPD](references/compliance-lgpd.md)
