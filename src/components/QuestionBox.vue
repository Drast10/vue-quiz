<template>
  <div>
    <h4>Category : Computer Science</h4>
     <b-jumbotron class="question-box-container">

    <template v-slot:lead>
     Question
    </template>
    <hr class="my-4">
    <p>
     list of answers
    </p>
    <b-button variant="success" href="#">Submit</b-button>
      <b-button variant="primary" href="#">Next</b-button>
  </b-jumbotron>

  </div>
</template>

<script>
export default {
  mounted(){
    fetch("https://opentdb.com/api.php?amount=10&category=18&type=multiple",)
  }
}
</script>

<style scoped>
h4{
  margin: 15px;
}
</style>