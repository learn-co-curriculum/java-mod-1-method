# Method

## Learning Goals

- Explain methods in Java
- Describe the method header
- Discuss how to write methods

## Introduction

We have been hearing about methods in previous lessons, let's now finally dive into what a method actually is in Java!

## What is a Method?

A method is a way to group instructions so that they can be called upon as a group any time we need them to be executed.

When we create a program, we give the computer instructions on what to do in a specific language, in our case in Java.
To do so, Java gives us access to built-in functionality, such as the ability to display a text message on the screen:

```java
System.out.println("this message will be displayed as text on the screen"); 
```

`println()` is a "method" - it has instructions inside it that allow it to tell the computer to print the
desired message on the screen. Those instructions, the ones inside `println` might be complex, but since they are
wrapped up in a method, we can simply call that method and not care about how it goes about doing its work.

## Method Headers and Writing Methods

Before we can write a method ourselves, we need to understand the method header. 

![method-header](https://curriculum-content.s3.amazonaws.com/java-mod-1/method/Method-Header.png)

### Access Modifiers

Every method has an **access modifier**. We have learned about the `private`, `public`, and default access modifiers
already, so we can use one of those access modifiers to create our new method! Keep in mind if other classes should
be able to have access to the method(s) we intend on creating.

### Return Values

A method can return a value after it's done executing. In Java, we want to specify what data type is to be returned
once the method has completed. We call this a **return type**. It may return another object, a primitive, or even
nothing! 

Consider the `println()` method for example. The job of the `println()` method is to write text on the console and
once it's done performing that work, it simply returns the execution to the method that called it without returning
any value. This is expressed in the header of the method with the `void` keyword:

```java
public void thisMethodReturnsNothing() {
    System.out.println("I print something on the screen, and then return nothing");     
} 
```

Another example is the `public static void main(String[] args)` method we have been referring to. This method also
makes use of the `void` return type to tell us that it will not have a return value when the program finishes
executing.

Here are a few rules to remember about method return types:
- A method must always have a return type, but that type can be `void` to specify that the method does not return
  anything.
- A method return type can be any valid Java type, which means it can be any pre-defined Java type or
  any of our own classes we create.
- If a method is declared with a return type other than `void`, it _must_ return a value compatible with that type.

### Method Name

The **method name** is what we want to call our method.
When naming methods, it is best to be descriptive yet concise with the action that is to be performed inside the method.
For example, if we expect the method to cook us some food, we should not name the method `x()` but rather `cook()`.

Simplifying the method name, yet being descriptive with the name to make it clear to other developers is very helpful.

### Parameter List

A **parameter list** is a list of the declarations needed for the method to function properly. Each parameter in the
parameter list needs to be in a declaration format as such: `<type> <variableName>`. It is also possible to not have a
parameter list. An empty parameter list would look like this: `()`. If multiple parameters exist, then they are to be
separated by a comma `,` between each parameter. Example: `cook("eggs", "bacon")`.

In the `public static void main(String[] args)` method, we can see that this `main` method does indeed
have some parameters associated with it. It looks like the `main` method takes in a parameter `String[] args`.
`args` is the variable name and has the data type of `String[]`. We haven't yet learned about the symbol `[]`, but know
that this parameter is saying it takes in an array of `String` values. The array of `String` values is called `args`
because it represents the arguments that can be passed into the program when it is run from the command line. We will
learn more about this in a later unit, so we can ignore the `args` variable for now, just know that it does need
to be part of the method definition for the `main` method.

Now that we have defined the method header defined, we can see how to write a method!

### Writing Methods

Let us consider our `Bicycle` class again and try to write a method for it!

Let's create a public method named `ride` that takes no parameters and returns nothing:

```java
public class Bicycle {
    private String color;
    private int height;
    
    public void ride() {
        System.out.println("We're going for a ride! Whee!");
    }

}
````

Now we can call the `ride()` method using the syntax dot notation again. Except this time, instead of accessing the
attribute, we will be accessing the method. So the `Bicycle` instance will receive a message called `ride()` by
separating the receiving object from the message using a dot (`.`).

```java
Bicycle johnsBike = new Bicycle();
Bicycle clairesBike = new Bicycle();
johnsBike.ride();
clairesBike.ride();
```

Notice that we can call the method on multiple objects. We can also add a parameter to the `ride()` method.

```java
public class Bicycle {
    private String color;
    private int height;
    
    public void ride(String message) {
        System.out.println(message);
    }
    
    public static void main(String[] args) {
        Bicycle johnsBike = new Bicycle();
        johnsBike.ride("Pedal faster!");
    }
}
````

We can also have the `ride()` method return a `String`.

```java
public class Bicycle {
    private String color;
    private int height;
    
    public String ride() {
        return "Look! No handlebars!";
    }
    
    public static void main(String[] args) {
        Bicycle johnsBike = new Bicycle();
        String message = johnsBike.ride();
    }
}
````

The `return` keyword is used to return a specific value from a method. Note that the `return` keyword interrupts the
execution of the current method and returns the specified value to the caller (i.e. the method that called this method).

It's important to understand that any instruction after a `return` statement does not get executed. 
For example, the following code will not compile because the code after the `return` statement can never be reached by
the JVM and is therefore considered invalid:

```java
public class Bicycle {
    private String color;
    private int height;
    
    public String ride() {
        return "We're going for a ride! Whee!";
        System.out.println("This code can never be reached");
    }

}
````

Note that methods that do not return anything can still use the `return` keyword to interrupt their execution. 
The usefulness of this feature will become more apparent once we introduce conditional statements.
