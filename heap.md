class Heap {
constructor(arr) {
this.arr = arr;
}
heapy() {
for (let i = Math.floor((this.arr.length - 2) / 2); i >= 0; i--) {
sink(this.arr, i);
}
}
sink(arr, i) {
//当左孩子节点的索引合规
while (2 _ i + 1 < arr.length) {
//初始将最大孩子指针指向左孩子
let j = i + 1;
//如果当前节点的左孩子节点比右孩子更大，最大孩子指针指向右孩子
if (2 _ j + 1 < arr.length && arr[j] < arr[j + 1]) {
j++;
}
//当前节点的左右孩子<=当前节点时，停止下沉
if (arr[i] > arr[j]) break;
[arr[i], arr[j]] = [arr[j], arr[i]];
i = j;
}
}
insert(val) {
let i=this.arr.l
}
}
