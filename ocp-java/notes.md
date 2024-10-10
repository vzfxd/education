
## Chapter 1: Building Blocks

### Defining Instance and Class Variables 
Instance and class variables do not require you to initialize them. As soon as you declare these variables, they are given a default value.
```java
class Animal{
    private int a; // 0
    private static int b; // also 0
}
```

### Inferring the Type with var
full name is local variable type inference, so you can use it only with local variables.<br>

```java
class VarKeyword {
   var tricky = "Hello"; // DOES NOT COMPILE
}
```

```java
public int addition(var a, var b) { // DOES NOT COMPILE
   return a + b;
}
```
var variables cant be declared without initialization
```java
var a;
a = 10  
```
var cannot be used in compound declaration
```java
var a = 5, a = 10;
```
### Summary
Java begins program execution with a ```main()``` method. The most common signature for this method run from the command line is
```public static void main(String[] args)```
.Arguments are passed in after the class name, as in ```java NameOfClass firstArgument```. Arguments are indexed starting with ```0```.

Java code is organized into folders called packages. To reference classes in other packages, you use an ```import``` statement. A wildcard ending an ```import``` statement means you want to ```import``` all classes in that package. It does not include packages that are inside that one. The package java.lang is special in that it does not need to be imported.

For some class elements, order matters within the file. The package statement comes first if present. Then come the ```import``` statements if present. Then comes the class declaration. Fields and methods are allowed to be in any order within the class.

Primitive types are the basic building blocks of Java types. They are assembled into reference types. Reference types can have methods and be assigned a ```null``` value. Numeric literals are allowed to contain underscores (```_```) as long as they do not start or end the literal and are not next to a decimal point (```.```). Wrapper classes are reference types, and there is one for each primitive. Text blocks allow creating a ```String``` on multiple lines using ```"""```.

Declaring a variable involves stating the data type and giving the variable a name. Variables that represent fields in a class are automatically initialized to their corresponding ```0, null, or false``` values during object instantiation. Local variables must be specifically initialized before they can be used. Identifiers may contain letters, numbers, currency symbols, or``` _```. Identifiers may not begin with numbers. Local variable declarations may use the ```var``` keyword instead of the actual type. When using ```var```, the type is set once at compile time and does not change.

Scope refers to that portion of code where a variable can be accessed. There are three kinds of variables in Java, depending on their scope: instance variables, class variables, and local variables. Instance variables are the non-```static``` fields of your class. Class variables are the ```static``` fields within a class. Local variables are declared within a constructor, method, or initializer block.

Constructors create Java objects. A constructor is a method matching the class name and omitting the return type. When an object is instantiated, fields and blocks of code are initialized first. Then the constructor is run. Finally, garbage collection is responsible for removing objects from memory when they can never be used again. An object becomes eligible for garbage collection when there are no more references to it or its references have all gone out of scope.


### Exam Essentials
**Be able to write code using a main() method**. A ```main()``` method is usually written as ```public static void main(String[] args)```. Arguments are referenced starting with ```args[0]```. Accessing an argument that wasn't passed in will cause the code to throw an exception.

**Understand the effect of using packages and imports**. Packages contain Java classes. Classes can be imported by class name or wildcard. Wildcards do not look at subdirectories. In the event of a conflict, class name imports take precedence. Package and `import` statements are optional. If they are present, they both go before the class declaration in that order.

**Be able to recognize a constructor**. A constructor has the same name as the class. It looks like a method without a return type.

**Be able to identify legal and illegal declarations and initialization**. Multiple variables can be declared and initialized in the same statement when they share a type. Local variables require an explicit initialization; others use the default value for that type. Identifiers may contain letters, numbers, currency symbols, or `_`, although they may not begin with numbers. Also, you cannot define an identifier that is just a single underscore character `_`. Numeric literals may contain underscores between two digits, such as `1\_000`, but not in other places, such as `\_100\_.0\_`.

**Understand how to create text blocks**. A text block begins with `"""` on the first line. On the next line begins the content. The last line ends with `"""`. If """ is on its own line, a trailing line break is included.

**Be able to use var correctly**. A `var` is used for a local variable. A `var` is initialized on the same line where it is declared, and while it can change value, it cannot change type. A `var` cannot be initialized with a `null` value without a type, nor can it be used in multiple variable declarations.

**Be able to determine where variables go into and out of scope**. All variables go into scope when they are declared. Local variables go out of scope when the block they are declared in ends. Instance variables go out of scope when the object is eligible for garbage collection. Class variables remain in scope as long as the program is running.

**Know how to identify when an object is eligible for garbage collection**. Draw a diagram to keep track of references and objects as you trace the code. When no arrows point to a box (object), it is eligible for garbage collection.

## Chapter 2: Operators

### Numeric Promotion
1. If two values have different data types, Java will automatically promote one of the values to the larger of the two data types.
2. If one of the values is integral and the other is floating-point, Java will automatically promote the integral value to the floating-point value's data type.
3. Smaller data types, namely, `byte`, `short`, and `char`, are first promoted to `int` any time they're used with a Java binary arithmetic operator with a variable (as opposed to a value), even if neither of the operands is int.
4. After all promotion has occurred and the operands have the same data type, the resulting value will have the same data type as its promoted operands.

### Compound Assignment Operators
`a+=b` itp.<br>
automaticly cast variables.
```java
long goat = 10;
int sheep = 5;
sheep *= goat;
```

### instanceof
```java
public void openZoo(Number time) {
   if(time instanceof String) // DOES NOT COMPILE
      System.out.print(time);
}
```
always returns false with null
```java
System.out.print(null instanceof Object);  // false
 
Object noObjectHere = null;
System.out.print(noObjectHere instanceof String);  // false
```
```java
System.out.print(null instanceof null);  // DOES NOT COMPILE
```


### Summary
This chapter covered a wide variety of Java operator topics for unary, binary, and ternary operators. Hopefully, most of these operators were review for you. If not, you need to study them in detail. It is important that you understand how to use all of the required Java operators covered in this chapter and know how operator precedence and parentheses influence the way a particular expression is interpreted.

There will likely be numerous questions on the exam that appear to test one thing, such as NIO.2 or exception handling, when in fact the answer is related to the misuse of a particular operator that causes the application to fail to compile. When you see an operator involving numbers on the exam, always check that the appropriate data types are used and that they match each other where applicable.

Operators are used throughout the exam, in nearly every code sample, so the better you understand this chapter, the more prepared you will be for the exam.

### Exam Essentials
**Be able to write code that uses Java operators**. This chapter covered a wide variety of operator symbols. Go back and review them several times so that you are familiar with them throughout the rest of the book.

**Be able to recognize which operators are associated with which data types**. Some operators may be applied only to numeric primitives, some only to boolean values, and some only to objects. It is important that you notice when an operator and operand(s) are mismatched, as this issue is likely to come up in a couple of exam questions.

**Understand when casting is required or numeric promotion occurs**. Whenever you mix operands of two different data types, the compiler needs to decide how to handle the resulting data type. When you're converting from a smaller to a larger data type, numeric promotion is automatically applied. When you're converting from a larger to a smaller data type, casting is required.

**Understand Java operator precedence**. Most Java operators you'll work with are binary, but the number of expressions is often greater than two. Therefore, you must understand the order in which Java will evaluate each operator symbol.

**Be able to write code that uses parentheses to override operator precedence**. You can use parentheses in your code to manually change the order of precedence.

## Chapter 3: Making Decisions

### Determining Acceptable Case Values
values in each case statement must be compile-time constant values of the same data type as the switch value.
```java
final int getCookies() { return 4; }
void feedAnimals() {
   final int bananas = 1;
   int apples = 2;
   int numberOfAnimals = 3;
   final int cookies = getCookies();
   switch(numberOfAnimals) {
      case bananas:
      case apples:        // DOES NOT COMPILE
      case getCookies():  // DOES NOT COMPILE
      case cookies :      // DOES NOT COMPILE
      case 3 * 5 :
   } }
```

### Summary
This chapter presented how to make intelligent decisions in Java. We covered basic decision-making constructs such as `if, else, and switch` statements and showed how to use them to change the path of the process at runtime. We also presented newer features in the Java language, including pattern matching and `switch expressions`, both designed to reduce boilerplate code.

We then moved our discussion to repetition control structures, starting with `while and do/while` loops. We showed how to use them to create processes that loop multiple times and also showed how it is important to make sure they eventually terminate. Remember that most of these structures require the evaluation of a particular `boolean` expression to complete.

Next, we covered the extremely convenient repetition control structures: the `for` and `for-each` loops. While their syntax is more complex than the traditional `while or do/while` loops, they are extremely useful in everyday coding and allow you to create complex expressions in a single line of code. With a `for-each `loop, you don't need to explicitly write a boolean expression, since the compiler builds one for you. For clarity, we referred to an enhanced `for` loop as a `for-each` loop, but syntactically both are written using the `for` keyword.

We concluded this chapter by discussing advanced control options and how flow can be enhanced through nested loops coupled with `break, continue, and return` statements. Be wary of questions on the exam that use nested loops, especially ones with labels, and verify that they are being used correctly.

This chapter is especially important because at least one component of this chapter will likely appear in every exam question with sample code. Many of the questions on the exam focus on proper syntactic use of the structures, as they will be a large source of questions that end in “Does not compile.” You should be able to answer all of the review questions correctly or fully understand those that you answered incorrectly before moving on to later chapters.

### Exam Essentials

**Understand if and else decision control statements**. The `if` and `else` statements come up frequently throughout the exam in questions unrelated to decision control, so make sure you fully understand these basic building blocks of Java.

**Apply pattern matching and flow scoping**. Pattern matching can be used to reduce boilerplate code involving an `if` statement, `instanceof` operator, and cast operation using a pattern variable. It can also include a pattern or filter after the pattern variable declaration. Pattern matching uses flow scoping in which the pattern variable is in scope as long as the compiler can definitively determine its type.

**Understand switch statements and their proper usage**. You should be able to spot a poorly formed `switch` statement on the exam. The `switch` value and data type should be compatible with the `case` statements, and the values for the `case` statements must evaluate to compile-time constants. Finally, at runtime, a `switch` statement branches to the first matching `case`, or `default` if there is no match, or exits entirely if there is no match and no `default` branch. The process then continues into any proceeding `case` or `default` statements until a break or return statement is reached.

**Use switch expressions correctly**. Discern the differences between `switch` expressions and `switch` statements. Understand how to write `switch` expressions correctly, including proper use of semicolons, writing `case` expressions and blocks that yield a consistent value, and making sure all possible values of the switch variable are handled by the `switch` expression.

**Write while loops**. Know the syntactical structure of all `while` and `do/while` loops. In particular, know when to use one versus the other.

**Be able to use for loops**. You should be familiar with `for` and for-each loops and know how to write and evaluate them. Each loop has its own special properties and structures. You should know how to use for-each loops to iterate over lists and arrays.

**Understand how break, continue, and return can change flow control**. Know how to change the flow control within a statement by applying a `break, continue, or return` statement. Also know which control statements can accept `break` statements and which can accept `continue` statements. Finally, you should understand how these statements work inside embedded loops or `switch` statements.

## Chapter 4: Core APIs

### Summary
In this chapter, you learned that a String is an immutable sequence of characters. Calling the constructor explicitly is optional. The concatenation operator (+) creates a new String with the content of the first String followed by the content of the second String. If either operand involved in the + expression is a String, concatenation is used; otherwise, addition is used. String literals are stored in the string pool. The String class has many methods.

By contrast, a StringBuilder is a mutable sequence of characters. Most of the methods return a reference to the current object to allow method chaining. The StringBuilder class has many methods.

Calling == on String objects will check whether they point to the same object in the pool. Calling == on StringBuilder references will check whether they are pointing to the same StringBuilder object. Calling equals() on String objects will check whether the sequence of characters is the same. Calling equals() on StringBuilder objects will check whether they are pointing to the same object rather than looking at the values inside.

An array is a fixed-size area of memory on the heap that has space for primitives or pointers to objects. You specify the size when creating it. For example, int[] a = new int[6];. Indexes begin with 0, and elements are referred to using a [0]. The Arrays.sort() method sorts an array. Arrays.binarySearch() searches a sorted array and returns the index of a match. If no match is found, it negates the position where the element would need to be inserted and subtracts 1. Arrays.compare() and Arrays.mismatch() check whether two arrays are equivalent. Methods that are passed varargs (…) can be used as if a normal array was passed in. In a multidimensional array, the second-level arrays and beyond can be different sizes.

The Math class provides a number of static methods for performing mathematical operations. For example, you can get minimums or maximums. You can round or even generate random numbers. Some methods work on any numeric primitive, and others only work on double.

A LocalDate contains just a date, a LocalTime contains just a time, and a LocalDateTime contains both a date and a time. All three have private constructors and are created using LocalDate.now() or LocalDate.of() (or the equivalents for that class). Dates and times can be manipulated using plusXXX or minusXXX methods. The Period class represents a number of days, months, or years to add to or subtract from a LocalDate or LocalDateTime. The date and time classes are all immutable, which means the return value must be used.

### Exam Essentials
Be able to determine the output of code using String. Know the rules for concatenating with String and how to use common String methods. Know that a String is immutable. Pay special attention to the fact that indexes are zero-based and that the substring() method gets the string up until right before the index of the second parameter.

Be able to determine the output of code using StringBuilder. Know that a StringBuilder is mutable and how to use common StringBuilder methods. Know that substring() does not change the value of a StringBuilder, whereas append(), delete(), and insert() do change it. Also note that most StringBuilder methods return a reference to the current instance of StringBuilder.

Understand the difference between == and equals(). == checks object equality. equals() depends on the implementation of the object it is being called on. For the String class, equals() checks the characters inside of it.

Be able to determine the output of code using arrays. Know how to declare and instantiate one-dimensional and multidimensional arrays. Be able to access each element and know when an index is out of bounds. Recognize correct and incorrect output when searching and sorting.

Identify the return types of Math methods. Depending on the primitive passed in, the Math methods may return different primitive results.

Recognize invalid uses of dates and times. LocalDate does not contain time fields, and LocalTime does not contain date fields. Watch for operations being performed on the wrong time. Also watch for adding or subtracting time and ignoring the result. Be comfortable with date math, including time zones and daylight saving time.

## Chapter 5: Methods

### Summary
In this chapter, we presented a lot of rules for declaring methods and variables. Methods start with access modifiers and optional specifiers in any order (although commonly with access modifiers first). The access modifiers we discussed in this chapter are private, package (omitted), protected, and public. The optional specifier for methods we covered in this chapter is static. We cover additional method modifiers in future chapters.

Next comes the method return type, which is void if there is no return value. The method name and parameter list are provided next, which compose the unique method signature. The method name uses standard Java identifier rules, while the parameter list is composed of zero or more types with names. An optional list of exceptions may also be added following the parameter list. Finally, a block defines the method body (which is omitted for abstract methods).

Access modifiers are used for a lot more than just methods, so make sure you understand them well. Using the private keyword means the code is only available from within the same class. Package access means the code is available only from within the same package. Using the protected keyword means the code is available from the same package or subclasses. Using the public keyword means the code is available from anywhere.

Both static methods and static variables are shared by all instances of the class. When referenced from outside the class, they are called using the class name—for example, Pigeon.fly(). Instance members are allowed to call static members, but static members are not allowed to call instance members. In addition, static imports are used to import static members.

We also presented the final modifier and showed how it can be applied to local, instance, and static variables. Remember, a local variable is effectively final if it is not modified after it is assigned. One quick test for this is to add the final modifier and see if the code still compiles.

Java uses pass-by-value, which means that calls to methods create a copy of the parameters. Assigning new values to those parameters in the method doesn't affect the caller's variables. Calling methods on objects that are method parameters changes the state of those objects and is reflected in the caller. Java supports autoboxing and unboxing of primitives and wrappers automatically within a method and through method calls.

Overloaded methods are methods with the same name but a different parameter list. Java calls the most specific method it can find. Exact matches are preferred, followed by wider primitives. After that comes autoboxing and finally varargs.

Make sure you understand everything in this chapter. It sets the foundation of what you learn in the next chapters.


### Exam Essentials
Be able to identify correct and incorrect method declarations. Be able to view a method signature and know if it is correct, contains invalid or conflicting elements, or contains elements in the wrong order.

Identify when a method or field is accessible. Recognize when a method or field is accessible when the access modifier is: private, package (omitted), protected, or public.

Understand how to declare and use final variables. Local, instance, and static variables may be declared final. Be able to understand how to declare them and how they can (or cannot) be used.

Be able to spot effectively final variables. Effectively final variables are local variables that are not modified after being assigned. Given a local variable, be able to determine if it is effectively final.

Recognize valid and invalid uses of static imports. Static imports import static members. They are written as import static, not static import. Make sure they are importing static methods or variables rather than class names.

Apply autoboxing and unboxing. The process of automatically converting from a primitive value to a wrapper class is called autoboxing, while the reciprocal process is called unboxing. Watch for a NullPointerException when performing unboxing.

State the output of code involving methods. Identify when to call static rather than instance methods based on whether the class name or object comes before the method. Recognize that instance methods can call static methods and that static methods need an instance of the object in order to call an instance method.

Recognize the correct overloaded method. Exact matches are used first, followed by wider primitives, followed by autoboxing, followed by varargs. Assigning new values to method parameters does not change the caller, but calling methods on them does.

## Chapter 5: Class Design
### Class Modifiers
modifier `final` means the class may not be extended. 
```java
public final class Rhinoceros extends Mammal { }
 
public class Clara extends Rhinoceros { } // DOES NOT COMPILE
```

### Calling Overloaded Constructors with this()
When `this()` is used with parentheses, Java calls another constructor on the same instance of the class.<br>
Calling `this()` has one special rule you need to know. If you choose to call it, the this() call must be the first statement in the constructor.
```java
public Hamster(int weight) {
   System.out.println("chew");
   // Set weight and default color
   this(weight, "brown");     // DOES NOT COMPILE
}
```
Java does not allow cyclic constructor calls.
```java
public class Gopher {
   public Gopher(int dugHoles) {
      this(5);  // DOES NOT COMPILE
   }
}
```
### Constructors
the first line of every constructor is a call to either this() or super()<br>
Java compiler automatically inserts a call to the no-argument constructor super() if you do not explicitly call this() or super() as the first line of a constructor.

### Final methods
final methods cannot be overridden
```java
public class Bird {
   public final boolean hasFeathers() {
      return true;
   }
   public final static void flyAway() {}
}
 
public class Penguin extends Bird {
   public final boolean hasFeathers() {   // DOES NOT COMPILE
      return false;
   }
   public final static void flyAway() {}  // DOES NOT COMPILE
}
```

### Hiding
variables and static methods cannot be overriden only hidden.

### Summary
This chapter took the basic class structures we've presented throughout the book and expanded them by introducing the notion of inheritance. Java classes follow a single-inheritance pattern in which every class has exactly one direct parent class, with all classes eventually inheriting from java.lang.Object.

Inheriting a class gives you access to all of the public and protected members of the class. It also gives you access to package members of the class if the classes are in the same package. All instance methods, constructors, and instance initializers have access to two special reference variables: this and super. Both this and super provide access to all inherited members, with only this providing access to all members in the current class declaration.

Constructors are special methods that use the class name and do not have a return type. They are used to instantiate new objects. Declaring constructors requires following a number of important rules. If no constructor is provided, the compiler will automatically insert a default no-argument constructor in the class. The first line of every constructor is a call to an overloaded constructor, this(), or a parent constructor, super(); otherwise, the compiler will insert a call to super() as the first line of the constructor. In some cases, such as if the parent class does not define a no-argument constructor, this can lead to compilation errors. Pay close attention on the exam to any class that defines a constructor with arguments and doesn't define a no-argument constructor.

Classes are initialized in a predetermined order: superclass initialization; static variables and static initializers in the order that they appear; instance variables and instance initializers in the order they appear; and finally, the constructor. All final instance variables must be assigned a value exactly once.

We reviewed overloaded, overridden, hidden, and redeclared methods and showed how they differ. A method is overloaded if it has the same name but a different signature as another accessible method. A method is overridden if it has the same signature as an inherited method, with access modifiers, exceptions, and a return type that are compatible. A static method is hidden if it has the same signature as an inherited static method. Finally, a method is redeclared if it has the same name and possibly the same signature as an uninherited method.

We then moved on to abstract classes, which are just like regular classes except that they cannot be instantiated and may contain abstract methods. An abstract class can extend a non-abstract class and vice versa. Abstract classes can be used to define a framework that other developers write subclasses against. An abstract method is one that does not include a body when it is declared. An abstract method can only be placed inside an abstract class or interface. Next, an abstract method can be overridden with another abstract declaration or a concrete implementation, provided the rules for overriding methods are followed. The first concrete class must implement all of the inherited abstract methods, whether they are inherited from an abstract class or an interface.

Finally, this chapter showed you how to create immutable objects in Java. Although there are a number of different techniques to do so, we included the most common one you should know for the exam. Immutable objects are extremely useful in practice, especially in multi-threaded applications, since they do not change.

### Exam Essentials
Be able to write code that extends other classes. A Java class that extends another class inherits all of its public and protected methods and variables. If the class is in the same package, it also inherits all package members of the class. Classes that are marked final cannot be extended. Finally, all classes in Java extend java.lang.Object either directly or from a superclass.

Be able to distinguish and use this, this(), super, and super(). To access a current or inherited member of a class, the this reference can be used. To access an inherited member, the super reference can be used. The super reference is often used to reduce ambiguity, such as when a class reuses the name of an inherited method or variable. The calls to this() and super() are used to access constructors in the same class and parent class, respectively.

Evaluate code involving constructors. The first line of every constructor is a call to another constructor within the class using this() or a call to a constructor of the parent class using the super() call. The compiler will insert a call to super() if no constructor call is declared. If the parent class doesn't contain a no-argument constructor, an explicit call to the parent constructor must be provided. Be able to recognize when the default constructor is provided. Remember that the order of initialization is to initialize all classes in the class hierarchy, starting with the superclass. Then the instances are initialized, again starting with the superclass. All final variables must be assigned a value exactly once by the time the constructor is finished.

Understand the rules for method overriding. Java allows methods to be overridden, or replaced, by a subclass if certain rules are followed: a method must have the same signature, be at least as accessible as the parent method, must not declare any new or broader exceptions, and must use covariant return types. Methods marked final may not be overridden or hidden.

Recognize the difference between method overriding and method overloading. Both method overloading and overriding involve creating a new method with the same name as an existing method. When the method signature is the same, it is referred to as method overriding and must follow a specific set of override rules to compile. When the method signature is different, with the method taking different inputs, it is referred to as method overloading, and none of the override rules are required. Method overriding is important to polymorphism because it replaces all calls to the method, even those made in a superclass.

Understand the rules for hiding methods and variables. When a static method is overridden in a subclass, it is referred to as method hiding. Likewise, variable hiding is when an inherited variable name is reused in a subclass. In both situations, the original method or variable still exists and is accessible depending on where it is accessed and the reference type used. For method hiding, the use of static in the method declaration must be the same between the parent and child class. Finally, variable and method hiding should generally be avoided since it leads to confusing and difficult-to-follow code.

Be able to write code that creates and extends abstract classes. In Java, classes and methods can be declared as abstract. An abstract class cannot be instantiated. An instance of an abstract class can be obtained only through a concrete subclass. Abstract classes can include any number of abstract and non-abstract methods, including zero. Abstract methods follow all the method override rules and may be defined only within abstract classes. The first concrete subclass of an abstract class must implement all the inherited methods. Abstract classes and methods may not be marked as final.

Create immutable objects. An immutable object is one that cannot be modified after it is declared. An immutable class is commonly implemented with a private constructor, no setter methods, and no ability to modify mutable objects contained within the class.

## Chapter 7: Beyond Classes
