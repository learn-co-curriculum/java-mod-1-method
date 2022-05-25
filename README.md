# Method

## Learning Goals

- Explain methods in Java
- Explain how to return values from methods

## Introduction

A method is a way to group instructions so that they can be called upon as a group any time we need them to be executed. 

When we create a program, we give the computer instructions on what to do in a specific language, in our case in Java. 
To do so, Java gives us access to built-in functionality, such as the ability to display a text message on the screen: 

```java 
System.out.println("this message will be displayed as text on the screen"); 
```

`println()` is a "method" - it has instructions inside it that allow it to tell the computer to print the 
desired message on the screen. Those instructions, the ones inside `println` might be complex, but since they are 
wrapped up in a method, we can simply call that method and not care about how it goes about doing its work. 

When you go to a restaurant and ask for something on the menu, you communicate your order to the waiter and fully expect 
your food to show up on a plate at your table as a result a few minutes later. You don't need to know who cooked it 
or the exact steps taken to cook it. You can imagine the cooking process being abstracted in a method called `cook()`

That method looks incomplete because you would expect to be able to specify what it is that you would like to have cooked. 
The information you pass to a method when you call it is contained in "parameters". Parameters are passed to a method inside 
the parenthesis following the method name: `cook("eggs")`, for example. 

You can also specify more than one parameter when you define a method - how would you like your eggs cooked: 
`cook("eggs", "scrambled")`. Multiple parameters are separated by a comma `,` between each parameter in the method call

The Java call to print something on the screen takes a single parameter, which is the same to print. You will also note that 
the method call is inside a specific "object", which is itself inside a specific "class". We know what a class is from
the section above, and we're about to learn about an "object" is. We can refer to the `System` class within any of our 
own classes in Java, and then we can use the dot notation `.` to access one of the objects in that class, in this case the 
`out` object: 

```java
System.out.println("The println() method is in the out object, which is in the System class"); 
```

## Method return type 

A method can return a value after it's done executing. This is optional and some methods, such as the `println()` method 
we have been discussing, do not return anything. The job of the `println()` method, for example, is to write text on the console - 
once it's done performing that work, it simply returns the execution to the method that called it and does not return 
any value. This is expressed in the signature of the method with the `void` keyword: 

```java
public void thisMethodReturnsNothing() {
    System.out.println("I print something on the screen, and then return nothing");     
} 
```

Methods can optionally specify a return type, meaning that every time the method is called, it is expected to return a value 
of the specified type. When a method returns something, its signature looks like this: 

```java
public int addTwoIntegers(int a, int b) {
    int sum = a + b; 
    return sum; 
}
```

The `return` keyword is used to return a specific value from a method. Note that the `return` keyword interrupts the 
execution of the current method and returns the specified value to the caller (i.e. the method that called this method). 

It's important to understand that any instruction after a `return` statement does not get executed. For example, the following 
code will not compile because the code after the `return` statement can never be reached by the JVM and is therefore considered invalid: 

```java
public int addTwoIntegers(int a, int b) {
        int sum = a + b;
        return sum;
        System.out.println("this code can never be reached"); 
}
```

The method we created to add two numbers can then be called as follows: 

```java
    ...
        
    int sum = addTwoIntegers(10, 15); 
    System.out.println("The result is " + sum); 
    
    ... 
```

The value that gets returned from calling the method can be saved in a variable for future use or can be used directly in an expression. 

Note that methods that do not return anything can still use the `return` keyword to interrupt their execution. The usefulness 
of this feature will become more apparent once we introduce conditional statements. 

Here are a few rules to remember about method return types: 

- A method must always have a return type, but that type can be `void` to specify that the method does not return anything 
- A method return type can be any valid Java type, which means it can be any pre-defined Java type or any of your own classes 
- If a method is declared with a return type other than `void`, it *must* return a value compatible with that type
- The only exception to the previous rule is if the method throws an actual exception, in which case it will only return 
the exception 
