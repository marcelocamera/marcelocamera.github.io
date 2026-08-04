---
title: Como decidir se um problema realmente precisa de IA ou regras simples
tags:
  - ia
---
Vamos começar com uma confissão: em algum momento da sua vida profissional, alguém vai te chamar numa sala (ou num canal do Slack, que é a sala de reuniões moderna) e vai dizer a frase mágica:

> "A gente precisa colocar IA nisso?"

E aí, dependendo do seu nível de café no sangue, você vai reagir de duas formas: ou fica animado e já começa a pensar em modelos, ou sente aquele aperto no estômago porque sabe que 80% das vezes esse problema poderia ser resolvido com um `if/else` bem escrito e ninguém precisava treinar nada.

Este post é um guia para você não cair (nem empurrar ninguém) nessa armadilha.

### A pergunta que ninguém faz antes de sair correndo atrás de modelo

Antes de perguntar "qual modelo eu uso?", a pergunta certa é:

> Eu sei exatamente as regras que decidem esse problema?

Se a resposta for **sim, com certeza, consigo escrever isso num quadro branco em 10 minutos**, você provavelmente não precisa de IA. Você precisa de lógica de negócio, e ponto.

Se a resposta for **"bem... depende... tem uns casos meio nebulosos... às vezes funciona, às vezes não"**, aí sim a IA começa a fazer sentido, porque ela é boa exatamente nisso: lidar com padrões complexos que ninguém consegue descrever em regras claras.

### O teste do "eu explico pro estagiário"

Aqui vai um truque simples e nada científico, mas que funciona surpreendentemente bem:

Imagine que você precisa explicar para um estagiário no primeiro dia de trabalho como resolver aquele problema, sem ele saber nada de tecnologia. Só usando bom senso e um passo a passo.

- Se você consegue escrever esse passo a passo em uma lista curta e ele vai acertar 95% das vezes → **regra simples**.
- Se depois de explicar, ele ainda erra muito, porque cada caso é "meio diferente" e exige intuição → **candidato a IA**.

Exemplo clássico de regra simples disfarçada de "problema de IA": "quero identificar pedidos com risco de fraude, se o valor for maior que X e o endereço de entrega for diferente do de cobrança, marca como suspeito." Isso não precisa de machine learning. Isso precisa de um filtro.

Já "quero identificar comportamentos suspeitos de fraude considerando histórico do cliente, padrão de compra, horário, dispositivo e mil outras variáveis que interagem entre si de um jeito que nem eu sei explicar" — aí sim, terreno fértil para um modelo.

### Sinais de que você precisa só de regras (e vai economizar tempo, dinheiro e sofrimento)
- As regras de negócio já existem em algum lugar (manual, política interna, lei, contrato)
- O problema tem poucas variáveis relevantes
- Você consegue prever com clareza todos (ou quase todos) os cenários possíveis
- Errar precisa ser 100% explicável — "por que o sistema decidiu isso?" tem que ter resposta simples
- Os dados que você tem são pequenos, ou você não tem dados históricos suficientes para treinar nada
- O problema muda pouco com o tempo

Se marcou 3 ou mais desses pontos, parabéns: você acabou de economizar um projeto de meses e um orçamento de GPU. Vá escrever um bom código de regras, com testes, documentado, e siga sua vida feliz.

### Sinais de que o problema realmente pede IA
- Existem muitas variáveis interagindo de forma difícil de descrever manualmente
- Você tem dados históricos suficientes e relevantes para aprender padrões
- O "certo" e o "errado" não são binários, existem gradientes e nuances
- Humanos especialistas fazem essa tarefa hoje usando "intuição" e experiência, não uma lista de regras
- O padrão muda com o tempo e regras fixas ficariam desatualizadas rápido
- Já tentaram fazer com regras e o sistema virou uma montanha de exceções e "ses" impossíveis de manter

Esse último ponto, aliás, é um dos melhores indicadores do mundo real: quando o time de regras já tem 200 exceções empilhadas e ninguém mais entende o próprio código, é sinal de que o problema tem complexidade demais para regra fixa — e é aí que a IA entra com folga.

### Um exemplo bem prático pra fixar a ideia

Imagina que você trabalha numa empresa de streaming e recebe dois pedidos:

**Pedido 1:** "Quero bloquear o cadastro de usuários que colocarem CPF com menos de 11 dígitos." Isso é regra. Não precisa de IA. É validação de formato, ponto final.

**Pedido 2:** "Quero recomendar os próximos filmes que esse usuário provavelmente vai gostar, considerando o que ele já assistiu, o que assistiu até o fim, o que abandonou, o horário que costuma assistir e o comportamento de usuários parecidos." Isso é IA. Tentar escrever regra manual pra isso seria escrever um livro de "se o usuário gostou de comédia romântica e assistiu 3 filmes de terror na sexta à noite, então recomenda..." — impossível de manter e sempre incompleto.

A diferença não está na "importância" do problema. Está na natureza dele: quanto mais ele depende de padrões implícitos nos dados, mais pende para IA. Quanto mais ele depende de critérios explícitos e estáveis, mais pende para regra.

### O erro mais caro que empresas cometem

Não é usar regra onde precisava de IA. É o contrário: usar IA (com todo o custo de dados, infraestrutura, manutenção de modelo, explicabilidade e monitoramento) para resolver um problema que uma função de 15 linhas resolveria igual ou melhor.

IA custa caro em três moedas: tempo de desenvolvimento, dinheiro de infraestrutura e complexidade de manutenção. Regra simples é barata nas três. Então a pergunta de ouro antes de qualquer projeto é:

"Se eu resolver isso com regras, o resultado seria pior o suficiente para justificar o custo extra da IA?"

Se a resposta for "não, seria basicamente igual", a decisão está tomada.

### Um mini-checklist pra guardar

Antes de embarcar num projeto de IA, pergunte:

1. Eu sei descrever as regras desse problema em uma lista curta e clara? → Se sim, talvez nem precise ler o resto.
2. Tenho dados históricos suficientes e de qualidade? → Sem dados bons, IA não funciona bem, ponto.
3. O problema muda com frequência ou tem muitas exceções? → Se sim, ponto pra IA.
4. Preciso explicar toda decisão de forma simples e auditável? → Se sim, ponto pra regra (ou pelo menos IA + camada de explicação bem pensada).
5. Já tentei resolver com regras e virou uma bagunça de exceções? → Ponto forte pra IA.

### Pra fechar

IA não é sinônimo de "solução melhor". É uma ferramenta específica para um tipo específico de problema: aquele em que os padrões existem, mas são complexos demais para escrever à mão. Quando alguém chegar pedindo "coloca IA nisso", a resposta profissional não é "sim" ou "não" de cara — é "deixa eu entender o problema primeiro, porque talvez a solução mais inteligente aqui seja simplesmente... simples."