function findDuplicate(nums) {
let slow = nums[0];
let fast = nums[0];

while (true) {
slow = nums[slow];
fast = nums[nums[fast]];
if (slow === fast) break;
}

let finder = nums[0];
while (finder !== slow) {
finder = nums[finder];
slow = nums[slow];
}

return slow;
}
