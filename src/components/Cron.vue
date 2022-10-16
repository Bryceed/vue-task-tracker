<!-- eslint-disable prettier/prettier -->
<!-- eslint-disable vue/multi-word-component-names -->
<!-- eslint-disable vue/no-parsing-error -->

<template>
    <section class="section">
        <strong>{{timeSpent}}</strong>
    </section>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  // eslint-disable-next-line vue/multi-word-component-names
  name: "Cron",
  props: {
    time: {
      type: Number,
      default: 0,
    },
  },
  computed: {
    timeSpent(): string {
      return new Date(this.time * 1000).toISOString().substr(11, 8);
    },
    humanizedTime(): string {
      const hrs = Math.floor(this.time / 3600);
      const min = Math.floor((this.time - hrs * 3600) / 60);
      const sec = this.time - hrs * 3600 - min * 60;
      return `${hrs.toString().padStart(2, "0")}:${min
        .toString()
        .padStart(2, "0")}:${sec.toString().padStart(2, "0")}`;
    },
  },
});
</script>
