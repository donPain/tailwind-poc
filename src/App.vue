<template>
  <ReportScheduleList></ReportScheduleList>
</template>

<script lang="ts">
import "./styles/app.css";
import { defineComponent } from "vue";
import ReportScheduleList from "@/components/ScheduleReportList/ReportScheduleList.vue";
// import ReportRegister from "@/components/ReportRegister.vue";

export default defineComponent({
  name: "App",
  components: { ReportScheduleList },
});
</script>
