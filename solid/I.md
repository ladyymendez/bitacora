# I - Interface Segregation Principle
*Clients should not be forced to implement interfaces they do not use.*

In other words, it is better to have many smaller interfaces, than fewer, fatter interfaces.
Class inheritance lets a class have just one superclass, but it doesn’t limit the number of interfaces that the class can implement at the same time.

### Example
```
const canFly = {
    fly() {
        console.log(`${this.name} flew`);
    }
}

const canWalk = {
    walk() {
        console.log(`${this.name} walked`);
    }
}

class Animal {
  constructor(name, age) {
    this.name = name;
    this.age = age;
  }
  get getName() {
    return this.name;
  }
  set setName(newName) {
    this.name = newName;
  }
  onomatopoeia(){}
}

class Dog extends Animal {
  onomatopoeia(){
    super.onomatopoeia();
    return 'Woof!'
  }
}

class Duck extends Animal {
  onomatopoeia(){
    super.onomatopoeia();
    return 'Quack!'
  }
}

Object.assign(Dog.prototype,canWalk);
Object.assign(Duck.prototype,canWalk);
Object.assign(Duck.prototype,canFly);

const dog = new Dog('Doris', 4);
console.log(dog.getName)
dog.walk();

const duck = new Duck('Peter', 4);
duck.walk();
duck.fly();
```
This will make sure that the client is only implementing the methods that they should use
