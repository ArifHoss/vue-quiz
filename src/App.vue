<template>
  <div id="app">
    <Quiz @quiz-completed="handleQuizCompleted" :key="quizKey" />
    <Modal
        v-show="showModal"
        header="Congratulations!"
        subheader="You've completed your Quiz!"
        v-bind:quizScore="quizScore"
        @reload="updateQuiz"
        @close="showModal = false"
    />

    <footer>
      <p id="createdBy">
        created by <a href="https://www.linkedin.com/in/arif-hossain-92b438206/" target="_blank">Arif Hossain</a>
        <a href="https://www.linkedin.com/in/karin-ismael-589285157/" target="_blank"> Karin Ismael, </a>
        <a href="#"> Jonathan Lissman & </a>
        <a href="#"> Tobias Ekman </a>
      </p>
    </footer>
  </div>
</template>

<script>
import Quiz from "@/components/Quiz.vue";
import Modal from "@/components/Modal";

export default {
  name: "App",
  components: {
    Quiz,
    Modal,
  },
  data() {
    return {
      quizKey: 0,
      showModal: false,
      quizScore: {
        allQuestions: 0,
        answeredQuestions: 0,
        correctlyAnsweredQuestions: 0,
      },
    };
  },
  methods: {
    handleQuizCompleted(score) {
      this.quizScore = score;
      this.showModal = true;
    },
    updateQuiz() {
      this.showModal = false;
      this.quizKey++;
    },
  },
};
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
}

#app {
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica,
    Arial, sans-serif, "Apple Color Emoji", "Segoe UI Emoji", "Segoe UI Symbol";
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

footer {
  position: fixed;
  bottom: 0;
  padding: 0.5rem 1rem;
  width: 100%;
  font-size: 0.7rem;
  background-color: rgb(102, 255, 166);
}

#createdBy {
  float: right;
}
</style>
