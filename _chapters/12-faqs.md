---
layout: chapter
title: FAQs
section: Extras
permalink: /capitulos/faqs/
description: Suas questões sobre o CSS Sustentável são respondidas aqui.
---

Se você não conseguir encontrar a resposta, por favor [publique uma issue no Github](https://github.com/adamsilver/maintainablecss.com/issues/new). Obrigado!

## Posso traduzir este livro?

Sim. Para isso:

1. [Faça um fork do repositório](https://github.com/adamsilver/maintainablecss.com/).
2. Aponte o domínio do seu país para ele.
3. Cite o original e me avise :).

## Quando eu devo usar isso?

Se você gosta de manter as coisas realmente simples, use esta abordagem. Ela funciona bem se você está construindo sites de longa duração, com design responsivo e sob medida que escalam e evoluem com o tempo.

## E se eu não quiser usar isso?

Se você não gosta, sinta-se livre para não utilizar. Ou usar as partes que você gosta. Se algo não funciona bem, me avise e podemos trabalhar nisso.

## Isso é o mesmo que [tal metodologia]?

Estes guias são resultado da construção de diferentes tipos de sites. Eu fui influenciado por diferentes experiências, requisitos e pessoas com as quais eu trabalhei.

Sem dúvida, há uma semelhança com BEM e ECSS. Se você está usando estas abordagens alegremente, continue com elas. Estes guias estão aqui se e quando você precisar deles.

## Devo criar uma classe para cada elemento?

Não. Você pode escrever `.modulo p {}` se quiser. E algumas vezes você vai precisar fazer isso, se, por exemplo, você está usando markdown. Mas tenha cuidado que, se você está em um módulo que contém um `p`, ele irá herdar os estilos e precisa ser sobrescrito.

## Porque eu devo prefixar o nome do módulo?

Boa pergunta. Aqui está um HTML sem prefixo:

	<div class="carrinho">
	  <div class="titulo">

E o CSS:

	/* módulo */
	.carrinho {}

	/* componente de título para o módulo de carrinho */
	.carrinho .titulo {}

Há dois problemas:

1. ao visualizar o HTML, é difícil diferenciar entre um módulo e um componente; e
2. o componente `.carrinho .titulo` irá herdar os estilos do módulo `.titulo`, o que causa um efeito colateral não intencional.

## Podemos encadear classes para estado?

Podemos usar um seletor encadeado para um estado, ex.: `.modulo.desabilitado`. O problema é que esta abordagem tem menos suporte de navegadores. Devemos evitar padrões que excluem usuários desnecessariamente, a menos que haja uma razão convincente para fazer isso.

## E quanto à herança para títulos, etc?

Idealmente, nosso HTML semântico combina com a integridade do design visual. O que significa que esperamos que os h1s sejam idênticos. Neste caso, podemos declarar o seguinte CSS:

	h1 {
	  /* etc */
	}

Porém, este raramente é o caso em sites comerciais de larga escala. Neste caso, podemos encapsular estilos ao módulo em questão:

	.modulo-titulo {
	  font-size: ...;
	  color: ...;
	}

## Onde eu coloco as media queries?

A tela deve se adaptar ao conteúdo, não o contrário.

Isto significa que o breakpoint de um módulo não deve ser determinado como *pequeno*, *médio* ou *grande*. Fazer isso restringe o design e degrada a experiência do usuário.

Assim, todos os estilos&mdash;mesmo aqueles que estão encapsulados em media queries&mdash;deveriam estar localizados próximos aos estilos regulares:

	.carrinho {}

	@media(min-width: 500px) {
	  .carrinho {}
	}

	@media(min-width: 1000px) {
	  .carrinho {}
	}

	.carrinho-titulo {}

## Onde eu coloco modificadores e estados?

Estados e modificadores, de modo similar às media queries, devem estar localizados próximos ao elemento ao qual eles pertencem:

	.carrinho {}

	.carrinho-escondido {}

	.carrinho-titulo {}

	.carrinho-titulo--algumModificador {}

## Devo adicionar comentários?

Se você usar uma abordagem em que vários módulos residem dentro de um único arquivo CSS, é uma boa ideia separar estes módulos com um comentário mais proeminente:

	/********************************************
	* Carrinho
	********************************************/

	.carrinho {}

	.carrinho-titulo {}

	/********************************************
	* Coisa
	********************************************/

	.coisa {}

	.coisa-detalhes {}

## Não conseguiu encontrar uma resposta aqui?

Crie uma issue no [Github](https://github.com/adamsilver/maintainablecss.com/issues/new) e irei dar um retorno a você o mais breve que eu puder. Obrigado!

