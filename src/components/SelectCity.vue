<template>
  <div class="select-city">
    <form action="" class="form" @submit.prevent>
      <div class="block-search">
        <input
            type="search"
            class="search"
            placeholder="Search location..."
            v-model="inputCity"
        >
      </div>
      <input
          type="submit"
          class="submit"
          value="Search"
          @click="selectCity"
      >
    </form>
  </div>
</template>

<script>
export default {
  name: "SelectCity",
  data() {
    return {
      inputCity: ""
    }
  },
  methods: {
    selectCity() {
      this.$emit('dataSelect', this.inputCity)
    }
  }
}
</script>

<style scoped>
.select-city {
  position: absolute;
  top: 200px;
  left: 50%;
  transform: translate(-50%);
}
.form {
  display: flex;
}
.block-search {
  display: block;
}
.search {
  width: 400px;
  height: 40px;
  border: none;
  padding: 0 2rem;
  font-size: 1rem;
}
.submit {
  height: 40px;
  padding: 0 2rem;
  border: none;
  color: #fff;
  font-size: 1rem;
  cursor: pointer;
  background: #5e5e5e;
}
</style>