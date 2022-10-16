<template>
  <main class="columns is-gapless is-multiline">
    <div class="column is-one-quarter">
      <Sidebar></Sidebar>
    </div>
    <div class="column is-three-quarter">
      <h1 class="title is-4">Hello World</h1>
      <p class="subtitle is-6">This is a subtitle</p>
      <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit.</p>
      <Form @completedTask="completedTask" />
      <CardBox>
        <h2 class="title is-4">My Tasks</h2>
        <p v-if="isListEmpty">
          No tasks yet. What about to start something cool today?
        </p>
        <Task v-for="(task, index) in tasks" :key="index" :task="task" />
      </CardBox>
    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import Sidebar from "@/components/SideBar.vue";
import Form from "@/components/Form.vue";
import Task from "@/components/Task.vue";
import ITasks from "@/interfaces/ITasks";
import CardBox from "@/components/cards/CardBox.vue";

export default defineComponent({
  name: "HomeView",
  components: {
    Sidebar,
    Form,
    Task,
    CardBox,
  },
  data() {
    return {
      tasks: [] as ITasks[],
    };
  },
  computed: {
    isListEmpty(): boolean {
      return this.tasks.length === 0;
    },
  },
  methods: {
    completedTask(task: ITasks): void {
      this.tasks.push(task);
    },
  },
});
</script>
