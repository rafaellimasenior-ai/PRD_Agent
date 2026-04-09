# Plano de Execução — hcm-database-backend

## Análise de Escopo

### Contexto da Solução (extraído de Contexto.md)
O diagrama draw.io descreve a arquitetura do sistema `hcm-database-backend`, composto por:

```
[serviços de negócio]
        |-- depende de --> [schemanameprovider]
        |-- depende de --> [migration]
                               |-- depende de (*) --> [schemanameprovider]
                               |-- depende de --> [client]
[impl]
  |-- depende de --> [server]
  |-- depende de --> [migration]
[server] --> [client]
[migration] --> [client]
```

Componentes identificados dentro do container `hcm-database-backend`:
- `impl` — implementação principal
- `server` — servidor de banco de dados
- `client` — cliente de banco de dados
- `migration` — gerenciamento de migrações de schema
- `schemanameprovider` — provedor de nome de schema (suporte a multi-tenancy)

Camada externa:
- `serviços de negócio` — camada de serviços de negócio que consome o backend

### Tipo de Projeto: Greenfield
### Risco: Médio (novo sistema HCM com multi-tenancy)

## Avaliação de Impacto
- Mudanças estruturais: Sim — novo sistema
- Modelos de dados: Sim — schema HCM
- APIs: Sim — interfaces entre componentes
- NFR: Sim — multi-tenancy, segurança de dados

## Fases a Executar

### INCEPTION PHASE
- [x] Workspace Detection — CONCLUÍDO
- [x] Requirements Analysis — CONCLUÍDO
- [x] Workflow Planning — EM ANDAMENTO
- [ ] Application Design — EXECUTAR (novos componentes identificados no diagrama)
- [ ] Units Generation — EXECUTAR (múltiplos componentes requerem decomposição)

### CONSTRUCTION PHASE
- [ ] Functional Design — EXECUTAR (lógica de negócio HCM + multi-tenancy)
- [ ] NFR Requirements — EXECUTAR (segurança, escalabilidade, multi-tenancy)
- [ ] NFR Design — EXECUTAR (padrões de isolamento de tenant)
- [ ] Infrastructure Design — EXECUTAR (banco de dados, schema por tenant)
- [ ] Code Generation — EXECUTAR (sempre)
- [ ] Build and Test — EXECUTAR (sempre)

### OPERATIONS PHASE
- [ ] Operations — PLACEHOLDER

## Critérios de Sucesso
- Backend HCM funcional com suporte a multi-tenancy via schemanameprovider
- Migrações de schema automatizadas
- Serviços de negócio desacoplados do backend de dados
- Análise de mercado competitiva entregue (TOTVS vs LG lugar de gente)
