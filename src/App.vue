<template>
  <div id="app">
    <el-menu :router="true" :default-active="activeIndex" class="el-menu-demo" mode="horizontal" @select="handleSelect">
      <el-menu-item v-for="link in linkMenu" :key="link.title" :route="link.url" :index=link><router-link class="el__link" :to=link.url>{{ link.title }}</router-link></el-menu-item>
      <!-- <el-menu-item index="1">Processing Center</el-menu-item>
      <el-submenu index="2">
        <template slot="title">Workspace</template>
        <el-menu-item index="2-1">item one</el-menu-item>
        <el-menu-item index="2-2">item two</el-menu-item>
        <el-menu-item index="2-3">item three</el-menu-item>
        <el-submenu index="2-4">
          <template slot="title">item four</template>
          <el-menu-item index="2-4-1">item one</el-menu-item>
          <el-menu-item index="2-4-2">item two</el-menu-item>
          <el-menu-item index="2-4-3">item three</el-menu-item>
        </el-submenu>
      </el-submenu>
      <el-menu-item index="3" disabled>Info</el-menu-item>
      <el-menu-item index="4"><a href="https://www.ele.me" target="_blank">Orders</a></el-menu-item> -->
    </el-menu>
    <el-container class="el-container">
      <el-header>
      <router-view></router-view>
      </el-header>
    </el-container>
  </div>
</template>

<script>
export default {
  data () {
    return {
      linkMenu: [
        { title: 'Home', url: '/' },
        { title: 'Login', url: '/login' },
        { title: 'Registration', url: '/registration' }
      ]
    }
  }
}
</script>

<style lang="scss">
  .el {
    &-container {
      margin: 0 auto;
      max-width: 1170px;
    }
    &-menu {
      &-demo {
        display: flex;
        justify-content: center;
      }
    }
    &__link {
      font-size: 20px;
      text-decoration: none;
      font-family: "Helvetica Neue", Helvetica;
    }
  }
</style>
