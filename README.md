
# Skild – The Registry for Agentic Intelligence

Skild é um registro de habilidades agenticas ("skills") para agentes, bots e fluxos de IA. Descubra, publique e opere capacidades reutilizáveis de agentes a partir de um workspace orientado a rotas.

## Principais Tecnologias

- [TanStack Start](https://tanstack.com/start) (React, TanStack Router, TanStack Query)
- [Firebase Data Connect](https://firebase.google.com/docs/data-connect) (PostgreSQL gerenciado)
- [Clerk](https://clerk.com) para autenticação
- [Tailwind CSS](https://tailwindcss.com/) para estilos
- [Biome](https://biomejs.dev/) para lint/format

## Como rodar localmente

```bash
npm install
npm run dev
```
Acesse http://localhost:3000

## Build de produção

```bash
npm run build
```

## Testes

```bash
npm run test
```

## Lint e formatação

```bash
npm run lint
npm run format
npm run check
```

## Estrutura de dados

O backend usa Firebase Data Connect com PostgreSQL. O schema principal está em `dataconnect/schema/schema.gql`:

- **User**: clerkId, email, username, imageUrl
- **Skill**: id, author (User), title, description, tags, installCommand, promptConfig, usageExample, createdAt

## Autenticação

O login é feito via Clerk. Configure a variável `VITE_CLERK_PUBLISHABLE_KEY` no `.env.local`.

## Desenvolvimento

- Rotas em `src/routes/`
- Componentes em `src/components/`
- Integração Data Connect em `src/lib/firebase.ts`
- Geração de tipos/SDK em `src/dataconnect-generated/`

## Skills e Data Connect

As operações de leitura e escrita de skills são feitas via Data Connect. Veja exemplos de queries em `dataconnect/Skill_read.gql` e mutations em `dataconnect/Skill_insert.gql`.

## Estilos

O projeto usa Tailwind CSS. O arquivo principal de estilos é `src/styles.css`.

## Observações

- O projeto é orientado a rotas (file-based routing com TanStack Router)
- O layout global está em `src/routes/__root.tsx`
- O Navbar está em `src/components/Navbar.tsx`

## Créditos

Projeto baseado em TanStack Start, com integrações para Firebase Data Connect e Clerk.

## Linting & Formatting

This project uses [Biome](https://biomejs.dev/) for linting and formatting. The following scripts are available:


```bash
npm run lint
npm run format
npm run check
```


## Setting up Clerk

1. Sign up at [clerk.com](https://clerk.com) and create an application
2. Copy the **Publishable Key** from the Clerk dashboard
3. Set it in your `.env.local`:
   ```bash
   VITE_CLERK_PUBLISHABLE_KEY=pk_test_...
   ```
4. Visit the demo route at `/demo/clerk` once `npm run dev` is running

### What's wired up

- **`<ClerkProvider>`** at the app root (`src/integrations/clerk/provider.tsx`) handles auth context for the whole tree
- **`<SignInButton>` / `<UserButton>`** in the header swap based on auth state
- **`/demo/clerk`** shows Clerk's prebuilt sign-in UI and a signed-in greeting

### Protecting a route

## Lint e formatação

Este projeto utiliza o [Biome](https://biomejs.dev/) para lint e formatação. Os scripts disponíveis são:

```bash
npm run lint
npm run format
npm run check
```

## Configuração do Clerk

1. Cadastre-se em [clerk.com](https://clerk.com) e crie uma aplicação
2. Copie a **Publishable Key** do painel do Clerk
3. Defina no seu `.env.local`:
   ```bash
   VITE_CLERK_PUBLISHABLE_KEY=pk_test_...
   ```
4. Acesse rotas protegidas após rodar `npm run dev`

O `<ClerkProvider>` em `src/integrations/clerk/provider.tsx` gerencia o contexto de autenticação. O `<UserButton>` aparece no cabeçalho quando autenticado, e o botão de login quando não autenticado.

Para proteger uma rota, utilize os componentes `<SignedIn>` e `<SignedOut>` do Clerk:

```tsx
import { SignedIn, SignedOut, RedirectToSignIn } from '@clerk/clerk-react'

function PaginaProtegida() {
  return (
    <>
      <SignedIn>
        <SeuConteudo />
      </SignedIn>
      <SignedOut>
        <RedirectToSignIn />
      </SignedOut>
    </>
  )
}
```

No deploy, lembre-se de usar as chaves de produção e configurar o domínio no painel do Clerk.

## Componentes Shadcn

Adicione componentes com:

```bash
pnpm dlx shadcn@latest add button
```

## Rotas

O projeto usa [TanStack Router](https://tanstack.com/router) com roteamento baseado em arquivos. As rotas ficam em `src/routes`.

Para adicionar uma rota, crie um novo arquivo em `src/routes/`. Use o componente `Link` para navegação SPA:

```tsx
import { Link } from "@tanstack/react-router";

<Link to="/sobre">Sobre</Link>
```

O layout global está em `src/routes/__root.tsx`.

## Funções de servidor e API

Você pode criar funções de servidor e rotas de API usando TanStack Start. Veja a documentação oficial para exemplos avançados.

## Carregamento de dados

Use TanStack Query ou o loader das rotas para buscar dados do backend. Veja exemplos em `src/routes/index.tsx`.

# Arquivos demo

Arquivos com prefixo `demo` podem ser removidos. Eles servem apenas como exemplo.

# Saiba mais

Mais informações em [TanStack](https://tanstack.com) e [TanStack Start](https://tanstack.com/start).
      { charSet: 'utf-8' },
