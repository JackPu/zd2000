zd2000
======

zd2000 project css files and js files

-----------
1 css
----------
  [1.css 母版页样式文件](https://github.com/JackPu/zd2000/blob/master/CSS/master.css)
  [newui2.css 信息展示]((https://github.com/JackPu/zd2000/blob/master/CSS/newui.css))
  
2 js
-------------------------

3 基于前端的数据渲染模型
-------------------
所有与对象有关的数据模型全部在ashx文件中比如：<br/>
      
      public class cedianfenbu : IHttpHandler
      {
          public void ProcessRequest()
          {
              ....
          }
          
          public void read()
          {
          
          }
          
          public void delete()
          {
          
          }
          
        ....
      }

返回的json数据说明：
      
    json = {
       "status ":(0:失败,1:错误),
         "data"：[],
         "msg":(错误信息)
    }

前端请求规范：
<pre>
  <code>
      $.getJSON(ajaxUrl,function(result){
        if(result.status == 1){
        // ....
          if(result.data.length > 0){
              var html = template('cedian', data);
              // ...
          }else{
            //....  
          } 
                  
        }else{
            MasterPage.notion(result.msg,5);
        }
   });
  </code>
</pre>

前端模板(<a href="https://github.com/aui/artTemplate">art-template</a>)：
<pre>
  <code>
  <script id="xm" type="text/html">
    <ul>
        {{each list as value}}
            <li><a data-id= "{{value[0]}}" href="#" onclick="Xm.setCedian({{value[0]}},this)" >{{value[1]}}</a></li>
        {{/each}}
    </ul>
  </script>
  </code>
</pre>







