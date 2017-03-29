---
layout: chapter
title: Reuso
section: Fundamentos
permalink: /capitulos/reuso/
description: Aprenda porque evitar reuso e abraçar a repetição faz a manutenção do CSS mais fácil.
---

Como diria Harry Roberts, *DRY<sup>1</sup> é mal interpretado como a necessidade de nunca repetir a mesma coisa duas vezes. Isso não é prático e geralmente contraproducente, e pode levar a abstrações forçadas, gasto extra de energia e pensamento.*
<sup>1</sup> *DRY - Don’t Repeat Yourself (não se repita)*

Essa abstração forçada frequentemente resulta em classes atômicas e visuais. Nós sabemos quão dolorosas elas podem ser pois discutimos isso no capítulo de [Semântica](/capitulos/semantica/). Mixins também podem ser problemáticos, como veremos em breve.

Enquanto tentamos abstrair o CSS muito cedo, e por vezes em demasia, há momentos em que reutilizar o código faz sentido. A pergunta que precisa ser respondida é, *como poderíamos reutilizar um estilo?*

## Como podemos reutilizar um estilo?

Se quiséssemos reutilizar um estilo, uma opção seria delimitar os seletores por uma vírgula em um arquivo bem nomeado. Por exemplo, se muitos elementos precisassem de texto vermelho, poderíamos fazer isso:

	.algumaCoisa,
	.outraCoisa {
		color: red;
	}

Essa abordagem deveria ser usada por conveniência, não por performance. (Se a abstração só tiver uma propriedade, estamos apenas trocando uma linha de código pela outra.)

Se um seletor se desvia das regras de dentro da abstração, ele deveria ser removido da lista. De outra forma poderíamos regredir outros seletores e ter problemas de sobreposição de propriedades.

É importante notar que essa é apenas uma entre as várias técnicas à nossa disposição. Quando algo é bem entendido, nós podemos fazer uso de outras técnicas, que discutiremos em [Módulos](/capitulos/modulos/), [Estado](/capitulos/estados/) e [Modificadores](/capitulos/modificadores/).

## E sobre mixins?

Mixins provêem o melhor dos dois mundos. Pelo menos em teoria.

Como classes de utilidade, a atualização de um mixin é propagada para todas as instâncias. Se não tivermos uma ideia do que está usando o mixin, aumentamos a chance de regressão. Ao invés de atualizar o mixin, podemos criar outro, mas isso causa redundância.

Além do mais, mixins facilmente acabam com muitas propriedades, muitos parâmetros e condições. E isso é complicado. Complicado é difícil de preservar.

Para mitigar essa complexidade, podemos criar mixins granulares, como um para textos em  vermelho. A princípio isso parece melhor. Mas a declaração de um mixin vermelho não é o mesmo que a regra `color: red`?

Se precisamos atualizar a regra em muitos lugares, buscar e substituir deve resolver o problema. Igualmente, quando o mixin *vermelho* mudar para *laranja*, o nome também vai precisar ser atualizado.

Com isso dito, mixins podem ser muito úteis. Nós poderíamos, por exemplo, querer aplicar regras de *clearfix* através diferentes elementos e apenas em alguns break points. Isso é algo que o CSS Vanilla não consegue fazer.

Assim sendo, mixins não são *ruins*, deveríamos usá-los, porém com moderação.

## E sobre a performance?

Nós complicamos as coisas além da conta quando o assunto é performance. Ficamos obcecados com os menores detalhes.

Mesmo se o CSS totalize mais do que 100kb, no quadro geral, não vale à pena tentar enxugar o código apenas pelo DRY. E como discutimos antes, diminuir o CSS aumenta o HTML.

A compressão de uma imagem já nos dá um retorno melhor. E como já discutimos antes, resolver formas de redundância aumenta performance *e* sustentabilidade.

## Estamos violando os princípios DRY?

Tentar reutilizar, por exemplo, `float: left`, é semelhante a tentar reutilizar nomes de variáveis em objetos diferentes no Javascript. Não é violação dos princípios.

## Conclusão

Se esforçar para não repetir leva a um código pensado e feito além da conta. Fazendo isso a manutenção complica, não melhora. Como alternativa, deveríamos focar em reutilizar módulos tangíveis. Vamos discutir isso nos próximos capítulos.
