<!-- eslint-disable vue/multi-word-component-names -->
<!-- eslint-disable prettier/prettier -->
<!-- eslint-disable vue/no-parsing-error -->

<template>
  <header>
    <h1>
      <img src="https://vuejs.org/images/logo.png" alt="Vue logo" />
    </h1>
  </header>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "SideBar",
});
</script>

<style scoped>
header {
  background-color: #42b983;
  padding: 1rem;
  text-align: center;
}
h1 {
  color: #fff;
  font-size: 2rem;
  font-weight: 300;
}
img {
  height: 1.5rem;
  vertical-align: middle;
}
</style>
