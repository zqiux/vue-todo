<template>
  <el-container>
    <el-header>
      <el-menu :default-active="defaultActiveIndex"
      more="horizontal" style="display:flex;justify-content:center;align-items:center;">
        <el-menu-item index="/">Home</el-menu-item>
        <el-menu-item index="/about">About</el-menu-item>
      </el-menu>
    </el-header>
    <router-view :key="defaultActiveIndex"/>
  </el-container>
</template>

<script>
export default {
  computed:{
    defaultActiveIndex(){
      return this.$route.path
    }
  }
}
</script>

