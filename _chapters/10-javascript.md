---
layout: chapter
title: Javascript
section: Extras
permalink: /capitulos/javascript/
description: Como escrever CSS sustentável e JavaScript sustentável ao mesmo tempo.
---

Podemos querer usar JavaScript para aplicar o mesmo comportamento a múltiplos módulos ou componentes.

Por exemplo, podemos usar um construtor `Recolhedor` que alterna a visibilidade de um elemento.

Há duas abordagens que podemos tomar, ambas complementando a abordagem CSS que discutimos nos capítulos anteriores.

## 1. Encapsulando o estado ao módulo

Para fazer isso, precisamos especificar uma classe de estado específico de módulo ao construtor da seguinte forma:

	var modulo1Recolhedor = new Recolhedor(elemento1, {
		cssClasseEscondido: 'moduloA-escondido' 
	});

	var modulo2Recolhedor = new Recolhedor(elemento2, {
		cssClasseEscondido: 'moduloB-escondido' 
	});

Então, reusar o estilo CSS da seguinte maneira:

	.moduloA-escondido,
	.moduloB-escondido {
		display: none;
	}

O dilema é que essa lista pode crescer rapidamente (ou você pode usar um mixin). E cada vez que adicionamos um comportamento, precisamos atualizar o CSS. Uma pequena mudança, mas ainda assim uma mudança. Neste caso, podemos considerar uma classe de estado global.

## 2. Criando uma classe de estado global

Se nos encontrarmos repetindo exatamente o mesmo conjunto de estilos para múltiplos módulos, talvez seja melhor usar uma classe de estado global deste modo:

	.estadoGlobal-escondido {
		display: none;
	}

Esta abordagem elimina a longa lista delimitada por vírgula. E não precisamos mais especificar a classe do módulo ao criar uma instância. Isto ocorre porque a classe global será referenciada internamente.

	var modulo1Recolhedor = new Recolhedor(elemento1);
	var modulo2Recolhedor = new Recolhedor(elemento2);

Porém, essa abordagem nem sempre faz sentido. Podemos ter dois módulos diferentes que se comportam da mesma forma, mas têm um aparência diferente, o qual é algo que discutimos em [Estados](/capitulos/estados/).

## 3. O melhor dos dois mundos

Poderíamos combinar as duas abordagens ao padronizar a classe para a classe de estado global. E então, somente quando necessário, podemos especificar uma classe durante a instanciação, como mostrado no primeiro exemplo acima.

## Conclusão

Quando pensamos sobre estado, particularmente com a nossa visão de Javascript, precisamos considerar como esse estado afeta o comportamento, bem como o estilo. Diferentes componentes podem compartilhar o mesmo comportamento, mas eles podem parecer bastante diferentes. Após uma consideração cuidadosa, podemos escolher a solução certa para o problema.
