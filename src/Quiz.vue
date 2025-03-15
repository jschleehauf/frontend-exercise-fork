<template>
  <div class="card">
    <h1>Question {{questionIndex + 1}}</h1>
    <p>{{  questions[questionIndex].text }}</p>
    <div v-for="(option, index) in questions[questionIndex].answers" v-bind:key=index>
      <label>
        <input type="radio" :value="option" v-model="selectedAnswer"/>
        {{ option }}
      </label>
    </div>
    <button @click="nextQuestion" :disabled="selectedAnswer === null">Next</button>
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
      questionIndex : 0,            // Position of in questions list.
      isQuestionAnswered : false,   // State for the current question of quiz if a user has made a selection.
      selectedAnswer: null,         // Holds the value of the selected radio button.
      quizEnded : false,            // True if the quiz is complete.
    };
  },
  methods: {
    nextQuestion() {
      this.questionIndex++;          // Increment the index to move to the next question.
      this.selectedAnswer = null;         // Reset the value held so that the next question is not answered.
    }
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