# Mixins

No Stylus, mixins e funções são definidas da mesma maneira, porém são aplicados de maneiras diferentes.

Mixins são invocados como **declarações** (*statements*). No exemplo, criamos um mixin `border-radius(n)`, quando ele invocando dentro de um seletor, as propriedades são expandidos e copiados para o seletor.

```
border-radius(n)
	-webkit-border-radius n
	-moz-border-radius n
	border-radius n
	
img
	border-radius(10px)
```

O que é compilado para:

```
img {
	-webkit-border-radius: 10px;
	-moz-border-radius: 10px;
	border-radius: 10px;
}
```

Mas com o Stylus, também podemos invocar um mixin sem os parênteses:

```
img
	border-radius 10px
```

Quando compilado, irá gerar o mesmo resultado.

Dentro do mixin `border-radius` que criamos, chamamos uma propriedade CSS também chamada `border-radius`, mas como nosso Stylus é muito esperto, ele será tratado como uma propriedade mesmo e não como uma invocação.

Com o Stylus, podemos utilizar os argumentos passados com uma variavel local, igual ao Javascript:

```
border-radius()
	-webkit-border-radius arguments
	-moz-border-radius arguments
	border-radius arguments

img
	border-radius 2px/4px 1px
```

Compilado fica desta maneira:

```
img {
	-webkit-border-radius: 2px/4px 1px;
	-moz-border-radius: 2px/4px 1px;
	border-radius: 2px/4px 1px;
}
```

Ou seja, o `arguments` é uma váriavel local que contém os argumentos passados quando o mixin é invocado. Desta forma, você não precisa ter um valor de parâmetros definido para o seu mixin.

## Referência pai

Assim como vimos em [seletores](selectors.md), também podemos usar o caractere `&`.

```
button-warning()
	background-color yellow
	&:hover
		background-color red

button
	button-warning()

```

Que será compilado para:

```
button {
	background-color: #ff0;
}
button:hover {
	background-color: #f00;
}
```

## Block mixins

Dentro de um mixin podemos definir um bloco, aonde ele pode ser chamado com o prefixo `+`. Dentro de nosso mixin para ser usado o bloco, devemos usar a váriavel `block` com interpolação:

```
foo()
	.bar
		{block}

+foo()
	width: 10px
```

Que será compilado para:

```
.bar {
	width: 10px;
}
```

## Mixin dentro mixins

Com toda certeza podemos usar um Mixin dentro de um Mixin, ficando desta maneira:

```
inline-list()
	li
		display inline

list-default()
	list-style none
	padding 0
	inline-list()

ul
	list-default()
```

Pode ver que dentro de `list-default`, chamamos nosso mixin `inline-list`. Compilado fica desta maneira:

```
ul {
	list-style: none;
	padding: 0;
}
ul li {
	display: inline;
}
```