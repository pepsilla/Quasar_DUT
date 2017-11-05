<template>
  <div>
    <h1>Test de Cuestionario</h1>
    <p v-if="getTestMainisOk()">
      <q-alert type="positive" color="positive" dismissible style="margin-bottom: 1.5rem">
        ¡Perfecto!, Questionario superado.
      </q-alert>
    </p>
    <p v-else>
      <q-alert type="negative" color="negative" dismissible style="margin-bottom: 1.5rem">
        Revisa todas las preguntas.
      </q-alert>
    </p>
    <p class="caption" v-for="prequestion, index in evaluacion.PREGUNTAS" >
      <b>{{getTittle(prequestion)}}</b>
      <q-list>
        <p v-if="getQuestionIsOk(index)">
          <q-alert type="positive" color="positive" dismissible style="margin-bottom: 1.5rem">
            ¡Perfecto!, revisa todas las preguntas.
          </q-alert>
        </p>
        <p v-else>
          <q-alert type="negative" color="negative" dismissible style="margin-bottom: 1.5rem">
            Revisa tus respuestas a esta pregunta.
          </q-alert>
        </p>  
               
        <p v-for="answer in prequestion.RESPUESTAS">
          <q-item >
            <q-item-side>
              <q-checkbox v-model="answer.isSelected" @change="checkSelected(answer)"/>
            </q-item-side>
            <q-item-main>
              <q-item-tile title><b><i>{{answer.respuesta}}</i></b><p v-if="getFeedbackTrue(answer)"> 
                <q-alert type="positive" color="positive" dismissible style="margin-bottom: 1.5rem">
                  {{answer.feedback}}
                </q-alert></p>
                <p v-else-if="getFeedbackFalse(answer)">
                  <q-alert type="negative" color="negative" dismissible style="margin-bottom: 1.5rem">
                  {{answer.feedback}}
                </q-alert></p>
                </q-item-tile>
            </q-item-main>
          </q-item>
        </p>
      </q-list>
    </p>
  </div>
</template>

<script>
// import FQuestion from './question.vue'
import {
  QList,
  QItem,
  QItemSide,
  QItemMain,
  QItemTile,
  QCheckbox,
  QAlert
} from 'quasar'
export default {
  components: {
    QList,
    QItem,
    QItemSide,
    QItemMain,
    QItemTile,
    QCheckbox,
    QAlert
  },
  methods: {
    getTestMainisOk () {
      var questions = this.evaluacion.PREGUNTAS
      for (var question in questions) {
        var value = this.evaluacion.PREGUNTAS[question]
        // console.log(value.isOk, question)
        if (!value.isOk) return false
      }
      return true
    },
    getQuestionIsOk (index) {
      // console.log('index: ' + index)
      var answers = this.evaluacion.PREGUNTAS[index].RESPUESTAS
      for (var answer in answers) {
        var value = this.evaluacion.PREGUNTAS[index].RESPUESTAS[answer]
        // console.log(value.isTrue, value.isSelected)
        if (value.isTrue !== value.isSelected) {
          this.evaluacion.PREGUNTAS[index].isOk = false
          return false
        }
      }
      this.evaluacion.PREGUNTAS[index].isOk = true
      return true
    },
    getIsSelected (answer) {
      console.log('answerSelected: ' + answer.isSelected)
      return (answer.isSelected)
    },
    getFeedbackTrue (answer) {
      if (answer.isTrue) {
        if (answer.isSelected) {
          return true
        }
      }
      return false
    },
    getFeedbackFalse (answer) {
      if (!answer.isTrue) {
        if (answer.isSelected) {
          return true
        }
      }
      return false
    },
    getTittle (prequest) {
      return (prequest.pregunta)
    },
    checkSelected (answer) {
      // console.log(answer.respuesta, answer.isSelected)
    }

  },
  data () {
    return {
      checked: false,
      evaluacion: {
        numPreguntas: 10,
        tiempo: 120,
        id: 'TOKEN_0F2A3F95D1AB',
        PREGUNTAS: [
          {
            pregunta: 'Cuerpo de la pregunta - 1 -',
            isOk: false,
            RESPUESTAS: [
              {
                respuesta: 'Cuerpo de la respuesta - 1.1 -',
                isTrue: true,
                isSelected: false,
                feedback: 'Enhorabuena, es la respuesta acertada'
              },
              {
                respuesta: 'Cuerpo de la respuesta - 1.2 -',
                isTrue: false,
                isSelected: false,
                feedback: 'Revisa el material de apoyo 1.2'
              },
              {
                respuesta: 'Cuerpo de la respuesta - 1.3 -',
                isTrue: true,
                isSelected: false,
                feedback: 'Enhorabuena, es la respuesta acertada'
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
            isOk: false,
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
            isOk: false,
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
                isSelected: false,
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
            isOk: false,
            RESPUESTAS: [
              {
                respuesta: 'Cuerpo de la respuesta - 4.1 -',
                isTrue: false,
                isSelected: false,
                feedback: 'Revisa el material de apoyo 4.1'
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
}
</script>

<style>
</style>
