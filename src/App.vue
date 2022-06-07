<template>
  <div id="app">
    <div class="wrapper">
      <VideoPlayer/>
      <h1 class="app-name">weatherApp</h1>
      <AppInfo :data="dataInput"/>
      <SelectCity @dataSelect="dataSelect"/>
    </div>
  </div>
</template>

<script>
import VideoPlayer from "@/components/VideoPlayer";
import AppInfo from "@/components/AppInfo";
import SelectCity from "@/components/SelectCity";

export default {
  components: {
    SelectCity,
    AppInfo,
    VideoPlayer,
  },
  data() {
    return {
      dataInput: "",
    }
  },
  methods: {
    dataSelect(data) {
      this.dataInput = data;
    }
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Manrope:wght@200;300;400;500;600;700;800&display=swap');

* {
  font-family: 'Manrope', sans-serif;
  text-decoration: none;
  text-align: left;
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.wrapper {
  width: 100%;
  height: 100vh;
  overflow: hidden;
}

.app-name {
  position: absolute;
  top: 64px;
  left: 64px;
  font-size: 1rem;
  color: #FFF;
  z-index: 2;
}
</style>
