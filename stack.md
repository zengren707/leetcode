class MyStack {
constructor() {
this.queue1 = [];
this.queue2 = [];
}
push(x) {
this.queue1.push(x);
}
pop() {
while (this.queue1.length > 1) {
this.queue2.push(this.queue1.shift());
}
let result = this.queue1.shift();
[this.queue1, this.queue2] = [this.queue2, this.queue1];
return result;
}
top() {
return this.queue1[this.queue1.length - 1];
}
empty() {
return this.queue1.length === 0;
}
}
