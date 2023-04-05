---
hide:
    - navigation
---

# Java

## The Basics

### Variables
For the scope of programming the robot, the following are the most important variables.

| Variable | Description                                                                               |
|----------|-------------------------------------------------------------------------------------------|
| int      | Can be used to represent any Integer number. Examples are 0, 7, -16, 1253.                | 
| double   | Can be used to represent decimal values. Examples are 1.2, -643.1742, 3.14159             |
| boolean  | Can be used to represent true or false                                                    |
| String   | Can be used to represent a sequence of text. Examples are "Hello, world", "2 plus 1 is 3" |

For a complete list, visit [Oracle's website](https://docs.oracle.com/javase/tutorial/java/nutsandbolts/datatypes.html)

```java
int myVar;
myVar = 2;

int numOne = -5;
double PI = 3.14159;
boolean isRaining = false;
String username = "ch1cken$1ayer123";
```

### Operators
| Operator    | Use                                                           |
|----------   |---------------------------------------------------------------|
| > and >=    | Greater than and greater than or equal to                     |
| < and <=    | Less than and less than or equal to                           |
| =           | Assignment. Used for setting variables                        |
| ==          | Checks if two variables are equal to each other               |
| !=          | Checks if two variables are not equal to each other           |
| +           | Adds two variables                                            |
| -           | Subtracts two variables                                       |
| *           | Multiplies two variables                                      |
| /           | Divides two variables                                         |
| %           | Mod operator. Finds the remainder (11 % 3 = 2)                |
| ++          | Increment. Increases a variable by one (varName++)            |
| --          | Decriment. Decreases a variable by one                        |
| +=, /=, etc | Applys the operation and updates the variable. (varName += 2) |

For more information, view: [arithmetic operators](https://docs.oracle.com/javase/tutorial/java/nutsandbolts/op1.html) and [equality operators](https://docs.oracle.com/javase/tutorial/java/nutsandbolts/op2.html)

### If statements

```java
boolean isRaining = false;
boolean isCold = true;

if(isRaining == true && isCold == false) {
    System.out.println("It's raining. Bring an umbrella!");
} else if(isRaining == true && isCold == true) {
    System.out.println("It's snowing!");
} else {
    System.out.println("It's not raining");
}
```

```java
int temperature = 32;
boolean willFreeze = false;
boolean willBoil = false;

if(temperature < 32) {
    willFreeze = true;
} else if (temperature == 32) {
    System.out.println("You are at the freezing point!");
} else if(temperature > 32 && temperature < 212) {
    System.out.println("It's your every day boring temperature");
} else if (temperature >= 212) {
    willBoil = true;
} else if (temperature != 5) {
    System.out.println("The temperature is not 5");
} else {
    System.out.println("Nothing interesting here");
}
```

### For loops

```java

// for(variable to count with; when to stop; by how much the variable should be changed)

// Prints the numbers 0 through 9
for(int i = 0; i < 10; i++) {
    System.out.println(i);
}

// Prints the numbers 0 through 9 backwards
for(int i = 9; i >= 0; i--) {
    System.out.println(i);
}

// Prints even numbers up to 20
for(int i = 0; i <= 20; i+=2) {
    system.out.println(i);
}

// Prints (0, 0), (0, 1), (0, 2), (1, 0), (1, 1), etc
for(int x = 0; x < 3; x++) {
    for(int y = 0; y < 3; y++) {
        System.out.println("(" + x + "," + y + ")");
    }
}
```

### Arrays

```java
int[] myArray;
myArray = new int[5];
myArray[0] = 1;
myArray[1] = 2;
myArray[2] = 3;
System.out.println(myArray[1]); // prints 2


double[] myDoubleArray = new double[] {2.31, -1.26, 3.14, 2.71, 7.1};
System.out.println(myDoubleArray[0]); // prints 2.31
System.out.println(myDoubleArray[myDoubleArray.length-1]); // prints 7.1

int[][] multiDimArray = new int[][] { {2, 4}, {7, 1}, {9, 3} };
System.out.println(multiDimArray[1][0]); // prints 7
System.out.println(multiDimArray.length); // prints 3
System.out.println(multiDimArray[0].length); // prints 2


int[] counting = new int[] {1, 2, 3, 4, 5, 6, 7, 8, 9};

for(int i = 0; i < counting.length; i++) { // Prints each number in the array
    System.out.println(counting[i]);
}

for(int c : counting) { // Same as the previous loop but shorter
    System.out.println(c);
}
```

### Classes
```java
public class Profile {
    // Instance variables
    private String username;
    private String password;
    private int age;

    // Constructor
    public Profile(String username, String password, int age) {
        this.username = username;
        this.password = password;
        this.age = age;
    }

    // Getters and setters
    public String getAge() { return age; }
    public void setAge(int age) { this.age = age; }

    // Functions
    public boolean login(String username, String password) {
        if(this.username.equals(username) && this.password.equals(password)) {
            return true;
        } else {
            return false;
        }
    }
}
```

The Profile class represents a user profile that has a username, password, and age. Here's a more detailed breakdown of each section of the code:

Instance variables:

```java
private String username;
private String password;
private int age;
```

These are the instance variables for the Profile class. They are marked as private, which means they can only be accessed within the class. username and password are of type String and represent the user's login information, while age is an int representing the user's age.

Constructor:
```java
public Profile(String username, String password, int age) {
    this.username = username;
    this.password = password;
    this.age = age;
}
```
This is the constructor for the Profile class. It takes three parameters (username, password, and age) and assigns them to the corresponding instance variables. The this keyword is used to refer to the current object (i.e., the Profile instance being created) and to disambiguate the instance variable from the parameter with the same name.

Getters and setters:

```java
public String getAge() { return age; }
public void setAge(int age) { this.age = age; }
```

These are the getter and setter methods for the age instance variable. The getter method `getAge()` returns the age value, while the setter method `setAge()` takes an int parameter and sets the age value to that parameter. The this keyword is used to disambiguate the instance variable from the parameter with the same name.

Functions:

```java
public boolean login(String username, String password) {
    if(this.username.equals(username) && this.password.equals(password)) {
        return true;
    } else {
        return false;
    }
}
```
This is the `login()` method, which takes two parameters (username and password) and returns a boolean indicating whether the supplied login information matches the Profile's username and password. The method compares the supplied username and password to the instance variables username and password using the `equals()` method of the String class. If both match, the method returns true; otherwise, it returns false.

An instance of this class can be created in the following manner:

```java
Profile jim = new Profile("Jim", "123", 21);
System.out.println(jim.login("Alice", "supersecurepassword123")); // Prints false
System.out.println(jim.login("Jim", "123")); // Prints true

Profile jill = new Profile();
jill.setAge(31);
jill.setUsername("Jill");
jill.setPassword("aXr2Lp?^2R&T");
```

## Advanced Java Principles

### Lambda Expressions
A lambda expression is a short block of code which takes in parameters and returns a value. Lambda expressions are similar to methods, but they do not need a name and they can be implemented right in the body of a method.

#### Suppliers


#### Consumers

#### Subscribers

