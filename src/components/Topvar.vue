<template>
  <div id="topbar">
    <div class="logo"> 简易简历</div>
    <div>努力奋斗</div>
    <div class="actions">
      <el-button v-on:click="preview">预览</el-button>
    </div>
  </div>
</template>
<script>
  export default {
    methods:{
      preview(){
        this.$emit("preview")
      }
    }
  }

</script>
<style lang="scss">
  #topbar {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 16px;
    font-size: 20px;
  }
</style>
