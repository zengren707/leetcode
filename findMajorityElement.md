问题:给的一个数组，找出出现次数超过 n/2 的字符
最高效算法为：摩尔投票算法
function findMajorityElement(nums) {
let count = 0,
candidate = null;
for (let num of nums) {
if (count == 0) {
candidate = num;
}
if (candidate == num) {
count++;
} else {
count--;
}
}
count = 0;
for (let num of nums) {
if (num == candidate) {
count++;
}
}
if (count > nums.length / 2) {
return candidate;
} else {
return null;
}
}
