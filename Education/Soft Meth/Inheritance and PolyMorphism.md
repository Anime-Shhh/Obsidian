In inheritance, @override is a safety mechanism for your code, which is technically an annotation
for instance, lets say you have the parent class Animal as follows:
```java 
class Animal {
    public void makeSound() {
        System.out.println("Some generic noise");
    }
}
```

and a class dog:

```java
class Dog extends Animal {
    // TYPO: You wrote 'makesound' instead of 'makeSound'
    public void makesound() { 
        System.out.println("Bark!");
    }
}
```

Now there is an error here where you have a typo **makeSound** vs **makesound**
#### Case 1:
* No override: the code compiles perfectly but now Dog has 2 functions of makesound and makeSound

#### Case 2:
```java
class Dog extends Animal {
    @Override
    // TYPO: You wrote 'makesound' instead of 'makeSound'
    public void makesound() { 
        System.out.println("Bark!");
    }
}
```
* override: Now that you have @Override, this won't compile because it throws an error saying "you said you were going to override a method from Animal, but I dont see one here, makesound is not present in Animal"

## Abstract Class + Superclass

### 1. The Superclass (The Parent)

"Superclass" is a **relational term**. It describes the relationship between two classes. If Class B extends Class A, then **Class A is the superclass**.

- **Role:** It holds common code (fields and methods) that you want to share across multiple child classes (Subclasses).
- **State:** A superclass can be "Concrete" (you can create an object from it) or "Abstract" (you cannot).

**Think of it as:** The "General Category."
- If you have `Car` and `Truck`, the Superclass is `Vehicle`.

---

### 2. The Abstract Class (The "Incomplete" Template)

"Abstract" is a **modifier** (like `public` or `static`). When you add `abstract` to a class definition, you change the rules of how that class works.

- **Rule #1: No Instantiation.** You cannot use `new` on an abstract class. It is "incomplete."
    - `Shape s = new Shape();` // **ERROR**
- **Rule #2: Can have Abstract Methods.** These are methods with **no body** (no code inside `{}`).
    
    - It tells the compiler: _"I don't know how to do this yet, but any child class MUST figure it out."_
        

**Think of it as:** A partial blueprint or a form with blank spaces. You can't use the form until the blank spaces are filled in by the child class.

**Code example**:
```java
// ABSTRACT CLASS
// We cannot say "new Shape()", it's just a template.
abstract class Shape {
    String color;

    // 1. REGULAR METHOD (Inherited normally)
    // Every shape can use this exact code.
    public void setColor(String c) {
        this.color = c;
    }

    // 2. ABSTRACT METHOD (The "Blank Space")
    // We don't know the math yet, but we FORCE children to define it.
    public abstract double calculateArea(); 
}

// SUBCLASS (The Concrete Implementation)
class Circle extends Shape {
    double radius;

    // We MUST override this, or the code won't compile.
    @Override
    public double calculateArea() {
        return 3.14 * radius * radius;
    }
}
```

### What is an Interface?

Think of an Interface as a **Contract** or a **Job Description**.

While an Abstract Class says "You are a version of me" (Inheritance), an Interface says "You are capable of doing this action."

### Key Characteristics

1. **100% Abstract (mostly):** An interface is a list of method names with **no body code**. It says _what_ needs to happen, but not _how_.
2. **"Can-Do" vs. "Is-A":**
    
    - **Abstract Class (`Shape`):** Represents what an object _is_. A Dog _is an_ Animal.
	
    - **Interface (`Runnable`):** Represents what an object _can do_. A Dog _can_ Run. A Robot _can_ Run. They are totally different things, but they share that ability.
3. **Multiple Implementation:** This is the most important part. A class can only extend **one** superclass, but it can implement **many** interfaces.
**code example**
```java
// THE CONTRACT
// Any class that implements this MUST have a takeDamage method.
interface Damageable {
    void takeDamage(int amount);
}

// THE IMPLEMENTATION
// Dog "is an" Animal, but also "signs the contract" to be Damageable.
class Dog extends Animal implements Damageable {
    @Override
    public void takeDamage(int amount) {
        this.health -= amount; // Organic damage logic
    }
}

// Robot "is a" Machine, but also "signs the contract".
class Robot extends Machine implements Damageable {
    @Override
    public void takeDamage(int amount) {
        this.shieldLevel -= amount; // Mechanical damage logic
    }
}
```