class Heap {
constructor(arr) {
this.arr = arr;
this.heapfy();
}
heapfy() {
let len = this.arr.length - 1;
for (let i = Math.floor((len - 1) / 2); i >= 0; i--) {
this.sink(this.arr, i);
}
}
sort() {
let resultArr = [];
for (let i = this.arr.length - 1; i > 0; i--) {
[this.arr[0], this.arr[i]] = [this.arr[i], this.arr[0]];
resultArr.push(this.arr.pop());
this.heapfy();
}
resultArr.push(this.arr.pop());
this.arr = resultArr;
}
sink(arr, i) {
//当左孩子节点的索引合规
while (2 _ i + 1 < arr.length) {
//初始将最大孩子指针指向左孩子
let j = 2 _ i + 1;
//如果当前节点的左孩子节点比右孩子更大，最大孩子指针指向右孩子
if (j + 1 < arr.length && arr[j] < arr[j + 1]) {
j++;
}
//当前节点的左右孩子<=当前节点时，停止下沉
if (arr[i] > arr[j]) break;
[arr[i], arr[j]] = [arr[j], arr[i]];
i = j;
}
}
insert(val) {
this.arr.push(val);
let j = this.arr.length - 1;
while (j > 0) {
let i = Math.floor((j - 1) / 2);
if (this.arr[i] >= this.arr[j]) {
break;
}
[this.arr[i], this.arr[j]] = [this.arr[j], this.arr[i]];
j = i;
}
}
delete() {
let len = this.arr.length;
[this.arr[0], this.arr[len - 1]] = [this.arr[len - 1], this.arr[0]];
this.arr.pop();
this.sink(this.arr, 0);
}
}
