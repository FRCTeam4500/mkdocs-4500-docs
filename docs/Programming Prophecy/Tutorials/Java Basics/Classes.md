A class is a template for an object, and they are the main building blocks of a java program. Each class contains a constructor to create an object and methods to define what that object can do. They also contain attributes, or variables, which allow them to hold information about themselves.

### Class Attributes
A class' attributes represent information that an object of that class would hold. These attributes can be primitives, like doubles or booleans, or they can be objects of other classes. 

### Class Methods
A class' methods represent actions that an object of that class could take. These methods can carry out tasks or return information. 

### Class Constructor
A class' constructor is a special method that is called when an object is first created. It has a return type of the class it belongs to, and is used for initializing values.

### Example Class

```java
public class Student {
    // Below are some examples of class attributes
    private double gpa;
    private int age;
    private String name;
    private boolean doesSports;

    // Here is a constructor
    public Student() {
        // Inside the constructor we set initial values
        gpa = 3.5;
        age = 14;
        name = "Bob";
        doesSports = false;
    }

    // Here is a class method that represents an action a student can take
    public void birthday() {
        age = age + 1;
    }

    // Here is a class method that returns information about the student
    public double getGpa() {
        return gpa;
    }
}```