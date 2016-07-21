# Sobre o Stylus

O pré-processador **Stylus** apareceu pela primeira vez em 2010 por _TJ Holowaychuk_, o criador da linguagem Luna. Ele é escrito em _JADE_ e _Node.js_, seu design é influenciado por _Sass_ e _Less_, considerado o terceiro mais usado pré-processador. Assim como os outros pré-processadores, ele tem o objetivo de aumentar a produtividade do CSS, no qual fornece mecanismos disponíves em linguagens de programação mais tradicionais que não estão disponíveis no CSS, através destes mecanismos, como variáveis, loops, funções e etc, é possível produzir o código, e entendê-lo, de forma mais rápida, com uma manutenção fácil, prática e de baixo custo.

## Pré-Processador

O **Stylus** precisa ser pré-processado antes de gerar o CSS que será renderizado pelo navegador, logo, o navegador nunca renderiza o código **Stylus** diretamente, então iremos compilá-lo para ser salvo o resultado em um arquivo CSS que será renderizado pelo navegador.


## Instalação

Para utilizar o **Stylus**, você precisa do Node.js instalado no seu computador.

```
sudo apt-get install nodejs
```

A seguir instalaremos o gerenciador de pacotes npm, ele permitirá instalar facilmente módulos e pacotes para utilizar com o Node.js.

```
sudo apt-get install npm
```

Finalmente instalamos o **Stylus** globalmente

```
npm install -g stylus
```

Agora o ambiente está pronto para utilizarmos o **Stylus**!

## .styl

Você pode utilizar o **Stylus** com a sintaxe: o .styl, aonde você pode usar com indentação, ou, usando chaves para denotar blocos de código e ponto e vírgula para separar linhas dentro de um bloco, igual no CSS.

```
body
	color #333
```

No curso, preferencialmente, utilizaremos o modo de indentação.

## Criando um arquivo Stylus

Para criar um arquivo **Stylus**, basta criar um arquivo e salvá-lo com a extensão _.styl_. Utilize o código abaixo para seguir como primeiro exemplo, salve como _exemplo1.styl_

```
body
	color white
```

## Compilando um arquivo Stylus

Você pode compilar um arquivo por vez ou uma pasta, entenda o comando.

```
stylus arquivo
```

Vamos compilar o nosso exemplo:

```
stylus exemplo1.styl
```

Deste modo irá gerar um arquivo _exemplo1.css_ na sua pasta, mas caso você queira definir uma pasta para onde ele irá compilar, basta por a flag _-o_, ficando desta forma:

```
stylus exemplo1.styl -o compilado.css
```