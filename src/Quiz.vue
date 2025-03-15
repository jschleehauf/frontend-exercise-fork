<template>
  <div class="card">
    <h1>Question {{question + 1}}</h1>
    <p>{{  questions[question].text }}</p>
    <button @click="question++">Next</button> 
  </div>
</template>

<script>
export default {
  props: {
    questions: {
      type: Array,
      required: true
    }
  },
  data() {
    return {
      question : 0
    };
  },
  methods: {
    
  }
};
</script>

<style>
  .card {
    border: 1px solid rgb(59, 192, 101);
    border-radius: 8px;
    padding: 16px;
    margin: auto;
    margin-top: 20px;
    box-shadow: 2px 2px 10px rgb(0, 0, 0, 0.1);
    background-color: #c0dcc7;
    width: 75vw;
    
  }
  .card p{
    font-size: 18px;
  }
  .card h1 {
    font-size: 20px;
    margin-top: 4px;

  }
</style>