# Vue路由传参的三种基本方式

现有如下场景，点击父组件的li元素跳转到子组件中，并携带参数，便于子组件获取数据。
父组件中：

```js
  <li v-for="article in articles" @click="getDescribe(article.id)">
```
methods：

## case1
```js
      getDescribe(id) {
      //直接调用$router.push 实现携带参数的跳转
        this.$router.push({
          path: `/describe/${id}`,
        })
```
case需要对应路由配置如下：
```js
    {
     path: '/describe/:id',
     name: 'Describe',
     component: Describe
   }
```
很显然，需要在path中添加/:id来对应 $router.push 中path携带的参数。在子组件中可以使用来获取传递的参数值。
```js
$route.params.id
```
