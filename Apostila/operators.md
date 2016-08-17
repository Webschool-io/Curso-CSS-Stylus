# Operadores

Através do Stylus é possível realizar algumas operações. Aqui está a lista dos operadores, o de valor mais alto para o mais baixo:

```
.
[]
! ~ + -
is defined
** * / %
+ -
... ..
<= >= < >
in
== is != is not isnt
is a
&& and || or
?:
= := ?= += -= *= /= %=
not
if unless
```

## Operadores Unários

Os operadores unários disponíveis são: `!`, `not`, `-`, `+` e `~`. Aplicados fica desse modo:

``` 
!0 
//=> true

!!0 
//=> false

!1 
//=> true

!!5px 
//=> true

-5px 
//=> -5px

--5px 
//=> 5px

not true 
//=> false

not not true 
//=> true
```

O operador logico `not` não tem precedência baixa, então o exemplo a seguir pode ser substituido por:

```
a = 0
b = 1

a! and !b
// => false
// analisado como: (!a) and (!b)
```

Por:

```
not a or b
// => false
// analisado como: not (a or b)
```

## Operadores Binários

### Subscript []

O operador subscript nos permite pegar um valor dentro de uma expressão baseado no seu índice (base zero). Valores de índices negativos começam do último valor da expressão.

```
list = 1, 10, 20, 30

list[0]
// => 1

list[-1]
// => -1
```

### Range .. ...

Os operadores de range (`..` e `...`) é usado para expandir expressões:

```
1..5
// => 1 2 3 4 5

1...5
// => 1 2 3 4

5..1
// => 5 4 3 2 1
```

### Adição e Subtração + -

Com o Stylus você consegue fazer operações com os operados `-`e `+` nas expressões:

```
15px - 5px
// => 10px

5 - 2
// => 3

5cm - 2mm
// => 4.8cm

5s - 1000ms
// => 4s

20mm + 4in
// => 121.6mm

"foo" + "bar"
// => "foo bar"

"num" + 9
// => "num 15"

```

### Multiplicativo / * %

```
2000ms + (1s * 2)
// => 4000ms


5s / 2
// => 2.5s

4 % 2
// => 0
```

Importante ressaltar, quando usar `/` como valor de propiedade, você deve usar dentro de parênteses.

```
.foo
	font-size (20px/2)
	font-size 20px/2
```

### Expoente **

O operador de expoente `**`:

```
2 ** 8
// => 256
```