# 快速排序
## 快排方法 1
### 步骤
1. 从数组中选择一个元素作为基数（取中间值）
2. 元素和基数做比较，比基数小的元素在左侧数组，反之比基数大的元素在右侧数组，基准值放在中间
3. 左侧和右侧的数组分别进行上述的1,2步操作
	
![快速排序](https://mysucceed.github.io/images/快排1.png)

``` javascript
function quickSort(arr){
	if(arr.length <= 1){
		return arr
	}
	var baseIndex = Math.floor(arr.length/2);  //基数的索引值 
	var baseElement = arr.splice(baseIndex,1);  //基数值，从原来数组剪切出来 
	var leftData = [], rightData = [];   //
	for (var i = 0; i < arr.length; i++) {
		var item = arr[i];
		if(item < baseElement){
			leftData.push(item)
		}else{
			rightData.push(item)
		}
	}
	return [].concat(quickSort(leftData), baseElement, quickSort(rightData))
}
```

## 快排方法 2
### 步骤
1. 选择数组最后一个元素作为基数base
2. 初始化指针i=-1
3. 循环数组，元素小于基数时，指针右移一位（i+1），元素和[i]元素互换位置
4. 循环结束后，基数与[i]元素互换位置
5. i作为数据的分界点，数组组成[0-i，i，i+1-end]
	
![快速排序](https://mysucceed.github.io/images/快排2.png)

``` javascript
function qucikMain(arr, start, end){
	if(end - start < 1){
		return
	}
	var point = doSort(arr, start, end)
	qucikMain(arr, start, (point<1? 0: point-1));
	qucikMain(arr, point+1, end);
}
/* 排序函数
 * @param {Array} arr
 * @param {Number} start 开始下标
 * @param {Number} end  结束下标
*/
function doSort(arr, start, end){
	var point = start-1, base = arr[end];  //指针 基数
	for(var j = start; j < end; j++){
		var item = arr[j];
		if(item <= base){
			point+=1
			exchange(arr, j, point)
		}
	}
	point+=1
	exchange(arr, end, point)
	return point;
}
/* 数组交换元素
 * @param {Array} arr  
 * @param {Number} indexA 下标A
 * @param {Number} indexB 下标B
*/
function exchange(arr, indexA, indexB){
	if(indexA == indexB){return};
	var value = arr[indexA];
	arr[indexA] = arr[indexB];
	arr[indexB] = value;
}
```
