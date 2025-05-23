function bigAdd(num1, num2) {
  if (typeof num1 != "string") return;
  if (typeof num2 != "string") return;
  let result = "";
  let carry = false;
  num1 = num1.split("");
  num2 = num2.split("");
  while (num1.length || num2.length || carry) {
    carry += ~~num1.pop() + ~~num2.pop();
    result = (carry % 10) + result;
    carry = carry > 9;
  }
  return result;
}