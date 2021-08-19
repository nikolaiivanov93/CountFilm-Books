<template>
  <div class="home">
    <h1>Home</h1>
    <el-input type="text" placeholder="What we will watch?" v-model="taskTitle" @keyup.enter="newTask"></el-input>
    <el-input
    class="el-textarea__inner"
      type="textarea"
      :rows="2"
      v-model="taskDescription"
      @keyup.enter="newTask">
    </el-input>
    <el-card v-for="film in films" :key="film.name" class="box-card">
      <div class="box-card__container">
        <div class="box-card__title">
          <el-tag
            v-for="item in itemFilm"
            :key="item.name"
            :type="itemFilm.type">
            {{ item.name }}
          </el-tag>
          <div class="box-card__text">Total time:</div>
        </div>
        <div class="box-card__block">
          <div class="box-card__name">{{ film.name }}</div>
          <div class="box-card__txt">{{ film.text }}</div>
        </div>
      </div>
    </el-card>
  </div>
</template>

<script>

export default {
  name: 'home',
  data () {
    return {
      taskTitle: '',
      taskDescription: '',
      itemFilm: [
        { name: 'Film', type: '' }
      ],
      films: [
        {
          id: '1',
          name: 'IT',
          text: 'fsdagkjdsgbfvukydvgkvkyuzbhkjdjfbsuygdfauigbidfasdfvbshjdjvdjhsjkbfsdfdgsdfuygsfhbvckljdiauswq'
        },
        {
          id: '2',
          name: 'lakjsbdf',
          text: 'fsdagkjdsgbfvukydv'
        }
      ]
    }
  },
  methods: {
    newTask () {
      this.films.push({
        id: this.taskId,
        title: this.taskTitle,
        text: this.taskDescription
      })
    }
  }
}
</script>

<style lang="scss">
  .home {
    font-size: 26px;
    color: #000;
    width: 480px;
  }
  // .el-textarea__inner {
  //   margin-top: 20px;
  // }
  .box-card {
    width: 480px;
    margin-top: 20px;
    &__title {
      display: flex;
      align-items: center;
    }
    &__container {
      width: 100%;
      height: 100%;
      // padding: 15px;
      // display: flex;
      // align-items: center;
    }
    &__block {
      width: 100%;
      position: relative;
      margin-top: 15px;
    }
    &__text {
      margin-left: 25px;
      font-size: 20px;
    }
    &__txt {
      margin-top: 7px;
      font-size: 18px;
      width: 100%;
      word-wrap: break-word;
    }
  }
</style>
