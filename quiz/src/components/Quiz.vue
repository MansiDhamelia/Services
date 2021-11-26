

<template>
  <div class="container">
    <h1>Quiz...</h1>

    <div v-for="(option, index) in questions" :key="index">
      <h3>{{ option.questionText }}</h3>
      <ol>
        <li v-for="responce in option.answerOptions" :key="responce">
          <label>
            <input
              type="radio"
              v-bind:value="responce.isCorrect"
              v-bind:name="index"
              @change="get(responce.isCorrect)"
            />{{ responce.answerText }}
          </label>
        </li>
      </ol>
    </div>
    <button class="btn_next" @click="next">Submit</button>
    <div v-if="isActive">
      <p>your score is : {{ score }} / {{ questions.length }}</p>
    </div>
  </div>
</template>

 <script>
export default {
  data() {
    return {
      currentQuestion: 0,
      score: 0,
      isActive: false,
      questions: [
        {
          questionText: "Which company invented Vue.js?",
          answerOptions: [
            { answerText: "Facebook", isCorrect: false },
            { answerText: "Oracle", isCorrect: false },
            { answerText: "Twitter", isCorrect: false },
            { answerText: "Google", isCorrect: true },
          ],
        },

        {
          questionText:
            " Which of the following data binding interpolation is also known as Mustache syntax?",
          answerOptions: [
            { answerText: "{{}}", isCorrect: true },
            { answerText: "v-on", isCorrect: false },
            { answerText: "v-model", isCorrect: false },
            { answerText: "[]", isCorrect: false },
          ],
        },
        {
          questionText:
            " Which of the following is the correct syntax to use for loop in Vue.js?",
          answerOptions: [
            { answerText: "Vfor", isCorrect: false },
            { answerText: "v-For", isCorrect: false },
            { answerText: "v-for", isCorrect: true },
            { answerText: "for", isCorrect: false },
          ],
        },
        {
          questionText:
            "Which of the following is the advantage of using Vue.js?",
          answerOptions: [
            { answerText: "Vue.js is very small in size.", isCorrect: false },
            {
              answerText:
                "The documentation of Vue.js is very easy and comprehensive.",
              isCorrect: false,
            },
            { answerText: "Vue.js is flexible in nature.", isCorrect: false },
            { answerText: "All of the above.", isCorrect: true },
          ],
        },
      ],
    };
  },

  methods: {
    get(isCorrect) {
      if (isCorrect) {
        this.score++;
      }
      console.log(this.score);
    },
    next() {
      this.isActive = true;
    },
  },
};
</script>

<style scoped>

.container {
  margin-left: 300px;
  text-align: start;
}
.btn_next {
  height: 30px;
}
p {
  font-size: large;
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Oxygen,
    Ubuntu, Cantarell, "Open Sans", "Helvetica Neue", sans-serif;
}
</style>


