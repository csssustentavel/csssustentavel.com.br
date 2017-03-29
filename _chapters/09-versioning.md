---
layout: chapter
title: Versionamento
section: Extras
permalink: /capitulos/versionamento/
description: Aprenda como o CSS Sustentável torna realmente fácil atualizar um módulo de teste AB para websites de rápida evolução.
---

Nós podemos querer, por exemplo, realizar um teste A/B com duas versões diferentes de um módulo para ver qual funciona melhor. Para fazer isso, precisamos duplicar o módulo e dar a ele um nome único. Por exemplo, se quisermos testar dois carrinhos de compra diferentes, o CSS poderia ser o seguinte:

	/* módulo existente (variante A) */
	.carrinho {}

	.carrinho-titulo {}

	/* nova versão (variante B) */
	.carrinho2 {}

	.carrinho2-titulo {}

Desta forma, podemos manter duas versões durante os testes até resolver qual é a melhor. E, uma vez que façamos isso, é fácil descartar o módulo redundante, uma vez que eles não estão entrelaçados. Bom código é fácil de apagar.