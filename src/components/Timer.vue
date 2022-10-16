<!-- eslint-disable vue/multi-word-component-names -->
<!-- eslint-disable prettier/prettier -->
<!-- eslint-disable vue/no-parsing-error -->

<template>
    <div class="is-flex is-align-items-center is-justify-content-space-between">
        <Cron :time="time" />
        <div class="buttons is-right">
            <button class="button" @click="startCounting" :disabled="isRunning">
                <span class="icon has-text-success">
                    <i class="fas fa-play"></i>
                </span>
                <span>Start</span>
            </button>
            <button class="button is-danger" @click="endCounting" :disabled="!isRunning">
                <span class="icon">
                    <i class="fas fa-pause"></i>
                </span>
                <span>Pause</span>
            </button>
        </div>
    </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import Cron from "./Cron.vue";

export default defineComponent({
  // eslint-disable-next-line vue/multi-word-component-names
  name: "Form",
  emits: ["whenEnds"],
  data() {
    return {
      time: 0,
      timeDisplay: "00:00:00",
      interval: 0, // records the interval 'id'
      isRunning: false,
    };
  },
  methods: {
    startCounting() {
      this.isRunning = true;
      this.interval = setInterval(() => {
        console.log(this.time);
        this.time++;
      }, 1000);
    },
    endCounting() {
      clearInterval(this.interval);
      this.$emit("whenEnds", this.time);
      this.isRunning = false;
      this.time = 0;
    },
  },
  components: { Cron },
});
</script>

<style scoped>
button:disabled {
  display: none;
}
</style>
