<template>
  <div class="chart-container">
    <Doughnut :data="chartData" :options="chartOptions" />
  </div>
</template>

<script>
import {
  Chart as ChartJS,
  ArcElement,
  Tooltip,
  Legend
} from 'chart.js'
import { Doughnut } from 'vue-chartjs'

ChartJS.register(
  ArcElement,
  Tooltip,
  Legend
)

export default {
  name: 'TopAlertingDBPieChart',
  components: { Doughnut },
  data() {
    return {
      chartData: {
        labels: ['Oracle – HRMS'],
        datasets: [
          {
            data: [100],
            backgroundColor: [
              '#fc8181'
            ],
            borderColor: '#1a1b1e',
            borderWidth: 2
          }
        ]
      },
      chartOptions: {
        responsive: true,
        maintainAspectRatio: false,
        plugins: {
          legend: {
            position: 'top',
            labels: {
              color: '#e4e6eb',
              boxWidth: 12,
              padding: 10
            }
          },
          tooltip: {
            backgroundColor: '#242526',
            titleColor: '#e4e6eb',
            bodyColor: '#e4e6eb',
            borderColor: '#3a3b3c',
            borderWidth: 1,
            callbacks: {
              label: function(context) {
                return `${context.label}: ${context.raw}%`;
              }
            }
          }
        },
        cutout: '70%'
      }
    }
  }
}
</script>

<style scoped>
.chart-container {
  width: 100%;
  height: 100%;
  background: #1a1b1e;
  border-radius: 8px;
  padding: 0.75rem;
  border: 1px solid #3a3b3c;
}
</style> 