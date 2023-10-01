## Command Design Pattern

The Command Design Pattern is a behavioral design pattern that turns a request into a stand-alone object that contains all information about the request. This transformation lets you pass requests as a method arguments, delay or queue a request’s execution, and support undoable operations.

WPI implements the Command Design Pattern in the WPILib library. The `Command` class is the base class for all commands in WPILib. A command is an object that represents an action to be taken. It is used to encapsulate the code that implements the action, and to provide a way to undo the action if necessary. 

To use the Command Design Pattern in WPILib, you can create a new class that extends the `Command` class. You can then override the `initialize()`, `execute()`, and `end()` methods to define the behavior of the command. Once you have defined your command, you can add it to a `CommandGroup` to create more complex behavior.

```java title="Using Command Class Provided"
public class MyCommand extends CommandBase { // Sendable and Command
    public MyCommand() {
        super("MyCommand");
    }

    @Override
    protected void initialize() {
        // TODO: Add initialization code here
    }

    @Override
    protected void execute() {
        // TODO: Add execution code here
    }

    @Override
    protected void end() {
        // TODO: Add end code here
    }

    @Override
    protected void interrupted() {
        // TODO: Add interrupted code here
    }
}
```
