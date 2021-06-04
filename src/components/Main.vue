<template>
  <div class="calc">
    <span class="disp">{{current || "0"}}</span>
    <button @click="clear">C</button>
    <button @click="sign">+/-</button>
    <button @click="percentage">%</button>
    <button @click="divide"  class="operator">÷</button>
    <button @click="append('7')">7</button>
    <button @click="append('8')">8</button>
    <button @click="append('9')">9</button>
    <button @click="multiply"  class="operator">×</button>
    <button @click="append('4')">4</button>
    <button @click="append('5')">5</button>
    <button @click="append('6')">6</button>
    <button @click="minus"  class="operator">-</button>
    <button @click="append('1')">1</button>
    <button @click="append('2')">2</button>
    <button @click="append('3')">3</button>
    <button @click="plus"  class="operator">+</button>
    <button class="zero" @click="append('0')">0</button>
    <button @click="dot">.</button>
    <button @click= "equals" class="operator">=</button>
    
  </div>
</template>

<script>
export default {
  data() {
    return {
      current: "",
      previous: null,
      operatorActive: false,
      operator: null
    }
  },
  methods: {
    clear() {
      this.current = ""
      this.previous= null
    },
    compute() {
      this.current = this.operator(parseFloat(this.previous), parseFloat(this.current))

      this.previous= null
    },
    sign() {
      this.current = this.current.charAt(0) ==="-" ? this.current.slice(1) : `-${this.current}`
    },
  
    percentage() {
      this.current = `${parseFloat((this.current/100))}`
    },
    append(number) {
      if (this.operatorActive){
        this.current = `${number}`
        this.operatorActive=false
      } 
      else {
        this.current = `${this.current}${number}`
      }
      
    },
    dot() {
      if(this.current.indexOf(".") === -1) {
        this.append('.')
      }
    },
    setPrevious() {
      this.previous = this.current
      this.operatorActive = true
    },
    divide() {
      if(this.operatorActive) {this.compute()}
      
      this.setPrevious()
      this.operator = (a,b)=> a/b
    },
    multiply() {
      
      this.setPrevious()
      this.operator = (a,b)=> a*b

    },
    minus() {
      
      this.setPrevious()
      this.operator = (a,b)=> a-b

    },
    plus() {
      
      this.setPrevious()
      this.operator = (a,b)=> a+b

    },
    equals() {
      this.compute()
    }
  }
}
</script>


<style scoped>
 .calc {
   width: 400px;
   margin: 4rem auto;
   font-size: 40px;
   display: grid;
   grid-template-columns: repeat(4, 1fr);
   grid-auto-rows: minmax(50px, auto);
 }
 .disp {
   text-align: center;
   grid-column: 1/5;
   background-color: #333;
   color: white;

 }
 .zero {
   grid-column: 1/3;
 }
 button {
   background-color: #f2f2f2;
   border: 1px solid #999;
   font-size: 40px;
 }
 .operator {
   background-color: orange;
   color: white
 }

</style>
