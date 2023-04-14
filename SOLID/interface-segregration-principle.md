# Interface Segregation Principle in JavaScript 🚀

The Interface Segregation Principle (ISP) is a fundamental principle of object-oriented programming that states that no client should be forced to depend on methods it does not use. In other words, it suggests that you should split a large interface into smaller and more specific interfaces that are tailored to the needs of the clients.

## Key Points 🔑

Here are some key points to remember about the Interface Segregation Principle:

- The ISP is one of the SOLID principles of object-oriented design.
- It aims to prevent clients from depending on methods they do not need or use.
- The principle states that it is better to have smaller and more specific interfaces than one large and general-purpose interface.
- By adhering to the ISP, you can reduce the coupling between classes and make your code more maintainable, extensible, and testable.

## Examples 🌟

Let's take a look at an example to understand the ISP in action.

```javascript
class Document {
  constructor(title, content) {
    this.title = title;
    this.content = content;
  }

  getTitle() {
    return this.title;
  }

  getContent() {
    return this.content;
  }

  save() {
    console.log(`${this.title} has been saved.`);
  }
}

class Printer {
  print(document) {
    console.log(`${document.getTitle()}: ${document.getContent()}`);
  }
}

class Scanner {
  scan() {
    console.log("Scanning...");
  }
}

class Fax {
  sendFax() {
    console.log("Sending fax...");
  }
}
```

In this example, we have a `Document` class that has a `getTitle()`, `getContent()`, and `save()` methods. We also have three different machines that interact with the document: `Printer`, `Scanner`, and `Fax`.

However, not all machines need all the methods of the `Document` class. For instance, the `Printer` only needs to print the document, and it does not need to save it. The `Scanner` only needs to scan the document, and it does not need to retrieve the title and content. The `Fax` only needs to send the document, and it does not need to retrieve the title and content or save it.

We can split the `Document` class into smaller and more specific interfaces that are tailored to the needs of the clients:

```javascript
class PrintableDocument {
  constructor(title, content) {
    this.title = title;
    this.content = content;
  }

  getTitle() {
    return this.title;
  }

  getContent() {
    return this.content;
  }
}

class SavableDocument {
  save() {
    console.log(`${this.title} has been saved.`);
  }
}

class Printer {
  print(document) {
    console.log(`${document.getTitle()}: ${document.getContent()}`);
  }
}

class Scanner {
  scan() {
    console.log("Scanning...");
  }
}

class Fax {
  sendFax() {
    console.log("Sending fax...");
  }
}
```

Now, each machine depends only on the methods it needs, and we have reduced the coupling between the `Document` class and the machines.

```javascript
const document = new PrintableDocument(
  "My Document",
  "Lorem ipsum dolor sit amet."
);

const printer = new Printer();
printer.print(document); // Output: My Document: Lorem ipsum dolor sit amet.

const scanner = new Scanner();
scanner.scan(); // Output: Scanning...

const fax = new Fax();
fax.sendFax(); // Output: Sending fax...
```

## Conclusion 🎉

The Interface Segregation Principle is an important principle of object-oriented programming that suggests that you should split a large interface into smaller and more specific interfaces that are tailored to the needs
