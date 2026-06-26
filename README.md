# People Pilot

**People Pilot** é uma plataforma de gestão de pessoas (RH) construída com foco em performance e experiência do usuário. O sistema permite gerenciar colaboradores, times, onboarding, avaliações e muito mais, tudo em um único lugar.

Front-end desenvolvido com [Next.js](https://nextjs.org) App Router e React Server Components, integrado ao [Supabase](https://supabase.com) para autenticação e banco de dados.

---

## Stack

| Camada | Tecnologia |
|---|---|
| Framework | [Next.js 16](https://nextjs.org/docs) (App Router) |
| UI Library | [React 19](https://react.dev) + TypeScript |
| Estilização | [TailwindCSS 4](https://tailwindcss.com) + [tw-animate-css](https://github.com/Wombosvideo/tw-animate-css) |
| Componentes | [shadcn/ui](https://ui.shadcn.com) + [Base UI](https://base-ui.com) + [Lucide React](https://lucide.dev) |
| Formulários | [React Hook Form](https://react-hook-form.com) + [Zod](https://zod.dev) |
| Auth & DB | [Supabase](https://supabase.com) |
| Deploy | [Vercel](https://vercel.com) |

---

## Pré-requisitos

- Node.js 20+
- npm 10+
- Conta no [Supabase](https://supabase.com) (para variáveis de ambiente)

---

## Instalação

```bash
# Clone o repositório
git clone https://github.com/DieguinhoHR/peoplepilot-front.git
cd peoplepilot-front

# Instale as dependências
npm install

# Configure as variáveis de ambiente
cp .env.example .env.local
```

Preencha o `.env.local` com as credenciais do Supabase e demais variáveis necessárias.

```bash
# Suba o servidor de desenvolvimento
npm run dev
```

Acesse [http://localhost:3000](http://localhost:3000) no navegador.

---

## Scripts

| Comando | Descrição |
|---|---|
| `npm run dev` | Servidor local em modo desenvolvimento |
| `npm run build` | Build de produção |
| `npm run start` | Sobe o build de produção |
| `npm run lint` | Lint com ESLint |
| `npm run type-check` | Checagem de tipos com `tsc --noEmit` |

> Após uma série de mudanças, sempre rode: `npm run type-check && npm run lint`

---

## Estrutura do projeto

```
peoplepilot-front/
├── app/                        # Rotas (Next.js App Router)
│   └── (grupo)/
│       └── nome-da-pagina/
│           ├── page.tsx        # Server Component (ponto de entrada)
│           ├── _components/    # Componentes específicos da página
│           │   └── content.tsx
│           ├── _actions/       # Server Actions (mutações + validação Zod)
│           │   └── action.ts
│           └── _data-access/   # Data Access Layer (queries ao banco)
│               └── get-data.ts
│
├── components/
│   └── ui/                     # Primitivos reutilizáveis (shadcn/ui)
│
├── lib/                        # Helpers e clients (supabase, utils)
├── types/                      # Tipos globais e schemas Zod compartilhados
└── public/                     # Assets estáticos
```

### Fluxo de dados

```
page.tsx (Server Component)
  └── busca dados via _data-access/
  └── renderiza _components/content.tsx (Client Component)
        └── usuário interage → chama _actions/
              └── valida com Zod → atualiza banco → retorna resultado
```

---

## Convenções de código

- **Sem `any` explícito** — usar `unknown` + type guard
- **Tailwind only** — sem CSS inline ou styled-components
- **Server Components por padrão** — `'use client'` apenas quando necessário (hooks, eventos, browser APIs)
- **Mutações via Server Actions** — nunca acesso ao banco direto em Client Components
- **Arquivos**: kebab-case | **Componentes**: PascalCase
- **Branches**: `feat/`, `fix/`, `chore/` + descrição em kebab-case
- **Commits**: em inglês, no imperativo (ex: `add OAuth callback handler`)
- **Variáveis de ambiente**: `NEXT_PUBLIC_*` apenas para valores seguros no client

---

## Deploy

O deploy é feito via [Vercel](https://vercel.com). Ao fazer push para `main`, o deploy é acionado automaticamente.

Consulte a [documentação de deploy do Next.js](https://nextjs.org/docs/app/building-your-application/deploying) para mais detalhes.

---

## Guia completo

Arquitetura, convenções e instruções detalhadas para contribuidores e agentes em [CLAUDE.md](./CLAUDE.md).
