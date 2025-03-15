<template>
  <h1>{{  this.questions[1].text }}</h1>
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
    return {};
  }
};
</script>
