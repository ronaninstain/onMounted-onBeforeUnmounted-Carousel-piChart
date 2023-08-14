<template>
  <div>
    <h2>Pie Chart</h2>
    <pie-chart :data="chartData" :options="chartOptions" />
  </div>
</template>

<script setup>
import { ref, onMounted, onBeforeUnmount } from "vue";
import { Pie, mixins } from "vue-chartjs";

const { reactiveProp } = mixins;

const chartData = ref(null);
const chartOptions = ref({
  responsive: true,
  maintainAspectRatio: false,
});

onMounted(() => {
  // Sample data for the pie chart
  const data = {
    labels: ["Category A", "Category B", "Category C"],
    datasets: [
      {
        data: [30, 20, 50],
        backgroundColor: ["#FF6384", "#36A2EB", "#FFCE56"],
      },
    ],
  };

  chartData.value = data;
});

onBeforeUnmount(() => {
  // Clean up any ongoing tasks or event listeners here
});
</script>

<script>
export default {
  extends: Pie,
  mixins: [reactiveProp],
  props: ["data", "options"],
  mounted() {
    this.renderChart(this.data, this.options);
  },
};
</script>
