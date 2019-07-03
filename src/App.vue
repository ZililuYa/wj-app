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
                线上
            </MenuItem>
            <MenuItem name="4">
                <Icon type="logo-android"/>
                线上
            </MenuItem>
        </Menu>
        <div v-if="num === '1'" class="down">
            <a target="_blank"
               href="http://app.crc.com.cn:8889/appstore/appdownload/download.html?appId=43A1297F439F4C75A468197E2DB6DD21">
                点击下载
            </a>
        </div>
    </div>
</template>

<script>

    export default {
        name: 'App',
        data() {
            return {
                num: '1'
            }
        },
        mounted() {
        },
        methods: {
            select(name) {
                this.num = name;
                console.log(name)
            }
        }
    }
    // 71 140 233
</script>

<style>
    @import "~iview/dist/styles/iview.css";

    #app {
        font-family: 'Avenir', Helvetica, Arial, sans-serif;
    }

    #app .ivu-menu-item-active {
        background-color: rgb(8, 100, 233);

    }

    #app .ivu-menu-item {
        width: 25%;
        text-align: center;
    }

    #app .ivu-menu-item .ivu-icon {
        font-size: 20px;
        margin-bottom: 4px;
    }

    #app .down {
        text-align: center;
        padding: 20px;
    }
</style>
