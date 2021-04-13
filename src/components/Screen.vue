<template>
  <div :class="fontSizeClass">{{display}}</div>
</template>

<script>
export default {
  props: ['display', 'fontSizeClass']
}
</script>

<style scoped>

</style>