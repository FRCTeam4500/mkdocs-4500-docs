A method is a block of code that does something. Every method has five parts: the scope, return type, name, parameters, and actual code.

### Scope
The scope of the method states where in the program it can be used. There are two main scopes that we use, public and private.\
Public scope, also known as global scope, means that the method can be used anywhere in the program. \
Private scope, also known as local scope, means that the method can only be used inside the class it was created in.

### Return Type
Sometimes, a method should hand back data to where it was called. Return type is used to declare what type of information the method will send back. Methods can return primatives or objects, using the `return` keyword. If a method returns a data type, that method call can be used as if it was that data type. \
However, not all methods need to return data. If a method doesn't need to return data, its return type is `void`.

### Name
Every method needs a name, which is how it can be called by other parts of the program. By convention, we use camel case to name our methods, meaning every word is capitalized except for the first. For example `testMethod` would be a conventional method name. Your method name should be descriptive enough that the person using it should have a clear idea of its purpose.

### Parameters
Sometimes, a method needs outside information to complete its task. We can pass in this outside information as parameters. Inside the parentheses beside the method name, we can put in as many parameters as needed, seperated by commas. Each parameter needs a type and a name. For example, a method could have the parameters `double runtime, boolean logData`, since each parameter has a name and type, and the parameters are seperated by commas.

### Code
The final part of the method is the code that runs when the method is called. Pretty much anything can go inside a method, from creating objects to calling other methods. If the method has a return type that isn't void, it must return data of that type. Parameters can be called by their name, and if there is a conflict between a parameter name and the name of another variable, the parameter will be chosen.

### Example Function
```java 
private int studentAge = 14;
/*** This method has a public scope and returns a student's age as an integer */
public int getStudentAge() {
    return studentAge;
}

/*** This method has a public scope, but no return type. It takes a new age as an input and sets the students age to that age. */
public void setStudentAge(int newAge) {
    studentAge = newAge;
}

/*** This method also has a public scope and no return type. It changes the student's age by a certain amount of years. Notice how it is calling the setStudentAge function, and also how the getStudentAge function is being used in place of an integer */
public void changeStudentAge(int yearsAdded) {
    setStudentAge(getStudentAge() + yearsAdded);
}
```
