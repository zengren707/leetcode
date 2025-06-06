题目：给定一个整数数组，找到其中和大于等于某个值的最短连续子数组。
最优解放：滑动窗口
function minSubArrayLen(nums, target) {
let left = 0,
right = 0;
let currSum = 0,
minLen = Infinity;
for (let num of nums) {
currSum += num;
right++;
while (currSum >= target) {
minLen = Math.min(minLen, right - left);
currSum -= nums[left];
left++;
}
}
return minLen == Infinity ? 0 : minLen;
}
