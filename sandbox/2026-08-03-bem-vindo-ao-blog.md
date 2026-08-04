---
title: "Bem-vindo ao blog"
tags: [meta, blog]
---

Este é o primeiro post. Para criar um novo, basta adicionar um arquivo
Markdown dentro da pasta `_posts/`, seguindo o padrão de nome:

```
AAAA-MM-DD-titulo-do-post.md
```

E começando com um cabeçalho como este:

```yaml
---
title: "Título do post"
tags: [tag-um, tag-dois]
---
```

O campo `tags` é opcional. Se você incluir, as tags aparecem logo depois da
data de publicação, e o post passa a listar também em `/tags/`.

Tudo que vier depois do cabeçalho é o corpo do post, escrito em **Markdown**
normal: `# títulos`, `**negrito**`, `*itálico*`, listas, links, imagens,
blocos de código, tudo funciona.

Não existe botão "publicar" — o próprio ato de fazer *commit* do arquivo (ou
dar merge de um Pull Request) é o que publica o post no ar, porque o GitHub
Pages reconstrói o site automaticamente a cada push na branch principal.

Duas formas de escrever posts novos:

1. **Pelo site do GitHub** (mais parecido com o Blogger): abra a pasta
   `_posts`, clique em "Add file → Create new file", escreva o conteúdo e
   clique em "Commit changes". Pronto, post publicado em ~1 minuto.
2. **Pelo computador**: crie o arquivo localmente, `git add`, `git commit`,
   `git push`.

Divirta-se escrevendo.
