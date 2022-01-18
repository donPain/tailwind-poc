<template>
  <ScheduleList></ScheduleList>
</template>

<script lang="ts">
import "./styles/app.css";
import { defineComponent } from "vue";
import ScheduleList from "@/components/Schedule/ScheduleList.vue";
// import ReportRegister from "@/components/ReportRegister.vue";

export default defineComponent({
  name: "App",
  components: { ScheduleList },
});
</script>
