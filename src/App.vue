<template>
  <Navbar />
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
import Navbar from "./components/Navbar";

export default {
  data() {
    return {
      questions: []
    };
  },
  name: "App",
  components: {
    QuestionBox,
    Navbar
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
