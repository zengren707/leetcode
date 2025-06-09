题目描述
给定一个非负整数数组 nums，每个元素代表从该位置可以跳跃的最大长度。返回到达数组末尾所需的最小跳跃次数。

function jump(nums) {
let jumps = 0, currentEnd = 0, farthest = 0;

for (let i = 0; i < nums.length - 1; i++) {
farthest = Math.max(farthest, i + nums[i]);

    if (i === currentEnd) {
      jumps++;
      currentEnd = farthest;
    }

}

return jumps;
}
