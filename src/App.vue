<template>
  <div id="app" v-bind:class="{previewMode:previewMode}">
    <Topbar class="topbar" v-on:preview="preview"></Topbar>
    <main>
      <Editor v-bind:resume="resume" class="editor"></Editor>
      <Preview v-bind:resume="resume" class="preview"></Preview>

    </main>
    <el-button id="exitPreview" v-on:click="exitPreview"> 退出预览</el-button>
  </div>
</template>

<script>
  import Topbar from './components/Topvar'
  import Editor from './components/Editor'
  import Preview from './components/Preview'
  import icons from './assets/sybo.js'

  export default {
    data() {

      return {
        previewMode: false,
        resume: {
          profile: {
            name: '韩文杰',
            city: '余姚',
            birthday: '1990年2月10日'
          },
          workHistory: [
            {company: '舜宇智能科技有限公司', content: 'java开发，2016年-2017年，spring+struts+ibatis+freemarker的mes项目代码开发,2018年至今是springboot项目的后端开发。参与项目前期的业务探讨，以及对新技术的应用。',ctime:'2016年9月——2019年4月'},
            {company: '方太营销有限公司', content: 'java开发，坐席CEM工作台系统的运维和开发',ctime:'2019年5月——至今'}
          ],
          studyHistory: [{school: '温州大学', duration: '2009年9月-2013年6月', degree: '本科',profession:'土木工程'}],
          projects: [{name: '工位平台的java部分开发', content: 'mes项目的周边技术开发，为了展示现场公司的生产情况，使用springboot+mybatis+mysql开发的工位辅助程序。使用开发工具是IDEA、NAVCAT、postman。工位数据传入到mes系统中，为了实现这个目的，使用消息队列activemq作为中转站,连接工位与mes系统的消息交互，上位机将工位信息转成json发送消息队列，java项目获取这个消息存入数据库，反之亦然。出现异常情况时发送企业微信给负责人，并且用websocket推送到mes系统的展示页面，用于实时展示。'},{
            name:'番茄闹钟小程序',content:'后端使用springboot+mybatis+fastjson+druid+mysql，后端工具用IDEA,前端用微信原生技术,工具是微信小程序工具。用json进行交互，按照番茄工作法的原理做的。'
          }],
          awards: [{name: "无"}],
          contacts: {
            qq: '911',
            wechat: '119',
            email: '400-882-3823',
            phone: '110'
          }
        }
      }
    },
    methods: {
      preview() {
        this.previewMode = true
      },
      exitPreview(){
        this.previewMode = false
      }
    },
    components: {
      Preview,
      Editor,
      Topbar
    }
  }
</script>

<style lang="scss">
  html, body, #app {
    height: 100%;
    overflow: auto;
  }

  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    height: 100vh;
    display: flex;
    flex-direction: column;
  }

  .topbar {
    position: relative;
    z-index: 1;
    box-shadow: 0 0 3px hsla(0, 0, 0, 0.5);
  }

  .icon {
    width: 1em;
    height: 1em;
    vertical-align: -0.15em;
    fill: currentColor;
    overflow: hidden;
  }

   main {

    display: flex;
    flex: 1;
    background: #DDD;

    > .editor {
      width: 40em;
      margin: 16px 8px 16px 16px;
      background: white;
      box-shadow: 0 0 3px hsla(0, 0, 0, 0.5);
      border-radius: 4px;
      overflow: hidden;
    }

    > .preview {
      flex: 1;
      margin: 16px 16px 16px 8px;
      background: white;
      box-shadow: 0 0 3px hsla(0, 0, 0, 0.5);
      border-radius: 4px;
      overflow: auto;

    }
  }

  .previewMode > #topbar {
    display: none;
  }

  .previewMode #editor {
    display: none;
  }

  .previewMode #preview {
    max-width: 800px;
    margin: 16px auto;
  }

  #exitPreview {
    display: none;
  }

  .previewMode #exitPreview {
    display: inline-block;
    position: fixed;
    right: 16px;
    bottom: 16px;
  }
</style>
