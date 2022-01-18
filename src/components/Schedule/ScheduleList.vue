<template>
  <div class="container mx-auto">
    <div class="flex flex-col">
      <div class="pt-10 -my-2 overflow-x-auto sm:-mx-6 lg:-mx-8">
        <div class="py-2 align-middle inline-block min-w-full sm:px-6 lg:px-8">
          <div
            class="shadow overflow-hidden border-b border-t border-gray-200 sm:rounded-lg"
          >
            <div class="pt-10 pb-10 flex flex-wrap items-center">
              <div class="relative w-full px-4 max-w-full flex-grow flex-1">
                <h3 class="font-semibold text-base text-xl text-blueGray-700">
                  Schedule Report List
                </h3>
              </div>
            </div>

            <body class="antialiased font-sans bg-white">
              <div class="container mx-auto px-4 sm:px-8">
                <div class="py-8">
                  <div class="my-2 flex sm:flex-row flex-col">
                    <div class="flex flex-row mb-1 sm:mb-0">
                      <div class="relative">
                        <select
                          class="appearance-none h-full rounded-l border block appearance-none w-full bg-white border-gray-400 text-gray-700 py-2 px-4 pr-8 leading-tight focus:outline-none focus:bg-white focus:border-gray-500"
                        >
                          <option>5</option>
                          <option>10</option>
                          <option>20</option>
                        </select>
                        <div
                          class="pointer-events-none absolute inset-y-0 right-0 flex items-center px-2 text-gray-700"
                        >
                          <svg
                            class="fill-current h-4 w-4"
                            xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 20 20"
                          >
                            <path
                              d="M9.293 12.95l.707.707L15.657 8l-1.414-1.414L10 10.828 5.757 6.586 4.343 8z"
                            />
                          </svg>
                        </div>
                      </div>
                      <div class="relative">
                        <select
                          class="appearance-none h-full rounded-r border-t sm:rounded-r-none sm:border-r-0 border-r border-b block appearance-none w-full bg-white border-gray-400 text-gray-700 py-2 px-4 pr-8 leading-tight focus:outline-none focus:border-l focus:border-r focus:bg-white focus:border-gray-500"
                        >
                          <option>All</option>
                          <option>Done</option>
                          <option>Waiting</option>
                          <option>In Progress</option>
                        </select>
                        <div
                          class="pointer-events-none absolute inset-y-0 right-0 flex items-center px-2 text-gray-700"
                        >
                          <svg
                            class="fill-current h-4 w-4"
                            xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 20 20"
                          >
                            <path
                              d="M9.293 12.95l.707.707L15.657 8l-1.414-1.414L10 10.828 5.757 6.586 4.343 8z"
                            />
                          </svg>
                        </div>
                      </div>
                    </div>
                    <div class="block relative">
                      <span
                        class="h-full absolute inset-y-0 left-0 flex items-center pl-2"
                      >
                        <svg
                          viewBox="0 0 24 24"
                          class="h-4 w-4 fill-current text-gray-500"
                        >
                          <path
                            d="M10 4a6 6 0 100 12 6 6 0 000-12zm-8 6a8 8 0 1114.32 4.906l5.387 5.387a1 1 0 01-1.414 1.414l-5.387-5.387A8 8 0 012 10z"
                          ></path>
                        </svg>
                      </span>
                      <input
                        placeholder="Search"
                        class="appearance-none rounded-r rounded-l sm:rounded-l-none border border-gray-400 border-b block pl-8 pr-6 py-2 w-full bg-white text-sm placeholder-gray-400 text-gray-700 focus:bg-white focus:placeholder-gray-600 focus:text-gray-700 focus:outline-none"
                      />
                    </div>
                    <div
                      class="relative w-full px-4 max-w-full flex-grow flex-1 text-right"
                    >
                      <button
                        class="h-8 bg-black text-white hover:bg-indigo-900 text-xs font-bold uppercase px-3 py-1 rounded outline-none focus:outline-none mr-1 mb-1 ease-linear transition-all duration-150"
                        type="button"
                        @click="showReportModal"
                        v-if="isAdmin"
                      >
                        Add Report
                      </button>
                      <button
                        class="h-8 bg-indigo-600 text-white hover:bg-indigo-900 text-xs font-bold uppercase px-3 py-1 rounded outline-none focus:outline-none mr-1 mb-1 ease-linear transition-all duration-150"
                        type="button"
                        @click="showScheduleModal"
                      >
                        New schedule
                      </button>
                    </div>
                  </div>

                  <div class="-mx-4 sm:-mx-8 px-4 sm:px-8 py-4 overflow-x-auto">
                    <div
                      class="inline-block min-w-full shadow rounded-lg overflow-hidden"
                    >
                      <table class="min-w-full leading-normal">
                        <thead>
                          <tr>
                            <th
                              class="px-5 py-3 border-b-2 border-gray-200 bg-gray-100 text-left text-xs font-semibold text-gray-600 uppercase tracking-wider"
                            >
                              Id
                            </th>
                            <th
                              class="px-5 py-3 border-b-2 border-gray-200 bg-gray-100 text-left text-xs font-semibold text-gray-600 uppercase tracking-wider"
                            >
                              Report Name
                            </th>

                            <th
                              class="px-5 py-3 border-b-2 border-gray-200 bg-gray-100 text-left text-xs font-semibold text-gray-600 uppercase tracking-wider"
                            >
                              Status
                            </th>
                            <th
                              class="px-5 py-3 border-b-2 border-gray-200 bg-gray-100 text-left text-xs font-semibold text-gray-600 uppercase tracking-wider"
                            >
                              Gen Type
                            </th>
                            <th
                              class="px-5 py-3 border-b-2 border-gray-200 bg-gray-100 text-left text-xs font-semibold text-gray-600 uppercase tracking-wider"
                            >
                              Last Gen
                            </th>
                            <th
                              class="px-5 py-3 border-b-2 border-gray-200 bg-gray-100 text-left text-xs font-semibold text-gray-600 uppercase tracking-wider"
                            >
                              Next Gen
                            </th>
                            <th
                              class="px-5 py-3 border-b-2 border-gray-200 bg-gray-100 text-left text-xs font-semibold text-gray-600 uppercase tracking-wider"
                            >
                              Action
                            </th>
                          </tr>
                        </thead>
                        <tbody
                          v-for="(scheduleObject, i) in scheduleArray"
                          :key="i"
                        >
                          <TableItem
                            :scheduleObject="scheduleObject"
                          ></TableItem>
                        </tbody>
                      </table>
                      <div
                        class="px-5 py-5 bg-white border-t flex flex-col xs:flex-row items-center xs:justify-between"
                      >
                        <span class="text-xs xs:text-sm text-gray-900">
                          Showing 1 to 5 of 50 Schedules
                        </span>
                        <div class="inline-flex mt-2 xs:mt-0">
                          <button
                            class="text-sm bg-gray-300 hover:bg-gray-400 text-gray-800 font-semibold py-2 px-4 rounded-l"
                          >
                            Prev
                          </button>
                          <button
                            class="text-sm bg-gray-300 hover:bg-gray-400 text-gray-800 font-semibold py-2 px-4 rounded-r"
                          >
                            Next
                          </button>
                        </div>
                      </div>
                    </div>
                  </div>
                </div>
              </div>
            </body>
          </div>
        </div>
      </div>
      <ScheduleRegister
        v-show="isShowScheduleModalVisible"
        @Close="closeScheduleModal"
      ></ScheduleRegister>
      <ReportRegister
        v-show="isShowReportModalVisible"
        @Close="closeReportModal"
      ></ReportRegister>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import TableItem from "@/components/Schedule/ScheduleItem.vue";
import ScheduleRegister from "@/components/Schedule/ScheduleRegister.vue";
import ReportRegister from "@/components/Report/ReportRegister.vue";

export default defineComponent({
  name: "ScheduleList",
  components: { TableItem, ScheduleRegister, ReportRegister },
  data() {
    return {
      isShowScheduleModalVisible: false,
      isShowReportModalVisible: false,
      isAdmin: true,
      scheduleArray: [
        {
          scheduleId: 1,
          scheduleReportId: 1,
          scheduleStatus: "Done",
          scheduleReportName: "Abastecimento",
          scheduleCreator: "Donzelitos",
          scheduleGenType: "Periodically",
          scheduleLastGen: "10/02/2021 8:00 AM",
          scheduleNextGen: "10/02/2022 9:00 AM",
        },
        {
          scheduleId: 2,
          scheduleReportId: 2,
          scheduleStatus: "Waiting",
          scheduleReportName: "Plague control report",
          scheduleCreator: "Donzelitos",
          scheduleGenType: "Specific",
          scheduleLastGen: "10/02/2021 8:00 AM",
          scheduleNextGen: "11/02/2022 8:00 AM",
        },
        {
          scheduleId: 3,
          scheduleReportId: 3,
          scheduleStatus: "In progress",
          scheduleReportName: "Plague control report",
          scheduleCreator: "Donzelitos",
          scheduleGenType: "Periodically",
          scheduleLastGen: "10/02/2021 8:00 AM",
          scheduleNextGen: "10/02/2022 9:00 AM",
        },
        {
          scheduleId: 4,
          scheduleReportId: 4,
          scheduleStatus: "Done",
          scheduleReportName: "Horas gerais",
          scheduleCreator: "El chap",
          scheduleGenType: "Specific",
          scheduleLastGen: "10/02/2021 8:00 AM",
          scheduleNextGen: "11/02/2022 8:00 AM",
        },
        {
          scheduleId: 5,
          scheduleReportId: 1,
          scheduleStatus: "Done",
          scheduleReportName: "Abastecimento",
          scheduleCreator: "Donzelitos",
          scheduleGenType: "Periodically",
          scheduleLastGen: "10/02/2021 8:00 AM",
          scheduleNextGen: "10/02/2022 9:00 AM",
        },
      ],
    };
  },

  methods: {
    showScheduleModal() {
      this.isShowScheduleModalVisible = true;
    },
    closeScheduleModal() {
      this.isShowScheduleModalVisible = false;
    },
    showReportModal() {
      this.isShowReportModalVisible = true;
    },
    closeReportModal() {
      this.isShowReportModalVisible = false;
    },
    mounted() {
      console.log("meio osl");
    },
  },
});
</script>
