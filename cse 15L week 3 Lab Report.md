# Minyan Shi's CSE 15L Week 1 Lab Report
---
# Part 1
---

---
# Part 2
---
## Array Method
1. The failure-inducing input and the symptom:
<img width="1110" alt="Week 3 Lab Screen Shots 1 2" src="https://user-images.githubusercontent.com/114315303/195725908-b2c7020d-b373-40c8-af55-88709927cef0.png">
The method reverseInPlace fail the test with {1,2,3,4} as input that we get {4,3,3,4} instead of the expected outcome {4,3,2,1}.<br />
<img width="1121" alt="Week 3 Lab Screen Shots 1 3" src="https://user-images.githubusercontent.com/114315303/195725973-b80e65c8-843f-4062-b66b-ff48fd5728af.png">
The method reverse fail the test with {1,2,3,4} as input that we get {0,0,0,0} instead of the expected outcome {4,3,2,1}.<br />

2. The bug:
<img width="956" alt="Week 3 Lab Screen Shots 1 0" src="https://user-images.githubusercontent.com/114315303/195727291-4b6d0d3f-c7e0-430d-a10a-6162614d96c9.png">
The method reverseInPlace fail the test because of the command `arr[i] = arr[arr.length-i-1]`. This command mirror the array by the middle of the array. It does reversed the entire array because those orginal values before the middle point of the array get changed without being stored. Using the input of the test `{1,2,3,4}` as an example, `1,2` has already been changed to `4,3` when we trying to pass their value to the later index. Value `1,2` does not get stored and can not be find later. Therefore, with this method we are unable to pass the orginal values before the midpoint to index after the mid point. \
\
The method reverse fail the test because of the command `arr[i] = newArray[arr.length-i-1]` and `return arr`. The command `arr[i] = newArray[arr.length-i-1]` let arr[i] equal to the defalt value 0 and `return arr` will return an array with value 0 at every index. After create `int[] newArry` with the same length as the input arguement `int[] arr` and the defalt value 0 for each element in the newArry, we should let `newArray[arr.length - i - 1] = arr[i]`, passing the value from the back of the `arry` to the `newArry`. After updating the value on each index of the `newArray` we should return `newArray` which is an array with the reversed value of the `arry`. \
<img width="1101" alt="Week 3 Lab Screen Shots 1 4" src="https://user-images.githubusercontent.com/114315303/195731356-f78ebbc8-3269-4fc7-86c8-5b5b22ccab6a.png">
(Then we may pass the test.)


## List Method
---
