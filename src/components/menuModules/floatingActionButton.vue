<template>
    <div class="layout-padding">
      <q-fixed-position corner="top-right" :offset="[16, 16]">
        <q-fab
          color="secondary"
          active-icon="card membership"
          direction="left"
          class="animate-pop"
        >
          <q-fab-action color="purple" @click="toast('speaker notes')" icon="speaker notes">
            <q-tooltip anchor="center left" self="center right" :offset="[20, 0]">Speaker Notes</q-tooltip>
          </q-fab-action>
          <q-fab-action color="primary" @click="toast('power settings new')" icon="power settings new">
            <q-tooltip anchor="center left" self="center right" :offset="[20, 0]">Close Unit</q-tooltip>
          </q-fab-action>
        </q-fab>
      </q-fixed-position>
    </div>
</template>

<script>
import {
  QFab,
  QFabAction,
  QTooltip,
  QBtn,
  QFixedPosition,
  Dialog,
  Toast
} from 'quasar'

export default {
  components: {
    QFab,
    QFabAction,
    QTooltip,
    QBtn,
    QFixedPosition
  },
  methods: {
    alert () {
      Dialog.create({
        title: 'FAB',
        message: 'Good job! Keep it going.'
      })
    },
    toast (icon) {
      Toast.create({
        icon,
        html: 'So you want your ' + icon + 's, huh?'
      })
    }
  }
}
</script>
