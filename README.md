# zhyz-cloudrender-v4

For information on how to use zhyz-cloudrender-v4, please see [documentation](http://47.93.101.157:9885/doc/CloudApi/Api-131.html).
For source files and issues, please visit the [repo](https://github.com/hzkLucky/zhyz-cloudrender-v4).

## Including zhyz-cloudrender-v4

Below are some of the most common ways to include zhyz-cloudrender-v4.

### Browser

#### Script tag
```js
<script type="text/JavaScript" src="http://47.93.101.157:8000/public/paas-skd/cloudRender.js"></script>
```

###

```html
<!DOCTYPE html>
<html lang="">
  <head>
    <meta charset="utf-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width,initial-scale=1.0" />
    <title>原生</title>
  </head>

  <body>
    <div id="player">
      <video></video>
    </div>
  </body>
  <script
    type="text/JavaScript"
    src="http://47.93.101.157:8000/public/paas-skd/cloudRender.js"
  ></script>
  <script type="module">
    window.onload = function() {
        var appli_id = "xxxx"; // 云渲染节点中的某个容器的ID
        var myhostname = "xxx.xxx.x.xx"; // 云渲染节点的流媒体地址
        var paasUrl = "http://xxxx:xxx"; // paas服务对应地址
        var username = 'zhangsan';
        var password = 'zhangsan_password';
        var protooPort = 'xxxx';  // 云渲染节点的流媒体端口
        // 初始化云渲染实例
        var Dandelion = new CloudRender(paasUrl, username, password);
         Dandelion.RtAPI("joinRoom", {
           ele: document.querySelector("#player"),
           myhostname,
           appliId,
           protooPort
         });
           /**
            *   以下方法非必须调用
            */

         // 异步解决方案 事件监听处理器函数, 接收所有从云渲染返回的数据
        Dandelion.RtAPI('RegisterCloudResponse', payload  => {
          switch(payload.type) {
            case 'getAllCloud_agents':
              // do something
              break;
             }
             case 'get_Allapp':
              // do something
              break;
             }
        });

       };
  </script>
</html>
```

#### Webpack / Browserify / Babel

There are several ways to use [Webpack](https://webpack.js.org/), [Browserify](http://browserify.org/) or [Babel](https://babeljs.io/). For more information on using these tools, please refer to the corresponding project's documentation. In the script, including zhyz-cloudrender-v4 will usually look like this:


To include zhyz-cloudrender-v4 in [Node](https://nodejs.org/), first install with npm.

```sh
npm install zhyz-cloudrender-v4
```

###

```js
<template>
  <div id="player">
    <video></video>
  </div>
</template>
<script>
import cloud from "zhyz-cloudrender-web/cloudRender.umd";
import { onMounted } from "vue";
export default {
  name: "",
  setup() {
    let appli_id = "xxxx"; // 云渲染节点中的某个容器的ID
    let myhostname = "xxx.xxx.x.xx"; // 云渲染节点的流媒体地址
    let paasUrl = "http://xxxx:xxx"; // paas服务对应地址
    let username = 'zhangsan';
    let password = 'zhangsan_password';
    let protooPort = 'xxxx';  // 云渲染节点的流媒体端口
    // 初始化云渲染实例
    let Dandelion = new cloud(paasUrl,username,password);
    onMounted(() => {
      //   // 在页面上显示场景
      Dandelion.RtAPI("joinRoom", {
        ele: document.querySelector("#player"), //指定的挂载三维场景的页面元素
        myhostname,
        appli_id,
        protooPort 
      });
       
         /**
          *   以下方法非必须调用
          */

       // 异步解决方案 事件监听处理器函数, 接收所有从云渲染返回的数据
      Dandelion.RtAPI('RegisterCloudResponse', payload  => {
        switch(payload.type) {
          case 'getAllCloud_agents':
            // do something
            break;
           }
           case 'get_Allapp':
            // do something
            break;
           }
      });
      // 注册场景报错时点击退出的事件函数
       Dandelion.RtAPI('registerLogoutFn', () => {
        // do something
      });
    return {};
  },
};
</script>

```