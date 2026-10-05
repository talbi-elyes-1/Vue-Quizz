<template>
  <div class="quiz">

    <div class="header">
      <h1>Quiz des formes</h1>
      <p>Score : {{ score }} / 5</p>
    </div>

    <progress :value="progression" max="5"></progress>

    <div v-if="!termine">

      <h2>Question {{ indexQuestion + 1 }} sur 5</h2>

      <img
        :src="questionCourante.image"
        :alt="questionCourante.descriptionImage"
        class="image"
      >

      <h3>{{ questionCourante.texte }}</h3>

      <div class="choix">
        <button
          v-for="(choix, index) in questionCourante.choix"
          :key="index"
          @click="repondre(index)"
          :disabled="reponseChoisie !== null"
        >
          {{ choix }}
        </button>
      </div>

      <p v-if="reponseChoisie !== null" class="message">
        {{ message }}
      </p>

      <button
        v-if="reponseChoisie !== null"
        @click="questionSuivante"
        class="suivant"
      >
        {{ indexQuestion === 4 ? "Voir le résultat" : "Question suivante" }}
      </button>

    </div>

    <div v-else class="resultat">

      <h2>Quiz terminé !</h2>

      <p>Votre score final est :</p>

      <h1>{{ score }} / 5</h1>

      <button @click="rejouer">
        Rejouer
      </button>

    </div>

  </div>
</template>

<script>
export default {

  data() {
    return {

      indexQuestion: 0,
      score: 0,
      reponseChoisie: null,
      termine: false,

      questions: [

        {
          texte: "Quelle forme voyez-vous dans l'image ?",
          image: "/images/triangle.jpg",
          choix: ["Triangle", "Cercle", "Carré"],
          bonneReponse: 0,
          descriptionImage: "Un triangle"
        },

        {
          texte: "Quelle forme voyez-vous dans l'image ?",
          image: "/images/carre.jpg",
          choix: ["Étoile", "Carré", "Rectangle"],
          bonneReponse: 1,
          descriptionImage: "Un carré"
        },

        {
          texte: "Quelle forme voyez-vous dans l'image ?",
          image: "/images/cercle.jpg",
          choix: ["Cercle", "Triangle", "Rectangle"],
          bonneReponse: 0,
          descriptionImage: "Un cercle"
        },

        {
          texte: "Quelle forme voyez-vous dans l'image ?",
          image: "/images/etoile.jpg",
          choix: ["Carré", "Triangle", "Étoile"],
          bonneReponse: 2,
          descriptionImage: "Une étoile"
        },

        {
          texte: "Quelle forme voyez-vous dans l'image ?",
          image: "/images/rectangle.jpg",
          choix: ["Rectangle", "Cercle", "Étoile"],
          bonneReponse: 0,
          descriptionImage: "Un rectangle"
        }

      ]

    }
  },

  computed: {

    questionCourante() {
      return this.questions[this.indexQuestion]
    },

    progression() {
      if (this.reponseChoisie !== null) {
        return this.indexQuestion + 1
      }

      return this.indexQuestion
    },

    message() {
      if (this.reponseChoisie === this.questionCourante.bonneReponse) {
        return "Bonne réponse !"
      }

      return "Mauvaise réponse !"
    }

  },

  methods: {

    repondre(index) {

      if (this.reponseChoisie !== null) {
        return
      }

      this.reponseChoisie = index

      if (index === this.questionCourante.bonneReponse) {
        this.score++
      }

    },

    questionSuivante() {

      if (this.indexQuestion < 4) {

        this.indexQuestion++
        this.reponseChoisie = null

      } else {

        this.termine = true

      }

    },

    rejouer() {

      this.indexQuestion = 0
      this.score = 0
      this.reponseChoisie = null
      this.termine = false

    }

  }

}
</script>

<style>

* {
  box-sizing: border-box;
}

body {
  margin: 0;
  font-family: Arial, sans-serif;
}

.quiz {
  max-width: 700px;
  margin: 40px auto;
  padding: 25px;
  text-align: center;
}

.header {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.header p {
  font-weight: bold;
}

progress {
  width: 100%;
  height: 20px;
  margin: 20px 0;
}

.image {
  width: 250px;
  height: 200px;
  object-fit: contain;
  margin: 20px;
}

.choix {
  display: flex;
  justify-content: center;
  gap: 10px;
  flex-wrap: wrap;
}

button {
  padding: 12px 20px;
  border: none;
  border-radius: 6px;
  cursor: pointer;
  font-size: 16px;
}

button:disabled {
  cursor: not-allowed;
  opacity: 0.6;
}

.suivant {
  margin-top: 20px;
}

.message {
  font-weight: bold;
  font-size: 18px;
}

.resultat {
  margin-top: 50px;
}

.resultat h1 {
  font-size: 50px;
}

</style>