<template>
  <div class="theme-div">
    <img
      src="./assets/themeswitch.svg"
      alt=""
      v-if="this.currentTheme === 'dark'"
      @click="switchTheme"
    />
    <img src="./assets/theme-switch.svg" alt="" v-else @click="switchTheme" />

    <p v-if="this.currentTheme === 'dark'"  @click="switchTheme">Dark Mode</p>
    <p v-else  @click="switchTheme">Light Mode</p>
  </div>

  <h2>This is a theme switcher tutorial</h2>
  <p>
    Lorem ipsum dolor sit amet consectetur adipisicing elit. Veniam, suscipit
    perspiciatis, maiores debitis quis sed, expedita eaque voluptatum est a
    error dolore consequatur! Placeat deleniti deserunt illum iste debitis
    perspiciatis!
  </p>

  <p>
    Lorem ipsum dolor sit amet consectetur adipisicing elit. Amet asperiores
    delectus similique temporibus. Suscipit molestiae unde minus excepturi esse
    in quam nobis, ullam eos atque dolor, quia repellendus, placeat hic.
  </p>
</template>

<script>
export default {
  name: "App",
  components: {},
  data() {
    return {
      currentTheme: localStorage.getItem("theme") || "dark",
    };
  },
  created() {
    let bodyElement = document.body;
    localStorage.setItem("theme", this.currentTheme);
    bodyElement.classList.add(this.currentTheme);
  },
  methods: {
    switchTheme() {
      let bodyElement = document.body;
      if (localStorage.getItem("theme") === "dark") {
        bodyElement.classList.remove("dark");
        localStorage.setItem("theme", "light");
        this.currentTheme = localStorage.getItem("theme");
        bodyElement.classList.add(this.currentTheme);
      } else if (localStorage.getItem("theme") === "light") {
        bodyElement.classList.remove("light");
        localStorage.setItem("theme", "dark");
        this.currentTheme = localStorage.getItem("theme");
        bodyElement.classList.add(this.currentTheme);
      }
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: var(--font-color);
  margin: 10vh auto;
  width: 600px;
  padding: 0;
  box-sizing: border-box;
}
body {
  background: var(--bg-color);
}
.theme-div {
  padding: 0px 20px;
  display: flex;
  background: var(--secondary-color);
}
.theme-div img {
  width: 15px;
  margin-right: 5px;
  cursor: pointer;
}
.light {
  --bg-color: hsl(0, 0%, 98%);
  --secondary-color: hsl(0, 0%, 100%);
  --font-color: hsl(200, 15%, 8%);
}
.dark {
  --secondary-color: hsl(209, 23%, 22%);
  --bg-color: hsl(207, 26%, 17%);
  --font-color: hsl(0, 0%, 100%);
}
</style>
