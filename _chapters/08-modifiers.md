---
layout: chapter
title: Modificadores
section: Conceitos Principais
permalink: /capitulos/modificadores/
description: Use modificadores para mudar a aparência baseado em pequenas diferenças.
---

Como os estados, os modificadores também sobrescrevem estilos. São úteis quando módulos (ou componentes) têm diferenças pequenas e bem definidas.

Pegue um site de e-commerce onde cada categoria tem uma imagem de fundo única no cabeçalho. Todos os cabeçalhos possuem o mesmo padding, margem etc. A única diferença é a imagem de fundo.

A categoria “garotos” poderia ter um modificador como esse:

	<div class=”cabecalhoCategoria cabecalhoCategoria--garotos”>

Similarmente, a categoria “garotas” teria um modificador *garotas*:

	<div class=”cabecalhoCategoria cabecalhoCategoria--garotas”>

O CSS seria:

	.cabecalhoCategoria {
	  padding-top: 50px;
	  padding-bottom: 50px;
	  /* etc */
	}

	.cabecalhoCategoria--garotos {
	  background-image: url(/caminho/para/garotos.jpg);
	}

	.cabecalhoCategoria--garotas {
	  background-image: url(/caminho/para/garotas.jpg);
	}

Por que as diferenças são pequenas e bem definidas, esse tipo de reutilização é mais sustentável.

Podemos usar a mesma abordagem para botões. A maioria dos sites têm um estilo de botão primário e secundário. Se tudo que muda são um ou dois estilos, podemos ter um modificador para os botões primários e secundários, desse jeito:

	.botao {
	  padding: 20px;
	  border-radius: 3px;
	  /* etc */
	}

	.botao--primario {
	  background-color: green;
	}

	.botao--secundario {
	  background-color: #eee;
	}

Novamente, isso só funciona porque as diferenças são bem contidas e bem definidas.

## Conclusão

Modificadores são um bom jeito de reutilizar estilos através de um elemento bem compreendido. Mas, o modificador por si só deve ser apenas um detalhe. Se ele contém muitas regras sobrescritas, então muitos modificadores não são um bom caminho. Use um [módulo](/capitulos/modulos/) ao invés disso.
