<script setup lang="ts">
import { computed, ref } from "vue";

const questionsData = [
  {
    question: "O que é o Vue.js?",
    answer: 0,
    options: [
      "Um framework de front-end",
      "Uma biblioteca",
      "Um fabricante de sorvetes",
      "Um sistema operacional",
      "Uma rede social",
    ],
    selected: null,
  },
  {
    question:
      "O que o Vue.js usa para renderizar componentes de forma declarativa?",
    answer: 2,
    options: [
      "HTML puro",
      "Templates em Markdown",
      "Template syntax",
      "JavaScript cru",
      "CSS",
    ],
    selected: null,
  },
  {
    question: "Qual é a arquitetura principal do Vue.js?",
    answer: 2,
    options: [
      "Modelo-Visão-Controle (MVC)",
      "Modelo-Visão-Modelo (MVM)",
      "Modelo-Visão-Componente (MVC)",
      "Modelo-Componente-Visão (MCV)",
      "Nenhuma das anteriores",
    ],
    selected: null,
  },
  {
    question: "O que são componentes em Vue.js?",
    answer: 2,
    options: [
      "Elementos HTML padrão",
      "Funções JavaScript globais",
      "Blocos de construção reutilizáveis de interface de usuário",
      "Variáveis em JavaScript",
      "Elementos CSS",
    ],
    selected: null,
  },
  {
    question:
      "Qual diretiva Vue.js é usada para renderizar elementos condicionalmente com base em uma expressão?",
    answer: 1,
    options: ["v-show", "v-if", "v-for", "v-switch", "v-conditional"],
    selected: null,
  },
  {
    question:
      "Qual diretiva Vue.js é usada para criar loops e renderizar uma lista de elementos?",
    answer: 2,
    options: ["v-show", "v-if", "v-for", "v-while", "v-repeat"],
    selected: null,
  },
  {
    question:
      "Como as propriedades computadas (computed properties) são diferentes das propriedades de dados (data properties) em Vue.js?",
    answer: 1,
    options: [
      "As propriedades computadas são armazenadas no servidor, enquanto as propriedades de dados são armazenadas no cliente.",
      "As propriedades computadas são usadas para cálculos dinâmicos e são armazenadas em cache, enquanto as propriedades de dados são estáticas.",
      "As propriedades de dados são usadas para cálculos dinâmicos e as propriedades computadas são estáticas.",
      "As propriedades computadas não podem ser acessadas em templates Vue.",
      "As propriedades de dados são usadas apenas para armazenar números inteiros.",
    ],
    selected: null,
  },
  {
    question: "Qual é a função da diretiva v-bind em Vue.js?",
    answer: 0,
    options: [
      "Ela cria uma ligação bidirecional entre elementos HTML e dados do Vue.",
      "Ela define uma função para manipular eventos de clique.",
      "Ela importa dados de um arquivo JSON externo.",
      "Ela cria uma animação de transição entre elementos.",
      "Ela cria um elemento HTML vazio.",
    ],
    selected: null,
  },
  {
    question:
      "Qual das seguintes opções NÃO faz parte da arquitetura oficial Vue.js?",
    answer: 2,
    options: ["Vue Router", "VueX", "Vue Server", "Vue Devtools", "Vue CLI"],
    selected: null,
  },
  {
    question: "Qual é a função do Vue Router em uma aplicação Vue.js?",
    answer: 3,
    options: [
      "Gerenciar o estado global da aplicação.",
      "Manipular a renderização de componentes.",
      "Fornecer um servidor de back-end para a aplicação.",
      "Roteamento de páginas e navegação.",
      "Definir a estrutura do banco de dados.",
    ],
    selected: null,
  },
  {
    question: "O que é o VueX em uma aplicação Vue.js?",
    answer: 2,
    options: [
      "Uma ferramenta de depuração para Vue.js.",
      "Uma biblioteca de gráficos e visualização de dados.",
      "Um sistema de gerenciamento de estado centralizado.",
      "Um compilador de templates Vue.",
      "Uma extensão para a criação de páginas AMP.",
    ],
    selected: null,
  },
  {
    question: "Qual é a principal diferença entre Vue.js e React?",
    answer: 1,
    options: [
      "Vue.js é baseado em TypeScript, enquanto React é baseado em JavaScript.",
      "Vue.js é um framework, enquanto React é uma biblioteca.",
      "Vue.js é mantido pelo Facebook, enquanto React é uma iniciativa de código aberto.",
      "Vue.js utiliza a sintaxe JSX, enquanto React utiliza templates.",
      "Não há diferenças significativas entre eles.",
    ],
    selected: null,
  },
  {
    question:
      "Em Vue.js, qual ciclo de vida é acionado quando um componente é criado?",
    answer: 0,
    options: ["created", "mounted", "updated", "destroyed", "initialized"],
    selected: null,
  },
  {
    question: "Qual é o objetivo da diretiva v-model em Vue.js?",
    answer: 3,
    options: [
      "Para criar modelos 3D em elementos HTML.",
      "Para criar gráficos de dados interativos.",
      "Para estilizar elementos HTML com base em dados.",
      "Para estabelecer uma ligação bidirecional entre um campo de entrada e um valor.",
      "Para criar componentes reutilizáveis.",
    ],
    selected: null,
  },
  {
    question: "Qual é o principal objetivo do Vue CLI?",
    answer: 2,
    options: [
      "Para criar aplicativos de desktop multiplataforma.",
      "Para gerar automaticamente documentação para projetos Vue.",
      "Para fornecer um ambiente de desenvolvimento completo e ferramentas para criar, desenvolver e testar aplicativos Vue.",
      "Para criar animações complexas em projetos Vue.",
      "Para configurar servidores web para aplicativos Vue.",
    ],
    selected: null,
  },
  {
    question: "O que é o Vue Single File Component (SFC)?",
    answer: 2,
    options: [
      "Uma página da web com um único arquivo HTML.",
      "Um arquivo de configuração para projetos Vue.",
      "Um arquivo que contém todo o código necessário para um componente Vue, incluindo HTML, JavaScript e CSS.",
      "Um arquivo de metadados para rastrear componentes Vue em um projeto.",
      "Uma ferramenta de compilação para Vue.js.",
    ],
    selected: null,
  },
  {
    question:
      "Qual diretiva Vue.js é usada para criar transições e animações entre elementos?",
    answer: 1,
    options: [
      "v-animate",
      "v-transition",
      "v-effect",
      "v-animate-css",
      "v-animate-transition",
    ],
    selected: null,
  },
  {
    question: "O que é o Vue Devtools?",
    answer: 0,
    options: [
      "Uma ferramenta para depurar e inspecionar aplicativos Vue em tempo real.",
      "Um sistema de controle de versão para projetos Vue.",
      "Uma extensão para navegadores que bloqueia sites com Vue.js.",
      "Um ambiente de desenvolvimento integrado (IDE) específico para Vue.",
      "Um serviço de hospedagem para aplicativos Vue.",
    ],
    selected: null,
  },
];

function selectRandomQuestions(data: any, numQuestions: number) {
  if (numQuestions > data.length) {
    console.error(
      "Número de questões solicitado é maior do que o tamanho do array"
    );
    return [];
  }

  const shuffledData = [...data];
  for (let i = shuffledData.length - 1; i > 0; i--) {
    const j = Math.floor(Math.random() * (i + 1));
    [shuffledData[i], shuffledData[j]] = [shuffledData[j], shuffledData[i]];
  }

  return shuffledData.slice(0, numQuestions);
}

const questions: any = ref(selectRandomQuestions(questionsData, 6));

const quizCompleted = ref(false);
const currentQuestion = ref(0);
const score = computed(() => {
  let value = 0;
  questions.value.map((q: any) => {
    if (q.selected == q.answer) {
      value++;
    }
  });
  return value;
});

const getCurrentQuestion = computed(() => {
  let question: any = questions.value[currentQuestion.value];
  question.index = currentQuestion.value;
  return question;
});

const SetAwswer = (evt: any) => {
  questions.value[currentQuestion.value].selected = evt.target.value;
  evt.target.value = null;
};

const NextQuestion = () => {
  if (currentQuestion.value < questions.value.length - 1) {
    currentQuestion.value++;
  } else {
    quizCompleted.value = true;
  }
};
</script>

<template>
  <main class="app">
    <h1>
      <img src="./assets/vue.svg" alt="VueJs Quiz" /><i
        style="margin-left: -6px; color: #41b883"
        >ue</i
      >
      Quiz
    </h1>

    <section class="quiz" v-if="!quizCompleted">
      <div class="quiz-info">
        <span class="question">{{ getCurrentQuestion.question }}</span>
      </div>

      <div class="options">
        <label
          v-for="(option, index) in getCurrentQuestion.options"
          :key="index"
          :class="`
        option ${
          getCurrentQuestion.selected == index
            ? index == getCurrentQuestion.answer
              ? 'correct'
              : 'wrong'
            : ''
        }
        ${
          getCurrentQuestion.selected != null &&
          index != getCurrentQuestion.selected
            ? 'disabled'
            : ''
        }
        `"
        >
          <input
            type="radio"
            :name="getCurrentQuestion.index"
            :value="index"
            v-model="getCurrentQuestion.selected"
            :disabled="getCurrentQuestion.selected"
            @change="SetAwswer"
          />
          <span>{{ option }}</span>
        </label>
      </div>
      <div class="footer">
        <button @click="NextQuestion" :disabled="!getCurrentQuestion.selected">
          {{
            getCurrentQuestion.index == questions.length - 1
              ? "Concluir"
              : getCurrentQuestion.selected == null
              ? "Selecione a resposta"
              : "Próxima"
          }}
        </button>
      </div>
    </section>
    <section v-else>
      <h2>
        {{
          score >= 4
            ? "Parabéns! Você é um especialista em Vue.js"
            : "Não desista, estude um pouco mais."
        }}
      </h2>
      <p>Você acertou {{ score }} / {{ questions.length }}!</p>
    </section>
  </main>
</template>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: "Montserrat", sans-serif;
}
body {
  background-color: #0f0f0f;
  color: #fff;
  overflow: hidden;
}

.app {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 2rem;
  min-height: 100vh;
}
h1 {
  font-size: 2rem;
  margin-bottom: 2rem;
}
.quiz {
  background-color: #2d2e2e;
  padding: 1rem;
  width: 100%;
  max-width: 640px;
}
.quiz .footer {
  width: 100%;
  display: flex;
  justify-content: end;
}
.quiz-info {
  display: flex;
  justify-content: space-between;
  margin-bottom: 1rem;
}
.quiz-info .question {
  font-size: 1.25rem;
}
.quiz-info .score {
  color: #fff;
  font-size: 1.25rem;
}
.options {
  margin-bottom: 1rem;
}
.option {
  display: block;
  padding: 1rem;
  background-color: #716969;
  margin-bottom: 0.5rem;
  border-radius: 0.5rem;
  cursor: pointer;
}
.option:hover {
  background-color: #504242;
}
.option.correct {
  background-color: #2cce7d;
}
.option.wrong {
  background-color: #ff5a5f;
}
.option:last-of-type {
  margin-bottom: 0;
}
.option.disabled {
  opacity: 0.5;
}
.option input {
  display: none;
}
button {
  appearance: none;
  outline: none;
  border: none;
  cursor: pointer;

  padding: 0.5rem 1rem;
  background-color: #2cce7d;
  color: #fff;
  font-weight: 700;
  text-transform: uppercase;
  font-size: 1.25rem;
  border-radius: 0.5rem;
  min-width: 40%;
}
button:disabled {
  opacity: 0.7;
}

h2 {
  font-size: 1.75rem;
  margin-bottom: 2rem;
  text-align: center;
}
p {
  color: #8f8f8f;
  font-size: 1.25rem;
  text-align: center;
}
</style>
