<template>
  <div class="calc">
    <span class="disp">Display</span>
    <button>C</button>
    <button>+/-</button>
    <button>%</button>
    <button class="operator">÷</button>
    <button>7</button>
    <button>8</button>
    <button>9</button>
    <button class="operator">×</button>
    <button>4</button>
    <button>5</button>
    <button>6</button>
    <button class="operator">-</button>
    <button>1</button>
    <button>2</button>
    <button>3</button>
    <button class="operator">+</button>
    <button class="zero">0</button>
    <button>.</button>
    <button class="operator">=</button>
    
  </div>
</template>

<script>
export default {
  name: 'Main',
  props: {
    msg: String
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
