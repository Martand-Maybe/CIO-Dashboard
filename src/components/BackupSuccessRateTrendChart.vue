<template>
  <div class="chart-container">
    <Line :data="chartData" :options="chartOptions" />
  </div>
</template>

<script>
import {
  Chart as ChartJS,
  CategoryScale,
  LinearScale,
  PointElement,
  LineElement,
  Title,
  Tooltip,
  Legend
} from 'chart.js'
import { Line } from 'vue-chartjs'

ChartJS.register(
  CategoryScale,
  LinearScale,
  PointElement,
  LineElement,
  Title,
  Tooltip,
  Legend
)

export default {
  name: 'BackupSuccessRateTrendChart',
  components: { Line },
  data() {
    return {
      chartData: {
        labels: ['Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat', 'Sun'],
        datasets: [
          {
            label: 'Backup Success Rate %',
            data: [98.8, 98.9, 98.9, 98.9, 99.0, 98.9, 98.9],
            borderColor: '#f6ad55',
            backgroundColor: 'rgba(246, 173, 85, 0.1)',
            tension: 0.4,
            fill: true,
            pointBackgroundColor: '#f6ad55',
            pointBorderColor: '#fff',
            pointRadius: 4
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
                return `${context.dataset.label}: ${context.raw}%`;
              }
            }
          }
        },
        scales: {
          x: {
            grid: {
              color: '#3a3b3c'
            },
            ticks: {
              color: '#b0b3b8'
            }
          },
          y: {
            beginAtZero: false,
            min: 98.7,
            max: 99.1,
            grid: {
              color: '#3a3b3c'
            },
            ticks: {
              color: '#b0b3b8',
              callback: function(value) {
                return value + '%';
              }
            }
          }
        }
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