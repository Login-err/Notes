##### html页面

```html
<script src="url" type="module"></script>
```

##### a.js 导入页面

```javascript
import {b1 as b,b2,b3} from './b.js';//b1 as b 将b1变量起别名
import b from './b.js'//默认导入的变量可随便

import * as obj  form './b.js';//当你不知道b.js里面的变量名时，给全部取个别名
```

##### b.js导出页面

```javascript
// 导出单个变量
export let b1 = "huanglian"
export let b2 = function(){
    console.log('导出函数')
}
export let b3 = {name:'huanglian'}

// 导出多个变量
const b4 = "huanglian"
const b5 = [1,2]
export {
	b4,b5
}

//默认导出  只能导出一次
export default ()=>{
    console.log('woshijiantouhanshu')
}
```

