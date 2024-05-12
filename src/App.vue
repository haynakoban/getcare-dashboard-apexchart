<script setup>
import { ref } from "vue";

// const options = ref({});
const sex = ref(["Male", "Female"]);

const pFeedbackSeries = ref([40, 60]);
const pFeedbackOptions = ref({
  chart: { type: "donut" },
  labels: ["Male", "Female"],
  dataLabels: { enabled: false },
  colors: ["#874CCC", "#FB6D48"],
  title: { text: "Patient Feedback by Sex" },
});

const pSatisfactionSeries = ref([59.19, 22.28, 13.32, 5.21]);
const pSatisfactionOptions = ref({
  chart: { type: "donut" },
  labels: ["Excellent", "Average", "Good", "Poor"],
  dataLabels: { enabled: false },
  colors: ["#874CCC", "#FB6D48", "#FFE6E6", "#524C42"],
  title: { text: "Patient Satisfaction" },
});

const pConsultTimeSeries = ref([{ data: [25, 15, 30, 10, 45, 20] }]);
const pConsultTimeOptions = ref({
  chart: { type: "bar" },
  xaxis: {
    categories: [
      ["Cardiology"],
      ["Dermatology"],
      ["Neurology"],
      ["Ophthalmology"],
      ["Orthopedics"],
      ["Pediatrics"],
    ],
  },
  yaxis: {
    title: { text: "Consulting Time" },
    min: function (min) {
      return min;
    },
    max: function (max) {
      return max;
    },
    show: true,
    stepSize: 10,
  },
  plotOptions: {
    bar: {
      columnWidth: "45%",
      distributed: true,
    },
  },
  dataLabels: { enabled: false },
  colors: ["#874CCC", "#FB6D48", "#FFE6E6", "#524C42", "#7469B6", "#E1AFD1"],
  title: { text: "Average Visit Length by Department" },
  responsive: [
    {
      breakpoint: 600,
      options: { chart: { width: "100%" }, title: { margin: 40 } },
    },
    {
      breakpoint: 2100,
      options: { chart: { width: 600 } },
    },
  ],
});

const pWaitingTimeSeries = ref([{ data: [20, 25, 40, 15, 30, 40] }]);
const pWaitingTimeOptions = ref({
  chart: { type: "bar" },
  xaxis: {
    categories: [
      ["Cardiology"],
      ["Dermatology"],
      ["Neurology"],
      ["Ophthalmology"],
      ["Orthopedics"],
      ["Pediatrics"],
    ],
  },
  yaxis: {
    title: { text: "Waiting Time" },
    min: function (min) {
      return min;
    },
    max: function (max) {
      return max;
    },
    show: true,
    stepSize: 10,
  },
  plotOptions: {
    bar: {
      columnWidth: "45%",
      distributed: true,
    },
  },
  dataLabels: { enabled: false },
  colors: ["#874CCC", "#FB6D48", "#FFE6E6", "#524C42", "#7469B6", "#E1AFD1"],
  title: { text: "Average Wait Length by Department" },
  responsive: [
    {
      breakpoint: 500,
      options: { chart: { width: "100%" }, title: { margin: 40 } },
    },
    {
      breakpoint: 2100,
      options: { chart: { width: 600 } },
    },
  ],
});

const pPerMonthSeries = ref([
  {
    name: "Male",
    data: [20, 45, 38, 55, 79, 120, 105, 152, 185, 178, 201, 230],
  },
  {
    name: "Female",
    data: [42, 65, 23, 80, 100, 142, 105, 175, 190, 220, 156, 292],
  },
]);
const pPerMonthOptions = ref({
  chart: { type: "line" },
  xaxis: {
    categories: [
      "Jan",
      "Feb",
      "Mar",
      "Apr",
      "May",
      "Jun",
      "Jul",
      "Aug",
      "Sep",
      "Oct",
      "Nov",
      "Dec",
    ],
  },
  yaxis: {
    title: { text: "Number of Patient" },
    show: true,
  },
  dataLabels: { enabled: false },
  title: { text: "Patient Per Month of 2024 by Sex" },
  responsive: [
    {
      breakpoint: 600,
      options: { chart: { width: "100%" }, title: { margin: 40 } },
    },
    {
      breakpoint: 2100,
      options: { chart: { width: 600 } },
    },
  ],
});
</script>

<template>
  <div class="px-5 py-2.5 shadow-lg">
    <h1 class="text-xl font-semibold">Patient Experience Analysis Dashboad</h1>
  </div>
  <div class="flex p-5 gap-5 flex-col xl:flex-row">
    <div class="w-full xl:w-[60%]">
      <!-- filter section -->
      <section class="flex gap-5 flex-col md:flex-row">
        <div class="flex-grow">
          <div
            class="w-full py-5 px-2.5 bg-white border border-gray-300 rounded-lg shadow-lg"
          >
            <p class="w-full mb-3 font-semibold text-gray-800">Day of Week</p>
            <select
              class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg block w-full p-2.5"
            >
              <option value="">All</option>
              <option value="1">Monday</option>
              <option value="2">Tuesday</option>
              <option value="3">Wednesday</option>
              <option value="4">Thursday</option>
              <option value="5">Friday</option>
              <option value="6">Saturday</option>
              <option value="7">Sunday</option>
            </select>
          </div>
        </div>
        <div class="flex-grow">
          <div
            class="w-full py-5 px-2.5 bg-white border border-gray-300 rounded-lg shadow-lg"
          >
            <p class="w-full mb-3 font-semibold text-gray-800">Department</p>
            <select
              class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg block w-full p-2.5"
            >
              <option value="">All</option>
              <option value="Cardiology">Cardiology</option>
              <option value="Dermatology">Dermatology</option>
              <option value="Neurology">Neurology</option>
              <option value="Ophthalmology">Ophthalmology</option>
              <option value="Orthopedics">Orthopedics</option>
              <option value="Pediatrics">Pediatrics</option>
            </select>
          </div>
        </div>
        <div class="flex-grow">
          <div
            class="w-full py-5 px-2.5 bg-white border border-gray-300 rounded-lg shadow-lg"
          >
            <p class="w-full mb-3 font-semibold text-gray-800">Sex</p>
            <select
              class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg block w-full p-2.5"
            >
              <option value="">All</option>
              <option v-for="(value, index) in sex" :key="index" :value="value">
                {{ value }}
              </option>
            </select>
          </div>
        </div>
      </section>
      <section class="flex gap-5 mt-5 flex-col md:flex-row">
        <div class="flex-grow">
          <div
            class="flex justify-center w-full h-full py-5 px-2.5 bg-white border border-gray-300 rounded-lg shadow-lg"
          >
            <apexchart
              width="350"
              type="donut"
              :options="pFeedbackOptions"
              :series="pFeedbackSeries"
            ></apexchart>
          </div>
        </div>
        <div class="flex-grow">
          <div
            class="flex justify-center w-full h-full py-5 px-2.5 bg-white border border-gray-300 rounded-lg shadow-lg"
          >
            <apexchart
              width="350"
              type="donut"
              :options="pSatisfactionOptions"
              :series="pSatisfactionSeries"
            ></apexchart>
          </div>
        </div>
      </section>

      <section class="flex gap-5 mt-5 flex-col md:flex-row">
        <div class="flex-grow">
          <div
            class="flex justify-center w-full h-full py-5 px-2.5 bg-white border border-gray-300 rounded-lg shadow-lg"
          >
            <apexchart
              height="370"
              :options="pPerMonthOptions"
              :series="pPerMonthSeries"
            ></apexchart>
          </div>
        </div>
      </section>
    </div>
    <div class="w-full xl:w-[40%]">
      <section class="flex flex-col gap-5">
        <div>
          <div
            class="flex justify-center w-full h-full py-5 px-2.5 bg-white border border-gray-300 rounded-lg shadow-lg"
          >
            <apexchart
              width="500"
              height="370"
              :options="pConsultTimeOptions"
              :series="pConsultTimeSeries"
            ></apexchart>
          </div>
        </div>
        <div>
          <div
            class="flex justify-center w-full h-full py-5 px-2.5 bg-white border border-gray-300 rounded-lg shadow-lg"
          >
            <apexchart
              width="500"
              height="370"
              :options="pWaitingTimeOptions"
              :series="pWaitingTimeSeries"
            ></apexchart>
          </div>
        </div>
      </section>
    </div>
  </div>
</template>

<style scoped></style>
