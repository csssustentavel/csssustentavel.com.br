---
layout: chapter
title: Módulos
section: Conceitos Principais
permalink: /capitulos/modulos/
description: Aprenda a diferença entre módulos e componentes e como identificar eles dentro de um projeto. Iremos codificar também alguns exemplos de módulos juntos.
---

## O que é um módulo?

Um módulo é uma unidade distinta e independente, que pode ser combinada com outros módulos para formar uma estrutura mais complexa.

Em uma sala de estar, podemos considerar a TV, o sofá e os quadros da parede como módulos. Todos unidos para criar uma sala utilizável.

Se nós retirarmos uma das unidades, as outras ainda funcionarão. Nós não precisamos da TV para poder sentar no sofá.

Em um site, o cabeçalho, o formulário de registro, o carrinho de compras, um artigo, uma lista de produtos, o painel de navegação e página inicial podem ser considerados módulos.

## O que é um componente?

Um módulo é feito de componentes. Sem eles, o módulo fica incompleto ou inutilizado.

Por exemplo: um sofá é feito de armações, estofado, pernas, almofadas e travesseiros do encosto, todos são componentes necessários para possibilitar que o sofá funcione como projetado.

Um módulo *logotipo* pode consistir em uma marca de copyright, uma imagem e um link, cada qual um componente. Sem a imagem, o logotipo fica inutilizado, sem o link o logotipo fica incompleto.

## Módulos vs componentes

Algumas vezes é difícil de decidir quando algo deve ser um componente ou um módulo. Por exemplo, podemos ter um cabeçalho contendo uma logo e um menu. Estes são componentes ou módulos?

Em um projeto recente, fez mais sentido que a logo fosse um componente e o menu um módulo. O que seria de um cabeçalho sem uma logo? E o painel de navegação poderia ser movido para baixo do cabeçalho.

Ninguém entende suas necessidades melhor do que você mesmo. Através da experiência, você vai pegar a prática para isso. E se você fizer errado, é fácil transformar um componente em um módulo.

Já temos teoria o suficiente. Vamos construir três diferentes módulos juntos. Fazendo isso, espero cobrir a maior parte das coisas que pensamos quando escrevemos CSS.

## 1. Criando um módulo de carrinho de compras

Nós vamos simplificar esse carrinho de compras por enquanto. Cada produto dentro do carrinho de compras vai mostrar seu título, com a possibilidade de remover ele da lista.

O modelo do carrinho de compras pode ser:

	<div class="carrinho">
	  <h1 class="carrinho-titulo">Seu carrinho</h1>
	  <div class="carrinho-item">
	    <h3 class="carrinho-tituloProduto">Título do produto</h3>
	    <form>
	      <input type="submit" class="carrinho-botaoRemover" value="Remover">
	    </form>
	  </div>
	</div>

E o CSS pode ser:

	.carrinho {}
	.carrinho-titulo {}
	.carrinho-item {}
	.carrinho-tituloProduto {}
	.carrinho-botaoRemover {}

## 2. Criando um módulo de resumo de pedido

Em seguida, iremos construir um módulo de resumo de pedido. Esse módulo é mostrado durante o pagamento e tem alguma semelhança com o carrinho de compras. Por exemplo, ele tem um título e mostra uma lista de produtos.

Ele, Contudo, tem uma estética diferente, e os produtos não podem mais ser removidos, ou seja, não haverá o formulário nem o botão de remoção.

A primeira coisa para abordarmos é a tentação de reutilizar o modelo do carrinho de compras (e o CSS). Mesmo havendo semelhanças, isso não significa que são a mesma coisa.

Se tentarmos combinar eles, vamos emaranhar dois módulos com lógicas de display e sobrescritas de CSS. Esse emaranhamento é, por definição, complexo, o que o torna difícil de sustentar e é facilmente evitável.

Ao invés disso, nós devemos criar um novo módulo com o seguinte modelo:

	<div class="resumoPedido">
	  <h2 class="resumoPedido-titulo">Resumo do pedido</h2>
	  <div class="resumoPedido-item">...</div>
	  <div class="resumoPedido-item">...</div>
	</div>

E o CSS seria:

	.resumoPedido {}
	.resumoPedido-titulo {}
	.resumoPedido-item {}

Muito embora pareça não intuitivo, duplicação é uma melhor abordagem. E, isso não é realmente duplicação. Duplicação é copiar a *mesma* coisa. Esses dois módulos podem parecer similares, mas não são a mesma coisa.

Manter as coisas separadas, mantém as coisas simples. Simplicidade é o mais importante aspecto quando se constrói um software confiável, escalável e sustentável.

## 3. Criando um módulo de botão

Como nosso módulo de carrinho de compras aparece apenas em sua própria página, não consideramos a possibilidade de reutilizar isso em nenhum outro lugar. Também não abordamos o fato de que o botão de remoção é um componente do carrinho de compras, fazendo isso ser difícil de reutilizar entre os módulos.

Botões são um exemplo de algo que queremos reutilizar em muitos lugares, e potencialmente *dentro* de módulos diferentes (um botão não é particularmente útil sozinho).

Uma opção seria transformar o componente de botão em um módulo, desse jeito:

	<input class="botao" type="submit" value="{{texto}}">

E o CSS poderia ser:

	.botao {}

O problema é que botões frequentemente têm diferentes posicionamentos, tamanhos e espaçamento, dependendo do contexto. E, claro, temos media queries para considerar.

Por exemplo, dentro de um módulo um botão poderia ser flutuado para a direita, próximo a algum texto. Em outro poderia ser centralizado com algum texto abaixo e alguma margem inferior.

Idealmente, deveríamos resolver essas inconsistências no *design*, antes mesmo de serem codificadas. Mas como isso nem sempre é possível, e por motivos de exemplo, assumiremos que temos que lidar com essas questões.

Então, por causa dessas diferenças, é difícil abstrair as regras comuns, pois não queremos acabar com um inferno de sobrescritas. Ou pior ainda, que fiquemos com medo de modificar as regras de CSS já abstraídas.

Para evitar esses problemas, podemos usar um mixin ou delimitar por vírgula as regras que não são afetadas pelo contexto. Por exemplo:

	.carrinho-botaoRemover,
	.outro-botaoLogin,
	.outro-botaoExcluir {
	  background-color: green;
	  padding: 10px;
	  color: #fff;
	}

Note que nesse exemplo, não especificamos `float`, `margin` ou `width` etc. Esses estilos são aplicados ao botão apenas:

	.carrinho-botaoRemover {
	  float: right;
	}
	.outro-botaoExcluir {
	  margin-bottom: 10px;
	}

Isso parece sensato, pois podemos optar por usar esses estilos comuns. Do contrário, teríamos que sobrescrever. Mas há uma terceira opção.

Imagine as etapas de um pagamento, onde cada página tem um botão de continuar e um link para a etapa anterior. Podemos reutilizá-lo atualizando-o em um módulo:

	<div class="acoesPagamento">
	  <input class="acoesPagamento-continuar">
	  <a class="acoesPagamento-voltar"></a>
	</div>

E o CSS seria:

	.acoesPagamento-continuar {}
	.acoesPagemento-voltar {}

Fazendo isso, abstraímos e aplicamos os estilos para o módulo ´.acoesPagamento`, que é fácil de entender. E também fizemos isso sem afetar botões parecidos, mas não idênticos.

Não discutimos ainda sobre ter mais de um tipo de botão (primário e secundário, etc). Para fazer isso, podemos usar modificadores, que será abordado depois.

## Conclusão

Um módulo, por definição, é um parte reutilizável de HTML e CSS. Antes de um grupo de elementos poder ser transformado em um módulo, devemos primeiro entender o que é e quais seus diferentes casos de uso.

Só então, podemos projetar a abstração correta. E fazendo isso, evitamos complexidade ao mesmo tempo, que é a fonte de um CSS não sustentável.
