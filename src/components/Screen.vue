<template>
  <div>{{display}}</div>
</template>

<script>
export default {
  props: ['display'],
  data() {
    return {
      displayy: 0,
    };
  }
}
</script>

<style scoped>
div{
  padding-top: 4.5rem;
  font-size: 2.5rem;
  text-align: right;
  padding-right: 3rem;
  border: none;
  color: #FFFFFF;
  background: linear-gradient(180deg, #2C3059 22.08%, #393E73 112.93%);
  border-radius: 0;
}
</style>