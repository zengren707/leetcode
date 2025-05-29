class EventEmiter {
constructor() {
this.events = {};
}
on(eventName, fn) {
this.events[eventName] = this.events[eventName] || [];
this.events[eventName].push(fn);
}
emit(eventName, ...val) {
this.events[eventName].forEach((cb) => {
cb(...val);
});
}
off(eventName, fn) {
const index = this.events[eventName].indexOf(fn);
if (index !== -1) {
this.events[eventName].splice(index, 1);
}
}
}
