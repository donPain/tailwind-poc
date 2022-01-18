<template>
  <div class="container mx-auto">
    <div class="pt-10 pb-10 flex flex-wrap items-center">
      <div class="relative w-full px-4 max-w-full flex-grow flex-1">
        <h3 class="font-semibold text-base text-blueGray-700">
          Schedule Report List
        </h3>
      </div>
      <div class="relative w-full px-4 max-w-full flex-grow flex-1 text-right">
        <button
          class="bg-indigo-700 text-white active:bg-indigo-600 text-xs font-bold uppercase px-3 py-1 rounded outline-none focus:outline-none mr-1 mb-1 ease-linear transition-all duration-150"
          type="button"
          @click="showModal"
        >
          New schedule
        </button>
      </div>
    </div>
    <div class="flex flex-col">
      <div class="-my-2 overflow-x-auto sm:-mx-6 lg:-mx-8">
        <div class="py-2 align-middle inline-block min-w-full sm:px-6 lg:px-8">
          <div
            class="shadow overflow-hidden border-b border-gray-200 sm:rounded-lg"
          >
            <table class="min-w-full divide-y divide-gray-200">
              <thead class="bg-gray-50">
                <tr>
                  <th
                    scope="col"
                    class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider"
                  >
                    Id
                  </th>
                  <th
                    scope="col"
                    class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider"
                  >
                    Report
                  </th>
                  <th
                    scope="col"
                    class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider"
                  >
                    Status
                  </th>
                  <th
                    scope="col"
                    class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider"
                  >
                    Next execution
                  </th>
                  <th scope="col" class="relative px-6 py-3">
                    <span class="sr-only">Edit</span>
                  </th>
                </tr>
              </thead>
              <tbody
                class="bg-white divide-y divide-gray-200"
                v-for="(schedule, i) in scheduleArray"
                :key="i"
              >
                <TableItem :scheduleObject="schedule"></TableItem>
              </tbody>
            </table>
          </div>
        </div>
      </div>
      <ReportRegister
        v-show="isModalVisible"
        @Close="closeModal"
      ></ReportRegister>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import TableItem from "@/components/ScheduleReportList/TableItem.vue";
import ReportRegister from "@/components/ReportRegisterModal/ReportRegister.vue";

export default defineComponent({
  name: "ReportScheduleList",
  components: { TableItem, ReportRegister },
  data() {
    return {
      isModalVisible: false,
      scheduleArray: [
        {
          scheduleId: 1,
          scheduleReportId: 1,
          scheduleStatus: "Done",
          scheduleReportName: "Abastecimento",
          scheduleCreator: "Donzelitos",
          genType: "Periodically",
          nextGenDate: "10/02/2022",
        },
        {
          scheduleId: 2,
          scheduleReportId: 2,
          scheduleStatus: "Waiting",
          scheduleReportName: "Plague control report",
          scheduleCreator: "Donzelitos",
          genType: "Specific",
          nextGenDate: "10/02/2022",
        },
        {
          scheduleId: 3,
          scheduleReportId: 3,
          scheduleStatus: "In progress",
          scheduleReportName: "Plague control report",
          scheduleCreator: "Donzelitos",
          genType: "Periodically",
          nextGenDate: "10/02/2022",
        },
        {
          scheduleId: 4,
          scheduleReportId: 4,
          scheduleStatus: "Done",
          scheduleReportName: "Horas gerais",
          scheduleCreator: "El chap",
          genType: "Specific",
          nextGenDate: "10/02/2022",
        },
      ],
    };
  },

  methods: {
    showModal() {
      this.isModalVisible = true;
    },
    closeModal() {
      this.isModalVisible = false;
    },
    mounted() {
      console.log("meio osl");
    },
  },
});
</script>
