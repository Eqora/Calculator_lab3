<template>
  <div class="container">
    <div id='calculator'>
      <screen :fontSizeClass="displayFontSize" :display="displayValue"></screen>

      <div class="buttons">
        <button-item v-for="(b, id) in buttons"
                     :key="id" @press="action(b.title)" :title="b.title" :id="b.id"></button-item>
      </div>
    </div>
  </div>
</template>

<script>
import Button from '@/components/Button.vue'
import Screen from "@/components/Screen";

export default {

  components: {
    'button-item': Button,
    'screen': Screen
  },
  computed: {
    displayValue: {
      get() {
        return this.display;
      },
      set(display) {

        if (this.display === 'undefined' || this.display === 0 || this.display.length < 17) {
          this.displayFontSize = 'default-font-size';
        } else {

          this.displayFontSize = 'grippen-font-size';
        }
        this.display = display;
      }
    }
  },
  data() {
    return {
      previous: null,
      display: 0,
      operator: null,
      operatorClicked: false,
      displayFontSize: 'default-font-size',
      buttons: [
        {title: "C"},
        {title: "+/-"},
        {title: "%"},
        {title: "÷"},
        {title: "7"},
        {title: "8"},
        {title: "9"},
        {title: "x"},
        {title: "4"},
        {title: "5"},
        {title: "6"},
        {title: "-"},
        {title: "1"},
        {title: "2"},
        {title: "3"},
        {title: "+"},
        {title: "0", id: "zero"},
        {title: "."},
        {title: "="}
      ]
    };
  },
  methods: {
    action(title) {
      if (title === 'C') {
        this.clear();
      }
      if (title === '+/-') {
        this.sign();
      }
      if (title === '%') {
        this.percent();
      }
      if (title === '÷') {
        this.divide();
      }
      if (title === 'x') {
        this.multiply();
      }
      if (title === '+') {
        this.add();
      }
      if (title === '-') {
        this.subtract();
      }
      if (title === '.') {
        this.decimal();
      }
      if (title === '=') {
        this.equal();
      }
      if (title >= '0' && title <= '9') {
        this.append(title);
      }
    },
    clear() {
      this.display = 0;
      this.displayValue = this.display;
      this.displayFontSize = 'default-font-size';
    },
    sign() {
      this.display =
          this.display < 0
              ? (this.display = this.display - this.display * 2)
              : (this.display = this.display - this.display * 2);
      this.displayValue = this.display;
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
      this.displayValue = this.display;
    },
    decimal() {

      if (this.display === 0) {
        this.append('0.');
      } else if (this.operatorClicked === true) {
        this.display = 0;
        this.displayValue = this.display;
        // this.append('.');
      } else if (this.display.indexOf('.') === -1) {
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
      this.displayValue = this.display;
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
  font-family: Actor, serif;
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
.default-font-size{
  padding-top: 4.5rem;
  font-size: 2.5rem;
  text-align: right;
  padding-right: 3rem;
  border: none;
  color: #FFFFFF;
  background: linear-gradient(180deg, #2C3059 22.08%, #393E73 112.93%);
  border-radius: 0;
}
.grippen-font-size{
  padding-top: 4.5rem;
  font-size: 1.5rem;
  text-align: right;
  padding-right: 3rem;
  border: none;
  color: #FFFFFF;
  background: linear-gradient(180deg, #2C3059 22.08%, #393E73 112.93%);
  border-radius: 0;
}
</style>
