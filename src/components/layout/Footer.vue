<script setup lang="ts">
import { ref } from "vue";
import { version, author, contributors } from "../../../package.json";
const thanked = ref(contributors.slice(0, 3));
</script>

<template>
  <footer>
    <p>
      Made with &#10084;&#65039; by
      <a target="_blank" :href="author.url">{{ author.name }}</a>
    </p>
    <p id="contributor-mapping">
      Thanks to
      <a
        v-for="(contributor, index) in thanked"
        :key="index"
        :href="contributor.url"
        >{{
          index !== thanked.length - 1
            ? contributor.name + "," + ` `
            : contributor.name
        }}</a
      >
      <a
        v-if="contributors.length !== thanked.length"
        target="_blank"
        href="https://github.com/TheodoreLefrancois/scrapp_royaleapi/graphs/contributors"
      >
        and more...
      </a>
    </p>
    <p>
      Version : <span>{{ version }}</span>
    </p>
  </footer>
</template>

<style scoped>
footer {
  margin-top: 40px;
  width: 100%;
  background-color: darkblue;
  color: darkgrey;
  text-align: center;
}
span {
  font-style: italic;
  color: crimson;
}
#contributor-mapping {
  display: flex;
  flex-direction: row;
  justify-content: center;
}
a {
  text-decoration: none;
  padding-left: 5px;
  padding-right: 5px;
  color: crimson;
}
</style>
