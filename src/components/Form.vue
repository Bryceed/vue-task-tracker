<!-- eslint-disable vue/multi-word-component-names -->
<!-- eslint-disable prettier/prettier -->
<!-- eslint-disable vue/no-parsing-error -->

<template>
  <div class="box">
    <div class="columns">
      <div class="column is-8" role="form" aria-label="Creation form">
        <input type="text" class="input" placeholder="Create new task" v-model="taskName" />
      </div>
      <div class="column is-4">
        <Timer @when-ends="endTask"/>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import Timer from "./Timer.vue";

export default defineComponent({
  components: { Timer },
  emits: ["completedTask"],
  methods: {
    endTask(time: number): void {
      this.$emit("completedTask", {
        description: this.taskName,
        spendedTimeInSeconds: time,
      });
      this.taskName = "";
    },
  },
  data() {
    return {
      taskName: "",
    };
  },
});
</script>
