RegExp 构造函数

在 ES5 中，RegExp构造函数的参数有两种情况。

第一种情况是，参数是字符串，这时第二个参数表示正则表达式的修饰符（flag）。

var regex = new RegExp('xyz', 'i');
// 等价于
var regex = /xyz/i;
第二种情况是，参数是一个正则表示式，这时会返回一个原有正则表达式的拷贝。

var regex = new RegExp(/xyz/i);
// 等价于
var regex = /xyz/i;
但是，ES5 不允许此时使用第二个参数添加修饰符，否则会报错。

var regex = new RegExp(/xyz/, 'i');
// Uncaught TypeError: Cannot supply flags when constructing one RegExp from another
ES6 改变了这种行为。如果RegExp构造函数第一个参数是一个正则对象，那么可以使用第二个参数指定修饰符。而且，返回的正则表达式会忽略原有的正则表达式的修饰符，只使用新指定的修饰符。

new RegExp(/abc/ig, 'i').flags
// "i"
上面代码中，原有正则对象的修饰符是ig，它会被第二个参数i覆盖。
