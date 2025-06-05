<template>
  <div class="video-container">
    <video
      ref="videoPlayer"
      :src="videoSrc"
      controls
      width="640"
      height="360"
      @play="onPlay"
      @pause="onPause"
      @ended="onEnded"
    >
      Your browser does not support the video tag.
    </video>
  </div>
</template>

<script setup>
import { ref } from 'vue';

const props = defineProps({
  videoSrc: {
    type: String,
    required: true,
  },
});

const videoPlayer = ref(null);

const onPlay = () => {
  console.log('Video is playing');
};

const onPause = () => {
  console.log('Video is paused');
};

const onEnded = () => {
  console.log('Video has ended');
};
</script>

<style scoped>
.video-container {
  display: flex;
  justify-content: center;
  align-items: center;
  margin: 20px 0;
}
</style>
