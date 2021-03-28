<template>
  <div class="container">
    <div id='calculator' onselectstart='return false'>
      <screen :display="display"></screen>

      <div class="buttons">
        <button-item @press='clear' title="C"></button-item>
        <button-item @press='sign' title="+/-"></button-item>
        <button-item @press='percent' title="%"></button-item>
        <button-item @press='divide' title="÷"></button-item>
        <button-item @press='append(7)' title="7"></button-item>
        <button-item @press='append(8)' title="8"></button-item>
        <button-item @press='append(9)' title="9"></button-item>
        <button-item @press='multiply' title="x"></button-item>
        <button-item @press='append(4)' title="4"></button-item>
        <button-item @press='append(5)' title="5"></button-item>
        <button-item @press='append(6)' title="6"></button-item>
        <button-item @press='subtract' title="-"></button-item>
        <button-item @press='append(1)' title="1"></button-item>
        <button-item @press='append(2)' title="2"></button-item>
        <button-item @press='append(3)' title="3"></button-item>
        <button-item @press='add' title="+"></button-item>
        <button-item id="zero" @press='append(0)' title="0"></button-item>
        <button-item @press='decimal' title="."></button-item>
        <button-item @press='equal' title="="></button-item>
      </div>
    </div>
  </div>
</template>

<script>
import Button from '@/components/Button.vue'
import Screen from "@/components/Screen";

export default {

  components:{
    'button-item' : Button,
    'screen' : Screen
  },

  data() {
    return {
      previous: null,
      display: 0,
      operator: null,
      operatorClicked: false
    };
  },
  methods: {
    clear() {
      this.display = 0;
    },
    sign() {
      this.display =
          this.display < 0
              ? (this.display = this.display - this.display * 2)
              : (this.display = this.display - this.display * 2);
    },
    percent() {
      this.operator = (a, b) => a * (b * 0.01);
      this.previous = this.display;
      this.operatorClicked = true;
    },
    append(number) {
      if (this.operatorClicked === true) {
        this.display = '';
        this.operatorClicked = false;
      }
      this.display =
          this.display === 0
              ? (this.display = number)
              : '' + this.display + number;
    },
    decimal() {
      if(this.display === 0){
        this.append('0.');
      } else {
        this.append('.');
      }
      if (this.display.indexOf('.') === -1) {
        this.append('.');
      }
    },
    divide() {
      this.operator = (a, b) => a / b;
      this.previous = this.display;
      this.operatorClicked = true;
    },
    multiply() {
      this.operator = (a, b) => a * b;
      this.previous = this.display;
      this.operatorClicked = true;
    },
    subtract() {
      this.operator = (a, b) => a - b;
      this.previous = this.display;
      this.operatorClicked = true;
    },
    add() {
      this.operator = (a, b) => a + b;
      this.previous = this.display;
      this.operatorClicked = true;
    },
    equal() {
      this.display = (this.operator(Number(this.previous), Number(this.display))).toFixed(4);
      this.previous = null;
      this.operatorClicked = true;
    }
  }
};
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
.container #calculator .buttons #zero {
  text-align: center;
  padding-left: 2rem;
  flex-grow: 2;
}
</style>
