#JavaScript笔记

标签（空格分隔）： JavaScript

---

##1.1 js基本概念
js的优秀思想：函数、弱类型、动态对象、对象字面量
JavaScript兼容HTML代码的注释，所以<!–和–>也被视为单行注释。

    x = 1; <!-- x = 2;
    --> x = 3;

上面代码中，只有x = 1会执行，其他的部分都被注释掉了。

JavaScript七种数据类型：
> - number数值
> - string字符串
> - boolean布尔值
> - undefined
> - null
> - object对象
> - //Symbol

number JavaScript内部，所有数字都是以64位浮点数形式储存
NaN表示非正常结果，NaN不等于任何值
JavaScript内部自动将八进制、十六进制、二进制转为十进制

##1.2 js变量结构、json
switch结构不利于代码重用，往往可以用对象形式重写。

    function getItemPricing(customer, item) {
      switch(customer.type) {
        case 'VIP':
          return item.price * item.quantity * 0.50;
        case 'Preferred':
          return item.price * item.quantity * 0.75;
        case 'Regular':
        case default:
          return item.price * item.quantity;
      }
    }

上面代码根据不同用户，返回不同的价格。你可以发现，switch语句包含的三种情况，内部逻辑都是相同的，不同只是折扣率。这启发我们可以用对象属性，重写这个判断。

    var pricing = {
      'VIP': 0.50,
      'Preferred': 0.75,
      'Regular': 1.0
    };

    function getItemPricing(customer, item) {
      if (pricing[customer.type])
        return item.price * item.quantity * pricing[customer.type];
      else
        return item.price * item.quantity * pricing.Regular;
    }

如果price再多一些，对象属性写法的简洁优势就更明显了。

##1.3 js对象
1. JavaScript对象：一种无序的数据集合，由若干个“键值对”（key-value）构成。
如果键名不符合标识名的条件（比如第一个字符为数字，或者含有空格或运算符），也不是数字，则必须加上引号。

    var o = {
      '1p': "Hello World",
      'h w': "Hello World",
      'p+q': "Hello World"
    };

2. js数组

    var typea = {
      "first-name": "Green",
      "last-name": "Lucy"
    };
    var typeb = {
      first_name = "Green",
      last_name = "Lucy"
    };
    
取数组值，两种方法：
a. array["one"]
b. array.one // 优先考虑

3. 对象通过引用来传递，它们永远不会被复制

4. 对象的检索、更新

5. 原型
每个对象都链接到一个原型对象、并从中继承属性

原型连接：
a. 修改对象的属性值不影响原型
b. 检索对象的某个属性，属性不存在时从它的原型中寻找
c. 为原型添加属性，该属性会立即对所有原型所属对象可见

bool hasOwnProperty('') 检查是否独有属性

'delete objecta.one' 删除objecta的one属性暴露出原型的one属性
##1.4 js函数作用域
js的函数是根据词法来划分作用域的，而不是动态划分














