# Funções

O Stylus possui algumas funções nativas e também possibilita que sejam criada novas funções.

## Criando uma função

A declaração de uma função começa com o nome da função, que pode conter combinação de caracteres alfabético e numéricos sem espaço, os argumentos entre parênteses e a definição da função a baixo (com identação) ou entre chaves (identação opcional).

```
calc-fluid(target, container)
	return ((target/container) * 100)%
```

## Utilizando uma função

Para utilizar uma função basta colocar o nome e passar os argumentos:

```
div
	width calc-fluid(650px, 1000px)
```

Será compilado para:

```
div{
	width: 65%;
}
```

## Parametros nomeados

No Stylus as funções aceita parametros nomeados. Isso pode servir quando você não lembra as ordens dos parametros ou simplesmente deseja mudar a ordem.

Por exemplo:
```
add(a, b)
	return a + b

add(b: 10, a: 5)
// => 15
```

## Funções como argumentos

Caso você queira passar uma função como argumento ao chamar uma função, é possivel. 

```
add(a, b)
	return a + b

invoke(x, y, fn)
	return fb(x, y)

invoke(10, 20, add)
// => 30
```

## Funções anônimas

Você pode definir funções anonimas em variaveis com o Stylus. A declaração de uma função anonima tem a sintaxe `@(){}`, aonde entre parenteses são os parametros, caso existam, e entre as chaves a função. Um exemplo:

```
add(a, b)
	fn = @(x, y){
		return x + y
	}
	return fn(a, b)
```

## arguments

Temos a variável local `arguments` aonde você pode acessar dentro de sua função:

```
sumAll()
	n = 0
	for num in arguments
		n = n + num
	return n

body
	padding sumAll(10,10,10,10,10,10,10,10,10,10)
```

## Funções nativas

Nesta apostila serão mostrada algumas das principais funções nativa do Stylus, É possível consultar uma lista com todas as funções nativas no site do [Stylus](http://stylus-lang.com/docs/bifs.html).

### Funções de cores

#### alpha(color[, value])

Retorna a cor com a opacidade argumentada, caso não seja passado nenum valor ele retorna a opacidade atual da cor

```
alpha(#fff)
// => 1

alpha(rgba(0,0,0,0.3))
// => 0.3

alpha(#fff, 0.5)
// => rgba(255,255,255,0.5)
```
#### dark(color)

Verifica se a cor é escura

```
dark(black)
// => true

dark(#5c5a5a)
// => true

dark(red)
// => false

dark(white)
// => false
```

#### light(color)

Verifica se a cor é clara

```
light(white)
// => true

light(red)
// => true

light(black)
// => false

light(#5c5a5a)
// => false

```

#### lightness(color[, value])

Caso o value seja passado, retorna uma cor mais clara com a porcentagem deseja, se não retorna a "claridade" da cor

```
lightness(#00c, 80%)
// => #99f

lightness(red)
// => red
```

### Funções com string e números

#### typeof(node)

Retorna o tipo da string. Esta função também tem duas alternativas: `type` e `type-of`.

```
type(12)
// => 'unit'

typeof(12)
// => 'unit'

typeof(#fff)
// => 'rgba'

type-of(#fff)
// => 'rgba'
```

#### unit(unit[, type])

Caso o valor `type` não seja argumentado, retorna o tipo da unidade, se ele for argumentado, retorna a unidade com o tipo desejado.

```
unit(10)
// => ''

unit(15in)
// => 'in'

unit(15%, 'px')
// => 15px

unit(15%, px)
// => 15px
```

