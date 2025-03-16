<template>
  <div>
    <div class="card" v-if="!quizEnded">
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
    <!-- If the quiz has ended display all questions and corresponding answers -->
    <div class="card" v-if="quizEnded">
      <h2>Quiz Results</h2>
      <div>
        <div v-for="(question, index) in questions" :key="index">
          <h3>{{ "Question " + (index + 1) }}</h3>
          <h4>{{ question.text }}</h4>
          <p>Your answer: {{  getSelectedAnswer(index) }}</p>
        </div>
      </div>
    </div>
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
      questionIndex : 0,            // Position in questions list.
      isQuestionAnswered : false,   // State for the current question of quiz if a user has made a selection.
      selectedAnswer: null,         // Holds the value of the selected radio button.
      userResponses: [],            // Holds user response for each question.
      quizEnded : false,            // True if the quiz is complete.
    };
  },
  methods: {
    nextQuestion() {
      // Ensure the userResponses array is initialized
      if (!this.userResponses) {
      this.userResponses = [];      // Initialize the array if it's null
      }
      
      this.userResponses.push(this.selectedAnswer); // User selection is added to userResponses array
      // this.console.log(this.userResponses);      // Check the response array
      
      if (this.questionIndex < this.questions.length - 1) {   // Make sure array is in bounds
        this.questionIndex++;          // Increment the index to move to the next question.
        this.selectedAnswer = null;    // Reset the value held so that the next question is not answered.
      } else {                          // Reached end of questions
        this.quizEnded = true;
        this.questionIndex = 0;
      }
    },
    getSelectedAnswer(index) {
      return this.userResponses[index]; // Return the user response which corresponds to the question
    }
  },
  computed: {
    console: () => console,
    window: () => window,
  },
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