<template>
  <div class="container">
          <div id="result">
            
            <input v-model="curNum" :placeholder="lastAnswer"><br>
          
              <button @click="n9()">9</button>
              <button @click="n8()">8</button>
              <button @click="n7()">7</button><br>
              <button @click="n6()">6</button>
              <button @click="n5()">5</button>
              <button @click="n4()">4</button><br>
              <button @click="n3()">3</button>
              <button @click="n2()">2</button>
              <button @click="n1()">1</button><br>
              <button @click="n0()">0</button>
              <button @click="equal()">=</button>
          </div>
      
          <div id="calculator">
            <!-- <button @click="Clear">C</button><br>
            <button @click="share">/</button><br>
            <button @click="multiply">*</button><br>
            
            <button @click="minus">-</button><br> -->
            <button @click="clear()">C</button><br>
            <button @click="plus()">+</button><br>
            <button @click="minus()">-</button><br>
            <button @click="multiply()">*</button><br>
            <button @click="divide()">/</button><br>
            <button @click="power()">^</button>
            <button @click="square()">sq</button>
            <button @click="percent()">%</button>
            
          </div>
  </div>
</template>

<script>
export default {
  name: 'Calculator',
  data(){
    return{
      
      curNum: '',
      lastAnswer: null,
      curOperator:null,
    }
  },
  methods:{
    performOp(){
      var answer ;
      var cur = Number(this.curNum);
      var last = Number(this.lastAnswer)
  console.log("kkkkkkkkkkkkkkkkk");
  console.log("cur " + cur);
  console.log("last " + last);
      switch (this.curOperator){
        case '+':
          answer = cur + last;
        break;
        case '-':
          answer = last - cur ;
        break;
        case '*':
          answer = cur * last;
        break;
        case '/':
          answer = last / cur ;
        break;
        case '^':
          answer = 1;
          for(var i = 0; i < cur; i++){
              answer = answer * last;
              console.log("answer " + answer);
          }  
        break;  
        // case '%':
        //   answer = last / 100;
        // case 'sq':
        //   answer = last * last ;
        // break;
      }
      // console.log("ádsdasdas " + answer);
      this.lastAnswer = String(answer);
      this.curNum = '';
      this.curOperator = '';
      console.log("----------this.lastAnswer " + this.lastAnswer);
    },
    equal(){
      if(this.curOperator != null){
          this.performOp();
      }
      this.curNum = this.lastAnswer;
      this.curOperator = null;
      this.lastAnswer = null;
    },
    plus(){
      if(this.curNum == '') {
        return;
      }
      else if(this.lastAnswer == null){ 
        this.lastAnswer = this.curNum;
        this.curOperator = '+';
        this.curNum = '';
      }
      else{ // curnum and lastanswer
        this.performOp();
        this.curOperator = '+';
      
      }
    },
    minus(){
      if(this.curNum == ''){
        return;
      }else if(this.lastAnswer == null){
        this.lastAnswer = this.curNum;
        this.curOperator = '-';
        this.curNum ='';
      }else{
        this.performOp();
        this.curOperator = '-';
      }
    },
    multiply(){
      if(this.curNum == ''){
        return;
      }else if(this.lastAnswer == null){
        this.lastAnswer = this.curNum;
        this.curOperator = '*';
        this.curNum = ''
      }else{
        this.performOp();
        this.curOperator = '*'
      }
    },
    divide(){
      if(this.curNum == ''){
        return;
      }else if(this.lastAnswer == null){
        this.lastAnswer = this.curNum;
        this.curOperator = '/'
        this.curNum = '';
      }else{
        this.performOp();
        this.curOperator = "/"
      }
    },
     power(){
      if(this.curNum == ''){
        return;
      }else if(this.lastAnswer == null){
        this.lastAnswer = this.curNum;
        this.curOperator = '^'
        this.curNum = '';
      }else{
        this.performOp();
        this.curOperator = "^"
      }
    },
     square(){
      if(this.curNum == ''){
        return;
      }else {
        this.lastAnswer = this.curNum * this.curNum;
        this.curOperator = ''
        this.curNum = '';
      }
     },
     clear(){
       this.curNum = '';
       this.lastAnswer = null;
       this.curOperator = null;
     },
      percent(){
      
      this.curNum =Number(this.curNum);
      this.lastAnswer =this.curNum/ 100;
      this.lastAnswer = String(this.lastAnswer);
      this.curOperator = null;
      this.curNum = '';
      console.log("ádsadsđsađấ")
    },
     
    n0() {
      this.curNum = this.curNum + '0';
    },
    n1() {
      console.log("do yopu seeee");
      this.curNum = this.curNum + '1';
    },
    n2() {
      this.curNum = this.curNum + '2';
    },
    n3() {
      this.curNum = this.curNum + '3';
    },
    n4() {
      this.curNum = this.curNum + '4';
    },
    n5() {
      this.curNum = this.curNum + '5';
    },
    n6() {
      this.curNum = this.curNum + '6';
    },
    n7() {
      this.curNum = this.curNum + '7';
    },
    n8() {
      this.curNum = this.curNum + '8';
    },
    n9() {
      this.curNum = this.curNum + '9';
    },
  },
  props: {
    msg: String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.container{
    background-color:aqua;
    display: flex;
    text-align: center;
    flex-direction: row;
    justify-content: center;
}
input{
  width: 200px;
  height: 20px;
}
button{
  width: 50px;
  height: 50px;
}
</style>