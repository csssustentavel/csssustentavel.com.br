---
layout: chapter
title: Organização
section: Extras
permalink: /capitulos/organizacao/
description: Aprenda como organizar seus arquivos CSS.
---

Código bom é fácil de encontrar e código fácil de encontrar é bem organizado. E isso significa que queremos o nosso CSS bem organizado. Há, de modo geral, duas abordagens para escolher, as quais discutiremos neste capítulo.

## 1. CSS em um único diretório

Esta abordagem coloca o CSS em um único diretório:

	/caminho/para/css
		/vendor
			algumArquivoDeTerceiros.css
			outroArquivoDeTerceiros.css
		/seuApp
			algo.css
			global.css
			carrinho.css

### Notas

* Arquivos CSS de terceiros (bibliotecas, frameworks, etc.) devem ficar dentro do diretório `/vendor`;
* O CSS da sua aplicação deve ficar no diretório `/seuApp` onde *seuApp* é o nome do seu projeto;
* Esta abordagem facilita a implementação porque um script de build pode facilmente mirar em um único diretório a fim de agrupar e comprimir os arquivos;
* Esta parece ser a abordagem mais comum, mas não significa que é a melhor.

## 2. CSS em um diretório de módulo

Esta abordagem coloca os CSS específicos de módulos em seus próprios diretórios:

	/global
		/css
			reset.css
			global.css
			etc.css
	/carrinho
		/controllers
		...
		/templates
			carrinho.html
			carrinhoVazio.html
		/partials
			cabecalhoCarrino.html
			resumoCarrinho.html
		/js
			...
		/css
			carrinho.css
	/header
		...

### Notas

* Geralmente nos orientamos por funcionalidade ao invés de tecnologias, tornando esta abordagem mais atraente;
* O CSS global precisa de um diretório próprio porque estilos globais, pela sua própria natureza, não pertencem a um módulo;
* Esta abordagem é mais suscetível de sofrer do *problema do limite de 31 arquivos CSS*, que é explicado a seguir.

## O problema do limite de 31 arquivos CSS

Qualquer que seja a abordagem que você use, tenha cuidado com o limite de 31 arquivos CSS encontrado em versões do Internet Explorer. Internet Explorer 9, por exemplo, ignora estilos armazenados no 32º (ou 33º etc) arquivo.

Para produção, está tudo bem, porque devemos agrupar os arquivos CSS para reduzir requisições HTTP. Mas, para desenvolvimento local, é melhor trabalhar com arquivos-fonte para facilitar o *debugging*. E é em navegadores legados onde os bugs geralmente aparecem.

**Se você tem uma etapa de compilação** para o desenvolvimento local&mdash;como no caso do uso de um pré-processador CSS&mdash;você não precisa se preocupar. O pré-processador irá agrupar os arquivos.

**Se você não tem uma etapa de compilação** para o desenvolvimento local&mdash;porque é mais fácil debugar os arquivos-fonte desta forma&mdash;então você pode querer remediar isto com uma das duas abordagens:

### 1. Adicionar uma opção para concatenar o CSS localmente

Ao fazer isso, você será capaz de imitar a produção e debug do CSS desconsiderando navegadores antigos.

### 2. Usar menos de 32 arquivos CSS

Como você provavelmente terá mais de 31 módulos, você não pode organizar seu CSS por módulo. Ao invés disso, você terá que colocar vários módulos dentro do mesmo arquivo CSS.

## Conclusão

Neste capítulo, discutimos duas formas de organizar o CSS. Qualquer que seja a abordagem que nós utilizemos, temos que ter cuidado com o problema do limite de 31 arquivos CSS porque faz com que o *debugging* do CSS seja mais difícil nos navegadores que causam mais problemas.
