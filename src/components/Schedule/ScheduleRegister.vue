<template>
  <div class="modal-backdrop self-center">
    <div class="hidden sm:block" aria-hidden="true">
      <div class="py-5">
        <div class="border-t border-gray-200" />
      </div>
    </div>
    <div class="w-1/4 mt-10 sm:mt-0">
      <div class="mt-5 md:mt-0 md:col-span-2">
        <div class="shadow overflow-hidden sm:rounded-md">
          <div class="px-4 py-5 bg-white sm:p-6 rounded-2xl">
            <div v-if="isLoading" class="div-center">
              <VueLoader class="ml-20"></VueLoader>
            </div>
            <div class="grid grid-cols-6 gap-6">
              <div class="col-span-6 sm:col-span-3">
                <div class="col-span-6 sm:col-span-3">
                  <label
                    for="reports"
                    class="block text-sm font-medium text-gray-700"
                    >Report</label
                  >
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
                <label
                  for="genTypes"
                  class="block text-sm font-medium text-gray-700"
                  >Generation Type</label
                >
                <select
                  id="genTypeId"
                  name="genTypeName"
                  autocomplete="report-name"
                  class="mt-1 block w-full py-2 px-3 border border-gray-300 bg-white rounded-md shadow-sm focus:outline-none focus:ring-indigo-500 focus:border-indigo-500 sm:text-sm"
                  v-model="genTypeName"
                >
                  <option>Periodically</option>
                  <option>Specific</option>
                </select>
              </div>
            </div>
            <div class="col-span-6 sm:col-span-4">
              <label class="mt-3 block text-sm font-medium text-gray-700"
                >Time</label
              >
              <div
                class="h-10 pl-2 border border-gray-300 pt-1 w-28 bg-white shadow-md rounded-md"
              >
                <div class="flex">
                  <select
                    name="hours"
                    class="mr-2 bg-transparent text-md appearance-none outline-none"
                  >
                    <option v-for="index in 12" :key="index" value="num">
                      {{ index }}
                    </option>
                  </select>
                  <span class="text-xl mr-3">:</span>
                  <select
                    name="minutes"
                    class="bg-transparent text-md appearance-none outline-none mr-2"
                  >
                    <option value="00">00</option>
                    <option v-for="index in 59" :key="index" value="index">
                      {{ index < 10 ? "0" + index : index }}
                    </option>
                  </select>
                  <select
                    name="ampm"
                    class="bg-transparent text-md appearance-none outline-none"
                    v-if="genTypeName == 'Specific'"
                  >
                    <option value="am">AM</option>
                    <option value="pm">PM</option>
                  </select>
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
                @click="saveClick"
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
import VueLoader from "@/components/Shared/VueLoader.vue";

export default defineComponent({
  name: "ScheduleRegister",
  components: { VueLoader },

  data() {
    return { genTypeName: "Periodically", isLoading: false };
  },

  methods: {
    close() {
      this.$emit("close");
    },
    setOptions() {
      console.log("show");
    },
    saveClick() {
      this.isLoading = true;
    },
  },
});
</script>

<style>
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
.div-center {
  display: inline-block;
  position: fixed;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  width: 200px;
  height: 100px;
  margin: auto;
}
</style>
