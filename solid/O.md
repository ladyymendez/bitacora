# O - Open-Closed Principle
*You should be able to extend a class’s behavior, without modifying it.*

==This principle is the foundation for building code that is maintainable and reusable.
Robert C. Martin==

A class follows the OCP if it fulfills these two criteria:

* Open for extension:
	* Open for extension means that we should be able to add new features or components to the application without breaking existing code.

* Closed for modification
	* Closed for modification means that we should not introduce breaking changes to existing functionality, because that would force you to refactor a lot of existing code.

-- [Eric Elliott](https://medium.com/@_ericelliott)

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
This way we do not need to modify the code whenever a new Animal is required to add. We can just create a class and extends it with the base class.

The info was taken from [medium](https://medium.com/@dhkelmendi/solid-principles-made-easy-67b1246bcdf)