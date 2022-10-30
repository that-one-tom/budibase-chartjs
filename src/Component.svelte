<script>
  import { getContext } from 'svelte';
  import { Line } from 'svelte-chartjs';
  /* import { Bar } from 'svelte-chartjs'; */
  import 'chart.js/auto';

  export let chartdata;
  export let chartoptions;
  
  const { styleable } = getContext("sdk");
  const component = getContext("component");
</script>

<div use:styleable={$component.styles}>
  <Line data={ typeof chartdata === 'string' ? JSON.parse(chartdata) : chartdata } options={Object.assign({ responsive: true }, typeof chartoptions === 'string' ? JSON.parse(chartoptions) : chartoptions)} />
</div>
