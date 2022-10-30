<script>
  import { getContext } from 'svelte';
  import { Line } from 'svelte-chartjs';
  /* import { Bar } from 'svelte-chartjs'; */
  import 'chart.js/auto';

  export let chartdata;
  
  const { styleable } = getContext("sdk");
  const component = getContext("component");
</script>

<div use:styleable={$component.styles}>
  <Line data={ typeof chartdata === 'string' ? JSON.parse(chartdata) : chartdata } options={{ responsive: true }} />
</div>
