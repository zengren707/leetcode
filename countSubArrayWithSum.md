题目：给定一个整数数组，返回数组中所有和为特定值的连续子数组的个数。
function countSubArrayWithSum(nums, target) {
let sumMap = new Map();
sumMap.set(0, 1);
let count = 0;
let currSum = 0;
for (let num of nums) {
currSum += num;
if (sumMap.has(currSum - target)) {
count += sumMap.get(currSum - target);
}
if (sumMap.has(currSum)) {
sumMap.set(currSum, sumMap.get(currSum) + 1);
} else {
sumMap.set(currSum, 1);
}
}
return count;
}
