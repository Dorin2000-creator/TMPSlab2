# Exemplu de aplicație web cu design pattern-uri

Acest proiect demonstrează utilizarea a patru design pattern-uri (Singleton, Factory Method, Abstract Factory și Builder) în contextul unei aplicații web simple.

## Cuprins

- [Introducere](#introducere)
- [Tehnologii](#tehnologii)
- [Instalare și configurare](#instalare-și-configurare)
- [Explicatie](#explicatie)
- [Singleton](#singleton)
- [Factory Method](#factory-method)
- [Abstract Factory](#abstract-factory)
- [Builder](#builder)


## Introducere

Acest proiect este un exemplu simplu de aplicație web care ilustrează cum să utilizați patru design pattern-uri populare în dezvoltarea unei aplicații. Scopul proiectului este de a oferi o înțelegere de bază a modului în care aceste patternuri pot fi utilizate și cum pot îmbunătăți calitatea și structura codului.

## Tehnologii

- HTML5
- CSS
- JavaScript

## Instalare și configurare
1. Trebuie de instalat Live server
2. click ,,GO LIVE"

## Explicatie:
## Singleton:
Singleton este un design pattern care asigură că o clasă are o singură instanță și oferă un punct de acces global la aceasta. În acest exemplu, Singleton este creat folosind o funcție care returnează un obiect cu metoda getInstance().
```
const Singleton = (function () {
  let instance;

  function createInstance() {
    const object = new Object({ message: "Hello World!" });
    return object;
  }

  return {
    getInstance: function () {
      if (!instance) {
        instance = createInstance();
      }
      return instance;
    },
  };
})();

function showMessage() {
  const singleton = Singleton.getInstance();
  alert(singleton.message);
}
```
Când apăsați butonul "Afiseaza mesaj", funcția showMessage() este apelată, care apelează Singleton.getInstance() pentru a obține instanța Singleton și afișează mesajul său.

## Factory Method:
Factory Method este un design pattern care definește o interfață pentru crearea de obiecte într-o superclasă, dar permite subclaselor să decidă ce obiecte să creeze. În acest exemplu, clasa CarFactory are metoda createCar() care creează și returnează un obiect Car.
```
class Car {
  constructor(model, year, type) {
    this.model = model;
    this.year = year;
    this.type = type;
  }

  getInfo() {
    return `${this.model} ${this.year} ${this.type}`;
  }
}

class CarFactory {
  createCar(model, year, type) {
    return new Car(model, year, type);
  }
}

const carFactory = new CarFactory();
function createCar() {
  const myCar = carFactory.createCar("Toyota", "2022", "SUV");
  document.getElementById("car-info").innerHTML = myCar.getInfo();
}
```
Când apăsați butonul "Creează mașină", funcția createCar() este apelată, care folosește carFactory.createCar() pentru a crea un obiect Car și afișează informațiile sale.

## Abstract Factory:
Abstract Factory este un design pattern care oferă o interfață pentru crearea de familii de obiecte înrudite sau dependente fără a specifica clasele concrete. În acest exemplu, clasa CarAbstractFactory are o metodă createCar() care primește tipul, modelul și anul mașinii și creează obiecte FordCar sau BMWCar în funcție de tip.
```
class FordCar {
  constructor(model, year) {
    this.model = model;
    this.year = year;
  }

  getInfo() {
    return `${this.model} ${this.year} by Ford`;
  }
}

class BMWCar {
  constructor(model, year) {
    this.model = model;
    this.year = year;
  }

  getInfo() {
    return `${this.model} ${this.year} by BMW`;
  }
}

class CarAbstractFactory {
  createCar(type, model, year) {
    if (type === "Ford") {
      return new FordCar(model, year);
    } else if (type === "BMW") {
      return new BMWCar(model, year);
    } else {
      throw new Error("Invalid car type.");
    }
  }
}

const carAbstractFactory = new CarAbstractFactory();
function createCar() {
  const carType = document.getElementById("car-type").value;
  const myCar = carAbstractFactory.createCar(carType, "Mustang", "2022");
  document.getElementById("car-info").innerHTML = myCar.getInfo();
}
```
## Builder:
Builder este un design pattern care separă construcția unui obiect complex de reprezentarea sa, astfel încât același proces de construcție poate crea reprezentări diferite. În acest exemplu, clasa CarBuilder are metode pentru a seta modelul, anul și tipul mașinii și o metodă build() care returnează obiectul Car.
```
class CarBuilder {
  constructor() {
    this.car = new Car({});
  }

  setModel(model) {
    this.car.model = model;
    return this;
  }

  setYear(year) {
    this.car.year = year;
    return this;
  }

  setType(type) {
    this.car.type = type;
    return this;
  }

  build() {
    return this.car;
  }
}

function buildCar() {
  const model = document.getElementById("model-input").value;
  const year = document.getElementById("year-input").value;
  const type = document.getElementById("type-input").value;

  const myCar = new CarBuilder()
    .setModel(model)
    .setYear(year)
    .setType(type)
    .build();

  document.getElementById("car-info").innerHTML = myCar.getInfo();
}
```