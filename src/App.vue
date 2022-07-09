<template>
  <h1>Math Quiz</h1>
  <PickingQuiz @goBack="ClearOperator" v-if="operator" :operator="operator" />
  <OperatorSelect v-if="!operator" @SelectOperator="SelectOperator" />
</template>

<script>
import OperatorSelect from "./components/OperatorSelect.vue";
import PickingQuiz from "./components/PickingQuiz.vue";
export default {
  name: "App",
  data() {
    return {
      operator: null,
    };
  },
  methods: {
    SelectOperator(op) {
      this.operator = op;
    },
    ClearOperator() {
      this.operator = null;
    },
  },
  components: { OperatorSelect, PickingQuiz },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
button {
  padding: 10px;
  width: 160px;
  height: 80;
  margin-right: 10px;
  margin-top: 10px;
  background-color: #10aeb2;
  color: white;
  font-size: 24px;
  cursor: pointer;
  border: none;
  border-radius: 10px;
}
</style>
