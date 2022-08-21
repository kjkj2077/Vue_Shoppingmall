<template>
  <div class="menu">
    <a v-for="(a, i) in menu" :key='i'>{{ a }}{{ i }}</a>
  </div>

  <!-- <div v-for="(a,i) in products" :key="i">
    <h4>{{ products[i] }}</h4>
    <p>{{price[i]}}만원</p>
  </div> -->
  <div>
    <h4>{{ products[0] }}</h4>
    <p>60만원</p>
    <button @click="count[0]++">허위매물신고</button> <span>신고수 : {{ count[0] }}</span>
  </div>
  <div>
    <h4>{{ products[1] }}</h4>
    <p>70만원</p>
    <button @click="count[1]+=1">허위매물신고</button> <span>신고수 : {{ count[1] }}</span>
  </div>
  <div>
    <h4>{{ products[2] }}</h4>
    <p>80만원</p>
    <button @click="count[2]+=1">허위매물신고</button> <span>신고수 : {{ count[2] }}</span>
  </div>
</template>

<script>


export default {
  name: 'App',
  data() {//데이터 보관함
    return {
      count: [0,0,0],
      price: [60, 70, 80],
      menu: ['Home', 'Shop', 'About'],
      products: ['역삼동원룸', '천호동원룸', '마포구원룸']
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

.menu {
  background: darkslateblue;
  padding: 15px;
  border-radius: 5px;
}

.menu a {
  color: white;
  padding: 10px;
}
</style>
