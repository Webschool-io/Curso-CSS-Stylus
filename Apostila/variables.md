# Variáveis

Um dos recursos mais importantes do Stylus é a criação de variáveis, as variáveis permitem armazenar informações para reutilizar em todo o estilo.
<br><br>
Variáveis Stylus podem começam com cifrão ou não e são definidas como propriedades CSS:


```
bg = #f0f0f3;
```

## Propiedade Lookup

Um recurso bem interessante e exclusido do Stylus, é a capacidade de referenciar propriedades sem atribuir seus valores a variáveis:


```
.foo
	position absolute
	top 50%
	left 50%
	width w = 150px
	height h = 200px
	margin-left -(w/2)
	margin-top -(h/2)
```

Mas você também pode, em vez de atribuir as variáveis `w` e `h`, pode ser usado o prefixo `@` e o nome da propiedade para acessar seu valor:


```
.foo
	position absolute
	top 20px
	left 20px
	width 150px
	height 80px
	margin-left -(@width/2)
	margin-top -(@height/2)
```

Um outro caso de uso, é definir uma propiedade dentro de mixins com base na existencia de outros.

```
position()
	position arguments
	z-index 1 unless @z-index

.foo
	z-index 20
	position absolute

.bar
	position absolute
```