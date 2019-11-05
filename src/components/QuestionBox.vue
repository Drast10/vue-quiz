<template>
  <div>
    <Header 
    :numCorrect="numCorrect"
    :numTotal="numTotal"/>
    <h4>Category : Computer Science</h4>

     <QueNAns 
     v-if="question.length"
     :currentQue="question[index]"
     :nextQue="next"
     :increment="increment "></QueNAns>

  </div>
</template>

<script>
 import QueNAns from "./QueNAns";
 import Header from "./Header"
export default {
  data(){
    return{
     question:[],
     index:0,
     numCorrect:0,
     numTotal:0
    }
  },
  methods:{
    next(){
      this.index++;
    },
    increment(isCorrect){
      if(isCorrect){
        this.numCorrect++;
      }
      this.numTotal++;
    }
    
  },
  mounted(){
    fetch("https://opentdb.com/api.php?amount=10&category=18&type=multiple",
    {method:'get'})
    .then(response=>{ return response.json()})
    // store ressults data in local question array
    .then(jsonData=>{
      this.question = jsonData.results;
      console.log(this.question)
      })
  },
  components:{
    QueNAns,
    Header
  }
}
</script>

<style scoped>
h4{
  margin: 15px;
}
</style>