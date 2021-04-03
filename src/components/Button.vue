<template>
  <div v-if="title" :id="id" @click="press" >{{title}}</div>
</template>

<script>
export default {
  props: ['title', 'id'],
  methods:{
    press: function (){
      this.$emit('press');
    }
  }
}
</script>

<style scoped>
  div{
    width: 25%;
    padding: 1.5rem 0;
    text-align: center;
    box-sizing: border-box;
    transition: box-shadow 0.3s;
  }
  div:nth-child(19) {
    background: #E33D3D;
  }
  div:nth-child(1) {
    filter: opacity(0.5);
  }
  div:nth-child(2) {
    filter: opacity(0.5);
  }
  div:nth-child(3) {
    filter: opacity(0.5);
  }
  div:hover {  filter: opacity(0.8);
  }
  div:active {
    box-shadow: 2px 2px 10px #F2736E inset;
  }
  #zero {
    text-align: center;
    padding-left: 2rem;
    flex-grow: 2;
  }
</style>