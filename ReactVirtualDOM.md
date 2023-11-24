## 传统方法（无虚拟 DOM）：

1. **数据**
2. **模板**
3. 结合 **数据 + 模板** 生成真实 DOM 进行显示。
4. 当 **状态发生改变** 时，重复这个过程以生成新的真实 DOM 并替换原始的 DOM。

**缺陷：**
- 第一次生成一个完整的 DOM 片段。
- 第二次生成一个完整的 DOM 片段。
- 第二次的 DOM 替换第一次的 DOM，非常耗性能。

---

## 传统方法与手动 DOM 更新：

1. **数据**
2. **模板**
3. 结合 **数据 + 模板** 生成真实 DOM 进行显示。
4. 当 **状态发生改变** 时，重复这个过程以生成新的真实 DOM，但不替换原始的 DOM。
5. 比较新的 DOM（DocumentFragment）和原始的 DOM，找到差异。
6. 找出发生变化的输入框等元素。
7. 仅使用新的 DOM 中的输入元素，替换原始 DOM 中的相应元素。

**缺陷：**
- 性能的提升并不明显。

---

## 优化方法与虚拟 DOM：

1. **状态数据**
2. **JSX 模板**
3. 结合 **数据 + 模板**
   ```jsx
   <div id="abc"><span>你好，世界</span></div>
   ```
 生成**虚拟DOM** (**虚拟DOM**就是一个**JS对象**， 用它来描述真实DOM). 
  - 损耗了新能 但是比起利用JS去生成真实DOM，利用JS 去生成JS 对象 更有性能
  - JSX -> React.CreateElement -> 虚拟DOM (JS 对象) -> 真实的DOM.

  ```jsx
    return <div>item</div>
    return React.CreateElement('div',{}, 'item');
  ```
 - JSX 语法可以让我们用更方便的写法写出来
    
4.  利用新的**虚拟DOM**生成真实 DOM 进行显示。
5. state 发生改变 
6. 数据 + 模板 结合， 生成新的虚拟的DOM
```javascript
['div', {id: 'abc', ['span'], {} , 'bye bye'}]
```
7. 比较原始虚拟DOM 和 新的虚拟DOM 的区别， 找到区别是span中内容 
8. 直接操作 DOM, 改span中的内容

### 好处
1. 提高新能
2. 跨端应用可以实现 React Native (虽然Desktop 和 手机App 没有 DOM的概念 但是依然能用 JS 对象 进行渲染)
---


1. 什么时候会发生比对
 - 当state 或者是 props （父组件的state） 发生改变

2. 如果三有个setState改变数据时的时间差较短，react会合拼成一个setState 然后做比对
   
![image](https://github.com/DhaiDev/ReactNote/assets/88443783/0f8fd4f3-04a8-4be9-aeb0-167ccc7bd0b6)

3. Diff 算法
   对两个的旧和新的 虚拟DOM 利用 tree的方式 去 做同级比较


