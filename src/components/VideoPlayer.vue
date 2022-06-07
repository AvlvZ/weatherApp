<template>
  <div class="video">
    <video
        src="./../assets/video/001.mp4"
        class="video__item"
        autoplay
        muted
        loop
    />
  </div>
</template>

<script>
export default {
  name: "VidePlayer"
}
</script>

<style scoped>
.video {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100vh;
  overflow: hidden;
}
.video__item {
  width: 100%;
  height: 100vh;
  object-fit: cover;
  overflow: hidden;
  z-index: -3;
}
</style>