<template>
  <div>
    <h1>{{  questions[question].text }}</h1>
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
