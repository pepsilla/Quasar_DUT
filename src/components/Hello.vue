<template>
  <q-layout
    ref="layout"
    view="lHh Lpr fff"
    :left-class="{'bg-grey-2': true}"
  >
    <q-toolbar slot="header" class="glossy">
      <q-btn
        flat
        @click="$refs.layout.toggleLeft()"
      >
        <q-icon name="menu" />
      </q-btn>

      <q-toolbar-title>
        Título de la unidad didáctica
        <div slot="subtitle">Escena de la unidad didáctica. -Running on Quasar v{{$q.version}}-</div>
      </q-toolbar-title>
    </q-toolbar>

    <div slot="left">
      <!--
        Use <q-side-link> component
        instead of <q-item> for
        internal vue-router navigation
      -->
      <q-list no-border link inset-delimiter>
        <q-list-header>Índice de la unidad didáctica</q-list-header>
        <q-item >          
          <q-item-side icon="fingerprint" />
          <q-item-main label="Título de la escena" sublabel="Breve descripción de la acción a desarrollar" />
        </q-item>
        <q-item >          
          <q-item-side icon="fingerprint" />
          <q-item-main label="Título de la escena" sublabel="Breve descripción de la acción a desarrollar" />
        </q-item>
        <q-item >          
          <q-item-side icon="fingerprint" />
          <q-item-main label="Título de la escena" sublabel="Breve descripción de la acción a desarrollar" />
        </q-item>
      </q-list>
      <q-list no-border link inset-delimiter>
        <q-list-header>Menú de la unidad didáctica</q-list-header>
        <q-item @click="$refs.locutionModal.open()">
          <q-item-side icon="speaker notes" />
          <q-item-main label="Locución" sublabel="Mostrar la transcripción del audio incorporado en la escena de la unidad didáctica" />
        </q-item>
        <q-item @click="$refs.glossaryModal.open()">
          <q-item-side icon="find in page" />
          <q-item-main label="Glosario" sublabel="Glosario de la unidad didáctica" />
        </q-item>
        <q-item  @click="$refs.bibliographyModal.open()">
          <q-item-side icon="library books" />
          <q-item-main label="Bibliografía" sublabel="Bibliografía relacionada con la unidad didáctica" />
        </q-item>
        <q-item @click= "launch('/statics/Test.pdf')">
          <q-item-side icon="book" />
          <q-item-main label="e-book" sublabel="Libro electrónico de la unidad didáctica en formato pdf" />
        </q-item>
        
      </q-list>

      <q-modal 
        ref="locutionModal"
        @open="notify('open locution')"
        @close="notify('close locution')"
        :content-css= "{minWidth:'80vw', minHeight:'80vh'}"
      >
        <q-modal-layout>
          <q-toolbar slot="header">
            <q-icon name="speaker notes e"></q-icon>
            <q-toolbar-tittle>Locución</q-toolbar-tittle>
          </q-toolbar>

          <p>Módulo vista de la locución del la unidad didáctica</p>
          <q-btn
              flat
              @click="$refs.locutionModal.close()"
            >
              Cerrar
              <q-icon name="power settins new"></q-icon>
          </q-btn>
          
        </q-modal-layout>
      </q-modal>

      <q-modal 
        ref="glossaryModal" 
        @open="notify('open glossary')"
        @close="notify('close glosary')"
        :content-css= "{minWidth:'80vw', minHeight:'80vh'}"
      >
        <q-modal-layout>
          <q-toolbar slot="header">
            <q-icon name="find in page e"></q-icon>
            <q-toolbar-tittle>Glosario</q-toolbar-tittle>
          </q-toolbar>

          <p>Módulo vista del glosario del la unidad didáctica</p>
          <q-btn
              flat
              @click="$refs.glossaryModal.close()"
            >
              Cerrar
              <q-icon name="power settins new"></q-icon>
          </q-btn>
          
        </q-modal-layout>
      </q-modal>

      <q-modal 
        ref="bibliographyModal"
        @open="notify('open library')"
        @close="notify('close library')"
        :content-css= "{minWidth:'80vw', minHeight:'80vh'}"
      >
        <q-modal-layout>
          <q-toolbar slot="header">
            <q-icon name="library books e"></q-icon>
            <q-toolbar-tittle>Bibliografía</q-toolbar-tittle>
          </q-toolbar> 

          <p>Módulo vista de la Bibliografía de la unidad didáctica</p>
          <q-btn
              flat
              @click="$refs.bibliographyModal.close()"
            >
              Cerrar
              <q-icon name="power settins new"></q-icon>
          </q-btn>
          
        </q-modal-layout>
      </q-modal>
      

      <q-list no-border link inset-delimiter>
        <q-item @click= "closeNavigatorWindow">
          <q-item-side icon="power settings new" />
          <q-item-main label="Cerrar" sublabel="Cerrar la unidad didáctica" />
        </q-item>
      </q-list>
    </div>

    <!--
      Replace following <div> with
      <router-view /> component
      if using subRoutes
    -->
    <div class="layout-padding logo-container non-selectable no-pointer-events">
      <div class="logo" :style="position">
        <img src="~assets/quasar-logo-full.svg">
      </div>
    </div>
  </q-layout>
</template>

<script>
import {
  dom,
  event,
  openURL,
  Toast,
  QLayout,
  QToolbar,
  QToolbarTitle,
  QBtn,
  QIcon,
  QList,
  QListHeader,
  QItem,
  QItemSide,
  QItemMain,
  QModal,
  QModalLayout
} from 'quasar'

const
  { viewport } = dom,
  { position } = event,
  moveForce = 30,
  rotateForce = 40,
  RAD_TO_DEG = 180 / Math.PI

function getRotationFromAccel (accelX, accelY, accelZ) {
  /* Reference: http://stackoverflow.com/questions/3755059/3d-accelerometer-calculate-the-orientation#answer-30195572 */
  const sign = accelZ > 0 ? 1 : -1
  const miu = 0.001

  return {
    roll: Math.atan2(accelY, sign * Math.sqrt(Math.pow(accelZ, 2) + miu * Math.pow(accelX, 2))) * RAD_TO_DEG,
    pitch: -Math.atan2(accelX, Math.sqrt(Math.pow(accelY, 2) + Math.pow(accelZ, 2))) * RAD_TO_DEG
  }
}

export default {
  name: 'index',
  components: {
    QLayout,
    QToolbar,
    QToolbarTitle,
    QBtn,
    QIcon,
    QList,
    QListHeader,
    QItem,
    QItemSide,
    QItemMain,
    QModal,
    QModalLayout
  },
  data () {
    return {
      orienting: window.DeviceOrientationEvent && !this.$q.platform.is.desktop,
      rotating: window.DeviceMotionEvent && !this.$q.platform.is.desktop,
      moveX: 0,
      moveY: 0,
      rotateY: 0,
      rotateX: 0
    }
  },
  computed: {
    position () {
      const transform = `rotateX(${this.rotateX}deg) rotateY(${this.rotateY}deg)`
      return {
        top: this.moveY + 'px',
        left: this.moveX + 'px',
        '-webkit-transform': transform,
        '-ms-transform': transform,
        transform
      }
    }
  },
  methods: {
    launch (url) {
      openURL(url)
    },
    move (evt) {
      const
        {width, height} = viewport(),
        {top, left} = position(evt),
        halfH = height / 2,
        halfW = width / 2

      this.moveX = (left - halfW) / halfW * -moveForce
      this.moveY = (top - halfH) / halfH * -moveForce
      this.rotateY = (left / width * rotateForce * 2) - rotateForce
      this.rotateX = -((top / height * rotateForce * 2) - rotateForce)
    },
    rotate (evt) {
      if (evt.rotationRate &&
          evt.rotationRate.beta !== null &&
          evt.rotationRate.gamma !== null) {
        this.rotateX = evt.rotationRate.beta * 0.7
        this.rotateY = evt.rotationRate.gamma * -0.7
      }
      else {
        /* evt.acceleration may be null in some cases, so we'll fall back
           to evt.accelerationIncludingGravity */
        const
          accelX = evt.acceleration.x || evt.accelerationIncludingGravity.x,
          accelY = evt.acceleration.y || evt.accelerationIncludingGravity.y,
          accelZ = evt.acceleration.z || evt.accelerationIncludingGravity.z - 9.81,
          rotation = getRotationFromAccel(accelX, accelY, accelZ)

        this.rotateX = rotation.roll * 0.7
        this.rotateY = rotation.pitch * -0.7
      }
    },
    orient (evt) {
      if (evt.beta === null || evt.gamma === null) {
        window.removeEventListener('deviceorientation', this.orient, false)
        this.orienting = false

        window.addEventListener('devicemotion', this.rotate, false)
      }
      else {
        this.rotateX = evt.beta * 0.7
        this.rotateY = evt.gamma * -0.7
      }
    },
    notify (eventName) {
      Toast.create(`Event "${eventName}" was triggered`)
    },
    closeNavigatorWindow () {
      window.top.close()
    }
  },
  mounted () {
    this.$nextTick(() => {
      if (this.orienting) {
        window.addEventListener('deviceorientation', this.orient, false)
      }
      else if (this.rotating) {
        window.addEventListener('devicemove', this.rotate, false)
      }
      else {
        document.addEventListener('mousemove', this.move)
      }
    })
  },
  beforeDestroy () {
    if (this.orienting) {
      window.removeEventListener('deviceorientation', this.orient, false)
    }
    else if (this.rotating) {
      window.removeEventListener('devicemove', this.rotate, false)
    }
    else {
      document.removeEventListener('mousemove', this.move)
    }
  }
}
</script>

<style lang="stylus">
.logo-container
  width 255px
  height 242px
  perspective 800px
  position absolute
  top 50%
  left 50%
  transform translateX(-50%) translateY(-50%)
.logo
  position absolute
  transform-style preserve-3d
</style>
