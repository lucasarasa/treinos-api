# FIT.AI - Backend API

API REST moderna para gerenciamento de treinos com chat assistido por IA e cálculo dinâmico de estatísticas de aderência.

> Este projeto é o backend completo da solução FIT.AI: autenticação segura, geração de planos de treino com IA, rastreamento de sessões e estatísticas em tempo real.

<div align="center">
  
  [![Docs OpenAPI](https://img.shields.io/badge/📚_Documentação_Completa-OpenAPI-blue?style=for-the-badge)](https://www.fitai-api.lucassarasadev.com.br/docs)

</div>

[![Node.js](https://img.shields.io/badge/Node.js-24-339933?logo=node.js&logoColor=white)](https://nodejs.org/)
[![Fastify](https://img.shields.io/badge/Fastify-5.8-000000?logo=fastify&logoColor=white)](https://www.fastify.io/)
[![Prisma](https://img.shields.io/badge/Prisma-7.4-2D3748?logo=prisma&logoColor=white)](https://www.prisma.io/)
[![PostgreSQL](https://img.shields.io/badge/PostgreSQL-Database-336791?logo=postgresql&logoColor=white)](https://www.postgresql.org/)
[![Better Auth](https://img.shields.io/badge/Auth-Better_Auth-111827)](https://www.better-auth.com/)
[![Vercel AI SDK](https://img.shields.io/badge/AI-Vercel_AI_SDK-000000)](https://sdk.vercel.ai/)

---

## 📋 Sobre o Projeto

A **FIT.AI API** oferece infraestrutura robusta e escalável para uma plataforma de treino orientada por dados e assistência de IA.

O backend foi construído com **Fastify**, **Prisma** e **PostgreSQL**, implementando:

- autenticação segura via Better Auth com OAuth social;
- chat contextual com IA (Google Gemini 2.5 Flash / OpenAI);
- geração dinâmica de planos de treino personalizados;
- rastreamento de sessões de treino em tempo real;
- cálculo de estatísticas e aderência de forma performática;
- documentação automática com Swagger/OpenAPI;
- suporte a múltiplas camadas e padrões de arquitetura.

---

## 🎯 Principais Funcionalidades

- **🔐 Autenticação Social** com Google via Better Auth.
- **💬 Chat com IA** (Gemini 2.5 Flash / OpenAI) para montagem de planos personalizados.
- **📅 Gestão de Planos de Treino** com exercícios, séries, reps e tempo de descanso.
- **🏃 Rastreamento de Sessões** com início/conclusão de treinos.
- **📊 Estatísticas Dinâmicas** com heatmap de consistência, streak e taxa de conclusão.
- **👤 Dados de Treino do Usuário** com métricas corporais (peso, altura, idade, % gordura).
- **🏠 Dashboard Data** com treino do dia, streak atual e histórico de aderência.
- **📃 OpenAPI Documentação** auto-gerada (Swagger + Scalar).
- **✅ Validação Rigorosa** com Zod em todas as rotas.

---

## 🚀 Tecnologias e Bibliotecas

### 🧩 Core

| Tecnologia | Versão | Uso                                |
| ---------- | ------ | ---------------------------------- |
| Node.js    | 24.x   | Runtime JavaScript no servidor     |
| Fastify    | 5.8.1  | Framework HTTP de alta performance |
| TypeScript | 5.9.3  | Tipagem estática                   |

### 💾 Banco de Dados e ORM

| Biblioteca        | Versão | Uso                       |
| ----------------- | ------ | ------------------------- |
| Prisma Client     | 7.4.0  | ORM TypeScript-first      |
| Prisma Adapter PG | 7.4.0  | Adapter para PostgreSQL   |
| PostgreSQL        | Latest | Banco de dados relacional |

### 🔐 Autenticação e IA

| Biblioteca     | Versão  | Uso                                 |
| -------------- | ------- | ----------------------------------- |
| Better Auth    | 1.4.18  | Autenticação segura e OAuth         |
| Vercel AI SDK  | 6.0.100 | Interface unificada para modelos IA |
| @ai-sdk/google | 3.0.34  | Provider Google Generative AI       |
| @ai-sdk/openai | 3.0.33  | Provider OpenAI                     |

### 🛠️ Validação e Type Provider

| Biblioteca                | Versão | Uso                           |
| ------------------------- | ------ | ----------------------------- |
| Zod                       | 4.3.6  | Validação e schema TypeScript |
| fastify-type-provider-zod | 6.1.0  | Integração Zod com Fastify    |

### 🎨 Documentação e Ferramentas

| Ferramenta                    | Versão  | Uso                             |
| ----------------------------- | ------- | ------------------------------- |
| @fastify/swagger              | 9.7.0   | Geração de OpenAPI Schema       |
| @scalar/fastify-api-reference | 1.44.20 | UI interativa para documentação |
| Pino + Pino Pretty            | 13.1.3  | Logging estruturado             |
| ESLint + TypeScript ESLint    | 10.0.2  | Qualidade de código             |
| Prettier                      | 3.8.1   | Formatação automática           |

---

## 🏗️ Arquitetura do Projeto

```txt
src/
├── 📁 generated/                 # Código auto-gerado (Prisma)
│   └── 📁 prisma/
│       ├── client.ts             # Cliente Prisma tipado
│       └── enums.ts              # Enums (WeekDay, etc)
├── 📁 lib/                       # Bibliotecas e utilidades
│   ├── auth.ts                   # Configuração Better Auth
│   ├── db.ts                     # Conexão e adaptador Prisma
│   └── env.ts                    # Variáveis de ambiente validadas
├── 📁 routes/                    # Rotas REST (controllers)
│   ├── ai.ts                     # Chat com IA + orquestração
│   ├── home.ts                   # Dashboard/home data
│   ├── me.ts                     # Perfil e dados do usuário
│   ├── stats.ts                  # Estatísticas de treino
│   └── workout-plan.ts           # Gestão de planos + sessões
├── 📁 schemas/                   # Schemas Zod para validação
│   └── index.ts                  # Definições centralizadas
├── 📁 usecases/                  # Lógica de negócio
│   ├── CreateWorkoutPlan.ts      # Orquestração criar plano
│   ├── GetWorkoutDay.ts          # Buscar dia específico
│   ├── GetWorkoutPlan.ts         # Buscar plano completo
│   ├── GetUserTrainData.ts       # Buscar dados do usuário
│   ├── ListWorkoutPlans.ts       # Listar planos
│   ├── StartWorkoutSession.ts    # Iniciar sessão
│   ├── UpsertUserTrainData.ts    # Salvar dados do usuário
│   └── UpdateWorkoutSession.ts   # Finalizar sessão
├── 📁 errors/                    # Classes de erro customizadas
│   └── index.ts                  # Exceções da aplicação
├── 📁 prisma/                    # Configuração Prisma
│   ├── schema.prisma             # Schema do banco de dados
│   └── migrations/               # Histórico de migrações
├── index.ts                      # Entry point (registro de rotas)
└── .env                          # Variáveis de ambiente
```

### 🎯 Padrões Adotados

- **Separation of Concerns**: rotas (HTTP) → usecases (lógica) → database (persistência).
- **Autenticação via Better Auth**: integrada em middleware nas rotas protegidas.
- **Type Safety**: Zod schemas validam entrada/saída de todas as rotas.
- **Transações Atômicas**: operações críticas com `prisma.$transaction()`.
- **Logging Estruturado**: Pino para debug e monitoramento.
- **Dokumentação Automática**: OpenAPI 3.0 gerado a partir dos schemas.

---

## 🔄 Fluxos de Produto

### 1. Autenticação

1. Cliente chama `/api/auth/social/signin` com provedor (Google).
2. Better Auth gerencia OAuth flow, cria sessão e retorna cookie.
3. Sessão é validada em `fromNodeHeaders()` em cada rota protegida.

### 2. Onboarding Inteligente

1. Usuário acessa chat (`POST /ai/`).
2. IA valida se há dados cadastrados via `getUserTrainData`.
3. Se vazio, solicita: peso, altura, idade, % gordura corporal.
4. Dados são salvos com `upsertUserTrainData` (conversão kg → gramas).

### 3. Criação de Plano de Treino

1. Chat coleta objetivo, dias/semana e restrições do usuário.
2. IA gera estrutura completa do plano (7 dias com exercícios).
3. `createWorkoutPlan` persiste com transação atômica.
4. Plano fica ativo e disponível em `/workout-plans/`.

### 4. Execução de Treino

1. `POST /workout-plans/{id}/days/{dayId}/sessions` inicia sessão.
2. `PATCH /workout-plans/{id}/days/{dayId}/sessions/{sessionId}` com `completedAt` finaliza.
3. Estatísticas são recalculadas automaticamente.

### 5. Dashboard e Estatísticas

1. `GET /home/{date}` retorna: treino do dia, streak, consistência por dia.
2. `GET /stats/?from=&to=` retorna: completadas, taxa conclusão, tempo total.

---

## 🔌 Endpoints Principais

### 🏠 Home

| Método | Endpoint       | Finalidade                                             |
| ------ | -------------- | ------------------------------------------------------ |
| GET    | `/home/{date}` | Dados do dashboard (treino hoje, streak, consistência) |

### 👤 Usuário

| Método | Endpoint | Finalidade                                              |
| ------ | -------- | ------------------------------------------------------- |
| GET    | `/me/`   | Buscar dados de treino (peso, altura, idade, % gordura) |
| PUT    | `/me/`   | Criar/atualizar dados de treino                         |

### 📊 Estatísticas

| Método | Endpoint                                | Finalidade              |
| ------ | --------------------------------------- | ----------------------- |
| GET    | `/stats/?from=YYYY-MM-DD&to=YYYY-MM-DD` | Estatísticas do período |

### 📅 Planos de Treino

| Método | Endpoint                                                | Finalidade                             |
| ------ | ------------------------------------------------------- | -------------------------------------- |
| GET    | `/workout-plans/`                                       | Listar todos os planos                 |
| POST   | `/workout-plans/`                                       | Criar novo plano                       |
| GET    | `/workout-plans/{id}`                                   | Detalhes do plano                      |
| GET    | `/workout-plans/{id}/days/{dayId}`                      | Detalhes de um dia específico          |
| POST   | `/workout-plans/{id}/days/{dayId}/sessions`             | Iniciar sessão de treino               |
| PATCH  | `/workout-plans/{id}/days/{dayId}/sessions/{sessionId}` | Atualizar sessão (registrar conclusão) |

### 💬 Chat IA

| Método | Endpoint | Finalidade                                                             |
| ------ | -------- | ---------------------------------------------------------------------- |
| POST   | `/ai/`   | Stream de chat com IA (suporta tools: criarPlano, atualizarDados, etc) |

### 📚 Documentação

| Método | Endpoint        | Finalidade                          |
| ------ | --------------- | ----------------------------------- |
| GET    | `/swagger.json` | Schema OpenAPI 3.0                  |
| GET    | `/docs/`        | UI Scalar (documentação interativa) |

---

## 🔒 Segurança

### Implementações

- **✅ Autenticação JWT via Better Auth**: cookies seguros com `sameSite=strict`.
- **✅ CORS configurado**: apenas `WEB_APP_BASE_URL` pode acessar.
- **✅ Validação com Zod**: entrada/saída de todas as rotas.
- **✅ Rate Limiting**: considerar adicionar para produção.
- **✅ Transações ACID**: garante consistência em operações críticas.
- **✅ Variáveis de ambiente**: nunca commitadas, carregadas via `.env`.

---

## ⚙️ Variáveis de Ambiente

```env
# Servidor
PORT=8080

# Database
DATABASE_URL="postgresql://usuario:senha@localhost:5432/treinos_api"

# Autenticação
BETTER_AUTH_SECRET="seu-secret-muito-seguro-aqui"

# URLs
API_BASE_URL="http://localhost:8080"
WEB_APP_BASE_URL="http://localhost:3000"

# Google OAuth
GOOGLE_CLIENT_ID="seu-client-id.apps.googleusercontent.com"
GOOGLE_CLIENT_SECRET="seu-client-secret"

# IA
GOOGLE_GENERATIVE_AI_API_KEY="sua-chave-google-ai"
OPENAI_API_KEY="sk-proj-..."
```

---

## 🏃 Como Rodar Localmente

### Pré-requisitos

- Node.js 24+
- PostgreSQL 14+
- pnpm (recomendado) ou npm

### 1. Clonar e Instalar Dependências

```bash
git clone <url-do-repositorio>
cd treinos-api
pnpm install
# alternativa
# npm install
```

### 2. Configurar Banco de Dados

```bash
# Criar arquivo .env
cp .env.example .env
```

Preencha os valores do `.env` com suas credenciais PostgreSQL.

### 3. Executar Migrações Prisma

```bash
pnpm exec prisma migrate dev --name init
```

Isso cria as tabelas no banco e gera o cliente Prisma.

### 4. Executar em Desenvolvimento

```bash
pnpm dev
```

API disponível em `http://localhost:8080`  
Documentação em `http://localhost:8080/docs`

---

## 📝 Scripts Disponíveis

```bash
pnpm dev              # Inicia servidor com modo watch
pnpm build            # Compila TypeScript e gera Prisma
pnpm start            # Inicia servidor compilado (produção)
```

### Prisma

```bash
pnpm exec prisma migrate dev   # Cria/aplica migrações (dev)
pnpm exec prisma migrate deploy # Aplica migrações (produção)
pnpm exec prisma generate       # Regenera cliente Prisma
pnpm exec prisma studio         # Abre UI para gerenciar dados
```

### Linting

```bash
pnpm exec eslint src/
pnpm exec prettier --write src/
```

---

## 📚 Documentação da API

A API expõe documentação automática em dois formatos:

- **Swagger JSON**: `GET /swagger.json` (raw OpenAPI 3.0)
- **Scalar UI**: `GET /docs/` (interface interativa)

Ambas são geradas automaticamente a partir dos schemas Zod das rotas.

---

## 🚀 Deploy

### Build de Produção

```bash
pnpm build
pnpm start
```

### Variáveis para Produção

Certifique-se de configurar todas as variáveis de ambiente no provedor:

- `PORT`
- `DATABASE_URL` (use PostgreSQL em nuvem, ex: Vercel Postgres, Railway)
- `BETTER_AUTH_SECRET`
- `API_BASE_URL`
- `WEB_APP_BASE_URL`
- `GOOGLE_CLIENT_ID` e `GOOGLE_CLIENT_SECRET`
- `GOOGLE_GENERATIVE_AI_API_KEY` e/ou `OPENAI_API_KEY`

### Docker (Opcional)

Projeto inclui `Dockerfile` e `docker-compose.yml`:

```bash
docker-compose up
```

---

## 🎨 Boas Práticas

- **Tipagem Forte**: TypeScript strict mode, Zod para validação.
- **Logs Estruturados**: Pino com contexto e níveis (debug, info, error).
- **Tratamento de Erros**: Exceções customizadas com códigos padronizados.
- **Separação de Responsabilidades**: routes → usecases → database.
- **Migrations Versionadas**: histórico completo com Prisma Migrate.
- **Documentação Automática**: OpenAPI/Swagger sempre sincronizados.

---

## 📄 Licença

Este projeto está sob a licença MIT. Veja o arquivo [LICENSE](LICENSE) para mais detalhes.

---

## 👨‍💻 Autor

**Lucas Sarasa**

- 🌐 GitHub: [@lucasarasa](https://github.com/lucasarasa)
- 💼 LinkedIn: [Lucas Sarasa](https://www.linkedin.com/in/lucassarasa/)
- ✉️ Email: lucasmsarasa@gmail.com

---

<div align="center">
  <p>Desenvolvido com ❤️ por Lucas Sarasa</p>
  
  ⭐ Deixe uma estrela se este projeto te ajudou!
</div>
