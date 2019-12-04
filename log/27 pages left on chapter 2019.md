【js】js数组置空的三种方式

方式1：
```
var arr = new Array(1,2,3);
 alert(arr);
 arr.splice(0, arr.length);
alert(arr);
```
方式2：
```
var arr = new Array(1,2,3);
 alert(arr);
arr.length = 0;
 alert(arr);
 ```
方式3：
```
var arr = new Array(1,2,3);
 alert(arr);
arr = [];
 alert(arr);
 ```
