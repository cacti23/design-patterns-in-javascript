# Dependency Inversion Principle in JavaScript 🚀

The Dependency Inversion Principle (DIP) is a fundamental principle of object-oriented programming that promotes loose coupling and high cohesion between classes.

In simpler terms, the DIP suggests that high-level modules should not depend on low-level modules, but instead both should depend on abstractions. Additionally, abstractions should not depend on details, but details should depend on abstractions.

## Key Points 🔑

Here are some key points to remember about the Dependency Inversion Principle:

- The DIP was introduced by Robert C. Martin in 1996.
- It is one of the SOLID principles of object-oriented design.
- The principle suggests that modules should depend on abstractions rather than concrete implementations.
- The principle promotes loose coupling and high cohesion between classes.
- The principle helps to reduce the impact of changes made to one class on other classes in the system.

## Examples 🌟

Let's take a look at an example to understand the Dependency Inversion Principle in action.
To illustrate the principle, let's take the example of the `Research` class, which tries to find children of a person named John. The `Research` class should not depend on the `Relationships` class, as this creates a direct dependency between a high-level module (`Research`) and a low-level module (`Relationships`). Instead, `Research` should depend on an abstraction (i.e., an interface) that the `Relationships` class implements.

Here's a version of the code that follows the DIP:

```javascript
let Relationship = Object.freeze({
  parent: 0,
  child: 1,
  sibling: 2,
});

class Person {
  constructor(name) {
    this.name = name;
  }
}

// Abstraction
class RelationshipBrowser {
  constructor() {
    if (this.constructor.name === "RelationshipBrowser") {
      throw new Error("RelationshipBrowser is abstract!");
    }
  }
  findAllChildrenOf(name) {}
}

// Low-level module
class Relationships extends RelationshipBrowser {
  constructor() {
    super();
    this.data = [];
  }

  addParentAndChild(parent, child) {
    this.data.push({
      from: parent,
      type: Relationship.parent,
      to: child,
    });

    this.data.push({
      from: child,
      type: Relationship.child,
      to: parent,
    });
  }

  findAllChildrenOf(name) {
    return this.data
      .filter((r) => r.from.name === name && r.type === Relationship.parent)
      .map((r) => r.to);
  }
}

// High-level module
class Research {
  constructor(browser) {
    for (let p of browser.findAllChildrenOf("John")) {
      console.log(`John has a child named ${p.name}`);
    }
  }
}

let parent = new Person("John");
let child1 = new Person("Chris");
let child2 = new Person("Matt");

let rels = new Relationships();

rels.addParentAndChild(parent, child1);
rels.addParentAndChild(parent, child2);

new Research(rels);
```

In the updated code, we have introduced an abstraction called `RelationshipBrowser`. The `Relationships` class implements this interface and `Research` now depends on this abstraction rather than directly on the `Relationships` class. This way, the `Research` class is decoupled from the low-level `Relationships` module and can work with any module that implements the `RelationshipBrowser` interface.

To summarize, DIP is a principle that helps to reduce dependencies between high-level and low-level modules by introducing an abstraction layer. By doing so, it promotes decoupling and makes the code more modular and extensible.

## Conclusion 🎉

The Dependency Inversion Principle is an important principle of object-oriented programming that promotes loose coupling and high cohesion between classes. By depending on abstractions rather than concrete implementations, we can reduce the impact of changes made to one class on other classes in the system.
