### Hash（散列）和符号
#### Hash  
Hash本质上就是数组，不过它的索引不局限于只使用数字。Hash的索引（或者叫“键”）几乎可以使用任何对象。  
Hash用花括号{}中包含键值对的形式表示，如果只有一个花括号没有健值对就是一个空Hash（{}）。
需注意的是⚠️  ：Hash中的花括号和块中的花括号不是一个概念，Hash虽然和数组相似，但是有一个重要的区别：Hash中的元素没有特定的顺序。
>>  user = { }        # { } 是一个空 Hash  
=> { }   
>>  user [ "first_name" ] = "Gong"        #键为"first_name" ，值为"Gong"   
=>  "Gong"   
>>  user["last_name"] = "Yangbo"        #键为"last_name"，值为"Yangbo"   
=>"Yangbo"   
>>  user["first_name"]                             #获取元素的方式和数组一致   
=>  "Gong"   
>>  user                                                        #Hash的字面量形式   
=>  { "first_name" => "Gong" , "last_name" = "Yangbo" }   
通过方括号的形式每次定义一个元素的方式不太敏捷，使用=>分隔的键值对这种字面量形式定义散列要简洁得多：   
>> user = { "first_name" => "Michael", "last_name" => "Hartl" }   
=> {"last_name"=>"Hartl", "first_name"=>"Michael"}   
上面的代码中用到了一个 Ruby 句法约定，在左花括号后面和右花括号前面加入了一个空格，不过控制台会忽略这些空格。

#### 符号（ Symbol）  
符号（Symbol）看起来有点像字符串，只不过没有包含在一对引号中，而是在前面加了一个冒号。例如， :name就是一个符号，在rails中经常用符号做Hash的键。  
_Symbol是Ruby中特有的数据类型，在其他语言中很少见。Symbol和字符串不同，并不是所有的字符都可以在Symbol中使用（只要以字母开头，其后都使用单词中常用的字符就没事）。_

用Symbol做键时，可以用下面的方式定义user  Hash:  
>>  user = {:name => "GongYangbo", :email => "gongyangbo@cc.com" }  
=>{ :name => "GongYangbo", :email => "gongyangbo@cc.com" }  
>>  user[:name]            #获取:name 键对应的值  
=>  "GongYangbo"

由于符号做键的情况太普遍了，Ruby 1.9 干脆为这种用法定义了一种新句法：  
>> h1 = { :name => "Michael Hartl", :email => "michael@example.com" }  
=> {:name=>"Michael Hartl", :email=>"michael@example.com"}  
>> h2 = { name: "Michael Hartl", email: "michael@example.com" }  
=> {:name=>"Michael Hartl", :email=>"michael@example.com"}  
>> h1 == h2  
=> true  
第二种句法把“符号 ⇒”变成了“键的名字:”形式：  
{name:"Michael Hartl",email:"michael@example.com"}  
新句法让人困惑的地方：因为:name本身是一种数据类型（符号），但name:却没有意义。不过在散列字面量中，:name =>和name:作用一样。因此，{ :name => "Michael Hartl" }和{ name: "Michael Hartl" }是等效的。如果要表示符号，只能使用:name（冒号在前面）。

##### 嵌套Hash  
散列中元素的值可以是任何对象，甚至是另一个散列(图-1)。
![Configure your Github Page](/images/blog/ruby/001.png)

Rails中会大量使用这种Hash中有Hash的形式。

与数组和值域一样，Hash也可以响应each方法(下面是一个名为flash的散列，它的键是两个判断条件，:success和:danger)：  
>> flash = { success: "It worked!", danger: "It failed." }   
=> {:success=>"It worked!", :danger=>"It failed."}   
>> flash.each do |key, value|   
>>    puts "Key #{key.inspect} has value #{value.inspect}"   
>> end   
Key :success has value "It worked!"   
Key :danger has value "It failed."   
要注意的是⚠️   数组的each方法后面的块只有一个变量，而散列的each方法后面的块接受两个变量，分别表示键和对应的值。所以散列的each方法每次遍历都会以一个键值对为单位进行。

inspect方法作用是返回被调用对象的字符串字面量表示形式：   
>> puts "It worked!", "It worked!".inspect   
It worked!   
"It worked!"   
因为使用inspect打印对象的方式经常使用，为此还有一个专门的快捷方式，p方法：  
>> p :name            # 等价于 'puts :name.inspect'   
:name

Ruby 类

Ruby中的一切都是对象，Ruby和其他面向对象的语言一样，使用类来组织方法，然后实例化类，创建对象。

在类上调用的方法，叫类方法（class method）。在类上调用new方法，得到的结果是这个类的对象，也叫做这个类的实例（instance）。在实例上调用的方法，例如length，叫实例方法（instance method）。

superclass方法找出继承关系。（String.superclass.superclass）

String类的继承关系
⚠️   Ruby允许向内置的类中添加方法

attr_accessor :name, :email

这行代码为用户的名字和电子邮件地址创建属性访问器存取方法（attribute accessor），也就是定义读值方法（getter）和设值方法（setter），用于读取和设定@name和@email实例变量。在 Rails 中，实例变量的意义在于，它们自动在视图中可用。而通常实例变量的作用是在 Ruby 类中不同的方法之间传递值。实例变量都以@符号开头，如果未定义，值为nil。

require './example_user'    # 加载 example_user 文件中代码的方式   
上面代码中的点号.，在 Unix 中指“当前目录”，'./example_user'告诉 Ruby 在当前目录中寻找这个文件。


