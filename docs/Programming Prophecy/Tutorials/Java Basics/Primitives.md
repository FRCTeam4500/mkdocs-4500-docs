primitives are the most basic values in java. There are 8 types of primitives: boolean, char,  int, byte, shot, long, float, and double.

For the most part, we will only be using 3 of these primitives: int, double, and boolean. 

### Integers
The int keyword is used for integers, which are all positive and negative whole numbers, including zero. Some examples of integers are -1, 1, and 0.

### Doubles
The double keyword is used for decimals, which are all numbers, positive or negative. Some examples of decimals are 16.2, 0.01, -2.3, and 1.0. Notice how an integer (1) can also be stored as a double (1.0).

### Booleans
The boolean keyword is used to represent true and false statements. Booleans only have two states, true and false. Some examples of booleans are true and false.

### Strings: The Fake Primitive
The String keyword is used to represent a collection of characters, or a word. Strings are used similarly to primitives, but unlike primitives, Strings are objects with methods inside them. Some examples of Strings are "hi" and "a"

### How to Use primitives
The main differences between primitives and objects is how they are created. primitives don't need to be created via a constructor. Instead they can just be assigned a value. 

!!! warning "Examples:"

    ```java 
    int age = 5;
    ```

    ```java
    boolean trustworthy = false;
    ```

    ```java
    double timeSeconds = 0.5;
    ```

    ```java
    String name = "Bob";
    ```

    Notice how Strings can be assigned a value just like the other primitives. Althrough it is a class, you dont have to specify `new String()`.
