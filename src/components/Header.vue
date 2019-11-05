<template>
  <div>
    <b-nav tabs>
    <b-nav-item disabled>Question Quiz</b-nav-item>
    <b-nav-item disabled>Counter: {{numCorrect}}/{{numTotal}}</b-nav-item>
  </b-nav>
  </div>
</template>

<script>
export default {
   props: {
    numCorrect: Number,
    numTotal: Number
  },
}
</script>

<style scoped>
.nav{
  font-weight: 500;
  font-size: 20px;
}
</style>