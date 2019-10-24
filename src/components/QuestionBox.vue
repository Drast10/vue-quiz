<template>
  <div>
    <h4>Category : Computer Science</h4>

     <QueNAns 
     v-if="question.length"
     :currentQue=question[index]
     :nextQue=next ></QueNAns>

  </div>
</template>

<script>
 import QueNAns from "./QueNAns";
export default {
  data(){
    return{
     question:[],
     index:0
    }
  },
  methods:{
    next(){
      this.index++;
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
    QueNAns
  }
}
</script>

<style scoped>
h4{
  margin: 15px;
}
</style>