<template>
  <div id="preview">
    <h1>姓名：{{resume.profile.name || '请填写姓名'}}</h1>
    <p>城市：{{resume.profile.city ||'请填写城市'}}</p>

     <p>出生年月：{{resume.profile.birthday  ||'请填写出生年月'}}</p>
    <hr>
    <section v-if='filter(resume.workHistory).length>0'>
      <h2>工作经历</h2>
      <ul>
        <li v-for="work in filter(resume.workHistory)">
        <div>公司： {{work.company}}    工作内容： {{work.content}}  工作时间：{{work.ctime}}</div>
        </li>
      </ul>
    </section>
    <section v-if='filter(resume.studyHistory).length>0'>
      <h2>学习经历</h2>
      <ul>
        <li v-for="work in filter(resume.studyHistory)">
        <div> 学校： {{work.school}}
           时间：{{work.duration}}
           学历：{{work.degree}}
           专业：{{work.profession}}
           </div>
        </li>
      </ul>
    </section>
    <section v-if='filter(resume.projects).length>0'>
    <h2>项目</h2>
    <ul>
      <li v-for="project in filter(resume.projects)">
        <div> 项目名称： {{project.name}}</div>
        <div> 项目内容：{{project.content}}</div>
      </li>
    </ul>
  </section>
    <section v-if='filter(resume.awards).length>0'>
      <h2>获奖情况</h2>
      <ul>
        <li v-for="award in filter(resume.awards)">
          获奖名称：{{award.name}}

        </li>
      </ul>
    </section>
    <hr>

    <div>QQ号码：{{resume.contacts.qq ||'请填写QQ'}}</div>
    <div> 微信号码：{{resume.contacts.wechat  ||'请填写微信'}}</div>
    <div>  邮箱：{{resume.contacts.email  ||'请填写电子邮箱'}}</div>
    <div>手机号码：{{resume.contacts.phone  ||'请填写手机号码'}}</div>


  </div>

</template>
<script>
  export default {
    props: ['resume'],
    methods: {
      filter(array) {
        return array.filter(item => !this.isEmpty(item))
      },
      isEmpty(Object) {
        let empty = true
        for (let key in Object) {
          if (Object[key]) {
            empty = false
            break
          }
        }
      }
    }
  }
</script>


<style>
  #preview {
    min-height: 100px;
  }

</style>
