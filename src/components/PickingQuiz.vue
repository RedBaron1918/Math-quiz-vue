<template>
  <div v-if="isStarted">
    <h4>{{ opleft }} {{ operator }} {{ opright }}</h4>
  </div>

  <div v-if="!isStarted">
    <button @click="startQuiz">Start</button>
  </div>
  <button
    @click="SelectAnswer(answer)"
    v-for="(answer, index) in answers"
    :key="index"
  >
    {{ answer }}
  </button>
  <br />
  <button @click="$emit('goBack')">Back</button>
</template>

<script>
export default {
  props: ["operator"],

  data() {
    return {
      isStarted: false,
      opleft: null,
      opright: null,
      answers: [],
      correctAnswer: null,
    };
  },
  methods: {
    SelectAnswer(answer) {
      if (answer === this.correctAnswer) {
        this.startQuiz();
      } else {
        alert("Try again");
      }
    },
    startQuiz() {
      this.isStarted = true;
      this.opleft = Math.floor(Math.random() * 13) + 1;
      this.opright = Math.floor(Math.random() * 13) + 1;

      const methods = {
        "+": (a, b) => a + b,
        "-": (a, b) => a - b,
        "/": (a, b) => a / b,
        "*": (a, b) => a * b,
      };

      const methodstoUse = methods[this.operator];
      this.answers = [];
      this.answers.push(methodstoUse(this.opleft, this.opright + 4));
      this.answers.push(methodstoUse(this.opleft - 3, this.opright));
      this.answers.push(methodstoUse(this.opleft, this.opright + 5));
      this.answers.push(methodstoUse(this.opleft - 5, this.opright));
      this.answers.push(methodstoUse(this.opleft, this.opright - 2));

      const rightAnswer = methodstoUse(this.opleft, this.opright);
      this.answers[Math.floor(Math.random() * this.answers.length)] =
        rightAnswer;
      this.correctAnswer = rightAnswer;
    },
  },
};
</script>

<style></style>
