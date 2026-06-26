# People Pilot

Front-end do People Pilot, construído com [Next.js](https://nextjs.org) (App Router).

## Stack

- [Next.js 16](https://nextjs.org/docs) (App Router) + [React 19](https://react.dev) + TypeScript
- [TailwindCSS 4](https://tailwindcss.com) + [shadcn/ui](https://ui.shadcn.com)
- [React Hook Form](https://react-hook-form.com) + [Zod](https://zod.dev) para validação de formulários

## Getting Started

Instale as dependências e copie as variáveis de ambiente:

```bash
npm install
cp .env.example .env.local
```

Suba o servidor de desenvolvimento:

```bash
npm run dev
```

Abra [http://localhost:3000](http://localhost:3000) no navegador.

## Scripts

| Comando | Descrição |
| --- | --- |
| `npm run dev` | Servidor local em modo desenvolvimento |
| `npm run build` | Build de produção |
| `npm run start` | Sobe o build de produção |
| `npm run lint` | Lint com ESLint |
| `npm run type-check` | Checagem de tipos com `tsc --noEmit` |

Após uma série de mudanças, rode `npm run type-check && npm run lint`.

## Estrutura do projeto

```
app/         # rotas (App Router), agrupadas por (grupo)/
actions/     # Server Actions (mutações)
components/  # componentes de feature
components/ui/ # primitivos shadcn/ui
lib/         # helpers e clients (ex: supabase, stripe)
types/       # tipos globais e schemas Zod compartilhados
```

- Server Components por padrão — `'use client'` apenas quando necessário (hooks, eventos, browser APIs)
- Mutações sempre via Server Actions em `actions/`, nunca acesso a banco direto em Client Components

## Convenções de código

- Sem `any` explícito — usar `unknown` + type guard
- Tailwind only — sem CSS inline ou styled-components
- Novos design tokens entram em `tailwind.config.ts` antes de uso
- Arquivos em kebab-case, componentes em PascalCase
- Branches: `feat/`, `fix/`, `chore/` + descrição em kebab-case
- Commits em inglês, no imperativo (ex: `add OAuth callback handler`)

Guia completo de arquitetura e convenções para agentes/contribuidores em [CLAUDE.md](./CLAUDE.md).

## Deploy

O deploy é feito via [Vercel](https://vercel.com). Veja a [documentação de deploy do Next.js](https://nextjs.org/docs/app/building-your-application/deploying) para detalhes.
