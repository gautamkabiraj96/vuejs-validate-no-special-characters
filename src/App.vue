<template>
  <div id="app">
    <div>
      <h4>Please type some special characters to check</h4>
      <input type="text" placeholder="Type in here" v-model="inputValue" />
    </div>
    <div class="np-credits">wwww.nightprogrammer.com</div>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      inputValue: "",
    };
  },
  watch: {
    inputValue(newValue) {
      if (this.checkForSpecialCharacters(newValue)) {
        this.inputValue = this.removeSpecialCharacters(newValue);
      }
    },
  },
  methods: {
    removeSpecialCharacters(charactersString) {
      return charactersString.replace(/[^\w\s]/gi, "");
    },
    checkForSpecialCharacters(charactersString) {
      const specialCharactersRegex = /[^\w\s]/;
      return specialCharactersRegex.test(charactersString);
    },
  },
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  padding: 24px;
}

.np-credits {
  font-size: 12px;
  margin-top: 12px;
  color: #4b4b4b;
}
</style>