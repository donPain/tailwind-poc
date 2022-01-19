<template>
  <tr>
    <td class="px-5 py-5 bg-white text-sm">
      <div class="flex items-center">
        <div class="flex-shrink-0 w-10 h-10"></div>
        <div class="ml-3">
          <p class="text-gray-900 whitespace-no-wrap">
            {{ reportObject.reportId }}
          </p>
        </div>
      </div>
    </td>
    <td class="px-5 py-5 bg-white text-sm">
      <p class="text-gray-900 whitespace-no-wrap">
        {{ reportObject.reportName }}
      </p>
    </td>
    <td class="px-5 py-5 bg-white text-sm">
      <span class="period-bg">
        <span aria-hidden class="period-label"></span>
        <span class="relative">{{ reportObject.reportActivePeriod }}</span>
      </span>
    </td>
    <td class="px-5 py-5 bg-white text-sm">
      <p class="text-gray-900 whitespace-no-wrap">
        {{ reportObject.reportMinTime }}
      </p>
    </td>
    <td class="px-5 py-5 bg-white text-sm">
      <p class="text-gray-900 whitespace-no-wrap">
        {{ reportObject.reportMaxGenDay }}
      </p>
    </td>

    <td class="px-5 py-5 bg-white text-sm">
      <span
        class="report-status-bg"
        v-bind:class="{ inativo: reportObject.reportStatus == 'Inactive' }"
      >
        <span
          aria-hidden
          class="report-status-label"
          v-bind:class="{ inativo: reportObject.reportStatus == 'Inactive' }"
        ></span>
        <span class="relative">{{ reportObject.reportStatus }}</span>
      </span>
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
  name: "TableItem",
  props: {
    reportObject: {
      type: Object,
      default: () => ({}),
    },
  },
  created() {
    console.log(this.reportObject);
  },
});
</script>

<style>
.period-label {
  @apply absolute inset-0 bg-indigo-600 opacity-100 rounded-full;
}
.period-bg {
  @apply relative inline-block px-3 py-1 font-semibold text-white leading-tight;
}
.report-status-bg {
  @apply relative inline-block px-3 py-1 font-semibold text-green-900 opacity-100 leading-tight;
}
.report-status-label {
  @apply absolute inset-0 bg-green-400 opacity-100 rounded-full;
}
.report-status-bg.inativo {
  @apply relative inline-block px-3 py-1 font-semibold text-gray-900 leading-tight;
}
.report-status-label.inativo {
  @apply absolute inset-0 bg-gray-400 opacity-100 rounded-full;
}
a.svg {
  position: relative;
  display: inline-block;
}
</style>
