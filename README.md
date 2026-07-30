# GL Contabilidade Digital — site institucional

Next.js 16 (App Router) · TypeScript · Tailwind CSS v4 · Framer Motion · lucide-react

## Rodar localmente

```bash
npm install
npm run dev
```

Acesse http://localhost:3000

## Build de produção (testado e validado neste projeto)

```bash
npm run build
npm start
```

## Estrutura do Tailwind v4 (sem tailwind.config.js)

O Tailwind v4 usa configuração "CSS-first": não existe mais `tailwind.config.ts` por padrão.
Toda a paleta de cores, fontes e tokens do projeto está em `app/globals.css`, dentro do bloco `@theme`.
O PostCSS usa apenas o plugin oficial `@tailwindcss/postcss` (ver `postcss.config.mjs`).

Isso é a estrutura oficial recomendada pela documentação do Next.js + Tailwind v4 — adicionar um
`tailwind.config.ts` vazio por cima disso seria redundante e é o motivo mais comum de estilos
"sumirem" (dois sistemas de config brigando).

## Deploy na Vercel

Eu não tenho acesso para publicar diretamente na sua conta Vercel — falta a parte de deploy real,
que só você pode autorizar. Passo a passo:

**Opção A — via GitHub (recomendado)**
1. Suba esta pasta para um repositório no GitHub.
2. Em https://vercel.com/new, importe o repositório.
3. Framework preset: "Next.js" (detectado automaticamente). Não é preciso configurar nada manualmente.
4. Deploy.

**Opção B — via CLI**
```bash
npm i -g vercel
vercel
vercel --prod
```

Qualquer uma das duas opções já builda com o `npm run build` validado aqui, então os estilos
carregarão normalmente em produção.

## Estrutura de pastas

```
app/
  layout.tsx      → fontes (Google Fonts via <link>), metadata, JSON-LD
  globals.css      → @import "tailwindcss" + tokens @theme + estilos de assinatura
  page.tsx         → monta as seções da home
  robots.ts        → robots.txt gerado nativamente pelo Next.js
  sitemap.ts        → sitemap.xml gerado nativamente pelo Next.js
components/         → uma seção por arquivo (Hero, Benefits, Plans, Faq, etc.)
public/assets/       → logo e foto do responsável técnico
```
