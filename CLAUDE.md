# CLAUDE.md — OSSEGREDOSDOVITORIO

Site gerado pelo **SF (Site Factory)** em 15/04/2026.

## Contexto do Site

**Nome:** OSSEGREDOSDOVITORIO
**Nicho:** Marketing Digital
**Keywords:** NOS ENXERGAMOS O MUNDO DE FORMA DIFERENTE Nos do Os segredos do
**Paleta de cores:** ocean | **Fonte:** inter

NÓS ENXERGAMOS O MUNDO DE FORMA DIFERENTE. Nós, do Os segredos do Vitório queremos mudar a forma que você enxerga uma agência de marketing digital. Quem nos contrata tem experiências únicas de processo de trabalho, muita pró-atividade, organização e talento que são fundamentais para atingir os objetivos propostos para o projeto. Primeiro, o que nos move a trabalhar todos os dias é a vontade de compartilhar conhecimentos com todas as empresas donas de e-commerce. Fazemos isso por puro amor a nossa missão, ao nosso propósito e à nossa profissão. Mesmo que muitos clientes tenham chegado até nós após lerem algum conteúdo no nosso blog, temos a certeza que estamos fazendo a coisa certa, que estamos mudando vidas e que esse blog para compartilhamento de conteúdos conhecimentos sobre e-commerce, táticas e estratégias, é o maior ápice de amor ao próximo que podemos ter. São vários e vários comentários de pessoas que gostaram dos nossos conteúdos, e isso é digno demais. Hoje, em 2018, estamos reformulando tudo, mas já aviso de antemão que a cada dia mais você irá se surpreender. Sobre a Empresa A nossa empresa ajuda desde 2009 seus clientes crescerem. Entregamos mais de 105 sites e milhares de outras ações que fizeram nossos clientes inovar e obter resultados. Nossa equipe, formada por profissionais de marketing, publicidade e jornalismo, além de um viés analítico e gestor de negócios.  Tudo isso nos torna especialistas em marketing digital, criação de sites e gestão de mídias sociais. Mais que tudo isso.



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
  content/blog/    # Posts em Markdown
  pages/           # Rotas Astro (index, sobre, contato, blog, privacidade, termos)
  layouts/         # BaseLayout com fonte e cores dinâmicas
  styles/          # global.css com variáveis CSS de cor
public/
  images/          # hero.jpg, about.jpg, blog/*.jpg — inseridos automaticamente via Pexels
```

## O que editar

### Textos e conteúdo
- **`src/data/home.json`** — hero (título, subtítulo, botão), features (título, items), about section (título, desc, stats), posts
- **`src/data/sobre.json`** — conteúdo completo da página Sobre (hero, texto, missão)
- **`src/data/contato.json`** — título, subtítulo, email, tempo de resposta
- **`src/data/siteConfig.json`** — nome, slug, email, redes sociais, menu

### Imagens
Imagens já estão em `public/images/` (via Pexels). Para substituir, mantenha os mesmos nomes de arquivo:
- `hero.jpg` — imagem de fundo do Hero
- `about.jpg` — imagem da seção About (home)
- `sobre.jpg` — imagem de fundo da página Sobre
- `blog/{slug}.jpg` — imagens dos posts

### Posts do blog
Arquivos em `src/content/blog/`. Ajuste o tom de voz, adicione dados específicos do nicho e personalize conforme a identidade do site.

### Cores
Variáveis em `src/styles/global.css`: `--color-primary`, `--color-accent`, `--color-dark`.

## Deploy

```bash
bun install
bun run build
# Faça upload da pasta dist/ para Netlify, Vercel ou hosting estático
```
