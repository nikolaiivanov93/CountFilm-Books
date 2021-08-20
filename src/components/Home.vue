<template>
  <div class="home">
    <h1 class="home__title">Home</h1>
    <!-- <el-input type="text" placeholder="What we will watch?" v-model="taskTitle" @keyup.enter="newTask" clearable></el-input>
    <el-input
      class="textarea"
      type="textarea"
      :rows="2"
      v-model="taskDescription"
      @keyup.enter="newTask"
      clearable>
    </el-input> -->
    <div class="home__wrap">
      <input class="home-input" type="text" placeholder="What we will watch?" v-model="taskTitle" @keyup.enter="newTask">
      <textarea class="home-textarea" type="textarea" v-model="taskDescription" @keyup.enter="newTask"></textarea>
    </div>
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
      taskId: 3,
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
      if (this.taskTitle === '') {
        return
      }
      this.films.push({
        id: this.taskId,
        name: this.taskTitle,
        text: this.taskDescription
      })
      this.taskId += 1
      this.taskTitle = ''
      this.taskDescription = ''
    }
  }
}
</script>

<style lang="scss">
  .home {
    font-size: 26px;
    color: #000;
    width: 480px;
    &__title {
      font-family: "Helvetica Neue", Helvetica;
    }
    &__wrap {
      width: 100%;
      display: flex;
      flex-direction: column;
    }
    &-input {
      padding: 10px;
      font-size: 16px;
      border-radius: 5px;
      border: 1px Solid rgb(172, 172, 172);
      color: rgb(97, 97, 97);
      outline: none;
    }
    &-textarea {
      font-size: 16px;
      margin-top: 20px;
      height: 40px;
      padding: 10px;
      border-radius: 5px;
      border: 1px Solid rgb(172, 172, 172);
      resize: none;
      color: rgb(97, 97, 97);
      outline: none;
    }
  }
  .textarea {
    margin-top: 20px;
  }
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
      font-family: "Helvetica Neue", Helvetica;
    }
    &__name {
      font-family: "Helvetica Neue", Helvetica;
      font-weight: Bold;
    }
    &__txt {
      margin-top: 7px;
      font-size: 16px;
      width: 100%;
      word-wrap: break-word;
      font-family: "Helvetica Neue", Helvetica;
      font-weight: Regular;
    }
  }
</style>
