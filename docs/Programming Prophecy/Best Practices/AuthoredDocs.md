
# Authored Documentation

Authored documentation makes it easy to attribute credit to the people who made segments of the code.

What we would like from everyone is to make docstrings similar to this:

```java hl_lines="13"
/**
 * Some class is a class
 * @author Saaleh Poovathumkadavil
 */
public class SomeClass {

    [...Attributes]
    
    /**
     * Creates new SomeClass object
     * @param something is of type meters/second
     * @param somethingElse is of type meters
     * @author Saaleh Poovathumkadavil
     */
    public SomeClass(double something, double somethingElse) {
        this.something = something
        this.somethingElse = somethingElse
    }

    [...Methods]

}
```

!!! note "What this looks like in VSCode:"
    Creates new SomeClass object

    **Parameters**:

    - **something** is of type meters/second

    - **somethingElse** is of type meters

    **Author**:

    - Saaleh Poovathumkadavil

nessesary in use by [level 3](../../2024%20Badge%20System/Level3.md)


