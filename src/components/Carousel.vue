<script setup>
import { reactive, defineProps } from 'vue'
import { Carousel, Slide, Navigation } from 'vue3-carousel'
defineProps({
  imgs: {
    type: Array,
    required: true
  },
  settings: {
    type: Object,
    default: () => ({
      itemsToShow: 1,
      snapAlign: 'start',
    })
  },
  breakpoints: {
    type: Object,
    default: () => ({
      414: {
        itemsToShow: 3,
      },
      768: {
        itemsToShow: 4,
      },
      1024: {
        itemsToShow: 7,
      }
    })
  }
})

</script>

<template>
  <Carousel v-bind="settings" :breakpoints="breakpoints">
    <Slide v-for="(img, index) in imgs" :key="index">
      <div class="carousel__item">
        <slot :data="img">
          <img :src="img" alt="" />
        </slot>
      </div>
    </Slide>

    <template #addons>
      <Navigation />
    </template>
  </Carousel>
</template>