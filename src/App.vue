<template>
  <div id="app" :class="$style.app">
    <main :class="$style.container">
      <div :class="$style.searchBox">
        <input type="text" :class="$style.searchBar" placeholder="Search..." />
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
  box-shadow: 0px 0px 16px rgba(0, 0, 0, 0.25);
  border-radius: 0px 16px 0px 16px;
}
</style>
