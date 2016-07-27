# Seletores

No Stylus podemos utilizar os mesmo seletores do CSS: de tipo, classe e id.
<br> Neste tópico veremos algumas facilidades para tornar a escrita mais rápida utilizando seletores, conjunto de regras e referências.

## Seletores Aninhados

Os seletores aninhados ou nested selectors, permitem que as regras CSS fiquem aninhadas uma dentro da outra.
<br>
Por exemplo:

```
nav

	width: 100%;
	background: #000;
	
	ul
		list-style: none

	li
		color: #fff;
		display: inline-block;
```

Lembrando que no Stylus, não precisamos obrigatoriamente a usar as chaves, isto é opcional.

Em ambos os casos (com ou sem chaves), será compilado para:

```
nav {
	width: 100%;
	background: #000;
}

nav ul {
	list-style: none
}

nav li {
	color: #fff;
	display: inline-block;
}
```

A regra interna aplica-se apenas dentro seletor da regra mais externa. Esta forma de escrita evita a repetição de seletores e faz com que blocos de CSS aninhados fiquem mais simples. 

**Use os seletores aninhados com cautela**
<br>
Um grande problema ao utilizar muitos níveis de seletores é a geração de código inútil que em vez de facilitar, pode dificultar seu trabalho criando regras muito específicas e aumentando o tamanho do arquivo CSS.
<br>
Para evitar problemas, recomenda-se o uso de no **máximo 3 aninhamentos**

## Conjuntos de regras

No Stylus, assim como no CSS, permite que você defina propriedades para vários seletores de uma só vez através da sepração da virgula, porém o mesmo pode ser feito quebrando a linha.

```
textarea
input
	border 1px solid #eee
```

Isso irá compilar:

```
textarea,
input{
	border: 1px solid #eee;
}
```

**Porém temos uma excepção para estra regra**, que são seletores que se parecem com propiedades. Por exemplo, o `baz foo bar` pode ser uma propiedade ou um seletor:

```
foo bar baz
input
	border 1px solid #eee
```

Então, por essa razão, podemos definir isso com uam vírgula, assim acabando com o problema:

```
foo bar baz,
input
	border 1px solid #eee
```

## Referência pai

O caractere `&` referencia o seletor(s) pai.

Exemplo:

``` 
a
	color #ffa
	&:hover
		color #faf
```

O qual, será compilado para:

```
a{
	color: #ffa;
}

a:hover{
	color: #faf;
}
```
<br /> <br />
Um outro exemplo seria:

```
#main
	section.foo
		font-weight bold
		a
			color #ffa
			&:hover
				color #faf
```

Será compilado para:

```
#main section.foo{
	font-weight: bold;
}

#main section.foo a{
	color: #ffa;
}

#main section.foo a:hover{
	color: #faf;
}
```
<br /><br />
Também podemos usar o `&` depois de um seletor, ficando assim:

```
section.bar
	font-weight bold
	color #ffa
	div.baz
		color #faf
		main#foo &
			font-style italic
```

Que é compilado para:

```
section.bar {
	font-weight: bold;
	color: #ffa;
}
section.bar div.baz {
	color: #faf;
}
main#foo section.bar div.baz {
	font-style: italic;
}
```

## Referência parcial

Em qualquer lugar de um seletor, podemos usar `^ [N]`, onde `N` pode ser um número, representa uma ferência parcial.

Refêrencia parcial é semelhante à referência pai, só que a referência pai contém o seletor todo, já a referência parcial contem apenas o seletor a partir do seu `N`.

O `^[0]` lhe retorna o primeiro nível do seletor, já `^[1]` retornaria o seletor `0` e `1`, e assim por diante. Um exemplo:

```
.foo
	&__bar
		width: 10px

	^[0]:hover
		width: 20px
```

Que compila para: 

```
.foo__bar {
	width: 10px;
}

.foo:hover {
	width: 20px;
}
```

<br /><br />
Um outro exemplo seria:

```
.foo
	.bar
		width 15px
		.baz
			width 30px
			^[1]:hover
				width 40px
```

Que compilado é:

```
.foo .bar {
	width: 15px;
}
.foo .bar .baz {
	width: 30px;
}
.foo .bar:hover {
	width: 40px;
}
```

<br /><br />
Também podemos usar o `&` com a `^[N]` que ficaria:

```
.foo
	.bar
		width 20px
		^[0]:hover &
			width 30px	
```

Quando compilado é:

```
.foo .bar {
	width: 20px;
}
.foo:hover .foo .bar {
	width: 30px;
}

```

### Varias referências parciais

Também podemos usar vários valores em referêcias parciais nos seletores, usando `^[N..M]`.

```
.foo
	& .bar
		width: 10px

		^[0]:hover ^[1..-1]
			width: 20px
```

Que compilado é:

```
.foo .bar {
	width: 10px;
}
.foo:hover .bar {
	width: 20px;
}
```

# Referência inicial

Com o `~/` no inicio de um seletor pode ser utilizado para apontar para o primeiro nível do seletor, que pode ser um atalho para `^[0]`. O único problema é que você pode usar `~/`apenas no início de um seletor.

```
.block
	&__foo
		~/:hover &
			color: red
```

Resultado:

```
.block:hover .block__foo {
	color: #f00;
}
```