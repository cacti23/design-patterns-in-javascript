📚 Builder Pattern

The Builder Pattern is a creational design pattern that lets you construct complex objects step by step. It allows you to produce different types and representations of an object using the same construction code. This pattern is particularly useful when dealing with objects that have a large number of optional or required properties. Instead of using a constructor with a long list of parameters, the Builder pattern helps you build the object incrementally, making the code more readable and maintainable.

🔑 Key Points

- Helps in constructing complex objects with multiple properties.
- Separates the construction process into several steps.
- Allows building different representations of a product using the same construction process.
- Can be used to construct Composite trees or other complex objects.

💻 Code Example

Here's an example of the Builder pattern in TypeScript:

```javascript
class Pizza {
  constructor(builder) {
    this.size = builder.size;
    this.cheese = builder.cheese;
    this.pepperoni = builder.pepperoni;
    this.bacon = builder.bacon;
  }
}

class PizzaBuilder {
  constructor(size) {
    this.size = size;
    this.cheese = false;
    this.pepperoni = false;
    this.bacon = false;
  }

  setCheese(value) {
    this.cheese = value;
    return this;
  }

  setPepperoni(value) {
    this.pepperoni = value;
    return this;
  }

  setBacon(value) {
    this.bacon = value;
    return this;
  }

  build() {
    return new Pizza(this);
  }
}

// Usage
const pizza = new PizzaBuilder(12)
  .setCheese(true)
  .setPepperoni(true)
  .setBacon(true)
  .build();
```

🎭 Practice Usage in Node.js

To use the Builder pattern in a Node.js application, you can simply create a separate module for the Builder class and import it where needed. Here's an example:

1.  Create a file `pizza.ts` with the Pizza and PizzaBuilder classes:

```javascript
// pizza.ts
export class Pizza {
  // ...
}

export class PizzaBuilder {
  // ...
}
```

1.  In your main file, import the PizzaBuilder class and use it to create a Pizza instance:

```javascript
// app.ts
import { PizzaBuilder } from "./pizza";

const pizza = new PizzaBuilder(12)
  .setCheese(true)
  .setPepperoni(true)
  .setBacon(true)
  .build();

console.log(pizza);
```

1.  Run your Node.js application:

```javascript
$ tsc app.ts pizza.ts
$ node app.js
```

Keep in mind that the Builder pattern might not be suitable for all cases. It can lead to bloated code and requires constructing two objects (the Builder instance and the actual product). However, it is particularly useful when dealing with complex objects that need to be created multiple times with different configurations.

📌 Conclusion

The Builder pattern is an effective way to simplify the construction of complex objects with numerous properties. It improves code readability and maintainability by allowing you to build objects step by step, using only the steps that are necessary. The pattern is especially useful when constructing objects with many optional or required properties, and it can be applied in various software development contexts.
