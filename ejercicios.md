**Check Magic Square**  
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
