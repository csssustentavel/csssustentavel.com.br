---
layout: chapter
title: Estados
section: Conceitos Principais
permalink: /capitulos/estados/
description: Aprenda como prover diferentes estilos para seus módulos e componentes baseado em estados, como visível, escondido e carregando.
---

Com frequência, particularmente com interfaces ricas, estilos precisam ser aplicados em resposta à uma mudança de estado de um elemento. Por exemplo, podemos ter diferentes estilos quando um módulo (ou componente) está:

- visível ou invisível;
- ativo ou inativo;
- habilitado ou desabilitado;
- carregando ou carregado;
- temProdutos ou semProdutos;
- vazio ou cheio.

Para representar estados precisamos de uma classe adicional, que deve ser adicionada ao elemento do módulo (ou componente) ao qual pertence. Por exemplo, se nosso módulo de carrinho de compras precisa de um fundo cinza quando está vazio, o HTML deveria ser:

	<div class="carrinho carrinho-vazio">

E o CSS seria:

	.carrinho-vazio {
	  background-color: #eee;
	}

O nome da classe é prefixado com o módulo (ou componente) porque enquanto estados podem ser comuns, estilos associados podem não ser. Por exemplo, um *carrinho* vazio tem um fundo cinza, enquanto uma pesquisa sem resultados têm uma imagem posicionada absolutamente.

## E para reutilizar estados?

Algumas vezes, podemos de fato querer reutilizar estados entre módulos ou componentes. Por exemplo, alternando a visibilidade de um elemento. Isso será discutido mais detalhadamente no capítulo intitulado [Javascript](/capitulos/javascript/).

## E os atributos ARIA?

Nem todos os estados visuais podem ser representados por um [atributo ARIA](https://www.w3.org/TR/wai-aria/states_and_properties#attrs_widgets). Por exemplo, não há atributo para representar `temProdutos`. Portanto, devemos usar eles apenas quando necessário, em adição às classes.

Também, usar um seletor de atributo (ao invés de uma classe) possui [menos suporte](https://www.impressivewebs.com/attribute-selectors/). Enquanto alguns desenvolvedores podem considerar esses navegadores velhos, inseguros ou irrelevantes, deveríamos evitar técnicas que possam excluir usuários.

## Conclusão

Se o estilo de um elemento precisa mudar baseado em seu estado, devemos adicionar uma classe extra para aplicar as diferenças. Quando necessário, use atributos ARIA para tecnologias assistivas, não para estilizar. Fazendo isso empregamos uma abordagem consistente e inclusiva de estilização.
