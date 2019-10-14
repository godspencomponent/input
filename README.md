## 组件：输入框
### 配置项
- 默认值（初始值）
配置默认值有两种方案：①直接属性面板输入；②脚本方法写入`this.setValue(val)`
- 占位符配置
- 输入框类型：文本、数值、密码、复选框
- 最大字符数（默认为-1，不限制）

### 获取输入值，可以使用`getValue`方法

#### demo 
组件1：输入框，id为"input",脚本设置初始值
```
<!-- input.js -->

// 设置初始值
this.setValue('我是初始值')

// 获取输入值
this.getValue()
```
组件2：提交按钮，id为"btn",点击按钮提交数据
```
<!-- btn.js -->
submit (id) {
    let val
    let $com = this.$parent.getComponent(id)
    if (!!$com) val = $com.$refs[id].getValue()
    console.log('输入值为', val)
}
```