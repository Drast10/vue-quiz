<template>
  <div id="app">
    <b-container class="bv-example-row">
     <b-row>
    <b-col sm="6" offset="3">  
    <QuestionBox /> 
    </b-col>
  </b-row>
</b-container>
  
  </div>
</template>

<script>

// import Header from './components/Header';
import QuestionBox from './components/QuestionBox';

export default {
  name: 'app',
  components: {
   
    // Header,
    QuestionBox
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
