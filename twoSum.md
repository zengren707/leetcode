function twoSum(nums, target) {
let map = new Map();
for (let i = 0; i < nums.length; i++) {
let cuts = target - nums[i];
if (map.has(cuts)) {
return [map.get(cuts), i];
}
map.set(nums[i], i);
}
}
