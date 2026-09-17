# hugoramos.dev

Site profissional de Hugo Ramos, desenvolvido em Astro e publicado como site estático.

## Objetivo

Centralizar identidade profissional, projetos, publicações e artigos técnicos em um domínio próprio, com foco em performance, acessibilidade, SEO técnico e descoberta por mecanismos de busca e sistemas de IA.

## Stack

- Astro
- TypeScript
- Markdown Content Collections
- GitHub Actions
- GitHub Pages

## Desenvolvimento local

```bash
npm install
npm run dev
```

Validação:

```bash
npm run check
npm run build
```

## Conteúdo

Projetos ficam em `src/content/projects/` e artigos em `src/content/articles/`.

O site é gerado de forma estática, sem banco de dados ou backend em runtime.

## Deploy

Pushes para `main` executam `.github/workflows/deploy-pages.yml`, geram o site em `dist/` e publicam no GitHub Pages.

Domínio canônico: `https://hugoramos.dev`.
