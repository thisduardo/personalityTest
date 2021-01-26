<template>
  <div class="jumbotron jumbotron-fluid">
    <div class="container-fluid">
      <div v-show="showEmail">
        <h4>Qual é seu e-mail?</h4>
        <input
          class="form-control smr-sm-2 my-4"
          type="email"
          placeholder="Digite seu e-mail"
          aria-label="Pesquisar"
        />
        <b-button class="btn btn-success" href="#" @click="nextStart"
          >Proximo</b-button
        >
      </div>
      <div v-show="showQuestions" v-if="!isEnd">
        <p>Questões {{ currentQuestion + 1 }} de {{ questions.length }}</p>
        <h4>{{ questions[currentQuestion] }}</h4>
        <div>
          <br class="my-4" />
          <ul class="list-group">
            <li
              class="list-group-item abc justify-content-between"
              v-for="(answer, index) in answers"
              v-bind:key="answer.index"
              @click="selectAnswer(index)"
              :class="[selectedIndex === index ? 'selected' : '']"
            >
              {{ answer }}
            </li>
          </ul>

          <b-button class="btn btn-primary" href="#" @click="back"
            >Voltar</b-button
          >
          <b-button class="btn btn-success" href="#" @click="next"
            >Proximo</b-button
          >
        </div>
      </div>
      <div v-else>FIM</div>
    </div>
  </div>
</template>

<script>
export default {
  props: {},
  data() {
    return {
      show: true,
      showQuestions: false,
      showEmail: true,
      selectedIndex: null,
      currentQuestion: 0,
      questions: [
        "Você acha difícil se apresentar para outras pessoas.",
        "Você tenta responder aos seus e-mails o mais rapidamente possível e não suporta uma caixa de entrada bagunçada",
        "Você fica frequentemente tão absorto em seus pensamentos que ignora ou esquece do seu entorno",
        "Você permanece relaxado e concentrado mesmo sob pressão.",
        "Geralmente, você não inicia conversas.",
        "Você raramente faz alguma coisa por pura curiosidade.",
        "Você se sente superior às outras pessoas."
      ],
      answers: ["Muito provavel", "Pouco provavel"]
    };
  },
  computed: {
    isEnd() {
      return this.questions.length <= this.currentQuestion;
    }
  },
  methods: {
    selectAnswer(index) {
      this.selectedIndex = index;
    },
    nextStart() {
      this.showQuestions = true;
      this.showEmail = false;
    },
    next() {
      if (this.index < this.questions.length - 1) {
        this.correctAnswers++;
      }
      this.currentQuestion++;
      this.index++;
      this.selectedIndex = null;
    },
    back() {
      this.currentQuestion = this.currentQuestion - 1;
    }
  }
};
</script>

<style scoped>
.list-group {
  margin-bottom: 15px;
}
.list-group-item:hover {
  background: #eeeeee;
  cursor: pointer;
}

.btn {
  margin: 0 5px;
}

.selected {
  background: rgb(96, 96, 231);
  color: white;
  transition: color 0.1s ease;
}

.selected:hover {
  background: rgb(96, 96, 231);
  color: white;
}

.abc {
  -webkit-transition: all 200ms ease-in;
  -ms-transition: all 200ms ease-in;
  -moz-transition: all 200ms ease-in;
  transition: all 200ms ease-in;
}
.abc:hover {
  -webkit-transition: all 200ms ease-in;
  -webkit-transform: scale(0.9);
  -webkit-transform: scale(1.1);
  -ms-transition: all 200ms ease-in;
  -ms-transform: scale(0.9);
  -ms-transform: scale(1.1);
  -moz-transition: all 200ms ease-in;
  -moz-transform: scale(0.9);
  -moz-transform: scale(1.1);
  transition: all 200ms ease-in;
  transform: scale(0.9);
  transform: scale(1.1);
}
</style>
