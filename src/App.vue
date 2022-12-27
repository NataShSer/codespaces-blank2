<template>
  <div id="app">
    <BarComponent v-if="dataset.length > 0" :dataset="dataset" />
    <PieChart v-if="dataset.length > 0" :dataset="dataset" />
    <LineComponent v-if="dataset.length > 0" :dataset="dataset" />
  </div>
</template>

<script>
import BarComponent from './components/BarComponent.vue'
import PieChart from './components/PieChart.vue'
import LineComponent from './components/LineComponent.vue'

export default {
  name: 'App',
  components: {
    BarComponent,
    PieChart,
    LineComponent
  },
  data() {
    return {
      dataset: []
    }
  },
  created() {
    this.axios.get('data.json').then(response => {
      this.dataset = response.data
    })
  }
}
</script>