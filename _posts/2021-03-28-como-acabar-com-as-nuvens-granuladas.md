---
layout: post
title: "Como remover nuvens pixeladas (granuladas) no MSFS2020"
author: "Marcelo"
comments: true
tags: flight-simulator dicas
excerpt_separator: <!--more-->
---
O MSFS2020 trouxe um grau de realismo muito alto aos jogos de simulação de voo, mas existem ainda alguns detalhes que precisam ser ajustados. Um deles é a aparência de nuvens granuladas ou pixeladas. Nesse post, vou te explicar o que é como remover esse problema do jogo.
<!--more-->

#### O que granulação ou pixelação
Um pixel é a menor unidade que compõe uma imagem, seja ela de uma foto, de um desenho ou até de um filme. Cada pixel é baseado nas três cores básicas: vermelho, verde e azul. Cada cor possui 256 tonalidades, o que proporciona até 16 milhões de combinações de cores diferentes.

No MSFS2020, devido a qualidade empregada na renderização das nuvens e a velocidade relativa que sua aeronave passa perto delas, é possível identificar áreas onde as núvens ficam pixeladas (ou granuladas). Esse efeito torna o jogo visualmente menos real, uma vez que a aparência das nuvens fica prejudicada.

<figure align="center">
   <img src="/assets/nuvem-pixelada01.webp" alt="msfs2020, fs2020, dicas, tutoriais, flightsimulator">
</figure>

Esse problema deve ser resolvido em algum patch de correção do Flight Simulator, enquanto isso não é liberado, segue uma dica de como atuar.

#### Como acabar com a granulação das nuvens

**Alteração no arquivo UserCfg.opt**
O arquivo UserCfg.opt deve ter dois de seus parâmetros alterados.
O arquivo pode ser encontrado em um dos dois locais.

Para quem usa o MSFS no Steam:
{% highlight markdown %}
%localappdata%\user\Roaming\Microsoft Flight Simulator
{% endhighlight %}

Para quem usa o MSFS na Microsoft Store:
{% highlight markdown %}
%localappdata%\Packages\Microsoft.FlightSimulator_8wekyb3d8bbwe\LocalCache
{% endhighlight %}  

No arquivo, procure pelos parâmetros **Sharpen** e **FilmGrain**. Substitua o valor do parâmetro (número) na frente de casa um desses parâmetros para 0 (zero).

Salve o arquivo.

**Alteração da permissão de escrita do arquivo UserCfg.opt**
Da maneira como foi concebido, o MSFS2020 pode alterar o conteúdo deste arquivo, isso ocorre principalmente quando o jogo é iniciado e durante as atualizações.

Para evitar que isso ocorra durante quando o jogo é iniciado, é possível alterar a permissão de escrita do arquivo.

Clique com o botão direto do mouse em cima do arquivo e escolha a opção **Propriedades**. Quando a janela Propriedade abrir, marcar a opção **Somente Leitura**.

#### Quando o patch de correção for liberado pela Microsoft Asobo
Para quem fez a modificação na permissão de escrita do arquivo **UserCfg.opt**, tem que tomar cuidado com os eventuais updates do MSFS.

É recomendado remover o somente leitura do UserCfg antes de fazer o update, caso contrário você pode ter problemas. Especialmente se no update houver alguma atualização na textura das nuvens.
