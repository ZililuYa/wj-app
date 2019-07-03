<template>
  <div id="app">
    <Menu mode="horizontal" @on-select="select" theme="primary" active-name="1">
      <MenuItem name="1">
        <Icon type="logo-apple"/>
        测试
      </MenuItem>
      <MenuItem name="2">
        <Icon type="logo-android"/>
        测试
      </MenuItem>
      <MenuItem name="3">
        <Icon type="logo-apple"/>
        生产
      </MenuItem>
      <MenuItem name="4">
        <Icon type="logo-android"/>
        生产
      </MenuItem>
    </Menu>
    <div v-show="num === i.id" class="down" v-for="i in list">
      <div style="padding-bottom: 20px">长按扫描二维码</div>
      <div class="code" :id="'code'+i.id"></div>
      <div style="padding: 20px 0">or</div>
      <a target="_blank" :href="i.href">
        点击下载
      </a>
    </div>
  </div>
</template>

<script>
  import QRCode from 'qrcodejs2'

  export default {
    name: 'App',
    data() {
      return {
        num: '1',
        list: [{
          id: '1',
          href: 'http://app.crc.com.cn:8889/appstore/appdownload/download.html?appId=43A1297F439F4C75A468197E2DB6DD21'
        }, {
          id: '2',
          href: 'http://app.crc.com.cn:8889/appstore/appdownload/download.html?appId=3219A33DB8904DC0AC6B3FF57F8DAE7F'
        }, {
          id: '3',
          href: 'http://app.crc.com.cn:8889/appstore/appdownload/download.html?appId=43A1297F439F4C75A468197E2DB6DD21'
        }, {
          id: '4',
          href: 'http://app.crc.com.cn:8889/appstore/appdownload/download.html?appId=3219A33DB8904DC0AC6B3FF57F8DAE7F'
        }]
      }
    },
    mounted() {
      this.list.forEach(i => {
        this.qrCode(i.href, 'code' + i.id)
      })
    },
    methods: {
      select(name) {
        this.num = name;
        // const obj = this.list(name - 1);
        // setTimeout(() => this.qrCode(obj.url, 'code' + obj.id), 10)
      },
      qrCode(url, id) {
        let size = window.innerWidth * 80 / 100;
        if (size > 500)
          size = 500
        let qrCode = new QRCode(id, {
          width: size, //图像宽度
          height: size, //图像高度
          colorDark: "#000000", //前景色
          colorLight: "#ffffff", //背景色
          typeNumber: 4,
          correctLevel: QRCode.CorrectLevel.H //容错级别 容错级别有：（1）QRCode.CorrectLevel.L （2）QRCode.CorrectLevel.M （3）QRCode.CorrectLevel.Q （4）QRCode.CorrectLevel.H
        })
        qrCode.clear() //清除二维码
        qrCode.makeCode(url) //生成另一个新的二维码
      }
    }
  }
  // 71 140 233
</script>

<style>
  /*@import "~iview/dist/styles/iview.css";*/

  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
  }

  #app .ivu-menu-item-active {
    background-color: rgb(8, 100, 233);

  }

  #app .ivu-menu-item {
    width: 25%;
    text-align: center;
    padding: 0 10px;
  }

  #app .ivu-menu-item .ivu-icon {
    font-size: 20px;
    margin-bottom: 4px;
    margin-right: 3px !important;
  }

  #app .down {
    text-align: center;
    padding: 20px;
    font-size: 20px;
  }

  #app .code {
    text-align: center;
  }

  #app .code img {
    margin: 0 auto;
  }
</style>
