# O - Open-Closed Principle
*You should be able to extend a class’s behavior, without modifying it.*

==This principle is the foundation for building code that is maintainable and reusable.
Robert C. Martin==

A class follows the OCP if it fulfills these two criteria:

* Open for extension:
	* Means that we should be able to add new features or components to the application without breaking existing code.

* Closed for modification
	* Means that we should not introduce breaking changes to existing functionality, because that would force you to refactor a lot of existing code.

-- [Eric Elliott](https://medium.com/@_ericelliott)

A class is open if you can extend it, produce a subclass and do whatever you want with it—add new methods or fields, override base behavior, etc.

### Example
```
class Classification {
  printCaracteristics(Animal) {
    if(Animal.type=='Carnivores')
      return 'Print Caracteristics';
    else
      return 'Default Caracteristics';
  }
}

class Animal {
  constructor(name, age, type) {
    this.name = name;
    this.age = age;
    this.type = type;
    this.classification = new Classification();
  }
  get getName() {
    return this.name;
  }
  set setName(newName) {
    this.name = newName;
  }
  set setType(type) {
    this.type = type;
  };
  get getDescription(){
    return this.classification.printCaracteristics(this);
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

const dog = new Dog('Doris', 4, 'Carnivores');

console.log(dog.getDescription);
```
If we want create another type of classification in this way we do not need to modify the code whenever a new Animal is required. We can just modify classification without touching any of the Animal class’ code. 

The info was taken from [medium](https://medium.com/@dhkelmendi/solid-principles-made-easy-67b1246bcdf)