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
.container {
  height: 50rem;
  display: flex;
  align-items: center;
  justify-content: center;
  font-family: Actor,serif;
}
.container #calculator {
  display: flex;
  flex-direction: column;
  width: 20rem;
  background-color: #1d1f20;
}
.container #calculator #screen {
  padding-top: 4.5rem;
  font-size: 2.5rem;
  text-align: right;
  padding-right: 3rem;
  border: none;
  color: #FFFFFF;
  background: linear-gradient(180deg, #2C3059 22.08%, #393E73 112.93%);
  border-radius: 0;
}
.container #calculator .buttons {
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
  cursor: pointer;
  font-size: 1.5rem;
  display: flex;
  color: white;
  flex-wrap: wrap;
  background: linear-gradient(180deg, #F2736E -24.93%, #F04949 96.2%);
}
.container #calculator .buttons .button {
  width: 25%;
  padding: 1.5rem 0;
  text-align: center;
  box-sizing: border-box;
  border:1px #ffffff solid;
  transition: box-shadow 0.3s;
}
.container #calculator .buttons .button:nth-child(19) {
  background: #E33D3D;
}
.container #calculator .buttons .button:nth-child(1) {
  filter: opacity(0.5);
}
.container #calculator .buttons .button:nth-child(2) {
  filter: opacity(0.5);
}
.container #calculator .buttons .button:nth-child(3) {
  filter: opacity(0.5);
}
.container #calculator .buttons .button:hover {
  filter: opacity(0.8);
}
.container #calculator .buttons .button:active {
  box-shadow: 2px 2px 10px #F2736E inset;
}
.container #calculator .buttons #zero {
  text-align: center;
  padding-left: 2rem;
  flex-grow: 2;
}
</style>
