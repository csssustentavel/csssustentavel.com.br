---
layout: chapter
title: Semântica
section: Visão Geral
permalink: /capitulos/semantica/
description: Porque nomear algo baseado no que ele é, ao invés de como é sua aparência e como é seu comportamento é a base de um CSS bem arquiteturado e sustentável.
---

Semântica não diz respeito apenas aos elementos do HTML. É óbvio que devemos usar `<a>` para links, `<table>` para tabelas, `<p>` para parágrafos e assim em diante. O que não é tão óbvio: os nomes que usamos para classes.

Como Phil Karton diz, *apenas duas coisas são difíceis em Ciência da Computação: invalidação do cache e **nomear coisas***. Então um capítulo dedicado a isso parece uma coisa razoável.

Nomear é o que há de mais importante na hora de escrever um CSS Sustentável. Existem dois jeitos de escrever CSS: semanticamente, e não semanticamente. Vamos ver como são eles.

## Semântico vs Não-semântico

Aqui estão umas classes não-semânticas:

	<div class="vermelho puxar-esquerda pb3">
	<div class="grid row">
	<div class="col-xs-4">

Classes não-semânticas não passam a ideia do *quê* o elemento representa. No mais eles nos dão uma ideia de como ele se *parece*. Classes atômicas, visuais, comportamentais e utilitárias não são semânticas.

Agora, umas classes semânticas:

	<div class="cesta">
	<div class="produto">
	<div class="resultadosBusca">

As classes semânticas não passam a ideia de como se parecem, mas tudo bem. É pra isso que serve o CSS. Classes semânticas conversam com o HTML, CSS, Javascript e testes automatizados.

Existem muitos benefícios em usar classes semânticas:

## 1. São de fácil leitura

Aqui está um snippet real de classes atômicas:

	<div class="pb3 pb4-ns pt4 pt5-ns mt4 preto-70 fl-l w-50-1">
		<h1 class="f4 fw6 f1-ns lh-titulo medida mt0">Título</h1>
	<p class="f5 f4-ns fw4 b medida dib-m lh-copy">Parágrafo</p>
	</div>

Notas:

- Nós precisamos mapear mentalmente as abreviações, partindo do princípio que sabemos o que elas significam.
- Precisamos passar por muitas classes para entender o que está acontecendo; quais classes sobrescrevem as outras, quais são aplicadas em determinados break points etc.
- Essas classes são ambíguas. Por exemplo, `preto-70` significa a cor do fundo ou a cor da fonte? Se precisamos inspecionar para saber isso, confirmamos que os nomes das classes não são de fácil leitura.
- O conteúdo é facilmente ofuscado pelo tanto de HTML na tela.

Aqui temos o mesmo com classes semânticas:

	<div class="artigo">
		<h1 class="artigo-titulo">Título</h1>
		<p class="artigo-paragrafo">Parágrafo</p>
	</div>

Notas:

- Essas classes são fáceis de ler. Não é necessário mapear nada.
- O conteúdo aparece com mais clareza.
- Conseguimos ver onde o módulo começa e onde ele termina.
- A inspeção dos elementos se torna muito mais fácil.
- O HTML fica com metade do tamanho.

## 2. É melhor para construir sites responsivos

Imagine estar codificando um grid responsivo de duas colunas, onde:

* cada coluna tem `20px` e `50px` de padding em telas pequenas e grandes;
* cada coluna tem `2em` e `3em` de font-size em telas pequenas e grande; e
* as colunas são empilhadas em telas pequenas. Note que o nome *coluna* para a classe se torna enganoso.

Geralmente, é feito assim usando classes utilitárias e visuais:

	<div class="grid clearfix">
		<div class="col pd20 pd50 fs2 fs3">Coluna 1</div>
		<div class="col pd20 pd50 fs2 fs3">Coluna 2</div>
	</div>

Notas:

- Temos 7 classes, e algumas se sobrepõem.
- Para fazer as colunas verdadeiramente responsivas, precisaríamos de uma classe `fs3grande` etc. Isso significa que estaríamos usando uma convenção de nomes que recria as linguagens encontradas no CSS.
- Em certos break points, as classes se tornam redundantes e enganosas. Por exemplo `.clearfix` não faz nada em telas menores.

Mal começamos a avaliar este componente simples e já temos uma dor significativa.

Aqui temos o mesmo usando classes semânticas:

	<div class="coisa">
		<div class="coisa-coisa1"></div>
		<div class="coisa-coisa2"></div>
	</div>

Notas:

- As classes estão encapsuladas no conteúdo e estilo do módulo.
- É mais fácil estilizar elementos sem ter que escrever muitas classes e sem ter que mudar o HTML tantas vezes.
- As classes fazem sentido em telas pequenas e grandes.
Podemos usar media queries para remover elementos apenas quando necessário.

> Question: Pergunta: O quão valioso é um sistema de grids responsivo? O layout deveria se adaptar ao conteúdo, e não o contrário.

## 3. São mais fáceis de achar

Buscar por HTML com classes não-semânticas gera muitos resultados. Como as classes semânticas são únicas, buscar por elas retornam apenas um resultado, facilitando a manutenção do HTML.

## 4. Elas eliminam o risco de regressão

Atualizar uma classe visual poderia causar regressão através de muitos elementos. Atualizando uma classe semântica vai mudar apenas o módulo envolvido, eliminando a chance de regressão.

## 5. Classes visuais não valem à pena

Em alguns casos podemos até escrever CSS inline. Isso é mais explícito e reduz os rastros do CSS em zero. Entretanto, é problemático pois não conseguimos usar media queries, por exemplo. E colocar CSS com HTML mistura muita coisa e perde-se a habilidade de armazenamento em cache.

> Pergunta: A classe `.vermelho` não é a mesma abstração que o CSS já nos oferece de graça com `color: red`?

## 6. Elas oferecem ganchos para testes automatizados

Testes funcionais automatizados funcionam pesquisando por, e interagindo com elementos. Sendo eles:

1. clicar em um link;
2. achar um texto em uma caixa;
3. escrever um texto;
4. enviar um formulário; e também
6. verificar dados.

Não podemos usar as classes não-semânticas para atingir alvos específicos. E adicionar ganchos apenas para testes é mais perda de tempo do que você ter que baixar esse livro.

## 7. Elas oferecem ganchos para Javascript também

Não podemos usar classes não-semânticas para atingir elementos específicos, para que possamos melhorá-lo com Javascript.

## 8. Elas não precisam de manutenção

Se nomeamos a classe baseado no que ela é, não precisaremos atualizar o HTML novamente. Por exemplo, um cabeçalho é um cabeçalho, não importa como ele se *parece*.

Com classes visuais, tanto o HTML quanto o CSS precisarão de atualizações (assumindo que não há seletores disponíveis para uso).

## 9. São mais fáceis de debugar

Inspecionar um elemento com muitas classes atômicas significa patinar através de muitos seletores. Com uma classe semântica, só existe uma, facilitando na busca.

## 10. Porque é o padrão

Sobre usar o atributo classe, as especificações do HTML em 3.2.5.7 dizem o seguinte:

> "[...] autores são encorajados a usar os valores que descreva a natureza do conteúdo, ao contrário de escrever os valores que descrevem a apresentação de como o conteúdo deveria ser apresentado."

## 11. É mais fácil ao estilizar os estados

Considere o seguinte HTML:

	<a class="padding-esquerda-20 vermelho" href="#"></a>

Mudar o padding e o colour do elemento no hover seria problemático. É melhor para evitar ter que consertar problemas auto-induzidos, como esse.

## 12. Eles deixam um rastro menor no HTML

Como vimos acima, classes atômicas incham o HTML. Classes semânticas resultam em um HTML menor. E enquanto o CSS aumenta de tamanho, dá pra armazenar no cache.

## Conclusão

Classes semânticas são os pilares do CSS Sustentável. Sem elas, nada faria sentido. Então nomeie o elemento baseado no que ele é que as coisas vão se encaixando.