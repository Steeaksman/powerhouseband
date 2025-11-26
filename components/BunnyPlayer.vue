<template>
  <div :class="wrapperClasses">
    <div class="aspect-video rounded-xl overflow-hidden" :class="innerClasses">
      <iframe
        :src="playerUrl"
        loading="lazy"
        allow="accelerometer; gyroscope; autoplay; encrypted-media; picture-in-picture;"
        allowfullscreen
        class="w-full h-full"
      ></iframe>
    </div>
  </div>
</template>

<script setup>
import { computed } from 'vue'

const props = defineProps({
  libraryId: { type: String, required: true },
  videoId: { type: String, required: true },
  autoplay: { type: Boolean, default: false },
  /**
   * Customize outer wrapper styling (max width, padding, margins, etc.)
   */
  wrapperClasses: {
    type: String,
    default: 'w-full max-w-3xl mx-auto p-4'
  },
  /**
   * Customize inner container (shadow, border, hover effects, etc.)
   */
  innerClasses: {
    type: String,
    default: 'shadow-lg'
  }
})

const playerUrl = computed(() =>
  `https://iframe.mediadelivery.net/embed/${props.libraryId}/${props.videoId}?autoplay=${props.autoplay}`
)
</script>
