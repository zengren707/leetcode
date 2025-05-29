class Notifier {
  constructor() {
    this.observes = [];
  }
  add(observe) {
    this.observes.push(observe);
  }
  remove(observe) {
    this.observes = this.observes.filter((obs) => {
      return obs.id !== observe.id;
    });
  }
  notify() {
    this.observes.forEach((observe) => {
      observe.update();
    });
  }
}
class observed {
  constructor(id) {
    this.id = id;
  }
  update() {
    console.log(this.id);
  }
}
