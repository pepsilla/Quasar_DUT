<template>
  <q-gallery-carousel :src="slider" dots arrows></q-carousel >
      <!--q-carousel
        v-for="unitSlide in this.slider"
      >
        <div slot="slide">
          <img v-bind:src="unitSlide" />
        </div>
       
        
        <q-carousel-slide>
          <q-video
            class="absolute-full"
            src="https://www.youtube.com/embed/k3_tw44QsZQ?rel=0"
          />
        </q-carousel-slide>
        <q-carousel-slide img-src="/statics/parallax1.jpg" />
        <q-carousel-slide img-src="/statics/parallax2.jpg" />

        <q-carousel-slide>
          <div v-for="n in 50">
            Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.
          </div>
        </q-carousel-slide>
        <q-carousel-slide v-for="n in 7" :key="n" class="flex flex-center" :class="`bg-${colors[n % 5]}`">
          Slide 3-{{n}}
        </q-carousel-slide>

        <q-carousel-control slot="control" position="top-right" :offset="[18, 18]" class="text-white" style="background: rgba(0, 0, 0, .3); padding: 4px; border-radius: 4px">
          <q-toggle color="tertiary" v-model="infinite" label="Infinite" />
        </q-carousel-control>

        <q-carousel-control slot="control-left" slot-scope="carousel" position="top-left" :offset="[18, 18]">
          <q-btn small round color="tertiary" :icon="carousel.inFullscreen ? 'fullscreen_exit' : 'fullscreen'" @click="carousel.toggleFullscreen()" />
        </q-carousel-control>

        <q-carousel-control slot="control-nav" slot-scope="carousel" :offset="[18, 52]">
          <q-btn :disable="!carousel.canGoToPrevious" color="primary" icon="keyboard_arrow_left" round small @click="carousel.previous" class="q-mr-small" />
          <q-btn :disable="!carousel.canGoToNext" color="primary" icon="keyboard_arrow_right" round small @click="carousel.next" />
        </q-carousel-control>

        <q-carousel-control slot="progress" slot-scope="carousel" position="top">
          <q-progress :percentage="carousel.percentage" color="white" />
        </q-carousel-control>
        -->
      </q-gallery-carousel>
</template>
<script>
  import {
    QGalleryCarousel
  } from 'quasar'
  export default {
    components: {
      QGalleryCarousel
    },
    data () {
      return {
        slider: [
          './statics/L1/Diapositiva - 01.png',
          './statics/L1/Diapositiva - 02.png',
          './statics/L1/Diapositiva - 03.png',
          './statics/L1/Diapositiva - 04.png',
          './statics/L1/Diapositiva - 05.png',
          './statics/L1/Diapositiva - 06.png',
          './statics/L1/Diapositiva - 07.png',
          './statics/L1/Diapositiva - 08.png',
          './statics/L1/Diapositiva - 09.png',
          './statics/L1/Diapositiva - 10.png'
        ]
      }
    }
  }
</script>


