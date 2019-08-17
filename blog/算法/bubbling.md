# 冒泡排序
## 步骤
1. 相邻两个元素比较，如果前边元素大于后边元素，互换位置 
2. 第一次循环，最大的元素会排在最后一个位置
3. 按照第一步的继续循环比较，最后一个位置元素不参与比较
 
![冒泡排序](https://mysucceed.github.io/images/冒泡排序.png)

``` javascript
	function bubblingSort(arr){
	    for(var i = arr.length-1; i >= 0; i--){
	    	sort(0,i)
	    }
	    
	    function sort(start,end){
	    	for(var i = start; i < end; i++){
		    	var previousElement = arr[i];   //前一个
		    	var nextElement = arr[i+1];     //后一个
		    	
		    	if(previousElement > nextElement){  //前>后  互换位置
		    		arr[i] = nextElement
		    		arr[i+1] = previousElement;
		    	}
		    }
	    }
	}
```
