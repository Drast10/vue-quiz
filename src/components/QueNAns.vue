<template>
  <div>
    <b-jumbotron class="question-box-container">

    <template>
     {{this.currentQue.question}}
    </template>

    <hr class="my-4">
    <p>
     <!-- list of answers
     {{this.currentQue.question}} -->
     <ul>
       <li  v-bind:key="answers" v-for="answers in this.currentQue.incorrect_answers">
         {{answers}}
       </li>
       <li >
         {{this.currentQue.correct_answer}}
       </li>
       </ul>
    </p>
    <b-button variant="success" href="#">Submit</b-button>
      <b-button variant="primary" @click="nextQue">Next</b-button>
  </b-jumbotron>
  </div>
</template>

<script>
export default {
  props:{
    currentQue : Object,
    nextQue : Function
  }
}
</script>