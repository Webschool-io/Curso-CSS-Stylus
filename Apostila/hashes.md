# Hashes

A partir da versão `0.39.0` do Stylus, você pode criar hash objects, como o Stylus é um pré-processador escrito em JavaScript, ele é bem similar aos objetos.

Você define iguais no JavaScript, do lado esquerdo keys, e no direito os valores.

Exemplo:

```
colors = {
	red: #840f0f,
	blue: #1563b0,
	yellow: #d6e12e
}
```

Outra maneira de definir, pode ser usando colchetes:

```
colors = []
colors['red'] = #840f0f
colors['blue'] = #1563b0
colors['yellow'] = #d6e12e
```

## Pegando valores

Para pegar valores de hashes, você pode usar o nome do objeto seguido de um ponto (assim como no JavaScript) seguido da key. Exemplo:

```
p
	color: colors.red
```

*Observação: Importante notar que quando eu usei a propriedade `color` eu usei `:` na frente, você só consegue pegar um valor usando `:` depois da propriedade.*

Você também pode pegar valores usando `['key']`. Exemplo:

```
p
	color colors['red']
```

E neste caso não é obrigatorio o uso dos dois pontos.