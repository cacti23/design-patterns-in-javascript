# SOLID Principles 🏗️

## 1\. Single Responsibility Principle (SRP) 🎯

A class should have only one reason to change, meaning it should have a single responsibility or job.

Example:

```javascript
// Bad
class Employee {
    void calculateSalary() {}
    void saveEmployee() {}
}

// Good
class Employee {
    void calculateSalary() {}
}

class EmployeeRepository {
    void saveEmployee() {}
}
```

## 2\. Open/Closed Principle (OCP) 🔓

Software entities (classes, modules, functions, etc.) should be open for extension but closed for modification.

Example:

```javascript
// Bad
class Rectangle {
    int width, height;
}

class AreaCalculator {
    int calculateArea(Rectangle r) {
        return r.width * r.height;
    }
}

// Good
interface Shape {
    int calculateArea();
}

class Rectangle implements Shape {
    int width, height;

    int calculateArea() {
        return width * height;
    }
}

class Circle implements Shape {
    int radius;

    int calculateArea() {
        return (int) (Math.PI * radius * radius);
    }
}
```

## 3\. Liskov Substitution Principle (LSP) 👩‍👧

Derived classes must be substitutable for their base classes, meaning objects of the derived class should be able to replace objects of the base class without affecting the correctness of the program [baeldung.com](https://www.baeldung.com/solid-principles).

Example:

```javascript
// Bad
class Bird {
    void fly() {}
}

class Penguin extends Bird {}

// Good
class Bird {}

class FlyingBird extends Bird {
    void fly() {}
}

class Penguin extends Bird {}
```

## 4\. Interface Segregation Principle (ISP) 📐

Clients should not be forced to depend on interfaces they do not use. This principle deals with the separation of interfaces so that clients only need to know about the methods that are of interest to them.

Example:

```javascript
// Bad
interface Worker {
    void work();
    void eat();
}

// Good
interface Workable {
    void work();
}

interface Eatable {
    void eat();
}
```

## 5\. Dependency Inversion Principle (DIP) 🔄

High-level modules should not depend on low-level modules. Both should depend on abstractions. Abstractions should not depend on details. Details should depend on abstractions.

Example:

```javascript
// Bad
class LightBulb {}

class ElectricPowerSwitch {
    private LightBulb lightBulb;

    void press() {}
}

// Good
interface Switchable {
    void turnOn();
    void turnOff();
}

class LightBulb implements Switchable {
    void turnOn() {}
    void turnOff() {}
}

class ElectricPowerSwitch {
    private Switchable device;

    void press() {}
}
```
