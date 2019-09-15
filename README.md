# CHEngineer
A single page framework developed with JavaScript
# 特点：
## 使用以下HTML代码即可引入：
<pre><code>&lt;link rel="stylesheet" href="chEngineer.css"&gt;
&lt;script src="chEngineer.js"&gt;&lt;/script&gt;</pre></code>

## 引入两个文件就可以快速创建一个单页面网站。

# 功能：

## 返回键拦截功能：
### onBack事件可以拦截返回键

## 生命周期：
### 使用onLoad作为应用逻辑开始。
### 使用onBack作为返回键是否有效的判断。

## 组件
### iscroll-x 横向弹性滚动组件
&lt;iscroll-x&gt;&lt;/iscroll-x&gt;
### iscroll-y 纵向弹性滚动组件
&lt;iscroll-y&gt;&lt;/iscroll-y&gt;
### .ch-ripple 涟漪效果组件
&lt;view class="ch-ripple"&gt;&lt;/view&gt;

## 数据绑定
### 自带数据绑定，只需app.data.abc="xxx";修改变量，无需使用document.getElementById("").innerHTML="XXX"来修改。
#### bindtap 点击事件绑定：
<pre><code>
  &lt;view bindtap="click_event"&gt;点我&lt;/view&gt;&lt;!--view标签等效于div标签--&gt;
  &lt;script&gt;
    app({
      click_event:function(){
        console.log("点击成功！");
      }
    })
  &lt;/script&gt;
</code></pre>
#### catchtap 防止冒泡的点击事件绑定：
<pre><code>
&lt;view bindtap="click2" style="width:100px;height:300px;background-color:orange;"&gt;
  &lt;view catchtap="click_event" style="width:50px;height:100px;background-color:green;"&gt;点我&lt;/view&gt;&lt;!--view标签等效于div标签--&gt;
  &lt;script&gt;
    app({
      click_event:function(){
        console.log("防止冒泡点击成功！");
      },click2:function(){
        console.log("点我成功！");
      }
    })
  &lt;/script&gt;
</code></pre>


#### bindlongtap 长按事件绑定：
<pre><code>
  &lt;view bindlongtap="click_event"&gt;点我&lt;/view&gt;&lt;!--view标签等效于div标签--&gt;
  &lt;script&gt;
    app({
      click_event:function(){
        console.log("长按成功！");
      }
    })
  &lt;/script&gt;
</code></pre>

#### ch-html HTML绑定
<pre><code>
  &lt;view ch-html="text1"&gt;&lt;/view&gt;
  &lt;script&gt;
    app({
      data:{
        text1:"&lt;span&gt;文本1&lt;/span&gt;"
      }
    })
  &lt;/script&gt;
</code></pre>
#### ch-text TEXT绑定（会编码标签）
<pre><code>
  &lt;view ch-text="text1"&gt;&lt;/view&gt;
  &lt;script&gt;
    app({
      data:{
        text1:"&lt;span&gt;文本1&lt;/span&gt;"
      }
    })
  &lt;/script&gt;
</code></pre>
#### ch-text TEXT绑定（会编码标签）
<pre><code>
  &lt;view ch-text="text1"&gt;&lt;/view&gt;
  &lt;script&gt;
    app({
      data:{
        text1:"&lt;span&gt;文本1&lt;/span&gt;"
      }
    })
  &lt;/script&gt;
</code></pre>
#### ch-val input绑定
<pre><code>
  &lt;input type="text" ch-val="text1"&gt;&lt;/view&gt;
  &lt;script&gt;
    app({
      data:{
        text1:"输入框1"
      }
    })
  &lt;/script&gt;
</code></pre>
#### ch-watch input数据获取
<pre><code>
  &lt;input type="text" ch-val="text1" ch-watch="text1"&gt;&lt;/view&gt;
  &lt;script&gt;
    app({
      data:{
        text1:"输入框1"//text1会随着input的内容改变而改变
      }
    })
  &lt;/script&gt;
</code></pre>



# HTML例子代码如下：
<pre><code>
&lt;view bindtap="click1" ch-html="button1"&gt;&lt;/view&gt;
</code></pre>
# JS例子如下：

<pre><code>
&lt;script&gt;
app({
  data:{
    button1:"点我"
  },
  click1:function(){
    api.toast("点击成功！");
    app.data.button1="再点我！";
  },
  onLoad:function(){
    //这里是框架启动时触发的事件
    api.toast("启动成功！");//使用自带api库弹出一个toast
    
  },onBack:function(){
    //这里是按返回键触发的事件
    //这里return false即可拦截返回键
  },
})

&lt;/script&gt;
</pre></code>


# API
## 框架自带许多常用的API函数库

<pre><code>
  api.toast("str");//弹出一个toast
  api.showLoading("Loading");//显示加载框
  api.hideLoading();//隐藏加载框
  api.import("jq",function(){//动态引入js或css文件，可以直接填入js或css文件链接，第一个参数支持数组，可同时引入多个文件
    api.toast("引入成功！");
  })
  api.request({//网络请求
    url:"/api",
    type:"POST",//POST或GET
    dataType:"json",//返回数据格式
    success:function(res){
      api.toast("请求返回成功！");
    },fail:function(){
      api.toast("请求失败！");
    },complete:function(){
      api.toast("完成！"); 
    }
  });
  api.alert("弹出成功！","警告框",["确定","取消"],function(index){
    api.toast("按了"+index.id);
  });
  或：
  api.alert({
    text:"弹出成功！",
    title:"警告框",
    button:["确定","取消"],
    click:function(index){
      api.toast("按了"+index.id);
    }
  );
  api.bind();//动态生成的组件需要绑定的事件，如bindtap
  

</pre></code>

