<template>
  <tr>
    <td class="px-6 py-4 whitespace-nowrap">
      <div class="flex items-center">
        <div class="flex-shrink-0 h-10 w-10"></div>
        <div class="ml-4">
          <div class="text-sm text-gray-500">
            {{ scheduleObject.scheduleId }}
          </div>
        </div>
      </div>
    </td>
    <td class="px-6 py-4 whitespace-nowrap">
      <div class="text-sm text-gray-900">
        {{ scheduleObject.scheduleReportName }}
      </div>
      <div class="text-sm text-gray-500">{{ scheduleObject.genType }}</div>
    </td>
    <td class="px-6 py-4 whitespace-nowrap">
      <span
        class="px-2 inline-flex text-xs leading-5 font-semibold rounded-full bg-green-100 text-green-800"
      >
        {{ scheduleObject.scheduleStatus }}
      </span>
    </td>
    <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">
      {{ scheduleObject.nextGenDate }}
    </td>
    <td class="px-6 py-4 whitespace-nowrap text-right text-sm font-medium">
      <a href="#" class="text-indigo-600 hover:text-indigo-900">Edit</a>
    </td>
  </tr>
</template>

<script lang="ts">
import { defineComponent } from "vue";

// interface ScheduleObject {
//   scheduleId: Number;
//   scheduleReportId: Number;
//   scheduleStatus: String;
//   scheduleCreator: String;
// }

export default defineComponent({
  name: "TableItem",
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
