# Comentários

Assim como no CSS, o Stylus aceita os comentários, porém ele não é renderizado no CSS.

## Linha única

Para se escrever um comentário em linha única, é da mesma maneira:

```
// Here begins a project that never understand
body
	color #555
```

## Múltiplas linhas

Os comentários em múltiplas linhas é identico ao CSS. Porém, nesse caso ele escreve apenas se a opção `compress` não estiver ativada.

```
/*
 * Here begins a project that never understand
*/
body
	color #555
```

Caso você queira que ele escreva os comentários em todas as opções, basta usar o `!` logo após iniciar seu comentário, ficando assim:

```
/*!
 * Here begins a project that never understand
*/
body
	color #555
```