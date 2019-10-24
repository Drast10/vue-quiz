<template>
  <div>
    <b-jumbotron class="question-box-container">
      <template>
        {{ this.currentQue.question }}
      </template>

      <hr class="my-4" />
      <b-list-group>
        <b-list-group-item v-for="(answer, index) in queAnswers" 
        :key="index" @click="selectedAns(index)" >
          {{ answer }}
        </b-list-group-item>
      </b-list-group>
      <!-- <ul>
       <li  v-bind:key="answers" v-for="answers in this.currentQue.incorrect_answers">
         {{answers}}
       </li>
       <li >
         {{this.currentQue.correct_answer}}
       </li>
       </ul> -->

      <b-button variant="success" href="#">Submit</b-button>
      <b-button variant="primary" @click="nextQue">Next</b-button>
    </b-jumbotron>
  </div>
</template>

<script>
export default {
  data(){
    return{
      selectedIndex : null
    }
  },
  props: {
    currentQue: Object,
    nextQue: Function
  },
  methods:{
    selectedAns(index){
        console.log(index)
    }
  },
  computed: {
    queAnswers() {
      let answers = [...this.currentQue.incorrect_answers];
      answers.push(this.currentQue.correct_answer);
      // console.log('hiii',answers)
      return answers;
    }
  },
  mounted(){
console.log(this.currentQue)
  }
};
</script>
<style  scoped>
.list-group-item:hover{
  background-color: #eee;
}
.btn{
  margin-top:15px;
  margin-right: 10px;
}
</style>