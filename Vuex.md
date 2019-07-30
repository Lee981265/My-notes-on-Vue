### Vuex

## 定义

**vuex 是一个专门为vue.js应用程序开发的状态管理模式。**

  这个状态我们可以理解为在data中的属性，需要共享给其他组件使用的部分。
  也就是说，是我们需要共享的data，使用vuex进行统一集中式的管理。
  vuex中，有默认的五种基本的对象：

**vuex中，有默认的五种基本的对象：**
 
- state：存储状态（变量）
- getters：对数据获取之前的再次编译，可以理解为state的计算属性。我们在组件中使用 $sotre.getters.fun()
- mutations：修改状态，并且是同步的。在组件中使用$store.commit('',params)。这个和我们组件中的自定义事件类似。
- actions：异步操作。在组件中使用是$store.dispath('')
- modules：store的子模块，为了开发大型项目，方便状态管理而使用的。这里我们就不解释了，用起来和上面的一样
