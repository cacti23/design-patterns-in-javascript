# Liskov Substitution Principle in JavaScript 🚀

The Liskov Substitution Principle (LSP) is a fundamental principle of object-oriented programming that aims to ensure that derived classes can be substituted for their base classes without affecting the correctness of the program.

In simpler terms, if we have a base class and a derived class, any code that works with the base class should also work with the derived class without any issues.

## Key Points 🔑

Here are some key points to remember about the Liskov Substitution Principle:

- The LSP was introduced by Barbara Liskov in 1987.
- It is one of the SOLID principles of object-oriented design.
- The principle states that any derived class should be able to substitute its base class without changing the behavior of the program.
- Violating the LSP can lead to unexpected errors and bugs in your code.
- The LSP promotes the use of interfaces and abstract classes to ensure that derived classes adhere to the same contract as the base class.

## Examples 🌟

Let's take a look at an example to understand the LSP in action.

```javascript
class Animal {
  constructor(name) {
    this.name = name;
  }

  eat() {
    console.log(`${this.name} is eating.`);
  }
}

class Cat extends Animal {
  constructor(name) {
    super(name);
  }

  meow() {
    console.log(`${this.name} is meowing.`);
  }
}

class Dog extends Animal {
  constructor(name) {
    super(name);
  }

  bark() {
    console.log(`${this.name} is barking.`);
  }
}
```

In this example, we have a base class `Animal` with two derived classes `Cat` and `Dog`. Both `Cat` and `Dog` inherit from `Animal`.

Now, let's say we have a function that works with `Animal` objects:

```javascript
function feedAnimal(animal) {
  animal.eat();
}
```

According to the LSP, we should be able to substitute `Animal` with `Cat` or `Dog` without changing the behavior of the `feedAnimal` function.

```javascript
const cat = new Cat("Fluffy");
feedAnimal(cat); // Output: Fluffy is eating.

const dog = new Dog("Max");
feedAnimal(dog); // Output: Max is eating.
```

Both `Cat` and `Dog` were able to be substituted for `Animal` without affecting the behavior of the `feedAnimal` function.

## Conclusion 🎉

The Liskov Substitution Principle is an important principle of object-oriented programming that ensures that derived classes can be substituted for their base classes without affecting the correctness of the program. By adhering to the LSP, we can write code that is more maintainable, extensible, and easy to reason about.
