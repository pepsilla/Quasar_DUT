<template>
  <div>
      <p class="caption" v-for="prequestion in PREGUNTAS" >
          {{getTittle(prequestion)}}<br>
          <app-question-answers v-bind:data="{prequestion}"/></p>
  </div>
</template>

<script>
import answerForm from './answer.vue'
export default {
  methods: {
    getTittle (prequest) {
      return (prequest.pregunta)
    }
  },
  components: {
    'app-question-answers': answerForm
  },
  data () {
    return {
      PREGUNTAS: [
        {
          pregunta: 'Cuerpo de la pregunta - 1 -',
          RESPUESTAS: [
            {
              respuesta: 'Cuerpo de la respuesta - 1.1 -',
              isTrue: true,
              isSelected: true,
              feedback: 'Enhorabuena, es la respuesta acertada'
            },
            {
              respuesta: 'Cuerpo de la respuesta - 1.2 -',
              isTrue: false,
              isSelected: true,
              feedback: 'Revisa el material de apoyo 1.2'
            },
            {
              respuesta: 'Cuerpo de la respuesta - 1.3 -',
              isTrue: false,
              isSelected: false,
              feedback: 'Revisa el material de apoyo 1.3'
            },
            {
              respuesta: 'Cuerpo de la respuesta - 1.4 -',
              isTrue: false,
              isSelected: false,
              feedback: 'Revisa el material de apoyo 1.4'
            }
          ]
        },
        {
          pregunta: 'Cuerpo de la pregunta - 2 -',
          RESPUESTAS: [
            {
              respuesta: 'Cuerpo de la respuesta - 2.1 -',
              isTrue: false,
              isSelected: false,
              feedback: 'Revisa el material de apoyo 2.1'
            },
            {
              respuesta: 'Cuerpo de la respuesta - 2.2 -',
              isTrue: true,
              isSelected: false,
              feedback: 'Enhorabuena, es la respuesta acertada'
            },
            {
              respuesta: 'Cuerpo de la respuesta - 2.3 -',
              isTrue: false,
              isSelected: false,
              feedback: 'Revisa el material de apoyo 2.3'
            },
            {
              respuesta: 'Cuerpo de la respuesta - 2.4 -',
              isTrue: false,
              isSelected: false,
              feedback: 'Revisa el material de apoyo 2.4'
            }
          ]
        },
        {
          pregunta: 'Cuerpo de la pregunta - 3 -',
          RESPUESTAS: [
            {
              respuesta: 'Cuerpo de la respuesta - 3.1 -',
              isTrue: false,
              isSelected: false,
              feedback: 'Revisa el material de apoyo 3.1'
            },
            {
              respuesta: 'Cuerpo de la respuesta - 3.2 -',
              isTrue: false,
              isSelected: true,
              feedback: 'Revisa el material de apoyo 3.2'
            },
            {
              respuesta: 'Cuerpo de la respuesta - 3.3 -',
              isTrue: true,
              isSelected: false,
              feedback: 'Enhorabuena, es la respuesta acertada'
            },
            {
              respuesta: 'Cuerpo de la respuesta - 3.4 -',
              isTrue: false,
              isSelected: false,
              feedback: 'Revisa el material de apoyo 3.4'
            }
          ]
        },
        {
          pregunta: 'Cuerpo de la pregunta - 4 -',
          RESPUESTAS: [
            {
              respuesta: 'Cuerpo de la respuesta - 4.1 -',
              isTrue: false,
              isSelected: false,
              feedback: 'Revisa el material de apoy 4.1o'
            },
            {
              respuesta: 'Cuerpo de la respuesta - 4.2 -',
              isTrue: false,
              isSelected: false,
              feedback: 'Revisa el material de apoyo 4.2'
            },
            {
              respuesta: 'Cuerpo de la respuesta - 4.3 -',
              isTrue: false,
              isSelected: false,
              feedback: 'Revisa el material de apoyo 4.3'
            },
            {
              respuesta: 'Cuerpo de la respuesta - 4.4 -',
              isTrue: true,
              isSelected: false,
              feedback: 'Enhorabuena, es la respuesta acertada'
            }
          ]
        }
      ]
    }
  }
}
</script>

<style>
</style>
