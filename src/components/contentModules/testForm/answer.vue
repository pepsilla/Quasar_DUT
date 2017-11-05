<template>
      <q-list>
        <p v-for="answer in RESPUESTAS">
        <q-item >
          <q-item-side>
            <q-checkbox v-model="answer.isSelected"/>
          </q-item-side>
          <q-item-main>
            <q-item-tile title>{{getAnswer(answer)}}</q-item-tile>
          </q-item-main>
        </q-item>
        </p>
      </q-list>
</template>

<script>
import {
  QList,
  QItem,
  QItemSide,
  QCheckbox,
  QItemMain,
  QItemTile
} from 'quasar'
export default {
  components: {
    QList,
    QItem,
    QItemSide,
    QCheckbox,
    QItemMain,
    QItemTile
  },
  methods: {
    getAnswer (answer) {
      return (answer.respuesta)
    }
  },
  data () {
    return this.data
  }
}
</script>

<style>
</style>
