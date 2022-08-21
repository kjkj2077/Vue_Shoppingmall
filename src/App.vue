<template>

  <div class="black-bg" v-if="modal == true">
    <div class='white-bg'>
      <img :src="rooms[click].image" class="room-img" />
      <h4>{{rooms[click].title}}</h4>
      <p>{{rooms[click].price}}원</p>
      <button @click="modal = false">닫기</button>
    </div>
  </div>


  <div class="menu">
    <a v-for="(a, i) in menu" :key='i'>{{ a }}{{ i }}</a>
  </div>
  <div v-for="(a, i) in rooms" :key="i">
    <img :src="a.image" @click="modal = true; click=i " class="room-img" />
    <h4>{{ a.title }}</h4>
    <p>{{ a.price }}원</p>
  </div>

</template>
<script>
//npm run serve 

import data from './assets/data.js';
data

export default {
  name: 'App',
  data() {//데이터 보관함 리액트에서의 state임.
    return {
      click:0,
      rooms: data,
      modal: true,
      count: [0, 0, 0],
      price: [60, 70, 80],
      menu: ['Home', 'Shop', 'About'],
      products: ['역삼동원룸', '천호동원룸', '마포구원룸'],
    }
  },
  methods: {
    increase() {
      this.count++ //함수안에서 데이터 쓸땐 this.데이터명
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

body {
  margin: 0;
}

div {
  box-sizing: border-box;
}

.black-bg {
  width: 100%;
  height: 100%;
  background: black(0, 0, 0, 0.5);
  position: fixed;
  padding: 20px;
}

.white-bg {
  width: 100%;
  background: white;
  border-radius: 8px;
  padding: 20px;
}

.menu {
  background: darkslateblue;
  padding: 15px;
  border-radius: 5px;
}

.menu a {
  color: white;
  padding: 10px;
}

.room-img {
  width: 100%;
  margin-top: 40px;
}
</style>
