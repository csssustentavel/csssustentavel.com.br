---
layout: chapter
title: IDs
section: Fundamentos
permalink: /caputulos/ids/
description: Aprenda porque usar IDs como um gancho para estilo é problemático e o que você deve fazer no lugar.
---

Falando semanticamente, nós deveríamos usar a ID em um elemento que só apareça uma vez. E deveríamos usar classe quando aparecem várias vezes.

Entretanto, as [IDs têm uma ordem de magnitude maior do que as classes](http://www.w3.org/TR/css3-selectors/#specificity), o que é se torna problemático quando queremos sobrescrever um estilo.

Para demonstrar o problema, vamos sobrescrever a cor de um elemento de *vermelho* para *azul*, usando uma ID.

O HTML ficaria assim:

	<div id="modulo" class="modulo-sobreposto">

E o CSS:

	#modulo {
	  color: red;
	}

	.modulo-sobreposto {
	  color: blue;
	}

O elemento vai ser vermelho embora a classe de sobreposição declare azul. Vamos consertar isso trocando a ID por uma classe:

	<div class="modulo modulo-sobreposto">

E o CSS:

	.modulo {
	  color: red;
	}

	.modulo-sobreposto {
	  color: blue;
	}

Agora o elemento está azul e o problema foi resolvido.

Enquanto usar IDs para estilos seja problemático, nós ainda podemos utilizá-las de outra forma. Por exemplo, nós certamente vamos usá-las para: 

- linkar labels com inputs;
- ligar âncoras com o href; e
- conectar os atributos ARIA, ajudando a leitura de telas.

## Conclusão

Use IDs quando você queira ativar eventos comportamentais particulares para navegadores e para tecnologia de acessibilidade. Porém evite usá-las como ganchos para estilos.
