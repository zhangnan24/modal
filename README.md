# modal

# 说明
这是一个手撸的*.vue组件，代码灵感源于我冠宇兄的极简主义，不是通用性的，但可以自己改样式。符合ESLint-airbnb标准。

# 使用方法
在父组件中传入visible属性直接控制modal显隐，接受自定义方法hide隐藏modal
示例:
```父组件
    <modal :visible="modalShow" @hide="modalShow = $event">
      <div>这是插槽内容</div>
    </modal>
```
# 项目解析
- 为什么不取名为dialog? --避免冲突，dialog是一个原生HTML5元素，尽管现在支持度不佳
- 为什么style的样式要包裹在.modal下？ --为modal组件的样式创建命名空间，避免与父组件样式的冲突
- @click.stop是什么操作？ --阻止事件冒泡
- dialog自身没有数据的？ --既然要完全由父组件来控制子组件的显隐，当然只需要依托唯一布尔值即可

# 注意事项
- 父组件中不应有html元素的class名为modal,否则会引起样式冲突
- 传入的title不是必须的，但visible是必须的，否则会报错
- 插槽的内容置于modal的body部分
