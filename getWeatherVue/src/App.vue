<script>
export default {
  data() {
    return {
      city: '',
    };
  },
};
</script>

<template>
  <div class="wrapper">
    <h1>Weather App</h1>
    <p>Find out the weather in {{ city == '' ? 'your city' : city }}</p>
    <input type="text" v-model="city" placeholder="Enter city" />
    <button v-if="city != ''">Find weather</button>
    <button disabled v-else>Enter city</button>
  </div>
</template>

<style scoped>
.wrapper {
  width: 900px;
  height: 500px;
  border-radius: 50px;
  background: #1f0f24;
  padding: 20px;
  text-align: center;
  color: #fff;
}
.wrapper h1 {
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
