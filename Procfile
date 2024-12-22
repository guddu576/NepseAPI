web: gunicorn apinepse.wsgi:application --log-file -
const ctx = document.getElementById('candlestickChart').getContext('2d');

// Example data for candlestick chart
const labels = ['14:25', '14:26', '14:27', '14:28', '14:29'];
const data = {
  labels: labels,
  datasets: [
    {
      label: 'NEPSE Index',
      data: [
        { x: '14:25', y: [2600, 2606, 2595, 2603] },
        { x: '14:26', y: [2603, 2608, 2600, 2605] },
        { x: '14:27', y: [2605, 2607, 2601, 2604] },
        { x: '14:28', y: [2604, 2609, 2603, 2606] },
        { x: '14:29', y: [2606, 2609, 2602, 2605] },
      ],
      borderColor: 'rgba(75, 192, 192, 1)',
      backgroundColor: 'rgba(75, 192, 192, 0.2)',
    },
  ],
};

const config = {
  type: 'line', // You can use "candlestick" type if a plugin supports it
  data: data,
  options: {
    responsive: true,
    plugins: {
      legend: {
        position: 'top',
      },
    },
    scales: {
      x: {
        type: 'category',
        title: {
          display: true,
          text: 'Time',
        },
      },
      y: {
        title: {
          display: true,
          text: 'Index Value',
        },
      },
    },
  },
};

new Chart(ctx, config);
