## Multiple Choice Practice Questions Answers

## Question 1
On a bike, there are one or more tyres.
The following relationship is an example of:

**A) Aggregation**\
B) Composition\
C) Neither

**Rationale**\
This would be an example of Aggregation as opposed to Composition, because tyres can exist physically outside of the system. Tyres are entities that can exist independently from a bike in the context of a real world scenario.

## Question 2

Consider the following lambda function which prints log. The type signature has been redacted.

`[redacted] logger = log -> System.out.println(log);`

Pick the most semantically correct type from the list below:


A) Function<String, Boolean>\
**B) Consumer**\
C) Predicate\
D) Supplier

**Rationale**\
Consumer is the correct choice here, as the Consumer type is the only one of the types listed that actually maps the parameter to a void function, since the body of the anonymous function described only needs to print out a given parameter, `log`.

A) Would map a String to Boolean, C) Predicate maps from a single type to a Boolean, and D) Supplier maps from no given types to a specified type.

## Question 3

An insurance company wants to create a new way to process new home insurance claims. For an insurance claim to be processed, it needs to go through the following stages.

1. The general information of the applicant needs to be collected and processed.
2. The home/property information needs to be collected and processed.
3. Based on the level of insurance requested the quote needs to be calculated.
4. The quote is then sent to the customer.

Which design pattern would be the best for solving this problem?

**A) Builder Pattern**\
B) Factory Pattern\
C) Template Pattern\
D) Adapter

**Rationale**\
Builder pattern is the best answer here, as you can add multiple different parts/attributes which can be calculated. Template could be useful with a specific implementation for different types, its behaviour is static, and can't have any dynamic behaviour, Builder pattern excels since it can have numerous different components which the Template pattern lacks.

## Question 4
The following is taken from a student’s Assignment II blog.

> In Assignment II, after I completed Part 1 and refactored the code, I started work on Part 2 but found I had to go and modify everything because the design didn’t work with the new requirements.

Which SOLID principle is being violated? Select the most suitable answer.

A) Single Responsibility Principle\
B) **Open-Closed Principle**\
C) Liskov Substitution Principle\
D) Interface Segregation Principle\
E) Dependency Inversion Principle

**Rationale**\
The Open-Closed Principle is the main violation here, since the student had to go back and edit existing code to accomodate for a new change being introduced. Therefore the answer is B).

It is not A), as class responsbility is not a concern, nor is it the issue the question asks. It is not C), as subclass replacement seems not to be an issue outlined in the question. It is not D) as many client-specific interfaces is not a specific concern. Finally it is not E), as dependency on concretions rather than abstractions is not a specified concern.

## Question 5

Which of the following statements is correct?

A) Overloaded methods have the same method signature, while overridden methods have a different method signature.\
B) Overloaded methods can have different access modifiers, while overridden methods must have the same access modifier.\
C) Overloaded methods are defined in different classes, while overridden methods are defined in the same class.\
**D) Overloaded methods are resolved at compile-time, while overridden methods are resolved at runtime.**

**Rationale**\
D) is true, because method overloading is considered a compile-time polymorphism. Since the same method can have different method signatures, this is done at compile time - the type checking for a specific parameter(s) is done at compilation levels for the correct method to use. Whereas method overridding is an example of runtime polymorphism. To run overridden sublcasses, the compiler must know the exact type - otherwise it risks running the wrong method. 

A) is false, since the opposite is true. Overloaded methods have a different signature, whereas overriden methods have the same.

B) is false, since overridden methods can have different access modifiers and still be valid. For example, `protected` methods in a super class can be overriden as `public` in a subclass. This means overriding is valid as long as access modifiers are the same or increase visibility. However, `private` methods are an exception, since `private` means the function would not even be visible to a subclass, meaning overridding is impossible. 

C) is false, since overloaded methods are defined in the same class with different method signatures. Whilst overridden methods rely on inheritance, so they must be in subclasses.

## Question 6

Suppose we have the following classes defined: class Shape { … } class Circle extends Shape { … }

Now suppose we have a program that contains the following objects and lists:

```java
Object o;
Shape s;
Circle c;
List<? extends Shape> l1;
List<? super Shape> l2;
```



Suppose we wanted to run the following 12 commands:

```java
l1.add(c);
l2.add(c);
l1.add(s);
l2.add(s);
l1.add(o);
l2.add(o);
c = l1.get(0);
c = l2.get(0);
s = l1.get(0);
s = l2.get(0);
o = l1.get(0);
o = l2.get(0);
```

How many of the above commands have a type error?

A) 4\
B) 5\
C) 6\
**D) 7**\
E) 8

**Rationale**\
`l1` is a `List` which can contain any subclass of `Shape`, whereas `l2` is a `List` which can contain any subclass of `Shape`. With this in mind, 

`l1.add(c);` would be invalid since we cannot guarantee that all the elements in `l1` are `Shape` or a subclass of it. `l1` could contain a list of `Circle`, `Rectangle`, `Square`, etc. With this reasoning, `l1.add(s);` is also invalid.

`l2.add(c);` *is* valid, because the generic parameter in `l2` specifies that we can add any `Shape` or any `Shape` superclass to it. Whilst we do not know which specific superclass it is, we know that `Circle` is a subclass of `Shape`, meaning that it also can be cast as as any super class of `Shape`. This means we can guarantee that it fits any possible class in the domain specified by the generic parameter. `l2.add(s);` is valid for the same reason. 

`l1.add(o);` is invalid since we don't know if `o` is a `Shape` or a subclass of it. `l2.add(o);` is invalid since we can't guarantee that the `Object` is not a lower super class of `Shape`.

***

`c = l1.get(0); and c = l2.get(0);` is invalid, since we don't know if the elements in `l1` or `l2` would be a `Circle` for certain. `s = l2.get(0);` is invalid for similar reasons, we don't know for certain if the object inside `l2` is a `Shape`, just that anything in `l2` could contain super classes of `Shape`.

`o = l1.get(0);`, `o = l2.get(0);`, `s = l1.get(0);` is valid, since all classes are Objects, followed by the fact that all elements in `l1` must be a `Shape` or a a subclass of it.

Thus the total number of incorrect is 7.

## Question 7

Which of the following statements is untrue about method overriding?

A) Constructors cannot be overridden\
B) If a static method in the base class, is redefined in the sub-class, the later hides the method in the base class\
C) In method overriding, run-time polymorphism ensures that instantiated, the call to any method in the base class will be resolved to the correct method, based on the run-time type of the object instantiated.\
**D) During method overriding, the overridden method in the sub-class can specify a less permissive access modifier**

**Rationale**\
D) is untrue, since overridden methods in subclasses must be the same level of access modifier or greater. The only exception being that `private` cannot be changed since subclasses cannot even inherit them to change the access modifier. 

A) is true, since constructors cannot be overridden like a normal method can since you can't just make a subclass of it and override it.

B) is true, since static methods don't override in the traditional sense - it's that in subclasses, the static method fo the super class is hidden.

C) Is true because method overridding is run-time polymorphism, and the exact type at run-time must be known for overridden methods to be appropriately called.

## Question 8

A design pattern used to enhance a component’s functionality dynamically at run-time is:

A) Composite Pattern\
**B) Decorator Pattern**\
C) Abstract Factory Pattern\
D) Observer Pattern

**Rationale**\
B) is the answer, as Decorator's main function is to dynamically add new functionality to an object. 

## Question 9
Which of the following exceptions must be handled by a try-catch block or declared?

A) NullPointerException\
**B) MalformedURLException**\
C) ClassCastException\
D) ArithmeticException

**Rationale**\
A, C, D are all Exceptions that are extended from `RuntimeException`. These occur during runtime, thus do not need to be extended, since these are unchecked exceptions. Meanwhile, `MalformedURLException` extends from `IOException`, which is a checked exception and must be handled.


## Question 10
An online camping store, sells different kinds of camping equipment. Items selected by the customer are added to a shopping cart. When a user clicks on the checkout Button, the application is required to calculate the total amount to be paid. The calculation logic for each item type varies, and we want to move all the calculation logic to one separate class, to decouple the different items from the calculation logic applied on them. As the application iterates through the disparate set of items of the shopping cart, we apply the price computation logic in the class to each item type. Which of the following patterns would be useful to design this scenario?

A) Strategy Pattern\
B) Decorator Pattern\
C) Iterator Pattern\
**D) Visitor Pattern**

**Rationale**\
The answer is D), since Visitor Pattern allows algorithms to be executed on objects without needing to modify existing code for the class AND it can implement specializations of a virtual operation/method. This lines up with the main issue, being that the price calculation for different items can vary. This also greatly preserves the Open-Closed principle, which is very useful in a supermarket that might stock more and more items.

The answer is not A) Strategy Pattern, since whilst have a single execute method can be useful - we are not swapping between instances at runtime, but processing multiple.

The answer is not B) Decorator Pattern, since we aren't layering more functionalities on top - we want a lot of predefined methods for different items.

The answer is not C) Iterator Pattern, because while iteration is mentioned, it is not the main issue being addressed, being the different items need to have specialised calculation methods.

## Question 11

For generic types in Java, which of the following is/are correct? Select one or more:

A) `List<Integer>` is a subtype of `List<Number>`.\
**B) `List<? super Integer>` matches `List<Number>` and `List<Object>`.**\
**C) The wildcard `< ? extends Foo >` matches `Foo` and any subtype of `Foo`, where `Foo` is any type.**\
D) The wildcard `< ? extends Foo >` matches `Foo` and any super type of `Foo`, where `Foo` is any type.

**Rationale**\
B) and C) are correct:

B) is a List with a parameter which can contain an Integer or any super class of it. Number and Object fit this, so this is true. 
C) is a List with a parameter which can contain Foo or any subtype of Foo, so by definition, this is correct.

A) is incorrect, since generic parameters do not behave like that - the parameter does not make it a subclass. D) is incorrect as it contradicts the defintion in D).

## Question 12

Consider a vending machine application that dispenses products when the proper combination of coins is deposited. Which of the following design patterns is suitable for such a vending machine application?

A) Strategy Pattern\
B) Composite Pattern\
C) Visitor Pattern\
**D) State Pattern**

D) is the most appropriate, as the vending machine has predefined state behaviour as described. It will switch to a release state after a combination of coins is deposited.

A) is not appropriate, since the vending machine isn't responsive to dynamic change - it changes according to predefined behaviour.

B) is not appropriate, since there is no binary tree behaviour.

C) is not appropriate, since we don't have multiple specialised varying function implementations.

## Question 13

Consider the following code:

```java
class X {
    public void a() {}
}

class Y {
    public void b() {}
}

class Z extends X, Y {
    protected void a() {}

    public void b() {}

    public void b(String arg) {}
}

```
Now, consider the following statements about the code:

(1) The code doesn’t compile because there is more than one class in the same file;\
(2) The code doesn’t compile because double inheritance is not possible in Java;\
(3) The code doesn’t compile because the methods a and b are not marked with @Override\
(4) The code doesn't compile because you cannot overload a method that is overriding a method in a superclass;\
(5) The code doesn’t compile because a cannot have its visibility reduced from the superclass to the subclass.\
(6) The code does compile.
Which of the following sets of statements about the code are true

Which of the following sets of statements about the code are true?

A) (1), (2)\
B) (1), (3), (5)\ 
C) (2), (3), (4), (5)\
**D) (2), (5)**\
E) (2), (4), (5)\
F) (6)

**Rationale**\
D) is correct.\
`2)` is true since multiple inheritance is unsupported in Java.\
`5)` is also true, because the function `a()` is changing from `public` to `protected` in a subclass, which is more restrictive.

`1)` is false since Java supports this.\
`3)` is false, since overriding without an explicit `@Override` is compliable in Java.\
`4)` is false, since overloading is done in the same class and doesn't really affect overridding in any way.\
`6)` is false, because `2)` and `5)` are true.

## Question 14

Nick is currently working on a UNSW CSE system. Which of the following statements is most accurate about how Nick should build the system?

A) The system should be built in Java so that Design Patterns can be used.\
B) Documentation is unimportant as the code should be written so well it is understandable.\
**C) The design should allow new engineers to easily join the project after Nick has left.**\
D) Testing the system works is a lower priority than getting it working.

**Rationale**\
C) is correct, since this is the essence of readable, maintanable code.\
A) is incorrect, since Design Patterns aren't exclusive to Java.\
B) is incorrect, since Documentation is always necessary for maintanable code.\
D) is incorrect, since Testing should be a primary concern, and thoroughly written out before implementation begins.

## Question 15

Consider the following statement:

When we wrote the exam, we double-checked everything, but when it came to having the students sit the exam, there was a problem in Question 15 that we didn’t pick up.

What type of unknown is present in the above scenario?\
A) A known unknown\
**B) An unknown unknown**\
C) There are no unknowns present in the above scenario.

B) is the answer as the problem was not forseen during checking. So it is an unknown unknown.

## Question 16
Which of the following would be a valid use case for instanceof instead of getClass for checking the type of an object?

**A) Checking if an object complies with an interface so that we can use a method on that interface\**
B) Implementing the equals method for an object\
C) It’s a trick question, you should never use instanceof in your code at all

**Rationale**\
A) is correct, since `instanceof` can be very useful for typechecking certain interfaces and behaviours.\
B) is incorrect, since `equals()` should use `getClass()`\
C) is incorrect, since `instanceof` can and should be used.


















