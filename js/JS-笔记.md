
---

*一、我们想要调用创建好的函数，传统调用是定义好函数，然后再调用一次，如果需要页面加载就调用函数，可以用如下方式进行调用*
```javascript
!function() {/*代码块*/}()

+function() {/*代码块*/}()

-function() {/*代码块*/}()

~function() {/*代码块*/}()
```

*二、多种取整方法*
```javascript
1. Math.floor()  向下取整
2. parseInt()    取整
3. ~~()
```

Math.floor效率比parseInt高一些

*三、“&&”和“||”运算符用法*
```
a&&b  若a为true，则返回b，否则返回a
a||b  若a为true，则返回a，否则返回b

例如：
a>0&&hello()  若a大于0，则调用函数hello
```

*四、自己封装的方法如何回调*
```javascript
function hello(opt) {
	//如果有callback，那么执行回调，并把参数传入回调函数
	opt["callback"]&&opt["callback"](opt.msg);
}

//调用
hello({
   msg: "Hello World!",
   callback: function(data) {
       console.log(data);
   }
});
```

*五、函数自执行，不用手动调用函数*
```javascript
~~() //IIFE
()()

两种方式都可以

例如：
~~ function hi(){
	alert("你好！");
}()

或者

(function hi(){
	alert("你好！");
})()
```

*六、递归*

```javascript
var data = [{
    	name: "小峰",
    	age: 20
    },{
    	name: "小张",
    	age: 25
    },{
    	name: "小芳",
    	age: 18
    }]
    
//调用函数加载数据
loadData(data);

//递归加载数据
function loadData(data) {
	var tab = document.createElement("table");
	tab.style.width = "80%";
	tab.style.margin = "0px auto";
	var div = document.getElementById("main-data");
	var index = 0,len = data.length;	
	var arr = [];
	~function render(){
		var obj = data[index];
		var html = `
			<tr>
				<td>姓名</td>
				<td>${obj.name}</td>
				<td>年龄</td>
				<td>${obj.age}</td>
			</tr>
		`;
		arr.push(html);
		index++;
		index<len&&render();				
	}();
	tab.innerHTML = arr.join('');
	div.append(tab);
}

```

*七、获取数组最小值和最大值*

```javascript
var arr = [10,2,100,80,1000,200];
//获取数组最小值
arr.sort(function(a,b){return a-b});
console.log(arr);	

//最大值 return 1000
console.log(Math.max(...arr));

//最小值 return 2
console.log(Math.min(...arr));

//获取数组最小值的下标 return 0
console.log(arr.indexOf(Math.min(...arr)));
```

八、数组去重

```javascript
// ES6
function unique (arr) {
  const seen = new Map()
  return arr.filter((a) => !seen.has(a) && seen.set(a, 1))
}

//去重
function unique (arr) {
  return Array.from(new Set(arr))
}
```
九、判断元素是否存在与数组中

```javascript
//判断是否存在于数组中
  function contains(arr, value) {
      if(arr.indexOf&&typeof(arr.indexOf)=='function'){
          var index = arr.indexOf(value);
          if(index >= 0){
              return true;
          }
      }
      return false;
  }
```
十、获取对象的key


```javascript
var object = {id:1,name:"张三",sex:"男"}
Object.keys(object);
Object.values(object);
```
