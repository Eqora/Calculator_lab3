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
        <div class="line"></div>
        <div class="line-copy-5"></div>
        <div class="line-copy-6"></div>
        <div class="line-copy-2"></div>
        <div class="line-copy-3"></div>
        <div class="line-copy-4"></div>
        <div class="line-copy-7"></div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
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
.line{
  position: absolute;
  width: 1px;
  height: 296px;
  left: 365.5px;
  top: 535.5px;

  mix-blend-mode: normal;
  opacity: 0.1;
  border: 1px solid #ffffff;
}
.line-copy-5{
  position: absolute;
  width: 1px;
  height: 38%;
  left: 50%;
  top: 53.7%;

  mix-blend-mode: normal;
  opacity: 0.8;
  border: 1px solid lawngreen;
}
.line-copy-6{
  position: absolute;
  width: 1px;
  height: 390px;
  left: 525.5px;
  top: 535.5px;

  mix-blend-mode: normal;
  opacity: 0.8;
  border: 1px solid deeppink;
}
.line-copy-2{
  position: absolute;
  width: 415px;
  height: 3px;
  left: 287px;
  top: 830px;

  mix-blend-mode: normal;
  opacity: 0.1;
  border: 1px solid #fffffb;
}
.line-copy-3{
  position: absolute;
  width: 415px;
  height: 3px;
  left: 287px;
  top: 750px;

  mix-blend-mode: normal;
  opacity: 0.1;
  border: 1px solid #fffffb;
}
.line-copy-4{
  position: absolute;
  width: 415px;
  height: 3px;
  left: 287px;
  top: 675px;

  mix-blend-mode: normal;
  opacity: 0.1;
  border: 1px solid #fffffb;
}
.line-copy-7{
  position: absolute;
  width: 415px;
  height: 3px;
  left: 287px;
  top: 600px;

  mix-blend-mode: normal;
  opacity: 0.1;
  border: 1px solid #fffffb;
}
</style>
