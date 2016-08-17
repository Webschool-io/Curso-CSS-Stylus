# @extend

Com a diretiva @extend é possível herdar estilos de outras classes, sua utilização evita a duplicação de estilos no arquivo final.

Alguns exemplos de utilização:

Temos dois tipos de erro que possuem características iguais, porém possuem algumas exceções de cor de acordo com a gravidade do erro. Criamos a classe `.msg` que receberá as características semelhantes e estendemos a classe `.msg` nas classes de erro específicas.

```
.msg
	border 1px solid
	padding 4px
	text-align center

.msg-error
	@extend .msg
	border-color #ff0000de
	color #ff0000de
.msg-alert
	@extend .msg
	border-color #ff8e00de
	color #ff8e00de
```

Será compilado para:

```
.msg,
.msg-error,
.msg-alert {
	border: 1px solid;
	padding: 4px;
	text-align: center;
}
.msg-error {
	border-color: rgba(255,0,0,0.871);
	color: rgba(255,0,0,0.871);
}
.msg-alert {
	border-color: rgba(255,142,0,0.871);
	color: rgba(255,142,0,0.871);
}
```

Também é possível herdar estilos de pseudo-elementos:

```
a
	color #000
	&:hover
		text-decoration underline
.hoverlink
	@extend a:hover
```

Será compilado para:

```
a {
	color: #000;
}
a:hover,
.hoverlink {
	text-decoration: underline;
}
```

No Stylus, diferente do SASS, é permitido o uso de `@extend` para seletores aninhados:

```
form
	button
		padding:10px

a.button
	@extend form button 
```

Será compilado para:

```
form button,
a.button {
	padding: 10px;
}
```

## Estendendo múltiplos seletores

Com o Stylus é possível usar o `@extend` com múltiplos seletores, basta separá-los com vírgula.

```
.a
	color #f00

.b
	height 200px

.c
	@extend .a, .b
	width 100px
```

## Opcional estendendo

As vezes pode ser bem útil extender algo que possa ou não existir. Você pode usar o sufixo `!optional` para isso.

```
.a
	color #f00
.c
	@extend .a !optional, .b !optional
	width 100px
```