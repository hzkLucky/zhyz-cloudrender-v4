
## Example Usage

```js
<template>
  <div id="player">
  <video></video>
  </div>
</template>
<script>
import cloud from "zhyz-cloudrender-v4/cloudRender.umd";
import { onMounted } from "vue";
export default {
  name: "",
  setup() {
    let appliId = "xxxx"; // 云渲染节点中的某个容器的ID
    let myhostname = "xxx.xxx.x.xx"; // 云渲染节点的流媒体地址
    let paasUrl = "http://xxxx:xxx"; // paas服务对应地址
    let protooPort = 'xxxx';  // 云渲染节点的流媒体端口(非必传参数默认8888)
    let username = 'zhangsan';
    let password = 'zhangsan_password';
	let isHttps = false; //非必填
    // 初始化云渲染实例
    let Dandelion = new cloud(paasUrl,username,password, isHttps);
    onMounted(() => {
       // 在页面上显示场景
      Dandelion.RtAPI("joinRoom", {
        ele: document.querySelector("#player"), //指定的挂载三维场景的页面元素
        myhostname,
		appliId,
		protooPort
      });
        
         /**
          *   api调用示例
          */
      Dandelion.RtAPI("getPoiList", {
        view: false, //true获取视图内，false获取视图外
      },res => {
        // res 为接口返回数据
      })
    return {};
  },
};
</script>

```
