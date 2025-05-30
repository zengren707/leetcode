function maxSubArray(nums){
let maxSum,currSum=nums[0]
for(let i=1;i<nums.length;i++){
currSum=Math.max(currSum+num[i],num[i])
maxSum=Math.max(currSum,maxSum)
}
}
