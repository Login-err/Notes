```javascript
import AsyncValidator from 'async-validator';// 或者const Validator = require('async-validator');
const descriptor = {
    name: {type: 'string', require:true}
}
const validator = new AsyncValidator(descriptor);

validator.validate({name: 'demo'}, (errors ,fields) => {
    if (errors) {
        console.log(errors);
    }
    // success
})
```

#### 规则形式（descriptor形式）

所有的形式（descriptor）通过一系列的内部判断转化之后，其规则基本可以统一为：

```javascript
{
    name: [{type: 'string',validator: function () {}, field: 'name'}]
}
```

<p>必须字段包含type，validator两个字段。如果没有validator函数时，验证会自动跳过</p>
1. 规则是方法

    ```javascript
    const descriptor = {
        number: function custom () {} // 提供只一个validate方法
        // 也可以是
        number: [function custom () {}
        // 或者
    	number: {validator: function custom () {}}
    }
    const validator = new Validator(descriptor);
    ```

    <p>转化为：</p>
```javascript
    {
        number: [type: 'string', validator: function custom () {}, field: 'number']
    }
    ```
    
如果规则是方法时，在回调async-validator会注入五个参数rule，value，callback，source，options
    
* rule：当前验证使用的规则
    * value：字段的值
    * callback：验证完成时的回调函数，参数是null或者[]或者[new Error（'not valid'）]
    * source：验证时的所有数据
    * options：额外的验证选项，可以包含message来覆盖默认的错误信息
    
2. 规则是一个对象

    ```javascript
    const descriptor = {
        user: {required: true}
    }
    const validator = new Validator(descriptor);
    ```

    <p>验证时会被转化为：</p>
    
    ```javascript
    {
        // validators.required 是内部已定义好的检验函数
        user: [{type: 'string', require: true, validator: validators.required, field: 'user'}]
    }
    ```
    
3. 规则是个数组

    ```javascript
    const descriptor = {
        email: [{required: true},{type: 'email'}] // user字段必填
    }
    const validator = new Validator(descriptor);
    ```

4. <p>规则包含嵌套</p>

    ```javascript
    const descriptor = {
        address: {
            type: 'object',
            required: true,
            field: {
                province: {
                    type: 'string',
                    required: true,
                    min: 4
                },
                city: {
                    type: 'string',
                    message: 'custom message',
                    min: 5
                }
            }
        }
    }
    const vallidator = new Validator(descriptor);
    ```

    

#### 要被检验的值的格式：键值对 {a:xxx,b:xxx}

#### 验证的规则格式： 

```javascript
{
    a: [
        {验证规则1}，
        {验证规则2}
    ],
    b: [
        {验证规则3}
    ]
}
```

