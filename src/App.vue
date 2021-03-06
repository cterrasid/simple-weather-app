<template>
  <div
    id="app"
    :class="typeof weather.main !== 'undefined' && weather.main.temp > 16 ? 'warm' : ''"
  >
    <main :class="$style.container">
      <div :class="$style.searchBox">
        <input
          type="text"
          :class="$style.searchBar"
          placeholder="Search..."
          v-model="query"
          v-on:keypress="fetchWeather"
        />
      </div>
      <div :class="$style.weatherWrap" v-if="typeof weather !== 'undefined'">
        <div :class="$style.locationBox">
          <div :class="$style.location">{{weather.name}}, {{weather.sys.country}}</div>
          <div :class="$style.date">{{dateBuilder()}}</div>
        </div>
        <div :class="$style.weatherBox">
          <div :class="$style.temperature">{{Math.round(weather.main.temp)}}ºC</div>
          <div :class="$style.weather">{{weather.weather[0].main}}</div>
        </div>
      </div>
    </main>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      api_key: "a97e1796a597881d26e3289ae2a6dfe5",
      url_base: "https://api.openweathermap.org/data/2.5/",
      query: "",
      weather: {},
    };
  },
  methods: {
    fetchWeather(e) {
      if (e.key === "Enter") {
        fetch(
          `${this.url_base}weather?q=${this.query}&units=metric&APPID=${this.api_key}`
        )
          .then((res) => {
            return res.json();
          })
          .then(this.setResults);
      }
    },
    setResults(results) {
      if (typeof results !== "undefined") {
        this.weather = results;
      }
    },
    dateBuilder() {
      let d = new Date();
      let months = [
        "January",
        "February",
        "March",
        "April",
        "May",
        "June",
        "July",
        "August",
        "September",
        "October",
        "November",
        "December",
      ];
      let days = [
        "Sunday",
        "Monday",
        "Tuesday",
        "Wednesday",
        "Thursday",
        "Friday",
        "Saturday",
      ];

      let day = days[d.getDay()];
      let date = d.getDate();
      let month = months[d.getMonth()];
      let year = d.getFullYear();

      return `${day} ${date} ${month} ${year}`;
    },
  },
};
</script>

<style module>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: "monserrat", sans-serif;
}

#app {
  background-image: url("./assets/cold-bg.jpg");
  background-size: cover;
  background-position: bottom;
  transition: 0.4s;
}

.app.warm {
  background-image: url("./assets/warm-bg.jpg");
}

.container {
  min-height: 100vh;
  padding: 25px;
  background-image: linear-gradient(to bottom, #00000040, #000000bf);
}

.searchBox {
  width: 100%;
  margin-bottom: 30px;
}

.searchBox .searchBar {
  display: block;
  width: 100%;
  padding: 15px;
  color: #313131;
  font-size: 20px;
  appearance: none;
  border: none;
  outline: none;
  box-shadow: 0px 0px 16px #00000040;
  background-color: #ffffff80;
  border-radius: 0px 16px 0px 16px;
  transition: 0.4s;
}

.search-box .search-bar:focus {
  background-color: #ffffffbf;
  box-shadow: 0px 0px 16px #00000040;
  border-radius: 0px 16px 0px 16px;
}

.locationBox .location {
  color: #ffffff;
  font-size: 32px;
  font-weight: 500;
  text-align: center;
  text-shadow: 1px 3px #00000040;
}

.locationBox .date {
  color: #ffffff;
  font-size: 20px;
  font-weight: 300;
  text-align: center;
  font-style: italic;
}

.weatherBox {
  text-align: center;
}

.weatherBox .temperature {
  display: inline-block;
  padding: 10px 25px;
  color: #ffffff;
  font-size: 80px;
  font-weight: 900;
  text-shadow: 1px 3px #00000040;
  background-color: #ffffff40;
  border-radius: 16px;
  margin: 30px 0px;
  box-shadow: 3px 6px #00000040;
}

.weatherBox .weather {
  color: #ffffff;
  font-size: 48px;
  font-weight: 700;
  font-style: italic;
  text-shadow: 3px 6px #00000040;
}
</style>
