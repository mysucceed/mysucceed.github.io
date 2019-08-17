# xss攻击
## 定义 
人们经常将 **跨站脚本攻击** （Cross Site Scripting）缩写为CSS，但这会与层叠样式表（Cascading Style Sheets，CSS）的缩写混淆。因此，有人将跨站脚本攻击缩写为XSS。其他的攻击方式还有CSRF，dos攻击等。
## 原理	
攻击者往Web页面里插入恶意html标签或者javascript代码，当用户浏览该页或者进行某些操作时，攻击者利用用户对原网站的信任，诱骗用户或浏览器执行一些不安全的操作或者向其它网站提交用户的私密信息。
## 攻击方式
### 反射型
发出请求时，XSS代码出现在URl中，作为输入提交到服务器端，服务器端解析后响应，XSS代码随响应内容一起传回给浏览器，最后浏览器解析执行XSS代码。这个过程像一次反射，故叫反射形XSS。
### 存储型
存储型XSS和反射型XSS的差别仅在于，提交的代码会存储在服务器（数据库，内存，文件系统等），下次请求目标页面时不用再提交XSS代码。
## 如何针对性防御
<<<<<<< HEAD
使用htmlparser.js，过滤掉一些元素，例如，script，style，link，iframe，frame等。	
也可以过滤掉元素的属性，例如error，onclick事件。
```javaScript
function parseHtmlStr(htmlString){
	var result = "";
	var curtTag = "";
	HTMLParser(htmlString, {
		start: function(tag, attrs, unary) {  //开始标签
			curtTag = tag;
			if(filterTag(tag)){return};
			result+="<"+tag;
			for(var i=0; i<attrs.length; i++){
				var item = attrs[i];
				result+=" "+item.name+"="+"\""+item.escaped+"\""; 
			}
			result+=(unary?"/":"")+">"
		},
		end: function(tag) {   //结束标签
			if(filterTag(tag)){return};
			result+="</"+tag+">"
		},
		chars: function(text) {  //文本
			if(filterTag(curtTag)){return};
			result+=text
		},
		comment: function(text) {  //注释
			result+="<!-- "+text+" -->"
		}
	});	
	return result
}
//过滤掉敏感标签
function filterTag(tag){
	if(tag=="script"||tag=="style"||tag=="link"||tag=="iframe"||tag=="frame"){
		return true
	}
	return false
}
```
=======

>>>>>>> 1d6674e7a6136d8b81376ae56633abe1b7557586
## 模拟xss攻击
1. 开发者从url中获取携带的参数值，解析为html标签插入页面。攻击者利用网站的漏洞，参数值携带恶意的js攻击代码，可以实现获取用户的cookie信息，篡改页面，注入iframe广告页面等。	
![xss](https://mysucceed.github.io/images/xss1.gif)
2. 评价功能页面，在留言框内输入js代码，提交到服务器。当其他用户查看这条留言的时候，就会触发带有恶意的js攻击代码。	
![xss](https://mysucceed.github.io/images/xss0.gif)
<<<<<<< HEAD
=======


>>>>>>> 1d6674e7a6136d8b81376ae56633abe1b7557586
