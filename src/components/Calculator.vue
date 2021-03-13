<template>
  <div class="container">
    <div id='calculator' onselectstart='return false'>
      <div id='screen'>{{display}}</div>
      <div class="buttons">
        <div @click='clear' class='button'>C</div>
        <div @click='sign' class='button'>+/-</div>
        <div @click='percent' class='button'>%</div>
        <div @click='divide' class='button'>÷</div>
        <div @click='append(7)' class='button'>7</div>
        <div @click='append(8)' class='button'>8</div>
        <div @click='append(9)' class='button'>9</div>
        <div @click='multiply' class='button'>x</div>
        <div @click='append(4)' class='button'>4</div>
        <div @click='append(5)' class='button'>5</div>
        <div @click='append(6)' class='button'>6</div>
        <div @click='subtract' class='button'>-</div>
        <div @click='append(1)' class='button'>1</div>
        <div @click='append(2)' class='button'>2</div>
        <div @click='append(3)' class='button'>3</div>
        <div @click='add' class='button'>+</div>
        <div id="zero" @click='append(0)' class='button'>0</div>
        <div @click='decimal' class='button'>.</div>
        <div @click='equal' class='button'>=</div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
