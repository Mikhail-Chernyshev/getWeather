<script>
import axios from 'axios';

export default {
  data() {
    return {
      city: '',
      error: '',
      info: null,
    };
  },
  computed: {
    cityName() {
      return '"' + this.city + '"';
    },
    showTemp() {
      return 'Tempepature: ' + this.info.main.temp;
    },
    showFeelsLike() {
      return 'Feels like: ' + this.info.main.feels_like;
    },
    showMinTemp() {
      return 'Minimum tamperature: ' + this.info.main.temp_min;
    },
    showMaxTemp() {
      return 'Maximum temperature: ' + this.info.main.temp_max;
    },
  },
  methods: {
    getWeather() {
      if (this.city.trim().length < 2) {
        this.error = 'The name must be longer than one character';
        return false;
      }
      this.error = '';

      axios
        .get(
          `https://api.openweathermap.org/data/2.5/weather?q=${this.city}&units=metric&appid=0598b8d1c6e531315f2c6707ee8e25ed`
        )
        .then((res) => (this.info = res.data));
    },
  },
};
</script>

<template>
  <div class="wrapper">
    <h1>Weather App</h1>
    <p>Find out the weather in {{ city == '' ? 'your city' : cityName }}</p>
    <input type="text" v-model="city" placeholder="Enter city" />
    <button v-if="city != ''" @click="getWeather()">Find weather</button>
    <button disabled v-else>Enter city</button>
    <p class="error">{{ error }}</p>
    <div v-if="info != null">
          <p>{{ showTemp }}</p>
          <p>{{ showFeelsLike }}</p>
          <p>{{ showMinTemp }}</p>
          <p>{{ showMaxTemp }}</p>
    </div>
  </div>
</template>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Montserrat:wght@200&display=swap');
@import url('https://fonts.googleapis.com/css2?family=Montserrat:wght@200;500&display=swap');
.error {
  color: #d03939;
}
.wrapper {
  font-family: 'Montserrat', sans-serif;
  font-weight: 200;
  width: 900px;
  height: 500px;
  border-radius: 50px;
  background: #1f0f24;
  padding: 20px;
  text-align: center;
  color: #fff;
}
.wrapper h1 {
  font-weight: 500;
  margin-top: 50px;
}
.wrapper p {
  margin-top: 20px;
}
.wrapper input {
  margin-top: 30px;
  background: transparent;
  border: none;
  border-bottom: 2px solid rgb(45, 36, 36);
  color: rgb(190, 187, 187);
  font-size: 14px;
  padding: 5px 8px;
  outline: none;
}
.wrapper input:focus {
  border-bottom-color: #591a6c;
}
.wrapper button {
  background: #e3bc4b;
  color: #fff;
  border-radius: 10px;
  border: 2px solid #b99935;
  padding: 10px 15px;
  margin-left: 20px;
  cursor: pointer;
  transition: transform 500ms ease;
}
.wrapper button:hover {
  transform: scale(1.1) translateY(-5px);
}
.wrapper button:disabled {
  background: #746027;
  cursor: not-allowed;
}
</style>

// 0598b8d1c6e531315f2c6707ee8e25ed 5e2c657f35f5a90f3e065c9fb1b23eac //
https://api.openweathermap.org/data/2.5/weather?q=Seattle&units=metric&appid=5e2c657f35f5a90f3e065c9fb1b23eac
//
https://api.openweathermap.org/data/2.5/weather?q=Seattle&units=metric&appid=0598b8d1c6e531315f2c6707ee8e25ed
