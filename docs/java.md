# An Introduction to Java

## Variables
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

## Operators
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

## If statements

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

## For loops

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

## Arrays

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

## Classes

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

```java
Profile jim = new Profile("Jim", "123", 21);
System.out.println(jim.login("Alice", "supersecurepassword123")); // Prints false
System.out.println(jim.login("Jim", "123")); // Prints true

Profile jill = new Profile();
jill.setAge(31);
jill.setUsername("Jill");
jill.setPassword("aXr2Lp?^2R&T");
```