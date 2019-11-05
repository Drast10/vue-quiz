<template>
  <div>
    <b-jumbotron class="question-box-container">
      <template>
        {{ this.currentQue.question }}
      </template>

      <hr class="my-4" />
      <b-list-group>
        <b-list-group-item v-for="(answer, index) in queAnswers" 
        :key="index" 
        @click.prevent="selectedAns(index)" 
        :class="[selectedIndex === index ? 'selected':'']">
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

      <b-button variant="success" 
      @click="submitAns"
      :disabled="selectedIndex === null || userAnswered">
      Submit
      </b-button>
      <b-button variant="primary" @click="nextQue">Next</b-button>
    </b-jumbotron>
  </div>
</template>

<script>
import _ from 'lodash'

export default {
  data(){
    return{
      selectedIndex : null,
      correctIndex:null,
      shuffeldAns :[], //use for shuffled ans
      userAnswered: false, //check user selected or not for disabaling button condition
    }
  },
  props: {
    currentQue: Object,
    nextQue: Function,
    increment: Function
  },
  // watch changes on props
  //make a method currentQue() so when currentQue comes 
  //and ans will be shuffled every time. this method stop shuffling to watch over on props 
  watch:{
      currentQue:{
        immediate:true,
        handler(){
        this.selectedIndex = null;
        this.userAnswered = false;
        this.shuffleAns();
        }
      }
  },
  methods:{
    selectedAns(index){
      this.selectedIndex = index;
      console.log(index);
    },
    //shuffleAns not shuffled 1st question to load so for that making shuffle two ways 
    //1. use shuffledAns() in mounted lifecycle hooks to load data 
    //2. watch use currentque as object and imidiate:true so it when the load data it's immidiatly works same for first to last with using handler()
    shuffleAns(){
      let answers = [...this.currentQue.incorrect_answers, this.currentQue.correct_answer];
      //console.log(answers)
     //for shuffling ans use random method, forloop or JS library is lodash. here use lodash
      //lodash lib use _ for using any file here use shuffle.js file for shuffling
      this.shuffeldAns = _.shuffle(answers)
    },
    submitAns(){
      let isCorrect = false;
      if (this.selectedIndex === this.correctIndex) {
        isCorrect = true;
      }
      this.userAnswered = true;
      //increment number of correct ans in header
      this.increment(isCorrect);

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
  //this.shuffleAns();
  }
};
</script>
<style  scoped>
.list-group-item:hover{
  background-color: #eee;
  cursor: pointer;
}
.btn{
  margin-top:15px;
  margin-right: 10px;
}
.selected{
  background-color: lightblue;
}
.correctAns{
  background-color: lightgreen;
}
.wrongAns{
  background-color: pink;
}
</style>