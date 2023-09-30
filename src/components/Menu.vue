<template>
  <el-container>
  <el-header>Header</el-header>
  <el-main>Main</el-main>
  </el-container>
</template>

<script>
  export default {
  name: 'Menu',
  data () {
      return {
      msg: 'Welcome to Your Vue.js App'
      }
  }
  }
</script>

<style>
.el-header, .el-footer {
  background-color: #B3C0D1;
  color: #333;
  text-align: center;
  line-height: 60px;
}
</style>