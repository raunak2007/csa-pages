---
toc: true
comments: true
layout: post
title: First Java Notebook
description: My first java notebook. Hello World!
courses: { csa: {week: 1} }
type: hacks
---

::: {.cell .markdown id="d7AeW_5yaf9l"}

------------------------------------------------------------------------

toc: true comments: true layout: post title: First Java Notebook
description: My first java notebook. Hello World! courses: { csa: {week:
1} } type: hacks \-\--
:::

::: {.cell .markdown id="2AnphYxcdFm0"}
# Statistical Analysis of a Dataset

This markdown file provides an explanation of the Java code that
performs various statistical calculations on a dataset of numbers. The
code calculates and prints the following statistics: mean, median, mode,
standard deviation, first quartile (Q1), third quartile (Q3), and
interquartile range (IQR).

## Concepts and Tools Used

### 1. Functions {#1-functions}

-   The code uses several functions to calculate statistical measures:
    -   `mean(int[] numbers)`: Calculates the mean (average) of the
        dataset.
    -   `median(int[] numbers)`: Calculates the median (middle value) of
        the dataset.
    -   `mode(int[] numbers)`: Calculates the mode (most frequently
        occurring value) of the dataset.
    -   `standardDeviation(int[] numbers)`: Calculates the standard
        deviation, a measure of data dispersion.
    -   `firstQuartile(int[] numbers)`: Calculates the first quartile
        (Q1) or 25th percentile.
    -   `thirdQuartile(int[] numbers)`: Calculates the third quartile
        (Q3) or 75th percentile.
    -   `interquartileRange(int[] numbers)`: Calculates the
        interquartile range (IQR), Q3 - Q1.

### 2. Array Manipulation {#2-array-manipulation}

-   The code manipulates arrays to sort and extract subsets of the
    dataset for quartile calculations.

### 3. User Input and Output {#3-user-input-and-output}

-   The code prompts the user to enter a comma-separated list of
    numbers.
-   The input is split and converted into an integer array for
    calculations.
-   The calculated statistics are printed to the console.

## Running the Code

1.  Compile and run the Java program.
2.  Enter a comma-separated list of numbers (e.g.,
    `10, 15, 20, 25, 30, 35, 40, 45, 50, 55, 60`).

## Output Explanation

Suppose the user enters the dataset
`10, 15, 20, 25, 30, 35, 40, 45, 50, 55, 60`. The code calculates the
statistics as follows:

-   Mean: 35.0
-   Median: 35.0
-   Mode: -1 (No single mode)
-   Standard Deviation: 18.257418583505537
-   Q1: 20.0
-   Q3: 50.0
-   IQR: 30.0

The output provides insights into the central tendency, dispersion, and
distribution of the dataset.
:::

::: {.cell .code id="p8l_MZVzaf9m" outputId="5dcc3c0a-f147-4560-fd9b-6638449e29c6"}
``` java
// Define Static Method within a Class
public class HelloStatic {
    // Java standard runtime entry point
    public static void main(String[] args) {
        System.out.println("Hello World!");
    }
}
// A method call allows us to execute code that is wrapped in Class
HelloStatic.main(null);   // Class prefix allows reference of Static Method
```

::: {.output .stream .stdout}
    Hello World!
:::
:::

::: {.cell .code id="si9e9Io7af9o" outputId="48f40e5b-f4a8-4a6e-b3de-c6dc1e2fdaa8"}
``` java
// Define Class with Constructor returning Object
public class HelloObject {
    private String hello;   // instance attribute or variable
    public HelloObject() {  // constructor
        hello = "Hello, World!";
    }
    public String getHello() {  // getter, returns value from inside the object
        return this.hello;  // return String from object
    }
    public static void main(String[] args) {
        HelloObject ho = new HelloObject(); // Instance of Class (ho) is an Object via "new HelloObject()"
        System.out.println(ho.getHello()); // Object allows reference to public methods and data
    }
}
// IJava activation
HelloObject.main(null);
```

::: {.output .stream .stdout}
    Hello, World!
:::
:::

::: {.cell .code id="63IYK20qaf9o" outputId="01cde9ec-8f66-4598-9946-d474ef58762b"}
``` java


// Define Class
public class HelloDynamic { // name the first letter of class as capitalized, note camel case
    // instance variable have access modifier (private is most common), data type, and name
    private String hello;
    // constructor signature 1, public and zero arguments, constructors do not have return type
    public HelloDynamic() {  // 0 argument constructor
        this.setHello("Hello, World!");  // using setter with static string
    }
    // constructor signature, public and one argument
    public HelloDynamic(String hello) { // 1 argument constructor
        this.setHello(hello);   // using setter with local variable passed into constructor
    }
    // setter/mutator, setter have void return type and a parameter
    public void setHello(String hello) { // setter
        this.hello = hello;     // instance variable on the left, local variable on the right
    }
    // getter/accessor, getter used to return private instance variable (encapsulated), return type is String
    public String getHello() {  // getter
        return this.hello;
    }
    // public static void main(String[] args) is signature for main/drivers/tester method
    // a driver/tester method is singular or called a class method, it is never part of an object
    public static void main(String[] args) {
        HelloDynamic hd1 = new HelloDynamic(); // no argument constructor
        HelloDynamic hd2 = new HelloDynamic("Hello, Nighthawk Coding Society!"); // one argument constructor
        System.out.println(hd1.getHello()); // accessing getter
        System.out.println(hd2.getHello());
    }
}
// IJava activation
HelloDynamic.main(null);
```

::: {.output .stream .stdout}
    Hello, World!
    Hello, Nighthawk Coding Society!
:::
:::

::: {.cell .code id="nm28ramdaf9p"}
``` java
public class Person {
    private String name;

    // Setter method for name
    public void setName(String name) {
        this.name = name;
    }

    // Getter method for name
    public String getName() {
        return name;
    }

    public static void main(String[] args) {
        Person person = new Person();
        person.setName("John");
        System.out.println("Name: " + person.getName());
    }
}
```
:::

::: {.cell .code id="7s-xrK8Maf9p" outputId="7479f255-815e-452d-e341-dc9b013b31e5"}
``` java
import java.util.Arrays;
import java.util.HashMap;
import java.util.Map;
import java.util.Map.Entry;
import java.util.Scanner;

// Method to calculate the mean
double mean(int[] numbers) {
    double sum = 0;
    for (int num : numbers) {
        sum += num;
    }
    return sum / numbers.length;
}

// Method to calculate the median
double median(int[] numbers) {
    Arrays.sort(numbers);
    int middle = numbers.length / 2;
    if (numbers.length % 2 == 0) {
        return (numbers[middle - 1] + numbers[middle]) / 2.0;
    } else {
        return numbers[middle];
    }
}

// Method to calculate the mode
int mode(int[] numbers) {
    Map<Integer, Integer> countMap = new HashMap<>();
    for (int num : numbers) {
        countMap.put(num, countMap.getOrDefault(num, 0) + 1);
    }

    int maxCount = 0;
    int mode = -1;
    for (Entry<Integer, Integer> entry : countMap.entrySet()) {
        if (entry.getValue() > maxCount) {
            maxCount = entry.getValue();
            mode = entry.getKey();
        }
    }
    return mode;
}

Scanner scanner = new Scanner(System.in);
System.out.println("Enter a comma-separated list of numbers:");
String input = scanner.nextLine();
String[] numberStrings = input.split(",");
int[] numbers = new int[numberStrings.length];
for (int i = 0; i < numberStrings.length; i++) {
    numbers[i] = Integer.parseInt(numberStrings[i].trim());
}

System.out.println("Mean: " + mean(numbers));
System.out.println("Median: " + median(numbers));
System.out.println("Mode: " + mode(numbers));

import java.util.Arrays;

// ... (Rest of the code)

// Method to calculate the standard deviation
double standardDeviation(int[] numbers) {
    double mean = mean(numbers);
    double sumSquaredDifferences = 0;
    for (int num : numbers) {
        double difference = num - mean;
        sumSquaredDifferences += difference * difference;
    }
    double variance = sumSquaredDifferences / numbers.length;
    return Math.sqrt(variance);
}

// Method to calculate the first quartile (Q1)
double firstQuartile(int[] numbers) {
    Arrays.sort(numbers);
    int middle = numbers.length / 2;
    int[] lowerHalf = Arrays.copyOfRange(numbers, 0, middle);
    return median(lowerHalf);
}

// Method to calculate the third quartile (Q3)
double thirdQuartile(int[] numbers) {
    Arrays.sort(numbers);
    int middle = numbers.length / 2;
    int startIndex = numbers.length % 2 == 0 ? middle : middle + 1;
    int[] upperHalf = Arrays.copyOfRange(numbers, startIndex, numbers.length);
    return median(upperHalf);
}

// Method to calculate the interquartile range (IQR)
double interquartileRange(int[] numbers) {
    return thirdQuartile(numbers) - firstQuartile(numbers);
}

// ... (Rest of the code)

System.out.println("Standard Deviation: " + standardDeviation(numbers));
System.out.println("Q1: " + firstQuartile(numbers));
System.out.println("Q3: " + thirdQuartile(numbers));
System.out.println("IQR: " + interquartileRange(numbers));
```

::: {.output .stream .stdout}
    Enter a comma-separated list of numbers:
    Mean: 4.571428571428571
    Median: 5.0
    Mode: 5
    Standard Deviation: 18.257418583505537:
    Q1: 20.0Q3: 50.0IQR: 30.0
:::
:::
