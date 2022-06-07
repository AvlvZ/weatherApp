<template>
  <div class="app-info">
    <div class="info-column temperature">{{ celsius }}°</div>
    <div class="info-column">
      <div class="info__city">{{ city }}</div>
      <div class="info__date">
        {{dataDayOfTheWeek[getDay]}},
        {{getDate}}
        {{dataMonth[getMonth]}}
        {{getFullYear}}
      </div>
    </div>
    <div class="info-column">
      <img
          :src="codeIcon"
          alt="weather icon"
          class="info__icon"
      />
      <div class="info__status">{{weatherMain}}</div>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "AppInfo",
  props: {
    data: {
      type: String,
      require: true
    }
  },
  data() {
    return {
      city: "",
      celsius: "",
      weatherMain: "",
      codeIcon: "",
      getDay: new Date().getDay(),
      getDate: new Date().getDate(),
      getMonth: new Date().getMonth(),
      getFullYear: new Date().getFullYear(),
      dataDayOfTheWeek: ["Sunday", "Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday"],
      dataMonth : ["January", "February ", "March", "April", "May", "June", "July", "August", "September", "October", "November", "December"]
    }
  },
  methods: {
    async postFetch() {
      try {
        const response = await axios.get("https://api.openweathermap.org/data/2.5/weather?q=Buynaksk,ru&appid=40ac0aa81ef42692b78c1b396f0db823&units=metric");
        this.city = response.data.name;
        this.celsius = Math.ceil(response.data.main.temp);
        this.weatherMain = response.data.weather[0].main;
        this.codeIcon = "http://openweathermap.org/img/wn/" + response.data.weather[0].icon;
        console.log(this.codeIcon)
      } catch {
        alert("Error")
      }
    }
  },
  mounted() {
    this.postFetch()
  }
}
</script>

<style scoped>
.app-info {
  position: absolute;
  bottom: 264px;
  left: 64px;
  display: flex;
  gap: 32px;
}

.info-column {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}

.temperature {
  font-size: 5rem;
  color: #FFF;
}

.info__city {
  font-size: 2rem;
  color: #fff;
  text-align: center;
}

.info__date {
  color: #fff;
  font-size: 1rem;
  text-align: center;
}

.info__icon {
  width: 64px;
  height: 64px;
}

.info__status {
  font-size: 1rem;
  color: #FFF;
  text-align: center;
}
</style>