---
layout: answer

title: "Chapter TWO"
subtitle: "Utilizing Java Object-Oriented Approach - Part 2"
exam_objectives:
  - "Understand variable scopes, apply encapsulation, and create immutable objects. Use local variable type inference."
  - "Implement inheritance, including abstract and sealed types as well as record classes. Override methods, including that of the Object class. Implement polymorphism and differentiate between object type and reference type. Perform reference type casting, identify object types using the instanceof operator, and pattern matching with the instanceof operator and the switch construct."
  - "Create and use interfaces, identify functional interfaces, and utilize private, static, and default interface methods."
---

## Answers

**1. The correct answer is C.**

**Explanation:**

- **A)** The code compiles and outputs `3` followed by `1`.
  - This option is incorrect because, although the code prints `3` followed by `1` due to `x` being in scope, attempting to access `y` outside of its declaring block (the `if` block) will cause a compile-time error.

- **B)** The code compiles and outputs `3` followed by `1` and an undefined value for `y`.
  - This option is incorrect because Java does not allow access to local variables (`y` in this case) outside of their scope. The notion of an "undefined value for `y`" is not applicable here; the compiler will simply not compile the code.

- **C)** The code does not compile because `y` is accessed outside of its scope.
  - This is the correct option. Local variable `y` is declared inside the `if` block, and thus, it is only accessible within that block. Trying to access it outside of its scope, as done in the last `System.out.println(y);`, causes a compile-time error, specifically saying that `y` cannot be found.

- **D)** The code compiles but throws a runtime exception when trying to print `y`.
  - This option is incorrect because the issue with the code is at compile time, not runtime. The compiler will not allow the code to compile due to the scope violation of the local variable `y`, hence a runtime exception regarding `y` is out of the question.



**2. The correct answers are C and D.**

**Explanation:**

- **A)** `double x, double y;`
  - This option is incorrect because when declaring multiple variables of the same type in a single statement, you do not repeat the type before each variable. The correct syntax would be `double x, y;`.

- **B)** `int i = 0, String s = "hello";`
  - This option is incorrect for the same reason as A; you cannot declare variables of different types (`int` and `String` in this case) in a single statement. 

- **C)** `float f1 = 3.14, f2 = 6.28f;`
  - This is correct. You can declare multiple variables of the same type (`float` in this case) in a single statement, and it's also fine to initialize them with values in the same statement.

- **D)** `char a = 'A', b, c = 'C';`
  - This is correct. It's valid to declare multiple variables of the same type (`char` in this case), and initialize some, all, or none of them in the same statement.



**3. The correct answers are B and D.**

**Explanation:**

- **A)** `var` can be used to declare both local variables within methods and instance variables within classes.
  - This option is incorrect because `var` cannot be used to declare instance variables. It is specifically restricted to local variables within methods, constructors, or initializer blocks, as using `var` for fields would reduce the clarity of a class's public API.

- **B)** The use of `var` is restricted to local variables within methods, constructors, or initializer blocks.
  - This option is correct. `var` is intended for local variable type inference, significantly reducing the verbosity of Java code in scenarios where the compiler can easily determine the type of the local variable from its initializer. Its use is restricted to ensure clarity and prevent ambiguity in more complex constructs like class fields or method parameters.

- **C)** `var` can be used to declare method parameters.
  - This option is incorrect. The example clearly demonstrates that `var` cannot be used to declare method parameters. This limitation ensures that method signatures remain explicit in their type requirements, a critical aspect of a class's contract with its callers.

- **D)** `var` enhances readability by inferring types where it's clear from the context, but it's not allowed in method signatures to maintain clarity.
  - This option is correct. While `var` is primarily used to improve code readability by reducing the need for explicit type declarations where the type can be inferred from the context, it is not allowed in method signatures. This restriction ensures that the types of parameters in methods are always explicitly defined, aiding in the readability and maintainability of public APIs.

- **E)** `var` can be used to declare class (static) variables.
  - This option is incorrect. Similar to instance variables, `var` is not permissible for declaring class (`static`) variables. The rationale behind this restriction aligns with the goal of maintaining explicit type declarations in the class's structure, ensuring the class's design remains clear and unambiguous to both the compiler and developers.


**4. The correct answers are A and C.**

**Explanation:**

- **A)** Subclasses can directly access the `public` and `protected` members of their superclass, and package-private members when they are in the same package.
  - This option is correct. A subclass can use the `public` and `protected` members of its superclass directly. Package-private members work too, but only when the subclass is in the same package. `private` members stay off-limits, so the superclass must expose them through accessors.

- **B)** In Java, a class can extend multiple classes to achieve multiple inheritance.
  - This option is incorrect. Java does not support multiple inheritance for classes. A class in Java can only extend one other class, preventing complications like the diamond problem and the complexity associated with multiple inheritance.

- **C)** The `extends` keyword is used in Java to create a subclass that inherits from a superclass.
  - This option is correct. `extends` creates a subclass that inherits the fields and methods of a single superclass, giving an is-a relationship between them.

- **D)** A subclass in Java can directly access `private` members of its superclass.
  - This option is incorrect. A subclass cannot directly access `private` members of its superclass. Instead, it can access them through `public` or `protected` accessors provided by the superclass. This encapsulation principle ensures a controlled interaction with the superclass's state.


**5. The correct answers are A and C.**

**Explanation:**

- **A)** The code will compile and print `"Dog eats"` when executed.
  - This option is correct. The `Dog` class has provided an implementation for the `eat` method, which is abstract in the superclass `Animal`. Since `myAnimal` is of type `Animal` but instantiated as a `Dog`, it will call the overridden `eat` method in the `Dog` class, printing `"Dog eats"`.

- **B)** The `Animal` class can be instantiated.
  - This option is incorrect. The `Animal` class is abstract and cannot be instantiated. Attempting to create an instance of `Animal` directly (`new Animal()`) would result in a compilation error.

- **C)** Removing the `eat` method from the `Dog` class will cause a compilation error.
  - This option is correct. Since `Dog` extends the abstract class `Animal` and `Animal` has an abstract `eat` method, `Dog` must provide an implementation for `eat`. Failing to do so will prevent the code from compiling because `Dog` would also be considered abstract.

- **D)** The `Cat` class is necessary for the code to compile and run.
  - This option is incorrect. The `Cat` class is not referenced in the `main` method or anywhere else in the provided code snippet. Thus, it is unnecessary for the compilation and execution of the given code segment.


**6. The correct answers are B and C.**

**Explanation:**

- **A)** The `Person` class must override the `getSpeed` method.
  - This option is incorrect. The `Person` class is not required to override the `getSpeed` method because it is a default method in the `Runnable` interface. Default methods provide an implementation that can be used or overridden by implementing classes, but overriding is not mandatory.

- **B)** The `distance` variable in the `Walkable` interface is implicitly `public`, `static`, and `final`. 
  - This option is correct. In Java, all variables declared in an interface are implicitly `public`, `static`, and `final`. This means the `distance` variable in the `Walkable` interface is a constant and must be initialized at the point of declaration. It is accessible with the interface name, like `Walkable.distance`.

- **C)** A `Person` object can call the `getSpeed` method without any implementation in the `Person` class.
  - This option is correct. Since the `Runnable` interface provides a default implementation for the `getSpeed` method, a `Person` object can call the `getSpeed` method without any additional implementation in the `Person` class itself. The default implementation from the interface will be used.

- **D)** The `Runnable` interface causes a compilation error due to a naming conflict with `java.lang.Runnable`.
  - This option is incorrect because Java fully supports namespace resolution. The `Runnable` interface declared in the code snippet and `java.lang.Runnable` exist in different packages. There is no compilation error unless there's an attempt to import both in the same file without using a fully qualified name. Plus, this situation does not directly relate to the functionality or declaration of interfaces per the exam's focus.



**7. The correct answer is A.**

**Explanation:**

- **A)** The `Shape` class is correctly defined as a sealed class, allowing only specified classes to extend it.
  - This option is correct. The `Shape` class is declared as a sealed class, which means it can be extended only by the classes it explicitly permits through the `permits` clause. In this case, `Shape` permits `Circle` and `Square` to extend it, and both classes are correctly defined as permitted subclasses.

- **B)** The `Square` class does not correctly extend the `Shape` class because it is not marked as `final`. 
  - This option is incorrect. There's no requirement for classes extending a sealed class to be marked as `final` if they are non-sealed. The keyword `non-sealed` explicitly allows the `Square` class to extend the sealed `Shape` class without being final, indicating it can be further extended.

- **C)** The `Circle` class can be further extended by other classes. 
  - This option is incorrect. The `Circle` class is declared as `final`, which means it cannot be extended further and aligning with the constraints of extending a sealed class where the permitted subclass can be final, sealed, or non-sealed.

- **D)** The `area` method in the `Shape` class must provide a default implementation.
  - This option is incorrect. Abstract classes like `Shape` are not required to provide implementations for their abstract methods. The purpose of an abstract class is to define a template that its subclasses will follow, which includes implementing any abstract methods declared in the abstract class.


**8. The correct answer is D.**

**Explanation:**

- **A)** A reference to the `static` context of the class, allowing access to static methods and fields.
  - This option is incorrect. The `this` keyword does not refer to the static context of the class. It specifically refers to the current instance of the class. Static methods and fields belong to the class itself and are not part of any instance, so they cannot be accessed through `this`.

- **B)** A special variable that stores the return value of a method.
  - This option is incorrect. The `this` keyword does not store the return value of a method. It is used within an instance method or a constructor to refer to the current object the method or constructor is being invoked upon.

- **C)** An optional keyword that can always be omitted without affecting the functionality of the code.
  - This option is incorrect. While it is true that in some cases `this` can be omitted (for example, when accessing instance fields or methods without any naming conflict), its use is necessary for situations like constructor chaining (`this()` call) or when the method parameter names shadow the instance field names. In such scenarios, `this` clarifies to which variable the code is referring.

- **D)** A reference to the current object, whose instance variable is being called.
  - This option is correct. The `this` keyword in Java is used to refer to the current object—the object whose instance variable, method, or constructor is being called. You can see its usage in line 5 to call another constructor within the same class, in line 14 to differentiate between the method parameter `size` and the instance variable `size`, and in the `updateWidget` method to access the instance variable `size`. This usage demonstrates `this` as a way to refer explicitly to properties or methods of the current object.


**9. The correct answers are A and B.**

**Explanation:**

- **A)** The `super` keyword is used in the `Dog` constructor to call the superclass constructor.
  - This optional is correct. In the `Dog` constructor, `super(name);` is used to call the superclass (`Animal`) constructor with the `name` parameter. This is necessary to initialize the `name` field inherited from the `Animal` class in the `Dog` instance.

- **B)** The `eat` method in the `Dog` class uses `super` to invoke the superclass's `eat` method.
  - This optional is correct. The `eat` method in the `Dog` class calls `super.eat();` to invoke the `eat` method defined in the superclass (`Animal`). This allows the `Dog` class to extend the functionality of the `eat` method beyond what is defined in the superclass, demonstrating method overriding and use of `super` to access the overridden method.

- **C)** Removing the `super.eat();` call in the `Dog` class's `eat` method will prevent the `Dog` class from compiling.
  - This optional is incorrect. Removing the `super.eat();` call from the `Dog` class's `eat` method would not prevent the class from compiling. It would simply mean that the `Dog` class's `eat` method no longer calls the superclass's `eat` method, altering the program's behavior but not its compilability.

- **D)** The `super` keyword can be used to access `static` methods from the superclass.
  - This optional is incorrect. While `super` can indeed be used to access superclass methods, it's not specifically used or necessary for accessing static methods. Static methods belong to the class, not to instances, and should be invoked using the class name. `super` is used primarily for instance methods and constructors.



**10. The correct answer is C.**

**Explanation:**

- **A)** It compiles and prints `"Car driving at speed: 60"`.
  - This option is incorrect because the `drive` method in the `Car` class has a different parameter type (`long`) than the method in the `Vehicle` class (`int`). Due to the difference in parameter types, the `Car` class's `drive` method does not override but rather overloads the `Vehicle` class's `drive` method. Since the method is called on a `Vehicle` reference, the `Vehicle` class's `drive` method is invoked.

- **B)** It does not compile because the `drive` method cannot be called using a `Vehicle` reference. 
  - This option is incorrect because `Vehicle` defines the `drive` method correctly.

- **C)** It does not compile because the `drive` method in the `Car` class does not properly override the `drive` method in the `Vehicle` class.
  - This option is correct. The `@Override` annotation explicitly tells the compiler that the annotated method is intended to override a method from a superclass. However, the `drive` method in the `Car` class has a parameter of type `long`, while the `drive` method in the `Vehicle` class has a parameter of type `int`. Since the parameter types differ, the `Car` method does not override the `Vehicle` method, it's an overload. The compiler enforces the `@Override` contract strictly, so it produces an error such as: `method does not override or implement a method from a supertype`. As a result, the code fails to compile.
  
- **D)** It compiles and prints `"Vehicle driving at speed: 60"` because the `drive` method in the `Car` class is an overload, not an override.
  - This option is incorrect. It correctly identifies that the `Car` method is an overload rather than an override, but it incorrectly concludes that the code compiles. The `@Override` annotation prevents compilation because the annotated method is not actually overriding anything (see option C). If the `@Override` annotation were removed, then this option would describe the correct behavior. But with the annotation present, the code does not compile.


**11. The correct answer is E.**

**Explanation:**

- **A)** It compiles and prints `"Apple flavor"` followed by `"Red"`.
  - This option is incorrect because, while the `flavor` method will indeed print `"Apple flavor"` due to polymorphism (the `Apple` class overrides the `flavor` method of `Fruit`), the code will not compile if the `color()` method is called on a `Fruit` reference. This is because the `color` method is not part of the `Fruit` class's interface.

- **B)** It compiles and prints `"Fruit flavor"`.
  - This option is incorrect for a similar reason to A. The `flavor` method would print `"Apple flavor"` because of the overridden method in the `Apple` class, not `"Fruit flavor"`. However, the presence of the `color()` method call would still prevent compilation.

- **C)** It compiles but throws a runtime exception when attempting to call `color()`.
  - This option is incorrect because the issue occurs at compile time, not runtime. The Java compiler will not allow a method to be called on a reference type if that method is not defined in the reference type's class or its superclass hierarchy.

- **D)** It does not compile because `Apple` is not a valid type of `Fruit`.
  - This option is incorrect. `Apple` is a valid type of `Fruit` due to inheritance (`Apple extends Fruit`). This relationship allows an `Apple` object to be referenced by a `Fruit` variable.

- **E)** It does not compile because the `color` method is not defined in the `Fruit` class.
  - This option is correct. The `color` method is only defined in the `Apple` class and not in the `Fruit` class. Since the reference type of `myFruit` is `Fruit`, which does not have a `color` method, attempting to call `myFruit.color()` will result in a compilation error. This illustrates a key principle of polymorphism: the type of the reference (not the object) determines what methods can be called.


**12. The correct answers are B and D.**

**Explanation:**

- **A)** `((Dog)anotherAnimal).bark();`
  - This option is incorrect because it tries to cast `anotherAnimal` to `Dog` without checking its actual type first. Since `anotherAnimal` is an instance of `Animal` (not `Dog`), attempting this cast will compile, but it will cause a `ClassCastException` at runtime.

- **B)** `if (anotherAnimal instanceof Dog) ((Dog)anotherAnimal).bark();` 
  - This option is correct. It uses `instanceof` to check whether `anotherAnimal` is an instance of `Dog` before attempting the cast and calling `bark()`. In this case, since `anotherAnimal` is not an instance of `Dog`, the check prevents the cast and method call, avoiding a `ClassCastException`.

- **C)** `((Cat)animal).meow();`
  - This option is incorrect because it casts `animal` to `Cat` and attempts to call `meow()`. Since `animal` is actually an instance of `Dog`, this cast will compile but will result in a `ClassCastException` at runtime.

- **D)** `if (anotherAnimal instanceof Cat) ((Cat)anotherAnimal).meow();`
  - This option is correct. It checks if `anotherAnimal` is an instance of `Cat` before casting it to `Cat` and calling `meow()`.


**13. The correct answer is A.**

**Explanation:**

- **A)** It compiles and prints `"String with Java: Hello Java!"` followed by `"Integer greater than 10: 15"`.
  - This option is correct. The code snippet effectively demonstrates the use of pattern matching with the `instanceof` operator for both `String` and `Integer` types. The pattern matching feature checks if `input` is an instance of `String` or `Integer` and binds it to a variable (`s` for `String` and `i` for `Integer`) within the scope of the `if` and `else if` blocks. The logical operator `&&` is correctly used to further conditionally check properties of the variables (`s.contains("Java")` and `i > 10`). Thus, the method `process` prints output for inputs that are a `String` containing `"Java"` and an `Integer` greater than `10`, respectively.

- **B)** It compiles but only prints `"String with Java: Hello Java!"` because integers are not supported with pattern matching.
  - This option is incorrect because pattern matching works for any reference type, including `Integer`. The code does support integers and performs additional checks using pattern matching correctly.

- **C)** It does not compile because pattern matching in `instanceof` cannot be combined with logical operators like `&&`.
  - This option is incorrect. The code will compile and run as expected. Pattern matching in `instanceof` can indeed be combined with logical operators like `&&` for additional checks in the same conditional statement, as demonstrated in the code snippet.

- **D)** It compiles but prints all four lines due to incorrect use of pattern matching that always evaluates to `true`.
  - This option is incorrect because the use of pattern matching in the provided code is correct and does not always evaluate to `true`. The code correctly prints specific messages only for the inputs that match the given conditions.


**14. The correct answer is E.**

**Explanation:**

- **A)** Making the `setName`, `setPrice`, and `setStock` methods public would enhance the class's encapsulation.
  - This option is incorrect. Making the setters public would actually reduce the class's encapsulation by allowing external classes to modify the fields without restriction, potentially bypassing any validation logic contained within the setters.

- **B)** The class is not encapsulated because the `Product` class's fields are `private`. 
  - This option is incorrect. The use of `private` fields is a fundamental aspect of encapsulation. It prevents external classes from directly accessing and modifying the object's state, thus enforcing encapsulation.

- **C)** Encapsulation is weakened because the constructor allows direct setting of fields without validation.
  - This option is incorrect. The constructor does not weaken encapsulation; instead, it uses `private` setters that contain validation logic. This ensures that the object's state is correctly managed and validated upon creation.

- **D)** The `Product` class should have package-private getters to improve encapsulation.
  - This option is incorrect. Making getters package-private would limit the class's usability and does not inherently improve encapsulation. Public getters are necessary for external classes to view (but not modify) the object's state.

- **E)** The class is properly encapsulated by providing public getters for all fields and private setters with validation, ensuring control over the state of its objects.
  - This option is correct. The `Product` class demonstrates proper encapsulation practices by making its fields `private` and controlling access to them through `public` getters and `private` setters. The setters include validation logic, ensuring that only valid states are assigned to the fields. This design pattern ensures that the internal state of `Product` instances is both protected and correctly managed.


**15. The correct answers are A and E.**

**Explanation:**

- **A)** The `SavingsAccount` class cannot access the `balance` field directly due to its `private` access modifier in the `Account` class.
  - This option is correct. The design intentionally restricts direct access to the `balance` field to maintain encapsulation.

- **B)** The `getBalance` method should be `public` to allow `SavingsAccount` to access the account balance.
  - This option is incorrect. Making `getBalance` `public` would increase its visibility unnecessarily. `protected` is sufficient for subclass access, and this change is not required for `SavingsAccount` to function correctly, making this statement incorrect.

- **C)** The `deposit` method in the `Account` class should be marked as `final` to prevent overriding.
  - This option is incorrect. Marking `deposit` as `final` would prevent it from being overridden in subclasses, which is not a requirement or suggestion indicated by the given code. The decision to make a method `final` should be based on the specific design needs rather than a general principle of encapsulation.

- **D)** The `interestRate` field in the `SavingsAccount` class violates encapsulation principles by being `private`.
  - This option is incorrect. Using a `private` access modifier for `interestRate` in `SavingsAccount` is an example of proper encapsulation. It restricts access to the field from outside the class, which is aligned with encapsulation principles, making this option incorrect.

- **E)** The `Account` class correctly encapsulates the `balance` field, and `SavingsAccount` adheres to encapsulation by accessing `balance` through `getBalance` and `deposit`.
  - This option is correct. The `Account` class uses `private` access for the `balance` field to encapsulate its state, providing `protected` and package-private methods (`getBalance` and `deposit`) for controlled access and modification. `SavingsAccount` respects this encapsulation by using these methods to interact with the `balance` field, demonstrating a proper understanding and application of encapsulation principles. This design allows `SavingsAccount` to leverage functionality provided by `Account` without breaking encapsulation, which is a key objective in object-oriented design.


**16. The correct answer is C.**

**Explanation:**

- **A)** The `Contact` object is mutable because the `Address` class is not `final`.
  - This option is incorrect because the `Address` class does not directly impact the immutability of the `Contact` object. The `Contact` class ensures its immutability by not providing setters and by making deep copies of mutable objects, such as `Address`, both in the constructor and the getter.

- **B)** The `Contact` object is immutable, but only because it does not provide setters.
  - This option is incorrect. While it's true that it does not provide setters, this option does not fully capture the essence of immutability. Thus, it doesn't highlight the fact that all fields in `Contact` are `final` and the defensive copying strategy.

- **C)** The `Contact` object is immutable, and it properly prevents leakage of mutable internal state through defensive copying.
  - This is the correct option. The `Contact` class is immutable because it meets all criteria for immutability: the class is declared as `final` (preventing subclassing), all its fields are `private` and `final`, and it does not provide any setters. Also, it implements defensive copying for the mutable `Address` field to ensure that the internal state cannot be altered by external changes to `Address` objects passed in or returned. This prevents the leakage of its mutable internal state.

- **D)** The `Contact` object is mutable because the `Address` object can be changed via the `getAddress` method. 
  - This option is incorrect because the `Contact` object's immutability is maintained through defensive copying. The `getAddress` method returns a new `Address` instance each time it is called, ensuring that the original `Address` object's state cannot be altered from outside the `Contact` object.

- **E)** The `Contact` object is immutable but fails to prevent access to its mutable internal state.
  - This option is incorrect because the `Contact` object does implement a strategy to prevent access to its mutable internal state: it uses defensive copying for the `Address` object in both the constructor and the getter method, which ensures that the internal state remains unchanged from outside modifications.

