# S - Single Responsability Principle
*A class should have one, and only one, reason to change*

This principle states and recommends that a class should have only one responsibility. If a class contains multiple responsibilities then it becomes coupled. The coupling creates a chain of dependency which is never good for software.

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
  /*
  saveAnimal(Animal) {
    console.log('Saved!!', Animal.name)
  }
  */
}

class saveAnimalDB {
  saveAnimal(Animal) {
    console.log('Saved!!', Animal.name)
  }
}

const dog = new Animal('Doris', 4);
const saveDB = new saveAnimalDB();
saveDB.saveAnimal(dog);
```

We have to create another class that will handle the sole responsibility of database management.
This way our code becomes more cohesive and less coupled.