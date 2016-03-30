# Programação Dinâmica

É uma técnica de resolução de problemas que consiste em dividir o problema em mais de uma parte, resolver essas partes individualmente e combinar os resultados, parecido com o método de divisão e conquista. A programação dinâmica difere da divisão e conquista pois é aplicada a problemas onde as partes dos subproblemas gerados ao dividir o problema original se repetem e o calculo delas é reaproveitado.

Para podermos aplicar a programação dinâmica o problema precisa primeiro poder ser quebrado em partes menores. Por exemplo, a sequência de Fibonacci (1, 2, 3, 5, 8, 13, 19, 32, ...) é definida como `f(n) = f(n-1) + f(n-2)`. Ou em Java:

```Java
int fibonacci(int n) {
  if (n < 2) return 1;
  return fibonacci(n - 1) + fibonnaci(n - 2);
}
```

A própria definição da série de Fibonacci já divide o problema de calcular `f(n)` em dois problemas menores, o de calcular `f(n-1)` e `f(n-2)`. Portanto o código acima é um exemplo da técnica de divisão e conquista. Ao executar esse código temos a seguinte árvore de execução:

 fn
 fn-1  fn-2
 fn-2 fn-3 ...
    ...

`f(n)` vai executar de `f(n-1)` e `f(n-2)`, por sua vez, `f(n-1)` vai executar `f(n-2)` e `f(n-3)`.

Expandindo a árvore de chamadas para `f(10)` temos

ARVORE

Todos os valores da árvore que não estão marcados em azul são valores repetidos, pois aparecem em algum lugar da linha azul. O método de programação dinâmica reaproveita o cálculo desses valores para diminuir o tempo de execução do algoritmo. A solução para a cálculo do Fibonacci usando essa técnica é começar a calcular os valores de baixo para cima até chegar no valor de f(n).

```Java
int fibonacci(int n) {
  int prev = 1;
  int current = 1;
  for (int i = 2; i <= n; i++) {
    int next = current + prev; // f(n) = f(n - 1) + f(n - 2)
    prev = current;
    current = next;
  }
  return current;
}
```

MOSTRAR DIFERENCA DE TEMPO DE EXECUCAO

Nem todos os problemas podem ser quebrados em problemas menores e nem todos os problemas que podem ser quebrados tem subproblemas em comum. Portanto o primeiro passo para tentar aplicar esse método é tentar dividir o problema em problemas menores, se for, analisar se os problemas menores se repetem.

OUTROS EXEMPLOS DE PROGRAMACAO DINAMICA.