# D - Dependency Inversion Principle
*Classes should depend on abstraction but not on concretion*

*== A. High level modules should not depend upon low level modules. Both should depend upon abstractions.
B. Abstractions should not depend upon details. Details should depend upon abstractions.
Robert C. Martin ==*

From a functional point of view, these containers and injection concepts can be solved with a simple higher order function, or hole-in-the-middle type pattern which are built right into the language.

### Example
```
class ManagmentDB {
    constructor(db) {
      this.db = db;
    }

    insertDB(data) {
      this.db.makeInsert(data);
    }

    updateDB(data) {
      this.db.update(data);
    }

}

class MongoDB {
  constructor(user) {
    this.user = user;
  }
  makeInsert(data) {
    console.log(`${this.user} inserted the following data ${data} into MongoDB`)
  }
}

class Mysql {
  constructor(user) {
    this.user = user;
  }
  makeInsert(data) {
    console.log(`${this.user} inserted the following data ${data} into Mysql`)
  }
}

const db = new ManagmentDB(new Mysql('User1'));
db.insertDB("DATA");

```
The dependency inversion principle often goes along with the open/closed principle: you can extend low-level classes to use with different business logic classes without breaking existing classes.