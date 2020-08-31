<template>
  <div id="app" :class="$style.app">
    <main :class="$style.container">
      <div :class="$style.searchBox">
        <input type="text" :class="$style.searchBar" placeholder="Search..." />
      </div>
      <div :class="$style.weatherWrap">
        <div :class="$style.locationBox">
          <div :class="$style.location">Madrid, Spain</div>
          <div :class="$style.date">Monday 31 August 2020</div>
        </div>
        <div :class="$style.weatherBox">
          <div :class="$style.temperature">9ºC</div>
          <div :class="$style.weather">Rain</div>
        </div>
      </div>
    </main>
  </div>
</template>

<script>
export default {
  name: "App",
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

.app {
  background-image: url("./assets/cold-bg.jpg");
  background-size: cover;
  background-position: bottom;
  transition: 0.4s;
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
  font-size: 102px;
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
