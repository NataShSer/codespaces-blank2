<template>
    <Pie
      :chart-options="chartOptions"
      :chart-data="chartData"
      :chart-id="chartId"
      :dataset-id-key="datasetIdKey"
      :plugins="plugins"
      :css-classes="cssClasses"
      :styles="styles"
      :width="width"
      :height="height"
    />
  </template>
  
  <script>
  import { Pie } from 'vue-chartjs/legacy'
  
  import {
    Chart as ChartJS,
    Title,
    Tooltip,
    Legend,
    ArcElement,
    CategoryScale
  } from 'chart.js'
  
  ChartJS.register(Title, Tooltip, Legend, ArcElement, CategoryScale)
  
  export default {
    name: 'PieChart',
    components: {
      Pie
    },
    props: {
      chartId: {
        type: String,
        default: 'pie-chart'
      },
      datasetIdKey: {
        type: String,
        default: 'label'
      },
      width: {
        type: Number,
        default: 400
      },
      height: {
        type: Number,
        default: 400
      },
      cssClasses: {
        default: '',
        type: String
      },
      styles: {
        type: Object,
        default: () => {}
      },
      plugins: {
        type: Array,
        default: () => []
      },
      dataset: Array
    },
    data() {
      return {
        chartData: {
          labels: ["bachelor's degree", "some college", "master's degree", "associate's degree", "high school", "some high school"],
          datasets: [
            {
              backgroundColor: ['#41B883', '#E46651', '#00D8FF', '#DD1B16', '#FF1493', '#00FFFF'],
              data: [0, 0, 0, 0, 0, 0]
            }
          ]
        },
        chartOptions: {
          responsive: true,
          maintainAspectRatio: false
        }
      }
    },
    created() {
        this.dataset.forEach(student => {
        if (student["parental level of education"] == "bachelor's degree")
            this.chartData.datasets[0].data[0]++;
        else if (student["parental level of education"] == "some college")
            this.chartData.datasets[0].data[1]++;
        else if (student["parental level of education"] == "master's degree")
            this.chartData.datasets[0].data[2]++;
        else if (student["parental level of education"] == "associate's degree")
            this.chartData.datasets[0].data[3]++;
        else if (student["parental level of education"] == "high school")
            this.chartData.datasets[0].data[4]++;
        else if (student["parental level of education"] == "some high school")
            this.chartData.datasets[0].data[5]++;
        });
  }
}
  </script>
