<template>
  <tr>
    <td class="px-5 py-5 bg-white text-sm">
      <div class="flex items-center">
        <div class="text-left">
          <p class="text-gray-900 whitespace-no-wrap">
            {{ scheduleObject.scheduleId }}
          </p>
        </div>
      </div>
    </td>
    <td class="px-5 py-5 bg-white text-sm">
      <p class="text-gray-900 whitespace-no-wrap">
        {{ scheduleObject.scheduleReportName }}
      </p>
    </td>
    <td class="px-5 py-5 bg-white text-sm">
      <span class="status-bg">
        <span aria-hidden class="status-label"></span>
        <span class="relative">{{ scheduleObject.scheduleStatus }}</span>
      </span>
    </td>
    <td class="px-5 py-5 bg-white text-sm">
      <p class="text-gray-900 whitespace-no-wrap">
        {{ scheduleObject.scheduleGenType }}
      </p>
    </td>
    <td class="px-5 py-5 bg-white text-sm">
      <p class="text-gray-900 whitespace-no-wrap">
        {{ scheduleObject.scheduleLastGen }}
      </p>
    </td>
    <td class="px-5 py-5 bg-white text-sm">
      <p class="text-gray-900 whitespace-no-wrap">
        {{ scheduleObject.scheduleNextGen }}
      </p>
    </td>

    <td class="px-5 py-5 bg-white text-sm">
      <a href="#" fill="none" class="svg">
        <svg
          xmlns="http://www.w3.org/2000/svg"
          class="h-5 w-5"
          fill="none"
          viewBox="0 0 24 24"
          stroke="currentColor"
        >
          <path
            strokeLinecap="round"
            strokeLinejoin="round"
            strokeWidth="{2}"
            d="M11 5H6a2 2 0 00-2 2v11a2 2 0 002 2h11a2 2 0 002-2v-5m-1.414-9.414a2 2 0 112.828 2.828L11.828 15H9v-2.828l8.586-8.586z"
          />
        </svg>
      </a>
    </td>
  </tr>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "ScheduleItem",
  props: {
    scheduleObject: {
      type: Object,
      default: () => ({}),
    },
  },
  created() {
    console.log(this.scheduleObject);
  },
});
</script>
<style>
.status-bg {
  @apply relative inline-block px-3 py-1 font-semibold text-white leading-tight;
}
.status-label {
  @apply absolute inset-0 bg-indigo-600 opacity-100 rounded-full;
}

a.svg {
  position: relative;
  display: inline-block;
}
</style>
