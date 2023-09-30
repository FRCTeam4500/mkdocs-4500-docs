## Factory Design Pattern

The Factory Design Pattern is a creational design pattern that provides an interface for creating objects in a superclass, 
but allows subclasses to alter the type of objects that will be created. 
It is useful when we want to decouple the creation of objects from the rest of the code.

### Implementation

To implement the Factory Design Pattern, we need to create an interface or an abstract class for the objects that we want to create. 
We also need to create a factory class that implements this interface or extends this abstract class. 
This factory class should have a method that returns an object of the interface or abstract class type. 
Finally, we need to create concrete classes that implement the interface or extend the abstract class.

Here is an example implementation of the Factory Design Pattern in Java:

```java
public interface Shape {
    void draw();
}

public class Rectangle implements Shape {
    @Override
    public void draw() {
        System.out.println("Inside Rectangle::draw() method.");
    }
}

public class Square implements Shape {
    @Override
    public void draw() {
        System.out.println("Inside Square::draw() method.");
    }
}

public class Circle implements Shape {
    @Override
    public void draw() {
        System.out.println("Inside Circle::draw() method.");
    }
}

public class ShapeFactory {
    public Shape getShape(String shapeType) {
        if(shapeType == null){
            return null;
        }
        if(shapeType.equalsIgnoreCase("CIRCLE")){
            return new Circle();
        } else if(shapeType.equalsIgnoreCase("RECTANGLE")){
            return new Rectangle();
        } else if(shapeType.equalsIgnoreCase("SQUARE")){
            return new Square();
        }
        return null;
    }
}
```