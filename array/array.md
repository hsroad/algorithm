# JavaScript 算法之 Array

### 数组算法

look 代码吧。

```js
// 1三数字相加
var array = [-1, 0, 1, 2, -1, -4];
var arr = [];
// 思路
// 1 从小到大排序
// 2 如果三个数相加等于0 push进数组
// 3 如果大于0,
// 4 如果小于0,
// if (array.length < 3) {
//   return arr;
// }
array.sort((a, b) => a - b); // 排序
for (let index = 0; index < array.length; index++) {
  if (array[index] > 0) break;
  if (index > 0 && array[index] == array[index - 1]) continue;
  let L = index + 1,
    R = array.length - 1;
  while (L < R) {
    if (array[index] + array[L] + array[R] === 0) {
      arr.push(array[index], array[L], array[R]);
      while (L < R && array[L] == array[L + 1]) L++; // 去重
      while (L < R && array[R] == array[R - 1]) R--; // 去重
      L++;
      R--;
    } else if (array[index] + array[L] + array[R] > 0) {
      R--;
    } else if (array[index] + array[L] + array[R] < 0) {
      L++;
    }
  }
}
console.log(arr);
```
