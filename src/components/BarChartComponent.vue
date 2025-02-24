<template>
   
    <div>
        <div>
        <p class="text">Bar Chart - Displaying the height differnces</p>
    </div>
      <canvas ref="barChartCanvas"></canvas>
    </div>
  </template>
  
  <script>
  import { Chart } from 'chart.js/auto';
  import { mockData } from "@/mock-data/mockdata";
  
  export default {
    name: "BarChart",
    data() {
      return {
        jsonData: mockData,
        chart: null
      };
    },
    mounted() {
      this.createChart();
    },
    methods: {
      createChart() {
        const heightRanges = {
          "151cm - 160cm": 0,
          "161cm - 170cm": 0,
          "171cm - 180cm": 0
        };
  
        const totalPeople = this.jsonData.length;
  
        this.jsonData.forEach(person => {
          if (person.height >= 151 && person.height <= 160) {
            heightRanges["151cm - 160cm"]++;
          } else if (person.height >= 161 && person.height <= 170) {
            heightRanges["161cm - 170cm"]++;
          } else if (person.height >= 171 && person.height <= 180) {
            heightRanges["171cm - 180cm"]++;
          }
        });
  
        const percentages = Object.values(heightRanges).map(count => (count / totalPeople) * 100);
  
        const ctx = this.$refs.barChartCanvas.getContext('2d');
  
        this.chart = new Chart(ctx, {
          type: 'bar',
          data: {
            labels: Object.keys(heightRanges),
            datasets: [{
              label: 'Percentage of People Height',
              data: percentages,
              backgroundColor: ['#FF6384', '#36A2EB', '#FFCE56'],
              borderColor: ['#FF6384', '#36A2EB', '#FFCE56'],
              borderWidth: 1
            }]
          },
          options: {
            responsive: true,
            maintainAspectRatio: false,
            scales: {
              y: {
                beginAtZero: true,
                max: 100,
                title: {
                  display: true,
                  text: 'Percentage (%)'
                }
              }
            }
          }
        });
      }
    }
  };
  </script>
  
  <style scoped>
  canvas {
    width: 100% !important;
    height: 400px !important;
  }
  .text {
    font-size: 20px;
    font-weight: bolder;

  }
  </style>
  