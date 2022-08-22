<template>
  <div v-for="(a, i) in rooms" :key="i">
    <img @click="$emit('openModal',a.id)" :src="a.image" class="room-img" />
    <h4>{{ a.title }}</h4>
    <p>{{ a.price }}원</p>
  </div>
</template>

<script>
export default {
    name:'TheList',
    props:{
        rooms:Array,
    },
    methods: {
      // send(){
      //   this.$emit('openModal',this.a.id)
      // }
    },

}
</script>

<style>

</style>