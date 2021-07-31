[toc]

# HTML5 新增的表单属性
## form属性

&emsp;&emsp;在 HTML5 之前，所有的表单控件都必须放在 form 元素内部，HTML5 为表单控件新增了 form 属性，用于定义该表单控件所属的表单，它的属性值是所属表单的 id ：

```html
<form action="#" id="addForm"></form>
<textarea name="desc" cols="30" rows="10" form="addForm"></textarea>
```

## formaction 属性

&emsp;&emsp;假设有这样一个场景：页面中有一个表单，该表单内包含了两个以上的提交按钮，但程序需要不同的按钮提交不同的 action，formaction 就是用来解决这样的问题：

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title></title>
    
</head>
<body>
    <form method="POST">
        用户名：<input type="text" name="name"><br>        
        密码：<input type="password" name="password"><br>        
        <input type="submit" value="注册" formaction="regist">
        <input type="submit" value="登录" formaction="login">
    </form>
</body>
</html>
```

## formxxx 属性

+ <font color=orange>**formenctype：**</font> 可以让按钮动态地改变表单的 enctype 属性
+ <font color=orange>**formmethod：**</font> 可以让按钮动态地设置表单以 POST 还是 GET 方式提交
+ <font color=orange>**formtarget：**</font> 通过该属性可以让按钮动态地改变表单的 target 属性

&emsp;&emsp;下面案例是 formmethod 的作用：

```html
<form method="POST" accept="#">
    用户名：<input type="text" name="name"><br>    
    密码：<input type="password" name="password"><br>    <input type="submit" value="GET提交" formmethod="GET">
    <input type="submit" value="POST提交" formmethod="POST">
</form>
```

&emsp;&emsp;下面是formenctype属性的作用的案例：

```html
<form method="POST" accept="#">
    用户名：<input type="text" name="name"><br>    
    密码：<input type="password" name="password"><br>    
    头像：<input type="file" name="pic">
    <input type="submit" value="普通注册" formenctype="application/x-www-form-urlencoded">
    <input type="submit" value="上传图片" formenctype="multipart/form-data">
</form>
```

&emsp;&emsp;下面是 formtarget 的作用的案例：

```html
<form method="POST" accept="#">
    用户名：<input type="text" name="name"><br>    
    密码：<input type="password" name="password"><br>    <input type="submit" value="本窗口提交" formtarget="_self">
    <input type="submit" value="新窗口提交" formtarget="_blank">
</form>
```

## autofocus属性

&emsp;&emsp;当某个表单控件设置该属性后，浏览器打开该页面时该组件就会自动获取焦点，整个页面最多只能有一个表单控件可设置该属性：

```html
<form method="POST" accept="#">
    用户名：<input type="text" name="name"><br>    
    密码：<input type="passPOSTword" name="password" autofocus>
</form>
```

## placeholder属性

&emsp;&emsp;当用户还没有在单行文本输入框、多行文本输入框中输入内容时，就会显示对用户的提示信息，一旦用户开始输入就会自动消失：

```html
<body>
    用户名：<input type="text" name="name" placeholder="请输入用户名"><br>    
    描述：<textarea name="desc" placeholder="请输入描述信息"></textarea>
</body>
```

## list属性

&emsp;&emsp;该属性的值应该是一个 datalist 组件的 id，datalist 元素相当于一个看不见的 select 元素，用于生成一个隐藏的下拉菜单，它所能包含的子元素和 select 完全相同。当双击了 list 属性的文本框时，该文本框将会显示 datalist 生成的下拉菜单：

```html
<body>
    <input type="text" list="books">
    <datalist id="books">
        <option value="Java">Java</option>
        <option value="C">C</option>
        <option value="C#">C#</option>
    </datalist>
</body>
```

## autocomplete属性

&emsp;&emsp;该属性用于设置表单是否支持自动完成功能，如果启动，浏览器将会根据用户上次提交的数据生成列表框供用户选择，或提示自动完成。主要支持一下两个属性：

+ <font color=orange>**on：**</font> 打开该属性，文本框下方会显示下拉菜单
+ <font color=orange>**off：**</font> 关闭该属性，文本框下方不会显示下拉菜单

```html
<body>
    <input type="text" autocomplete="on">
</body>
```

## label 的 control 属性

&emsp;&emsp;该属性用来在 JavaScript 脚本中访问该 label 元素所关联的表单元素：

```html
<body>
    <label id="nameLb">姓名：<input type="text" name="name"></label>
    <input type="button" value="重设" onclick="document.getElementById('nameLb').control.value='aaa'">
</body>
```

## 表单元素的 labels 属性

&emsp;&emsp;与 label 元素的 control 属性对应，该属性用于获取该表单元素所关联的多个 label 元素。普通表单的 labels 属性返回一个 NodeList 属性，该属性代表了该表单元素所关联的多个 label 属性：

```html
<body>
    <label>姓名：<input type="text" name="name" id="name"></label>
    <label for="name">请输入名字</label>
    <input type="button" value="第一个" onclick="alert(document.getElementById('name').labels[0].innerHTML)">
    <input type="button" value="第二个" onclick="alert(document.getElementById('name').labels[1].innerHTML)">
</body>
```

## 文本框的 selectionDirection 属性

&emsp;&emsp;为单行文本框和多行文本框添加了该属性，用于返回文本框内文字的选择方向：

+ <font color=orange>**forward：**</font> 正向选取文字
+ <font color=orange>**backward：**</font> 逆向选取文字

> <font color=red>**注意：**</font> 如果用户没有选择文字，则返回上一次的用户的选择方向。如果用户从来没有选择过文字，则返回forward。

```html
<body>
    <input type="text" id="name">
    <input type="button" value="获取" onclick="alert(document.getElementById('name').selectionDirection)">
</body>
```

## 复选框的 indeterminate 属性

&emsp;&emsp;如果该属性为 true，就表明该复选框状态暂时是"不确定"的，该复选框既不处于勾选状态，也不处于为勾选状态。不管是勾选还是取消勾选，indeterminate 属性都会变成 true：

```html
<body>
    <label id="hobLb">
        爱好：<input type="checkbox" name="hob">
    </label>
    <input type="button" value="设置" onclick="document.getElementById('hobLb').control.indeterminate=true;">
    <input type="button" value="获取" onclick="alert(document.getElementById('hobLb').control.indeterminate);">
</body>
```

# HTML5 新增的客户端校验

+ <font color=orange>**required：**</font> 指定该表单元素必须填写
+ <font color=orange>**pattern：**</font> 该属性指定该表单控件的值必须符合指定的正则表达式，属性值必须是一个合法的正则表达式
+ <font color=orange>**min、max、setp：**</font> 这3个属性只对数值类型、日期类型有效，控制该表单控件的值必须在min ~ max之间，并符合setp步长

```html
<body>
    <form action="#">
        <input type="text" name="name" required><br>        <input type="text" name="isbn" required pattern="\d{3}-\d-\d{3}-\d{5}"><br>        
        <input type="number" name="price" min="20" max="150" step="5">
        <input type="submit" value="提交">
    </form>
</body>
```

&emsp;&emsp;在提交表单的时候，如果不符合规则，会看到相应的提示信息。

## 使用 checkValidity 方法进行校验

&emsp;&emsp;如果开发者想使用其它方式提示错误或者其它的校验要求，可以借助 checkValidity() 方法进行校验：

+ 如果表单对象调用 checkValidity() 方法返回 true，则表明该表单内的所有表单元素的输入都有效。主要任意一个表单元素不能通过输入校验，表单对象的 checkValidity() 就会返回 false
+ 如果表单对象调用 checkValidity 方法返回 true，则表明该表单内的所有表单元素可以通过输入校验，否则返回 false

```html
<body>
    <form action="#">
        生日：<input type="date" id="birth" name="birth"><br>        
        邮件地址：<input type="email" id="email" name="email"><br>        
        <input type="submit" value="提交" onclick="return check();">
    </form>
    <script>
        var check = function(){
            return commonCheck("birth", "生日", "字段必须是有效的日期！") && commonCheck("email", "邮件地址", "字段必须是有效的邮件格式！");
        }

        var commonCheck = function(field, filedname, tip) {
            var targetEle = document.getElementById(field);

            if (targetEle.value.trim() == "") {
                alert(filedname + "字段必须填写");
                return false;
            } else if (!targetEle.checkValidity()) {
                alert(filedname + tip);
                return false;
            }

            return true;
        }
    </script>
</body>
```

&emsp;&emsp;除此之外，HTML5 为所有表单、表单控件都提供了一个 validity 属性，该属性的值是一个 ValidityState 对象，该对象代表表单、表单控件的输入校验状态，其中 ValidityState 的 valid 属性可以表示该表单、表单控件是否通过输入校验。

## 自定义错误提示

&emsp;&emsp;如果希望定制自己的错误提示信息，而不是显示默认的提示信息，可以借助于 HTML5 为表单控件新增的 setCustomValidity() 方法，该方法接受一个字符串参数，该字符串将会作为用户自定义的错误提示。

> <font color=red>**注意：**</font> 只要调用了某个表单控件的 setCustomValidity() 方法，就意味着该表单控件没有通过输入校验，因此只有当表单控件本身没有通过校验的时候才能调用该方法。

```html
<body>
    <form action="#">
        <input type="text" name="name" required id="name"><br >        
        <input type="submit" value="提交" onclick="check();">
    </form>
    <script>
        var check = function() {
            if (!document.getElementById("name").checkValidity()) {
                document.getElementById("name").setCustomValidity("图书名称必填");
            }
        }
    </script>
</body>
```

> <font color=red>**注意：**</font> 目前浏览器对于自定义错误提示的支持不是很好，当调用了该方法改变错误提示之后，即使浏览者在表单控件中输入的内容符合校验规则，浏览者也必须要把页面刷新一次。

## 关闭校验

&emsp;&emsp;在某些时候，如果希望暂时关闭 HTML5 对表单提供的输入校验，可以通过下面的方法来实现：

+ 为 form 元素增加 novalidate 属性
+ 为 type 为 submit 的 input 或者 button 元素设置 formnovalidate 属性