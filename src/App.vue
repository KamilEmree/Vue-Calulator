<template>
  <div id="container">
    <div id="result-team">
      <input v-model="input1" readonly id="input-2" type="text">
      <input v-model="input2" readonly id="input-1" type="text">
    </div>
    <div id="span-team">
      <span @click="ClickDelete()" class="item-C">C</span>
      <span @click="ClickProcess($event.target.innerText)">%</span>
      <span @click="ClickProcess($event.target.innerText)" class="item-process">+</span>
      <span @click="ClickNumber($event.target.innerText)">7</span>
      <span @click="ClickNumber($event.target.innerText)">8</span>
      <span @click="ClickNumber($event.target.innerText)">9</span>
      <span @click="ClickProcess($event.target.innerText)" class="item-process">-</span>
      <span @click="ClickNumber($event.target.innerText)">4</span>
      <span @click="ClickNumber($event.target.innerText)">5</span>
      <span @click="ClickNumber($event.target.innerText)">6</span>
      <span @click="ClickProcess($event.target.innerText)"  class="item-process">*</span>
      <span @click="ClickNumber($event.target.innerText)">1</span>
      <span @click="ClickNumber($event.target.innerText)">2</span>
      <span @click="ClickNumber($event.target.innerText)">3</span>
      <span @click="ClickProcess($event.target.innerText)" class="item-process">/</span>
      <span @click="ClickNumber($event.target.innerText)" class="item-0">0</span>
      <span @click="ClickNumber($event.target.innerText)">.</span>
      <span @click="ClickEqual()" class="item-calc">=</span>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      input1 : '', 
      input2 : '',
      input3 : '',
      events : ''
    }
  },
  computed : {
    InputLength : function() {
      return this.input2.split('').length;
    },
  },
  methods : {
    ClickNumber : function(event) {
      if(this.InputLength === 20) {
        console.log('merhaba')
      }
      this.input2 += event;
    },
    ClickEqual : function() {
      switch (this.events) {
        case "+":
          this.input2 = Number(this.input3) + Number(this.input2);
          this.input1 = ''; 
        break;
        case "-":
          this.input2 = Number(this.input3) - Number(this.input2);
          this.input1 = ''; 
        break;
        case "/":
          this.input2 = Number(this.input3) / Number(this.input2);
          this.input1 = ''; 
        break;
        case "*":
          this.input2 = Number(this.input3) * Number(this.input2);
          this.input1 = ''; 
        break;
        case "%":
          this.input2 = (Number(this.input3) * Number(this.input2))  / 100;
          this.input1 = ''; 
        break;
        default:
          this.input1 = '';
          this.input2 = '';
        break;
      }
      this.events = '';
    },
    ClickProcess : function(event) {
      this.events = event;
      this.input1 = this.input2 + this.events;
      this.input3 = this.input2;
      this.input2 = '';
    },
    ClickDelete : function() {
      this.input2 = '';
      this.input1 = '';
    }
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Exo+2:wght@300;400;500&display=swap');
* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}
body {
  font-family: 'Exo 2', sans-serif;
  background: #95a5a6;  
  min-height: 100vh;
  color: #fff;
  display: flex;
  justify-content: center;
  align-items: center;
}
#container {
  box-shadow: rgba(14, 30, 37, 0.12) 0px 2px 4px 0px, rgba(14, 30, 37, 0.32) 0px 2px 16px 0px;
  padding: .2rem;
  background-color: #293241;
  border-radius: .3rem;
}
#result-team {
  width: 100%;
  display: flex;
  flex-direction: column;
  background-color: #293241;
  transition: all 200ms;
}
#result-team #input-1 , #input-2 {
  width: 100%;
  text-align: right;
  cursor: default;
  outline: none;
  border: none;
  background-color: #293241;
  color: #fff;
  letter-spacing: .1rem;  
}
#result-team #input-1  {
  font-size: 1.6rem;
  min-height: 3.5rem;
  margin-bottom: .5rem;
  padding: .6rem .6rem .2rem .6rem;
}
#result-team #input-2  {
  font-size: 1.2rem;
  min-height: 2.5rem;
  padding: .6rem;
}
#span-team {
  font-size: 1.4rem;
  display: grid;
  grid-template-columns: auto auto auto auto;
  text-align: center;
}
#span-team span {
  box-shadow: rgba(60, 64, 67, 0.3) 0px 1px 2px 0px, rgba(60, 64, 67, 0.15) 0px 2px 6px 2px;
  cursor: pointer;
  display: flex;
  justify-content: center;
  align-items: center;
  min-width: 5rem;
  min-height: 5rem;
  background-color: #3d5a80;
  margin: .2rem;
  border-radius: .3rem;
}
#span-team .item-0 , .item-C {
  grid-column-start: 1;
  grid-column-end: 3;
}
#span-team .item-C {
  background-color: #ee6c4d;
}
#span-team .item-process {
  background-color: #02c39a;
}
#span-team .item-calc {
  background-color: #abc4ff;
  color: #16222A;
}
#span-team span:active {
  background-color: #2b3f58;
}
#span-team .item-C:active {
  background-color: #e94e28;
}
#span-team .item-process:active {
  background-color: #009474;
}
#span-team .item-calc:active {
  background-color: #8faffa;
  color: #16222A;
}
</style>