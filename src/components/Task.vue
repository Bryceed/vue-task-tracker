<!-- eslint-disable vue/multi-word-component-names -->
<!-- eslint-disable prettier/prettier -->
<!-- eslint-disable vue/no-parsing-error -->

<template>
    <CardBox>
        <div class="columns">
            <div class="column is-7">
                {{task.description || "(No description)"}}
            </div>
            <div class="column is-5">
                <Cron :time="task.spendedTimeInSeconds" />
            </div>
        </div>
    </CardBox>
</template>

<script lang="ts">
import { defineComponent, PropType } from "vue";
import Cron from "./Cron.vue";
import CardBox from "./cards/CardBox.vue";
import ITasks from "@/interfaces/ITasks";

export default defineComponent({
  // eslint-disable-next-line vue/multi-word-component-names
  name: "Task",
  props: {
    task: {
      type: Object as PropType<ITasks>,
      required: true,
    },
  },
  components: {
    Cron,
    CardBox,
  },
});
</script>
