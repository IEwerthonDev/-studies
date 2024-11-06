# Algoritmos com PHP

Um algoritmo é um conjunto de instruções ou passos lógicos e organizados que permitem resolver um problema ou realizar uma tarefa específica. Em programação, os algoritmos são a base para a resolução de problemas e a criação de soluções eficientes.

Vamos entender melhor o conceito de algoritmos usando alguns exemplos em PHP:

## Soma de dois números

```php
function somarNumeros($a, $b) {
    $resultado = $a + $b;
    return $resultado;
}

$numero1 = 10;
$numero2 = 20;
$soma = somarNumeros($numero1, $numero2);
echo "A soma de $numero1 e $numero2 é: $soma";
```

Neste exemplo, o algoritmo consiste em:
1. Definir uma função chamada `somarNumeros` que recebe dois parâmetros: `$a` e `$b`.
2. Dentro da função, somar os dois números usando o operador `+` e armazenar o resultado na variável `$resultado`.
3. Retornar o valor de `$resultado`.
4. Chamar a função `somarNumeros` passando os valores `10` e `20` como argumentos.
5. Armazenar o resultado da função em uma variável `$soma`.
6. Exibir a soma dos números.

## Verificar se um número é par ou ímpar

```php
function eParOuImpar($numero) {
    if ($numero % 2 == 0) {
        return "O número $numero é par.";
    } else {
        return "O número $numero é ímpar.";
    }
}

$numero = 17;
$resultado = eParOuImpar($numero);
echo $resultado;
```

Neste exemplo, o algoritmo consiste em:
1. Definir uma função chamada `eParOuImpar` que recebe um parâmetro: `$numero`.
2. Dentro da função, verificar se o número é par ou ímpar usando o operador de módulo `%`. Se o resto da divisão por 2 for igual a 0, o número é par; caso contrário, é ímpar.
3. Retornar uma string indicando se o número é par ou ímpar.
4. Chamar a função `eParOuImpar` passando o valor `17` como argumento.
5. Armazenar o resultado da função em uma variável `$resultado`.
6. Exibir o resultado.

## Busca linear em um array

```php
function buscaLinear($array, $valorBuscado) {
    for ($i = 0; $i < count($array); $i++) {
        if ($array[$i] == $valorBuscado) {
            return "O valor $valorBuscado foi encontrado no índice $i.";
        }
    }
    return "O valor $valorBuscado não foi encontrado no array.";
}

$numeros = [5, 12, 8, 3, 9, 1, 7];
$valorBuscado = 9;
$resultado = buscaLinear($numeros, $valorBuscado);
echo $resultado;
```

Neste exemplo, o algoritmo consiste em:
1. Definir uma função chamada `buscaLinear` que recebe dois parâmetros: `$array` e `$valorBuscado`.
2. Dentro da função, iterar sobre cada elemento do array usando um loop `for`.
3. Para cada elemento, verificar se ele é igual ao valor buscado.
4. Se o valor for encontrado, retornar uma mensagem informando o índice do elemento.
5. Caso o valor não seja encontrado, retornar uma mensagem informando que o valor não foi encontrado.
6. Chamar a função `buscaLinear` passando o array `[5, 12, 8, 3, 9, 1, 7]` e o valor `9` como argumentos.
7. Armazenar o resultado da função em uma variável `$resultado`.
8. Exibir o resultado.

Esses são apenas alguns exemplos básicos de algoritmos implementados em PHP. Na prática, os algoritmos podem ser muito mais complexos, envolvendo estruturas de dados avançadas, recursão, otimizações e muito mais. O importante é entender que um algoritmo é um conjunto de instruções lógicas que permitem resolver problemas de forma sistemática e eficiente.