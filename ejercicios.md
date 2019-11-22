## Check Magic Square

A "magic square" is a square divided into smaller squares each containing a number, such that the numbers in each vertical, horizontal, and diagonal row add up to the same value.  
Write a function that takes a 2D array, checks if it's a magic square and returns either true or false depending on the result.

```java
    public static boolean isMagicSquare(int[][] square) {
        int sumatoriaDiagonal1 = 0;
        for (int i = 0; i < square.length; i++) {
            sumatoriaDiagonal1 = sumatoriaDiagonal1 + square[i][i];
        }
        int sumatoriaDiagonal2 = 0;
        for (int i = 0; i < square.length; i++) {
            sumatoriaDiagonal2 = sumatoriaDiagonal2 + square[i][(square.length - 1) - i];
        }
        if (sumatoriaDiagonal1 != sumatoriaDiagonal2) {
            return false;
        }
        for (int i = 0; i < square.length; i++) {
            int sumatoriaFila = 0;
            for (int j = 0; j < square.length; j++) {
                sumatoriaFila = sumatoriaFila + square[i][j];
            }
            if (sumatoriaDiagonal1 != sumatoriaFila) {
                return false;
            }
        }
        for (int i = 0; i < square.length; i++) {
            int sumatoriaColumna = 0;
            for (int j = 0; j < square.length; j++) {
                sumatoriaColumna = sumatoriaColumna + square[j][i];
            }
            if (sumatoriaDiagonal1 != sumatoriaColumna) {
                return false;
            }
        }
        return true;
    }
```

## The Recamán Sequence

The Recamán Sequence is a numeric sequence that starts always with 0. The position of a positive integer in the sequence, or Recamán Index, can be established with the following algorithm:

* For every number to find, two variables are considered: the value of the last element of the sequence (last element from now on), and the actual sequence length (length from now on).
* If the subtraction of the length from the last element returns a number greater than 0 and not already present in the sequence, it is added to the sequence.
* When the conditions of the above statement are not meeted, will be added always the sum of the last element plus the length (even if it is a number already present in the sequence).
* Repeat until the number of interest is found.

Given a positive integer n, implement a function that returns its Recamán Index.

```java
    public static int recamanIndex(int n) {
        String registro = " 0 ";
        int ultimoValor = 0;
        int largo = 1;
        while (!registro.contains(" " + n + " ")) {
            if (ultimoValor - largo > 0 && !registro.contains(" " + (ultimoValor - largo) + " ")) {
                ultimoValor = ultimoValor - largo;
                registro = registro + " " + ultimoValor + " ";
                largo++;
            } else {
                ultimoValor = ultimoValor + largo;
                registro = registro + " " + ultimoValor + " ";
                largo++;
            }
        }
        int indice = largo - 1;
        return indice;
    }
```
