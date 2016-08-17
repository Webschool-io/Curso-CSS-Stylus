# Interpolação

É possível usar variáveis Stylus em seletores e nomes de propriedade com o recurso de interpolação. A interpolação é um recurso que está presente em várias linguagens de programação e permite que valores sejam encaixados dentro de outros valores.

Veja alguns exemplos a seguir.

Utilizando interpolação em nome de seletores:

```
$name = destaque
$attr = border


p.{$name}
	{$attr}-radius 6px
```

Será compilado para:

```
p.destaque {
	border-radius: 6px;
}
```

Utilizando interpolação em nome de propiedades:

```
$vendor = transition

.foo
	-webkit-{$vendor} all 250ms
	{$vendor} all 250ms
	-moz-{$vendor} all 250ms
	-ms-{$vendor} all 250ms
	-o-{$vendor} all 250ms
```

Será compilado para:

```
.foo {
	-webkit-transition: all 250ms;
	transition: all 250ms;
	-moz-transition: all 250ms;
	-ms-transition: all 250ms;
	-o-transition: all 250ms;
}
```

A interpolação pode ser muito bem utilizada dentro de funções e mixins. Serão exibidas outras formas de utilizar interpolação agregadas com recursos que serão vistos nos próximos tópicos.