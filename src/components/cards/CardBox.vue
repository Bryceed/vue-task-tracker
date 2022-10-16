<!-- eslint-disable vue/multi-word-component-names -->
<!-- eslint-disable prettier/prettier -->
<!-- eslint-disable vue/no-parsing-error -->

<template>
  <div class="box">
    <slot></slot> <!-- Means the origin content inside this component import will be rendered here-->
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "CardBox",
});
</script>
