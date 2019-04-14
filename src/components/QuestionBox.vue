<template>
  <div>
    <b-jumbotron lead="Bootstrap 4 Components for Vue.js 2">
      <template slot="lead">{{ currentQuestion.question }}</template>

      <hr class="my-4">

      <b-list-group>
        <b-list-group-item
          v-for="(answer, index) in answers"
          :key="index"
          @click="selectAnswer"
        >{{ answer }}</b-list-group-item>
      </b-list-group>

      <b-button variant="primary" href="#">Submit</b-button>
      <b-button @click="next" variant="success" href="#">Next</b-button>
    </b-jumbotron>
  </div>
</template>

<script>
export default {
  props: {
    currentQuestion: Object,
    next: Function
  },
  data() {
    return {
      selectedIndex: null
    };
  },
  computed: {
    answers() {
      return [
        ...this.currentQuestion.incorrect_answers,
        this.currentQuestion.correct_answer
      ];
    }
  },
  methods: {
    selectAnswer(index) {
      this.selectedIndex = index;
    }
  }
};
</script>

<style scoped>
.list-group {
  margin-bottom: 2em;
}

.list-group-item {
  cursor: pointer;
}

.list-group-item:hover {
  background-color: rgb(203, 225, 253);
}

.selected {
  font-weight: bold;
  color: white;
  background-color: rgb(50, 138, 252);
}

.correct {
  font-weight: bold;
  color: rgb(112, 255, 131);
  background-color: rgb(200, 255, 200);
}

.wrong {
  font-weight: bold;
  color: rgb(238, 52, 52);
  background-color: rgb(255, 200, 200);
}
</style>
