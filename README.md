# Seu blog

Blog estático feito com [Jekyll](https://jekyllrb.com), pronto para publicar
no GitHub Pages de graça, com um visual minimalista inspirado no
[zachholman.com](https://zachholman.com/).

## Publicar no GitHub Pages (uma vez só)

1. Crie um repositório novo no GitHub.
   - Se quiser que o blog fique em `https://seu-usuario.github.io`, o
     repositório precisa se chamar exatamente `seu-usuario.github.io`.
   - Se quiser que fique em `https://seu-usuario.github.io/nome-do-repo`, pode
     usar qualquer nome — só ajuste `url` e `baseurl` em `_config.yml`.
2. Suba estes arquivos para o repositório:
   ```bash
   git init
   git add .
   git commit -m "Primeiro commit do blog"
   git branch -M main
   git remote add origin https://github.com/seu-usuario/seu-usuario.github.io.git
   git push -u origin main
   ```
3. No GitHub, vá em **Settings → Pages** e confirme que a fonte é a branch
   `main` (pasta raiz). Se o repositório se chamar `usuario.github.io`, isso
   já costuma vir configurado automaticamente.
4. Espere ~1 minuto e acesse a URL. Pronto, o blog está no ar.

Antes de publicar, edite `_config.yml` com seu nome, bio, links e a URL real
do site, e edite `sobre.md` com sua apresentação.

## Como criar um post novo (o "Publicar" do Blogger)

Sem painel, sem login separado: publicar é fazer commit de um arquivo.

**Opção mais parecida com o Blogger — direto no navegador:**

1. No GitHub, entre na pasta `_posts`.
2. Clique em **Add file → Create new file**.
3. Nomeie o arquivo assim: `2026-08-10-titulo-do-post.md`
   (formato `ANO-MES-DIA-titulo.md` — a data também define a ordem/URL do post).
4. Escreva no topo:
   ```yaml
   ---
   title: "Título do post"
   ---
   ```
   e, embaixo, o texto em Markdown normal.
5. Clique em **Commit changes**. Em menos de um minuto o post aparece no ar.

**Opção pelo computador**, se preferir escrever localmente:

```bash
# crie o arquivo em _posts/, com o mesmo formato acima
git add _posts/2026-08-10-titulo-do-post.md
git commit -m "Novo post: Título do post"
git push
```

## Tags nos posts

Cada post pode ter tags, que aparecem logo depois da data de publicação.
Basta adicionar no cabeçalho:

```yaml
---
title: "Título do post"
tags: [tecnologia, pessoal]
---
```

Tags são opcionais — se não incluir o campo, o post simplesmente não mostra
nenhuma. Todas as tags usadas ficam listadas também em `/tags/`.

## Analytics (saber quantas pessoas visitam o blog)

O blog já vem preparado para o **Google Analytics (GA4)**, gratuito.

1. Crie uma conta em [analytics.google.com](https://analytics.google.com)
2. Crie uma propriedade nova, do tipo "Web", com a URL do seu blog
   (`https://marcelocamera.github.io`)
3. O Google vai te dar um **ID de medição**, no formato `G-XXXXXXXXXX`
4. Cole esse ID no `_config.yml`:
   ```yaml
   google_analytics: "G-XXXXXXXXXX"
   ```
5. Commit + push. Em alguns minutos, o Analytics já começa a registrar visitas.

Pra ver os números depois, acesse [analytics.google.com](https://analytics.google.com) 
e escolha a propriedade do seu blog. Lá você vê visitantes, quais posts são
mais lidos, de onde as pessoas vêm (Google, Twitter, direto, etc.), países, e
mais.

Se preferir uma opção mais simples e sem rastrear tanto dado pessoal, existem
alternativas leves e gratuitas/baratas como
[GoatCounter](https://www.goatcounter.com/) (grátis, open source, só um
contador de visitas) ou [Plausible](https://plausible.io/) (pago, foco em
privacidade). Ambas funcionam do mesmo jeito: você cola um `<script>` no
`_includes/analytics.html` no lugar do do Google, ou complementando ele.

## Página de métricas do blog

Existe uma página em `/metricas/` que mostra estatísticas do próprio
conteúdo, calculadas automaticamente pelo Jekyll a cada publicação — sem
precisar de nenhum serviço externo:

- Total de posts publicados
- Total de tags diferentes usadas
- Total de palavras escritas e média de palavras por post
- Data do primeiro e do post mais recente
- Lista de tags com a quantidade de posts em cada uma

Ela é gerada pelo arquivo `metricas.md` — não precisa editar nada, os números
atualizam sozinhos conforme você publica.

**Sobre visitas e tráfego:** como o blog é 100% estático (sem servidor), a
página não consegue puxar sozinha os números de visitantes do Google
Analytics — isso exigiria expor uma credencial de API no próprio código do
site, o que não é seguro em um repositório público. Por isso, a página de
métricas linka direto para o [painel do Google Analytics](https://analytics.google.com),
onde ficam os dados de visitas.

Se no futuro você quiser números de visita *dentro* da própria página (não só
o link), a alternativa mais simples é trocar o Google Analytics pelo
[GoatCounter](https://www.goatcounter.com/), que permite deixar as
estatísticas públicas e embutir um contador via `<iframe>` direto no
`metricas.md` — posso montar isso se você decidir seguir por esse caminho.

## Rodar localmente antes de publicar (opcional)

Precisa de Ruby instalado.

```bash
bundle install
bundle exec jekyll serve
```

Abre em `http://localhost:4000`.

## Estrutura do projeto

```
_config.yml       → título, bio, links sociais, URL do site
_posts/           → cada arquivo .md aqui é um post
_layouts/         → templates HTML (home, post, página)
_includes/        → cabeçalho (sidebar) e rodapé
assets/css/       → o visual do blog (style.css)
sobre.md          → página estática de exemplo (/sobre/)
index.html        → página inicial, lista os posts por ano
```

## Personalizar o visual

Todo o estilo está em `assets/css/style.css`. Pontos fáceis de ajustar:

- `--ink`, `--bg`, `--muted` no topo do arquivo → cores.
- `--serif` / `--sans` → fontes.
- `.wrap { grid-template-columns: 220px 1fr; }` → largura da coluna lateral.
