#JavaScript笔记

标签（空格分隔）： JavaScript

---

##1.1
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

JavaScript内部，所有数字都是以64位浮点数形式储存
JavaScript内部自动将八进制、十六进制、二进制转为十进制

##1.2
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

##1.3
JavaScript对象：一种无序的数据集合，由若干个“键值对”（key-value）构成。
如果键名不符合标识名的条件（比如第一个字符为数字，或者含有空格或运算符），也不是数字，则必须加上引号。

    var o = {
      '1p': "Hello World",
      'h w': "Hello World",
      'p+q': "Hello World"
    };













