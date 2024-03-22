---
toc: true
comments: true
layout: post
title: Workshop 1 Answers
type: tangibles
courses: {'compsci': {'week': 28}}
---
## Question 1: Primitive Types vs Reference Types (Unit 1)
a. What kind of types are person1 and person2?
   - Referance types
b. Do person1 and person3 point to the same value in memory?
   - Yes; person3 = person1
c. Is the integer “number” stored in the heap or in the stack?
   - In the stack; ints are local variables and therefore stored in a stack
d. Is the value that “person1” points to stored in the heap or in the stack?
   - In a heap

Situation: You are developing a banking application where you need to represent customer information. You have decided to use both primitive types and reference types for this purpose.

a. Define primitive types and reference types in Java. Provide examples of each.
   - Primitive types are basic data types like ints, chars, floats, etc. and they directly store their values in memory. Reference types hold memory addresses to objects rather than the object's actual data. Some examples include classes, arrays, and interfaces (most things defined by the user)

b. Explain the differences between primitive types and reference types in terms of memory allocation and usage in Java programs.
   - Primitive types store the object's data while reference types store their values in memory

c. You have a method `calculateInterest` that takes a primitive `double` type representing the principal amount and a reference type `Customer` representing the customer information. Write the method signature and the method implementation. Include comments to explain your code.

```java
public class Bank {
    public double calculateInterest(double principalAmount, Customer customer) {
        double interestRate = customer.getInterestRate();
        double interest = principalAmount * interestRate;
        return interest;
    }
}

class Customer {
    private double creditScore;

    public Customer(double creditScore) {
        this.creditScore = creditScore;
    }

    public double getInterestRate() {
        if (creditScore >= 700) {
            return 0.05;
        } else {
            return 0.08;
        }
    }
}

Bank.main(null)
```

## Question 2: Iteration over 2D arrays (Unit 4)

Situation: You are developing a game where you need to track player scores on a 2D grid representing levels and attempts.

(a) Explain the concept of iteration over a 2D array in Java. Provide an example scenario where iterating over a 2D array is useful in a programming task.
   - Iteration over a 2D array works by looping through each element of the array where one loop iterates over the rows and another loop iterates over the columns within each row. An example of where this can be used is in creating grid-like maps

(b) Code: You need to implement a method `calculateTotalScore` that takes a 2D array `scores` of integers representing player scores and returns the sum of all the elements in the array. Write the method signature and the method implementation. Include comments to explain your code.

```java
public class ScoreMathClass {
    public int calculateTotalScore(int[][] scores) { // method
        int totalScore = 0; 
        
        for (int i = 0; i < scores.length; i++) { // iterate over columns
            for (int j = 0; j < scores[i].length; j++) { // iterate over rows
                totalScore += scores[i][j];
            }
        }
        
        return totalScore;
    }
    
    public static void main(String[] args) {
        int[][] playerScores = {
            {10, 20, 30},
            {15, 25, 35},
            {5, 10, 15}
        };
        
        ScoreMathClass MathClass = new ScoreMathClass();
        int total = MathClass.calculateTotalScore(playerScores);
        System.out.println("Total Score: " + total);
    }
}

ScoreMathClass.main(null)
```

## Question 4: Math Class (Unit 2)

Situation: You are developing a scientific MathClass application where users need to perform various mathematical operations.

(a) Discuss the purpose and utility of the Math class in Java programming. Provide examples of at least three methods provided by the Math class and explain their usage.

   - It alllows you to do more math operations
   - Math.abs(double a): this helps when only the magnitude of a value matters and not its sign
   - Math.pow(double a, double b): this is how to do exponents
   - Math.sin(double a): helps in trig calculations with a radian value

(b) Code: You need to implement a method `calculateSquareRoot` that takes a `double` number as input and returns its square root using the Math class. Write the method signature and the method implementation. Include comments to explain your code.

```java
public class MathClass {
    public double calculateSquareRoot(double number) { // method
        double squareRoot = Math.sqrt(number);
        return squareRoot;
    }
    
    public static void main(String[] args) {
        MathClass MathClass = new MathClass();
        double number = 25.0;
        double squareRoot = MathClass.calculateSquareRoot(number);
        System.out.println(squareRoot);
    }
}

MathClass.main(null)
```
