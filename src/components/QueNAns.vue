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

      <b-button variant="success" href="#">Submit</b-button>
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
      shuffeldAns :[] //use for shuffled ans
    }
  },
  props: {
    currentQue: Object,
    nextQue: Function
  },
  // watch changes on props
  //make a method currentQue() so when currentQue comes 
  //and ans will be shuffled every time. this method stop shuffling to watch over on props 
  watch:{
      currentQue(){
        this.selectedIndex = null;
        this.shuffleAns();
      }
  },
  methods:{
    selectedAns(index){
      this.selectedIndex = index;
      console.log(index);
    },
    shuffleAns(){
      let answers = [...this.currentQue.incorrect_answers, this.currentQue.correct_answer];
      //console.log(answers)
     //for shuffling ans use random method, forloop or JS library is lodash. here use lodash
      //lodash lib use _ for using any file here use shuffle.js file for shuffling
      this.shuffeldAns = _.shuffle(answers)
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