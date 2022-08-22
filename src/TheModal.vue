<template>

  <div class="black-bg" v-if="modal == true">
    <div class='white-bg'>
      <img :src="rooms[click].image" class="room-img" />
      <h4>{{ rooms[click].title }}</h4>
      <p>{{ rooms[click].content }}</p>
      <input v-model='month' placeholder="how long month?" />
      <!-- @input='month = $event.target.value' 대신 v-model='month'해도됨 -->
      <p>{{ month }}개월 {{ rooms[click].price * month }}원</p>
      <button @click="$emit('closeModal')">닫기</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'TheModal',
  data() {
    return {
      month: 1
    }
  },
  watch: {
    month(a) { //a는 month 변경전 
      if (isNaN(a)==true) {
        alert('숫자만 입력가능');
      }
    }
  },
  props: {
    rooms: Array,
    click: Number,
    modal: Boolean,
  }
}
</script>

<style>
</style>