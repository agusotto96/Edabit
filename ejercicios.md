## Check Magic Square

A "magic square" is a square divided into smaller squares each containing a number, such that the numbers in each vertical, horizontal, and diagonal row add up to the same value.  
Write a function that takes a 2D array, checks if it's a magic square and returns either true or false depending on the result.

```java
public static boolean isMagicSquare(int[][] square) {

	int negativeDiagonalSum = 0;
	int positiveDiagonalSum = 0;
	int rowSum = 0;
	int columnSum = 0;

	for (int i = 0; i < square.length; i++) {
		negativeDiagonalSum = negativeDiagonalSum + square[i][i];
		positiveDiagonalSum = positiveDiagonalSum + square[i][(square.length - 1) - i];
	}
	if (negativeDiagonalSum != positiveDiagonalSum) {
		return false;
	}

	for (int i = 0; i < square.length; i++) {
		rowSum = 0;
		for (int j = 0; j < square.length; j++) {
			rowSum = rowSum + square[i][j];
		}
		if (negativeDiagonalSum != rowSum) {
			return false;
		}
	}

	for (int i = 0; i < square.length; i++) {
		columnSum = 0;
		for (int j = 0; j < square.length; j++) {
			columnSum = columnSum + square[j][i];
		}
		if (negativeDiagonalSum != columnSum) {
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
public static int calculateRecamanIndex(int n) {

	ArrayList<Integer> recamanSequence = new ArrayList<Integer>();
	int sequenceLength;
	int recamanIndex;
	int lastElement;
	
	recamanSequence.add(0);
	
	do {
		
		sequenceLength = recamanSequence.size();
		recamanIndex = sequenceLength - 1;
		lastElement = recamanSequence.get(recamanIndex);
		
		if (lastElement - sequenceLength > 0 && !recamanSequence.contains(lastElement - sequenceLength)) {
			recamanSequence.add(lastElement - sequenceLength);
		} else {
			recamanSequence.add(lastElement + sequenceLength);
		}

	} while (lastElement != n);

	return recamanIndex;

}
```

## The Fibonacci Sequence

The Fibonacci is a sequence of numbers that appears in nature all around us, in the arrangement of seeds in a sunflower and the spiral of a nautilus for example.
* It begins with 0 and 1 as its first and second terms.
* After these first two elements, each subsequent element is equal to the sum of the previous two elements.

Write a function that returns the Fibonacci sequence and receives as input the length of the sequence.

```java
public static int[] calculateFibonacciSequence(int sequenceLength) {

	int[] fibonacciSequence = new int[sequenceLength];

	switch (sequenceLength) {

	case 0:
		break;

	case 1:
		fibonacciSequence[0] = 0;
		break;

	default:
		fibonacciSequence[0] = 0;
		fibonacciSequence[1] = 1;

		for (int i = 2; i < sequenceLength; i++) {
			fibonacciSequence[i] = fibonacciSequence[i - 1] + fibonacciSequence[i - 2];
		}

	}

	return fibonacciSequence;

}
```

## Decimal to Binary Converter

Given a decimal number as input, write a function to convert the given decimal number into equivalent binary.

```java
public static int convertToBinary(int number) {

	if (number == 0) {
		return 0;
	}

	int digits = 1;
	int result = 0;

	while ((int) Math.pow(2, digits) <= number) {
		digits++;
	}

	for (int i = digits - 1; i >= 0; i--) {
		if (number - (int) Math.pow(2, i) >= 0) {
			result = result + (int) Math.pow(10, i);
			number = number - (int) Math.pow(2, i);
		}
	}

	return result;

}
```

## Crossed Wires

Two wires are connected to a central port and extend outward on a grid.
The wires twist and turn, but the two wires occasionally cross paths.
You need to find the intersection point closest to the central port.
Because the wires are on a grid, use the Manhattan distance for this measurement.
* While the wires do technically cross right at the central port where they both start, this point does not count, nor does a wire count as crossing with itself.

What is the Manhattan distance from the central port to the closest intersection?

Calculate the number of steps each wire takes to reach each intersection; choose the intersection where the sum of both wires' steps is lowest.
* If a wire visits a position on the grid multiple times, use the steps value from the first time it visits that position when calculating the total value of a specific intersection.
* The number of steps a wire takes is the total number of grid squares the wire has entered to get to that location, including the intersection being considered.

What is the fewest combined steps the wires must take to reach an intersection?


