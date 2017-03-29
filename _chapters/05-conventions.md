---
layout: chapter
title: Convenções
section: Conceitos Principais
permalink: /capitulos/convencoes/
description: Aprenda a convenção simples que o CSS Sustentável emprega para escrever módulos, componentes e estados.
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
