---
layout: chapter
title: Conventions
section: Core
permalink: /chapters/conventions/
description: Learn the simple conventions that MaintainableCSS employs to write modules, components and state.
---

*CSS Sustentável* segue as seguintes convenções:

	.<módulo>[-<componente>][-<estado>] {}

Os itens nos colchetes são opcionais, dependendo do módulo em questão. Aqui estão alguns exemplos:

	/* Container do Módulo */
	.resultadosBusca {}

	/* Componente */
	.resultadosBusca-cabecalho {}

	/* Estado */
	.resultadosBusca-carregando {}

Notas:

- componente e estado são delimitados por um hífen;
- nomes são escritos em lowerCamelCase;
- seletores são prefixados com o nome do módulo.
