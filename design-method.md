1. 单例模式 (Singleton)
确保一个类只有一个实例，并提供一个全局访问点。
class Singleton {
  constructor() {
    if (Singleton.instance) {
      return Singleton.instance;
    }
    Singleton.instance = this;
    this.data = "I am the singleton instance";
  }

  getData() {
    return this.data;
  }
}

const instance1 = new Singleton();
const instance2 = new Singleton();

console.log(instance1 === instance2); // true
console.log(instance1.getData()); // "I am the singleton instance"

2.工厂模式 (Factory Method)
提供一个创建对象的接口，让子类决定实例化哪个类。
class Car {
  drive() {
    console.log("Driving a car");
  }
}

class Truck {
  drive() {
    console.log("Driving a truck");
  }
}

class VehicleFactory {
  static createVehicle(type) {
    switch (type) {
      case "car":
        return new Car();
      case "truck":
        return new Truck();
      default:
        throw new Error("Unknown vehicle type");
    }
  }
}

const car = VehicleFactory.createVehicle("car");
car.drive(); // Driving a car

const truck = VehicleFactory.createVehicle("truck");
truck.drive(); // Driving a truck

 适配器模式 (Adapter)
 class OldSystem {
  oldMethod() {
    console.log("Old method executed");
  }
}

class NewSystem {
  newMethod() {
    console.log("New method executed");
  }
}

class Adapter {
  constructor(oldSystem) {
    this.oldSystem = oldSystem;
  }

  newMethod() {
    this.oldSystem.oldMethod();
  }
}

const oldSystem = new OldSystem();
const adapter = new Adapter(oldSystem);
adapter.newMethod(); // Old method executed

装饰器模式 (Decorator)
class Car {
  drive() {
    console.log("Driving a car");
  }
}

class CarDecorator {
  constructor(car) {
    this.car = car;
  }

  drive() {
    this.car.drive();
    this.additionalFeature();
  }

  additionalFeature() {
    console.log("Added new feature: Sunroof");
  }
}

const car = new Car();
const decoratedCar = new CarDecorator(car);
decoratedCar.drive(); // Driving a car \n Added new feature: Sunroof

外观模式 (Facade)
class CPU {
  freeze() {
    console.log("CPU freezing...");
  }

  jump() {
    console.log("CPU jumping...");
  }
}

class Memory {
  load() {
    console.log("Memory loading...");
  }
}

class HardDrive {
  read() {
    console.log("Hard drive reading...");
  }
}

class ComputerFacade {
  constructor(cpu, memory, hardDrive) {
    this.cpu = cpu;
    this.memory = memory;
    this.hardDrive = hardDrive;
  }

  start() {
    this.cpu.freeze();
    this.memory.load();
    this.hardDrive.read();
  }
}

const cpu = new CPU();
const memory = new Memory();
const hardDrive = new HardDrive();
const computer = new ComputerFacade(cpu, memory, hardDrive);
computer.start();
// Output:
// CPU freezing...
// Memory loading...
// Hard drive reading...

