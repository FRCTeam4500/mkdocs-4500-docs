## Singleton Design Pattern

The Singleton Design Pattern is a creational design pattern that ensures that a class has only one instance, 
while providing a global point of access to that instance. 
It is useful when exactly one object is needed to coordinate actions across the system.

### Implementation

To implement the Singleton Design Pattern, we need to make the constructor private, 
so that it cannot be instantiated from outside the class. 
We also need to create a static method that returns the instance of the class. 
This method should create the instance if it does not exist, and return the existing instance if it does.

Here is an example implementation of the Singleton Design Pattern in Java:

```java
public class Singleton {
    private static Singleton instance; // Acceseble through the getInstance method.

    private Singleton() {}

    public static Singleton getInstance() {
        if (instance == null) {
            instance = new Singleton(); // add params here
        }
        return instance;
    }
}
```
