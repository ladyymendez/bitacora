# L - Liskov Substitution Principle
*Derived classes must be substitutable for their base classes.*

This means that the subclass should remain compatible with the behavior of the superclass. When overriding a method, extend the base behavior rather than replacing it with something else entirely.

### Example
```
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

const dog = new Dog('Doris', 4);
// console.log(dog.getName)

dog.setName = 'Pulgas';
// console.log(dog.getName)

console.log(dog.onomatopoeia())
```
Now, wherever in our code we were using Animal class object we must be able to replace it with the Dog or Duck without exploding our code.
