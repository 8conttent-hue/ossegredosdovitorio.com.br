# CLAUDE.md — OSSEGREDOSDOVITORIO

Site gerado pelo **SF (Site Factory)** em 15/04/2026. Migrado para o modelo Cloudflare + Supabase em 25/09/2026.

## Contexto do Site

**Nome:** OSSEGREDOSDOVITORIO
**Nicho:** Marketing Digital
**Keywords:** NOS ENXERGAMOS O MUNDO DE FORMA DIFERENTE Nos do Os segredos do
**Paleta de cores:** ocean | **Fonte:** inter

NÓS ENXERGAMOS O MUNDO DE FORMA DIFERENTE. Nós, do Os segredos do Vitório, queremos mudar a forma que você enxerga uma agência de marketing digital. Quem nos contrata tem experiências únicas de processo de trabalho, muita pró-atividade, organização e talento que são fundamentais para atingir os objetivos propostos para o projeto. O que nos move a trabalhar todos os dias é a vontade de compartilhar conhecimentos com todas as empresas donas de e-commerce. Mesmo que muitos clientes tenham chegado até nós após lerem algum conteúdo no nosso blog, temos a certeza que estamos fazendo a coisa certa e que esse blog para compartilhamento de conteúdos sobre e-commerce, táticas e estratégias, é o maior ápice de amor ao próximo que podemos ter. A nossa empresa ajuda desde 2009 seus clientes crescerem. Entregamos mais de 105 sites e milhares de outras ações que fizeram nossos clientes inovar e obter resultados.

## Componentes visuais usados

| Seção | Variante |
|-------|----------|
| Header | Header-B |
| Hero | Hero-D |
| Features | Features-D |
| About Section | About-H |
| Posts | Posts-G |
| Footer | Footer-B |
| Página Sobre | Sobre-I |
| Página Contato | Contato-H |

## Estrutura do projeto

```
src/
  sections/        # Layout escolhido pelo SF — Header, Hero, Features, About, Posts, Footer, Sobre, Contato
  data/            # JSONs com todo o conteúdo editável
  lib/             # supabase.ts (cliente) e posts.ts (getPosts/getPostBySlug)
  components/      # Seo.astro (meta tags + JSON-LD)
  pages/           # Rotas Astro (index, sobre, contato, blog, privacidade, termos, [...slug])
  layouts/         # BaseLayout com fonte e cores dinâmicas
  styles/          # global.css com variáveis CSS de cor
public/
  images/          # hero.jpg, about.jpg, sobre.jpg
```

## O que editar

### Textos e conteúdo
- **`src/data/home.json`** — hero (título, subtítulo, botão), features (título, items), about section (título, desc, stats), posts
- **`src/data/sobre.json`** — conteúdo completo da página Sobre (hero, texto, stats)
- **`src/data/contato.json`** — título, subtítulo, email, tempo de resposta
- **`src/data/siteConfig.json`** — nome, slug, email, redes sociais, menu (título/descrição/OG/JSON-LD derivam daqui)

### Imagens
Imagens já estão em `public/images/` (via Pexels). Para substituir, mantenha os mesmos nomes de arquivo:
- `hero.jpg` — imagem de fundo do Hero (e og:image padrão)
- `about.jpg` — imagem da seção About (home)
- `sobre.jpg` — imagem de fundo da página Sobre

### Posts do blog
Os posts NÃO ficam mais em markdown local. São carregados do Supabase (tabela `network_posts`, filtrados por `domain = ossegredosdovitorio.com.br`).
- `src/lib/posts.ts` — `getPosts()` e `getPostBySlug()`; `formatContentToHtml()` converte markdown → HTML.
- Sem painel admin. Novos posts/posts editados entram pela plataforma 8links e publicam automaticamente (via Git/CF).

### Cores
Variáveis em `src/styles/global.css`: `--color-primary`, `--color-accent`, `--color-dark`.

## SEO

- `src/components/Seo.astro` injetado pelo `BaseLayout`: title, description, canonical, OG, Twitter, `name="robots"`, JSON-LD (WebSite nas páginas estáticas, BlogPosting nos artigos).
- `src/pages/robots.txt.ts` e `src/pages/sitemap.xml.ts` gerados dinamicamente (sitemap inclui posts com lastmod).

## Deploy

```bash
bun install
bun run build
# Publicar no Cloudflare: a pasta dist/ é servida como Worker (adaptador @astrojs/cloudflare)
# Envs opcionais no CF: SUPABASE_URL e SUPABASE_ANON_KEY (fallbacks embutidos no código)
```