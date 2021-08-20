<template>
  <div class="home">
    <h1 class="home__title">Home</h1>
    <div class="home__wrap">
      <input class="home-input" type="text" placeholder="What we will watch?" v-model="taskTitle" @keyup.enter="newTask">
      <textarea class="home-textarea" type="textarea" v-model="taskDescription" @keyup.enter="newTask"></textarea>
      <div class="home__radio-container">
        <div class="home__radio">
          <input class="home__radio-input" type="radio" id="radioFilm" value="Film" v-model="whatWatch">
          <label class="home__radio-label" for="radioFilm">Film</label>
        </div>
        <div class="home__radio">
          <input class="home__radio-input" type="radio" id="radioSerial" value="Serial" v-model="whatWatch">
          <label class="home__radio-label" for="radioSerial">Serial</label>
        </div>
      </div>
    </div>
    <el-card v-for="film in films" :key="film.name" class="box-card">
      <div class="box-card__container">
        <div class="box-card__title">
          <el-tag>
            {{ film.type }}
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
      whatWatch: 'Film',
      films: [
        {
          id: '1',
          name: 'IT',
          text: 'fsdagkjdsgbfvukydvgkvkyuzbhkjdjfbsuygdfauigbidfasdfvbshjdjvdjhsjkbfsdfdgsdfuygsfhbvckljdiauswq',
          type: 'Film'
        },
        {
          id: '2',
          name: 'lakjsbdf',
          text: 'fsdagkjdsgbfvukydv',
          type: 'Serial'
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
        text: this.taskDescription,
        type: this.whatWatch
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
    &__radio {
      display: inline-block;
      margin-top: 20px;
      &:last-child {
        margin-left: 20px;
      }
      &-container {
        display: flex;
        align-items: center;
      }
      &-label {
        // margin-left: 10px;
        display: inline-block;
        cursor: pointer;
        padding: 0px 15px;
        line-height: 34px;
        border: 1px solid #409EFF;
        border-radius: 6px;
        user-select: none;
        font-size: 14px;
        font-family: "Helvetica Neue", Helvetica;
        color: #409EFF;transition: 0.3s all;
        // &:hover {
        //   color: #666;
        // }
      }
      &-input {
        transition: 0.3s all;
        display: none;
        &:checked + .home__radio-label {
          background:#ecf5ff;
          border: 1px solid #ecf5ff;
          transition: 0.3s all;
        }
        &:disabled + .home__radio-label {
          background: #efefef;
          color: #666;
        }
      }
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
