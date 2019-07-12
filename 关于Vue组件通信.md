无论是Vue还是React父子组件通信都可以使用ref

### 在Vue中使用ref
 
 首先我们会引入一个自定义组件 ，当然vue组件是需要注册的并使用
 
 ```js
  import AddDepartment from './AddDepartment.vue';
  
 components:{
         AddDepartment,
  },
 ```
 
 ```Vue
   <AddDepartment
           ref='AddDepartmentDrawer'
           :titlt="title"
           :show="show"
           :showdeptEmployee="showdeptEmployee"
           @onreloadData="reloadData"
    />
 ```
 很显然这是一个添加部门的弹窗组件 ref名称自定义 ，这里我定义为 AddDepartmentDrawer
 
 **这里讲一下ref代表什么：**
 > `ref`代表子组件相当于子组件的this 
 
 如何使用呢？
 
 父组件调用：`this.$refs.AddDepartmentDrawer` 这样就可以调用子组件的函数 改变子组件的data 里面的属性
 
 你可能会好奇ref下面写的都是什么？
 
 `:title="title`   父组件把弹窗标题传给子组件
 
 `:show="show" :showdeptEmployee="showdeptEmployee" `    父组件把方法传给子组件
 
 ` @onreloadData="reloadData"`  父组件的监听子组件函数 
 
  子组件接收：
 
 ```js
 props:{
  title:{
    type: String
  },
  show:{
    type: Function
  },
  showdeptEmployee:{
    type: Function
   }
 }
 
 
 // 子组件向父组件传递数据
 this.$emit('reloadData',data);   // 父组件的 reloadData 函数返回 data
 ```
 
 
 父组件接收：
 
 ```js
 reloadData: function(data){
  console.log(data)
 }
 ```
 
 关于弹窗开关个人建议 使用子组件函数控制 
 
 ```js
  close: function(isVisible){
        if( isVisible == true){
            this.treeMessage();  // 打开弹窗加载数据
        }else{  // 关闭弹窗记得初始化哟 最好写一个初始化函数
            this.title = '';   
            this.type = '';
            this.deptName = '';
            this.deptCode = '';
            this.departmentList = [];
        }
        let self = this;
        self.isShow = isVisible;
    },
 ```
 
父组件打开弹窗

```js
this.$refs.AddDepartmentDrawer.close(true);

// 当然也可以在父组件里面加载子组件数据 和在close 为true里面调用等效
this.$refs.AddDepartmentDrawer.treeMessage();
```

当然有时候父组件传给子组件的东西，子组件需要改变其取值这时候我们需要使用计算属性动态监听 并刷新父组件取值 computed(){}



 
 
 
 
 
