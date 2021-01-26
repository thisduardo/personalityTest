<template>
  <div class="container-sm">
    <div>
      <div class-col sm="6" offset="3">
        <QuestionBox />
      </div>
    </div>
  </div>
</template>

<script>
import QuestionBox from "./components/QuestionBox";

export default {
  data() {
    return {
      questions: []
    };
  },
  name: "App",
  components: {
    QuestionBox
  },
  mounted() {}
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  background: #e9ecef;
  height: auto;
}
</style>
