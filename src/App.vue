<script setup>
  import { ref } from 'vue'

  const series = ref([
    {
      name: 'Прочее',
      data: [44, 55, 41, 67, 22, 43],
    },
    {
      name: 'ЗП',
      data: [13, 23, 20, 8, 13, 27],
    },
    {
      name: 'Мясо',
      data: [11, 17, 15, 15, 21, 14],
    },
  ])

  const chartOptions = ref({
    colors: ['#9747FF', '#0077F7', '#13D6FF'],
    theme: {
      mode: 'dark',
    },
    chart: {
      type: 'bar',
      height: 350,
      stacked: true,
      toolbar: {
        show: false,
      },
      zoom: {
        enabled: false,
      },
    },
    responsive: [
      {
        breakpoint: 480,
        options: {
          legend: {
            position: 'bottom',
            offsetX: -10,
            offsetY: 0,
          },
        },
      },
    ],
    plotOptions: {
      bar: {
        horizontal: false,
        borderRadius: 10,
        dataLabels: {
          total: {
            enabled: false,
          },
        },
      },
    },
    xaxis: {
      type: 'category',
      categories: ['Январь', 'Февраль', 'Март', 'Апрель', 'Май', 'Июнь'],
      colors: ['#000'],
    },
    legend: {
      show: false,
    },
    fill: {
      opacity: 1,
    },
  })
</script>

<template>
  <div>
    <h1>ОБЩАЯ ВЫРУЧКА</h1>
    <div class="data">
      <div class="data__item">
        <h3>Общее оплачено</h3>
        <span>1 123 500 ₽ </span>
      </div>
      <div class="data__item">
        <h3>Деньги за мясо</h3>
        <span>145 200 ₽ </span>
      </div>
      <div class="data__item">
        <h3>Расходы на ЗП</h3>
        <span>1 223 500 ₽ </span>
      </div>
      <div class="data__item">
        <h3>Прочее</h3>
        <span>23 500 ₽ </span>
      </div>
    </div>
    <apexchart
      type="bar"
      height="350"
      class="chart"
      :options="chartOptions"
      :series="series"
    ></apexchart>
  </div>
</template>

<style>
  h1 {
    font-size: 18px;
    letter-spacing: -0.108px;
    text-transform: uppercase;
    margin-bottom: 34px;
  }

  .data {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 31px;
  }

  .data__item {
    position: relative;
  }

  .data__item::before {
    content: '';
    position: absolute;
    top: 0;
    right: -25%;
    width: 1px;
    height: 100%;
    background-color: #272b33;
    transform: translateX(50%);
  }

  .data__item h3 {
    color: #93969c;
    font-size: 14px;
    text-transform: uppercase;
    margin-bottom: 16px;
  }

  .data__item:not(:first-child) h3 {
    position: relative;
    padding-left: 15px;
  }

  .data__item:not(:first-child) h3::before {
    content: '';
    position: absolute;
    top: 50%;
    left: 0;
    width: 6px;
    height: 6px;
    background-color: #9747ff;
    border-radius: 50%;
    transform: translateY(-50%);
  }

  .data__item:nth-child(3n) h3::before {
    background-color: #0077f7;
  }
  .data__item:nth-child(4n) h3::before {
    background-color: #13d6ff;
  }

  .data__item span {
    font-variant-numeric: lining-nums tabular-nums;
    font-size: 24px;
  }

  .chart {
    background-color: transparent !important;
    color: black;
  }

  .apexcharts-svg {
    background-color: transparent !important;
  }

  .apexcharts-svg line {
    background: #292829 !important;
    color: #292829 !important;
  }
</style>
