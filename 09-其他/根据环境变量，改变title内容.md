# vue cli 配置不同环境变量值

> 自己设置的变量，必须是`VUE_APP_`开头的，这是定死的

需求：项目开发过程中，对于同一个变量，在不同的环境测试下，需要取不同的值

```javascript

productNo = 'productNo1' 
productNo = 'productNo2' 
productNo = 'productNo3' 

```

环境变量和模式官方参考链接：[https://cli.vuejs.org/zh/guide/mode-and-env.html](https://cli.vuejs.org/zh/guide/mode-and-env.html)

在项目中使用
------

1.项目根目录下创建.env文件（ 用于所有环境）

```javascript
NODE_ENV=production 
VUE_APP_PRODUCT_NO=productNo3

```

2.项目根目录下创建.env.test文件（ 用于测试环境）

```javascript
NODE_ENV=production 
VUE_APP_PRODUCT_NO=productNo2

```

3.项目根目录下创建.env.development文件（ 用于开发环境,项目在本地运行的话，会默认走这个文件）

```javascript
NODE_ENV=production 
VUE_APP_PRODUCT_NO=productNo1

```

4.在项目的package.json配置相应的打包模式，在命令行的后面加上–mode test，表示对应的打包模式  
![](https://img-blog.csdnimg.cn/20201109094507842.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3d5dV9qZXJyeQ==,size_16,color_FFFFFF,t_70#pic_center)

5.尝试在main.js打印出来

```javascript
console.log(process.env.VUE_APP_PRODUCT_NO)  

```

PS:需要注意的事项
----------

1.三个环境都设置NODE_ENV=production，是为了webpack能打出正常的包  
2.–mode test 对应的是.env.test文件模式的内容，开发模式也试类似的  
3.自己设置的变量，必须是VUE\_APP\_开头的，这是定死的