# @media

A diretiva @media funciona no Stylus da mesma forma que funciona no CSS, porém há possibilidade de encaixá-las em regras CSS, desta forma é possível declarar dentro do seletor qual será o comportamento dele de acordo com cada @media.

Exemplo:

```
.widget
	padding 10px
	@media screen and (min-width: 600px)
		padding 20px
```

Será compilado para:

```
.widget {
	padding: 10px;
}
@media screen and (min-width: 600px) {
	.widget {
		padding: 20px;
	}
}

```

## Aninhamento de @media

Com o Stylus, também é possivel usar `@media` dentro de outro `@media` aonde ele irá gerar como dependência, exemplo:

```
.widget
	padding 10px
	@media screen and (min-width: 600px)
		padding 20px
		@media (max-width: 400px)
			padding 30px
```

Será compilado para:

```
.widget {
	padding: 10px;
}
@media screen and (min-width: 600px) {
	.widget {
		padding: 20px;
	}
}
@media screen and (min-width: 600px) and (max-width: 400px) {
	.widget {
		padding: 30px;
	}
}

```

## Interporlação e variavies

Você pode usar iterações e variaveis dentro das medias queries:

```
foo = 'width'
bar = 30em

@media (max-{foo}: bar)
	body
		color #fff
```

Será compilado para:

```
@media (max-width: 30em) {
	body {
		color: #fff;
	}
}
```

Um exemplo aplicando iterações dentro das medias queries

```
.foo
	for i in 1..4
		@media (min-width: 2**(i+7)px)
			width 100px*i
```

Será compilado para:

```
@media (min-width: 256px) {
	.foo {
		width: 100px;
	}
}
@media (min-width: 512px) {
	.foo {
		width: 200px;
	}
}
@media (min-width: 1024px) {
	.foo {
		width: 300px;
	}
}
@media (min-width: 2048px) {
	.foo {
		width: 400px;
	}
}
```