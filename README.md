# iframefileupload.js插件介绍

iframefileupload.js使用原生JS实现页面无刷新的情况下上传文件，同时脱离jquery和ajax，用最少的代码库依赖实现上传文件的同时也可以向后端传递json数据等。

### 使用说明

### html

``` html
<input type="file" name="file1" id="file1" />
<input type="file" name="file2" id="file2" />
<input type="button" value="提交" id="btn" />
```

### （1）script标签引入

``` javascript
<script type="text/javascript" src="iframefileupload.js"></script>
<script type="text/javascript">
	iframefileupload({
		type : 'post',
		url : './test.php',
		elementId : ['file1', 'file2'],
		data : {
			name : 'zym',
			blog : 'zymseo.com'
		},
		success : function (res) {
			console.log(JSON.parse(res));
		},
		error : function (res) {
			console.log(res);
		}
	});
</script>
```
### （2）require方法异步引入：
``` javascript
require(['iframefileupload'], function (iframefileupload) {
	iframefileupload({
		type : 'post',
		url : './test.php',
		elementId : ['file1', 'file2'],
		data : {
			name : 'zym',
			blog : 'zymseo.com'
		},
		success : function (res) {
			console.log(JSON.parse(res));
		},
		error : function (res) {
			console.log(res);
		}
	});
});
```
### （3）ES6语法引入：
``` javascript
import iframefileupload from './iframefileupload.js';
iframefileupload({
	type : 'post',
	url : './test.php',
	elementId : ['file1', 'file2'],
	data : {
		name : 'zym',
		blog : 'zymseo.com'
	},
	success : function (res) {
		console.log(JSON.parse(res));
	},
	error : function (res) {
		console.log(res);
	}
});
```
### 后端PHP：
``` php
$files = $_FILES;
$data = $_POST;

echo json_encode($files); // 向前端展示结果，判断是否接受成功，仅供测试
// echo json_encode($data); // 向前端展示结果，判断是否接受成功，仅供测试
```
### 插件遵循Apache开源许可协议
- 博客：[@赵一鸣](http://www.zymseo.com)
- QQ：1047832475