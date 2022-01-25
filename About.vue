<template>
  <div v-if="result" class="about">
    <h1>Weather</h1>
    <header>
      <p>
        <b> {{ result.name }} </b>
      </p>
    </header>

    <img
      :src="
        'http://openweathermap.org/img/w/' + result.weather[0].icon + '.png'
      "
      alt=" "
    />
    <p>{{ result.weather[0].description }}</p>
    <p>Temp: {{ result.main.temp }}</p>
    <p>Degrees: {{ result.wind.deg }}</p>
  </div>
</template>
<style></style>
<script>
import axios from "axios";
export default {
  data: () => ({
    result: null,
  }),
  created() {
    axios
      .get(
        "https://api.openweathermap.org/data/2.5/weather?q=mazatlan&APPID=312f667be3a4279a5707948323b672bc"
      )
      .then((result) => {
        this.result = result.data;
        console.log(result.data);
      });
  },
};
</script>
