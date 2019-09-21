#### 触发BFC的条件

* 浮动元素：float除none以外的值
* 绝对定位元素：position（absolute，fixed）
* display为inline-block、table-cells、flex
* overflow除了visible以外的值（hidden、auto、scroll）

##### bfc可以把他的所有子元素包裹起来