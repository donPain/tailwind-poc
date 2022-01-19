<template>
  <div class="main-div">
    <div class="hidden sm:block" aria-hidden="true">
      <div class="py-5">
        <div class="border-t border-gray-200" />
      </div>
    </div>
    <div class="w-1/3 mt-10 sm:mt-0">
      <div class="mt-5 md:mt-0 md:col-span-2">
        <div class="shadow overflow-hidden sm:rounded-md">
          <div class="px-4 py-5 bg-white sm:p-6 rounded-2xl">
            <div class="grid grid-cols-6 gap-6 p-3">
              <div class="col-span-6 sm:col-span-3">
                <div class="col-span-6 sm:col-span-3">
                  <label for="reports" class="label">Report</label>
                  <select
                    id="ReportId"
                    name="ReportName"
                    autocomplete="report-name"
                    class="mt-1 block w-full py-2 px-3 border border-gray-300 bg-white rounded-md shadow-sm focus:outline-none focus:ring-indigo-500 focus:border-indigo-500 sm:text-sm"
                  >
                    <option>Plant report</option>
                    <option>Plague report</option>
                  </select>
                </div>
              </div>

              <div class="col-span-6 sm:col-span-3">
                <div class="w-full md:w-2/2">
                  <label class="label" for="grid-last-name">
                    PBI Identifier
                  </label>
                  <input
                    class="h-9 appearance-none block w-full text-gray-700 border border-gray-200 rounded py-3 px-4 leading-tight focus:outline-none focus:bg-white focus:border-gray-500"
                    id="grid-last-name"
                    type="text"
                    placeholder="PBI Info"
                  />
                </div>
              </div>
            </div>
            <div class="grid grid-cols-6 gap-6 p-3">
              <div class="col-span-6 sm:col-span-3">
                <div class="col-span-6 sm:col-span-3">
                  <div class="w-full md:w-2/2">
                    <label class="label" for="max-daily-gen">
                      Maximum Daily Generations
                    </label>
                    <input
                      class="h-9 appearance-none block w-full text-gray-700 border border-gray-200 rounded py-3 px-4 leading-tight focus:outline-none focus:bg-white focus:border-gray-500"
                      id="max-daily-gen"
                      type="number"
                      placeholder="3"
                      min="1"
                      max="4"
                      q
                    />
                  </div>
                </div>
                <div class="w-full md:w-2/2 pt-3">
                  <label class="label" for="gen-period">
                    Generation Period
                  </label>
                  <div class="h-9 appearance-none flex w-full">
                    <input
                      class="col-span-3 h-9 appearance-none block w-1/2.6 text-gray-700 border border-gray-200 rounded py-3 px-4 leading-tight focus:outline-none focus:bg-white focus:border-gray-500"
                      id="gen-period-start"
                      type="time"
                      min="1:00"
                      max="12:00"
                      placeholder="1:00"
                    />
                    <input
                      class="ml-6 h-9 appearance-none flex- w-1/2.6 text-gray-700 border border-gray-200 rounded py-3 px-4 leading-tight focus:outline-none focus:bg-white focus:border-gray-500"
                      id="gen-period-end"
                      type="time"
                    />
                  </div>
                </div>
              </div>
              <div class="col-span-6 sm:col-span-3">
                <div class="w-full md:w-2/2">
                  <label class="label" for="minimum-time"> Minimum Time </label>
                  <input
                    class="h-9 appearance-none block w-full text-gray-700 border border-gray-200 rounded py-3 px-4 leading-tight focus:outline-none focus:bg-white focus:border-gray-500"
                    id="minimum-time"
                    type="time"
                    placeholder="2:00"
                  />
                </div>
              </div>
            </div>
            <div class="px-4 py-3 bg-white text-right sm:px-6">
              <button
                class="mr-2 inline-flex justify-center py-2 px-4 border border-transparent shadow-sm text-sm font-medium rounded-md text-black bg-gray-200 hover:bg-gray-400 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-gray-500"
                @click="close"
              >
                Cancel
              </button>
              <button
                class="inline-flex justify-center py-2 px-4 border border-transparent shadow-sm text-sm font-medium rounded-md text-white bg-indigo-600 hover:bg-indigo-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500 mr-30"
              >
                Save
              </button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "ScheduleRegister",
  data() {
    return { genTypeName: "Periodically" };
  },

  methods: {
    close() {
      this.$emit("close");
    },
    setOptions() {
      console.log("show");
    },
  },
});
</script>

<style>
.main-div {
  position: fixed;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  display: flex;
  justify-content: center;
  align-items: center;
}
.modal-backdrop {
  position: fixed;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  background-color: rgba(0, 0, 0, 0.3);
  display: flex;
  justify-content: center;
  align-items: center;
}
.label {
  @apply block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2;
}
</style>
