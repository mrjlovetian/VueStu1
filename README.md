# VueStu1
Vue学习之路

### 知识点
vue:
	读音:	v-u-e
	view

	vue到底是什么?
		一个mvvm框架(库)、和angular类似
		比较容易上手、小巧
	mvc:
		mvp
		mvvm
		mv*
		mvx
	官网:http://cn.vuejs.org/	
	手册： http://cn.vuejs.org/api/

vue和angular区别?
	vue——简单、易学
		指令以 v-xxx
		一片html代码配合上json，在new出来vue实例
		个人维护项目

		适合: 移动端项目,小巧

		vue的发展势头很猛，github上start数量已经超越angular
	angular——上手难
		指令以 ng-xxx
		所有属性和方法都挂到$scope身上
		angular由google维护
		
		合适: pc端项目

	共同点: 不兼容低版本IE
-------------------------------------------
vue基本雏形:
	angular展示一条基本数据:
		var app=angular.module('app',[]);

		app.controller('xxx',function($scope){	//C
			$scope.msg='welcome'
		})

		html:
		div ng-controller="xxx"
			{{msg}}
	vue:
		html:
			<div id="box">
				{{msg}}
			</div>

			var c=new Vue({
				el:'#box',	//选择器  class tagName
				data:{
				    msg:'welcome vue'
				}
			});
常用指令:
	angular: 
		 ng-model   ng-controller
		 ng-repeat
		 ng-click
		 ng-show  

		$scope.show=function(){}
	指令: 扩展html标签功能,属性

	v-model	一般表单元素(input)	双向数据绑定

	循环:
		v-for="name in arr"
			{{$index}}

		v-for="name in json"
			{{$index}}	{{$key}}
	
		v-for="(k,v) in json"
	事件:
		v-on:click="函数"

		v-on:click/mouseout/mouseover/dblclick/mousedown.....

		new Vue({
			el:'#box',
			data:{ //数据
			    arr:['apple','banana','orange','pear'],
			    json:{a:'apple',b:'banana',c:'orange'}
			},
			methods:{
			    show:function(){	//方法
			        alert(1);
			    }
			}
		});
	显示隐藏:
		v-show=“true/false”
bootstrap+vue简易留言板(todolist):
	
	bootstrap: css框架	跟jqueryMobile一样
		只需要给标签 赋予class，角色
		依赖jquery

	确认删除？和确认删除全部么?
-----------------------------------------
事件:
	v-on:click/mouseover......
	
	简写的:
	@click=""		推荐

	事件对象:
		@click="show($event)"
	事件冒泡:
		阻止冒泡:  
			a). ev.cancelBubble=true;
			b). @click.stop	推荐
	默认行为(默认事件):
		阻止默认行为:
			a). ev.preventDefault();
			b). @contextmenu.prevent	推荐
	键盘:
		@keydown	$event	ev.keyCode
		@keyup

		常用键:
			回车
				a). @keyup.13
				b). @keyup.enter
			上、下、左、右
				@keyup/keydown.left
				@keyup/keydown.right
				@keyup/keydown.up
				@keyup/keydown.down
			.....
-----------------------------------------
属性:
	v-bind:src=""
		width/height/title....
	
	简写:
	:src=""	推荐

	<img src="{{url}}" alt="">	效果能出来，但是会报一个404错误
	<img v-bind:src="url" alt="">	效果可以出来，不会发404请求
-----------------------------------------
class和style:
	:class=""	v-bind:class=""
	:style=""	v-bind:style=""

	:class="[red]"	red是数据
	:class="[red,b,c,d]"
	
	:class="{red:a, blue:false}"

	:class="json"
		
		data:{
			json:{red:a, blue:false}
		}
	--------------------------
	style:
	:style="[c]"
	:style="[c,d]"
		注意:  复合样式，采用驼峰命名法
	:style="json"
-----------------------------------------
模板:
	{{msg}}		数据更新模板变化
	{{*msg}}	数据只绑定一次
	
	{{{msg}}}	HTML转意输出
-----------------------------------------
过滤器:-> 过滤模板数据
	系统提供一些过滤器:
	
	{{msg| filterA}}
	{{msg| filterA | filterB}}

	uppercase	eg:	{{'welcome'| uppercase}}
	lowercase
	capitalize

	currency	钱

	{{msg| filterA 参数}}

	....
-----------------------------------------
交互:
	$http	（ajax）

	如果vue想做交互

	引入: vue-resouce

	get:
		获取一个普通文本数据:
		this.$http.get('aa.txt').then(function(res){
		    alert(res.data);
		},function(res){
		    alert(res.status);
		});
		给服务发送数据:√
		this.$http.get('get.php',{
		    a:1,
		    b:2
		}).then(function(res){
		    alert(res.data);
		},function(res){
		    alert(res.status);
		});
	post:
		this.$http.post('post.php',{
		    a:1,
		    b:20
		},{
		    emulateJSON:true
		}).then(function(res){
		    alert(res.data);
		},function(res){
		    alert(res.status);
		});
	jsonp:
		https://sug.so.360.cn/suggest?callback=suggest_so&word=a

		https://sp0.baidu.com/5a1Fazu8AA54nxGko9WTAnF6hhy/su?wd=a&cb=jshow

		this.$http.jsonp('https://sp0.baidu.com/5a1Fazu8AA54nxGko9WTAnF6hhy/su',{
		    wd:'a'
		},{
		    jsonp:'cb'	//callback名字，默认名字就是"callback"
		}).then(function(res){
		    alert(res.data.s);
		},function(res){
		    alert(res.status);
		});
		
https://www.baidu.com/s?wd=s

	作业:
		1. 简易留言-> 确认删除? 确认删除全部
		2. 用vue get 写个例子	weibo


	
	
		
	
	

	
	

		

	
	
	
		

	
	
	

	



	

















