<template>
  <div class="home">
    <h1>Home</h1>
    <el-card class="box-card">
      <el-tag
        class="el-tag"
        v-for="item in itemFilm"
        :key="item.name"
        :type="itemFilm.type">
        {{ item.name }}
      </el-tag>
    </el-card>
  </div>
</template>

<script>

export default {
  name: 'home',
  data () {
    return {
      itemFilm: [
        { name: 'Film', type: '' }
      ]
    }
  }
}
</script>

<style lang="scss">
  .home {
    font-size: 26px;
    color: #000;
  }

  .box-card {
    width: 480px;
  }
  .el {
    &-tag {
      font-size: 24px;
    }
  }
</style>
