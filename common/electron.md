# electron
electron + vue + edge

## 创建electron-vue
1. 命令：vue init simulatedgreg/electron-vue electron_vue
1. 参考
  * https://simulatedgreg.gitbooks.io/electron-vue/content/cn/getting_started.html
  * https://newsn.net/say/electron-vue-demo-mac-builder.html

## 增加edge支持
1. 需要electron V1.6.2和electron-edge
1. package.json修改
```
  "build": {
      "electronVersion": "1.6.2",
      "asar": false,
  }
  "dependencies": {
      "electron-edge": "^6.5.5",
  }
  "devDependencies": {
      "electron": "1.6.2"
  }
```

## 运行
1. yarn // 初始化
1. yarn run dev // 调试运行
1. yarn run build // 生成安装包，在build目录

## vue代码示例
```
<template>
  <div class="demo-controls">
    <button class="demo-button" id="app-info" @click="getapp">View Demo</button>
    <span class="demo-response" id="got-app-info"></span>
  </div>
</template>

<script>
  const ipc = require('electron').ipcRenderer

  ipc.on('got-app-path', function (event, path) {
    const message = `This app is located at: ${path}`
    console.log(message)
    document.getElementById('got-app-info').innerHTML = message
  })

  export default {
    methods: {
      getapp () {
        console.log('getapp')
        ipc.send('get-app-path')
      }
    }
  }
</script>

<style scoped>

</style>
```
