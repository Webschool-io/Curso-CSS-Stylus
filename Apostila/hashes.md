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