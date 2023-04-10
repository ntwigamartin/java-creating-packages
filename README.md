# Creating Packages

## Learning Goals

- Use IntelliJ to create an application with multiple packages

## Code-Along

Fork and clone this lesson.  We will create an application with multiple packages.

The current project contains a class named `Main` that is in the default Java package:

![initial project structure](https://curriculum-content.s3.amazonaws.com/6676/packages/main_in_default_package.png)


Right-click on the "java" folder and select "New/Package" from the menu.
Name the package "controller".

![IntelliJ create new package](https://curriculum-content.s3.amazonaws.com/6676/packages/new_controller_package.png)

Your project structure should look like this:

![Project structure with one packages](https://curriculum-content.s3.amazonaws.com/6676/packages/package_structure_1.png)

Drag the `Main` class to move it out of the default package and into the "controller" package.
Your project structure should look like this:

![Project structure with Main in controller package](https://curriculum-content.s3.amazonaws.com/6676/packages/package_structure_2.png)

Notice the `Main` class now has `package controller;` as the first statement.
The package statement is required when a class is not in the default package.


```java
package controller;

public class Main {
    
}
```


Right-click again on the "java" folder (make sure you are not right-clicking the "controller" folder)
and select "New/Package" from the menu.  Name the second package "entity".


![new entity package](https://curriculum-content.s3.amazonaws.com/6676/packages/new_entity_package.png)

Your project structure should look like this:

![Project structure with two packages](https://curriculum-content.s3.amazonaws.com/6676/packages/package_structure_3.png)


Right-click on the "entity" package and select "New/Java Class".
Name the class "Person".

![New Person Class in entity package](https://curriculum-content.s3.amazonaws.com/6676/packages/new_class_entity_package.png)

Your project structure should look like the image below.

![Project structure with Person class](https://curriculum-content.s3.amazonaws.com/6676/packages/package_structure_4.png)


Notice the first
statement in the `Person` class is `package entity;`.

```java
package entity;

public class Person {
    
}
```

Edit the `Person` class as shown:

```java
package entity;

public class Person {

    private String name;

    public Person(String name) {
        this.name = name;
    }

    @Override
    public String toString() {
        return "Person{" +
                "name='" + name + '\'' +
                '}';
    }
}
```


Now we will add a `main()` method  to the `Main` class located in the `controller` package.
The `main()` method should create an instance of `Person` as shown below.
The code  won't compile because we are missing the import statement
for the `Person` class.

```java
package controller;

public class Main {
    public static void main(String[] args) {
        Person person = new Person("Chai");
        System.out.println(person);
    }
}
```

IntelliJ's compiler indicates an error by changing the text color to red
for each reference to the `Person` class.  Hover over `Person` to
have IntelliJ suggest a quick fix for the compiler error.
Click the "Import class" suggestion.

![Hover over Person error](https://curriculum-content.s3.amazonaws.com/6676/packages/hover_over_person.png)

IntelliJ adds the statement `import entity.Person;`.  The import statement
specifies the package of the `Person` class. The import statement is written
after the package statement and before the class definition.

```java
package controller;

import entity.Person;

public class Main {
    public static void main(String[] args) {
        Person person = new Person("Chai");
        System.out.println(person);
    }
}
```

We should be able to run the `main()` method now and see the output:

```text
Person{name='Chai'}
```


The import statement can import a single class:

```java
import entity.Person;
```

We can also use the character `*` to import all classes
within a package, for example:

```java
import entity.*;
```

## Conclusion

A Java project may consist of multiple packages.  Each class must specify
the package as the first statement, unless the class is located in the default package.
An import statement can import an entire package or a single class.
