<template>
  <!-- prop 보낼때 작명="문자자료", :작명="숫자자료" -->
  <Transition name="fade">
    <TheModal :rooms='rooms' :click="click" :modal="modal" @closeModal="modal = false" />
  </Transition>

  <div class="menu">
    <a v-for="(a, i) in menu" :key='i'>{{ a }}{{ i }}</a>
  </div>
  <button @click="priceSort">가격순정렬</button>
  <button @click="priceSort_r">역순정렬</button>
  <TheDiscount v-if="showDiscount == true" />
  <TheList @openModal='modal = true, click = $event' :rooms='rooms' />
</template>
<script>
//npm run serve 

import data from './assets/data.js';
import TheDiscount from './Discount.vue';
import TheModal from './TheModal.vue';
import TheList from './TheList.vue';


export default {
  name: 'App',
  data() {//데이터 보관함 리액트에서의 state임.
    return {
      showDiscount: true,
      click: 0,
      rooms: data,
      modal: false,
      menu: ['Home', 'Shop', 'About'],
    }
  },
  methods: {
    increase() {
      this.count++ //함수안에서 데이터 쓸땐 this.데이터명
    },
    priceSort() {
      this.rooms.sort(function (a, b) {
        return a.price - b.price
      })
    },
    priceSort_r() {
      this.rooms.sort(function (a, b) {
        return b.price - a.price
      })
    },
  },
  components: {
    TheDiscount,
    TheModal,
    TheList
  },
  mounted() { //마운트됐을때 실행.
    setTimeout(() => {
      this.showDiscount = false //this쓸꺼면 에로우펑션써라.
    }, 2000)
  },
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

.fade-enter-from {
  opacity: 0;
}

.fade-enter-active {
  transition: all 1.2s;
}

.fade-enter-to {
  opacity: 1;
}

.fade-leave-from {
  opacity: 1;
}

.fade-leave-active {
  transition: all 1.2s;
}

.fade-leave-to {
  opacity: 0;
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
  background: whitesmoke;
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
  width: 80%;
  height: 80%;
  margin-top: 40px;
}

.discount {
  background: gainsboro;
  padding: 10px;
  margin: 10px;
  border-radius: 10px;
}
</style>
