# Budibase-chartjs

## Description
A simple Budibase plugin allowoing users to pass on data directly to [svelte-chartjs](https://www.npmjs.com/package/svelte-chartjs)

Find out more about [Budibase](https://github.com/Budibase/budibase).

## A Warning
You probably don't want to use this plugin. Budibase built-in charts are much better in almost all situations.

I am not a full time developer or Budibase power user. This plugins breaks with several Budibase concepts (while you can of course manually reference data from a data provider in your chart data, there is no direct connection and no built-in logic). The plugin is only ever useful if you need full control over your Chart.js configuration (I've created this to overcome [a problem](https://github.com/Budibase/budibase/discussions/8442) I was having). It also supports only line charts at this point.

## Screenshot
![Screenshot](/screenshot.png?raw=true)

## Instructions

To build your new  plugin run the following in your Budibase CLI:
```
budi plugins --build
```

You can also re-build everytime you make a change to your plugin with the command:
```
budi plugins --watch
```

To use the plugin, provide a valid Chart.js dataset in the `Data` field, for example:

```json
{
    "labels": ["January", "February", "March", "April", "May", "June", "July"],
    "datasets": [{
        "label": "My First dataset",
        "fill": true,
        "lineTension": 0.3,
        "backgroundColor": "rgba(225, 204,230, .3)",
        "borderColor": "rgb(205, 130, 158)",
        "borderCapStyle": "butt",
        "borderDash": [],
        "borderDashOffset": 0,
        "borderJoinStyle": "miter",
        "pointBorderColor": "rgb(205, 130,1 58)",
        "pointBackgroundColor": "rgb(255, 255, 255)",
        "pointBorderWidth": 10,
        "pointHoverRadius": 5,
        "pointHoverBackgroundColor": "rgb(0, 0, 0)",
        "pointHoverBorderColor": "rgba(220, 220, 220,1)",
        "pointHoverBorderWidth": 2,
        "pointRadius": 1,
        "pointHitRadius": 10,
        "data": [65, 59, 80, 81, 56, 55, 40]
    }, {
        "label": "My Second dataset",
        "fill": true,
        "lineTension": 0.3,
        "backgroundColor": "rgba(184, 185, 210, .3)",
        "borderColor": "rgb(35, 26, 136)",
        "borderCapStyle": "butt",
        "borderDash": [],
        "borderDashOffset": 0,
        "borderJoinStyle": "miter",
        "pointBorderColor": "rgb(35, 26, 136)",
        "pointBackgroundColor": "rgb(255, 255, 255)",
        "pointBorderWidth": 10,
        "pointHoverRadius": 5,
        "pointHoverBackgroundColor": "rgb(0, 0, 0)",
        "pointHoverBorderColor": "rgba(220, 220, 220, 1)",
        "pointHoverBorderWidth": 2,
        "pointRadius": 1,
        "pointHitRadius": 10,
        "data": [28, 48, 40, 19, 86, 27, 90]
    }]
}
```

You can, of course, also include data from a data provider, for example when using JavaScript. This example assumes your Data provider is named `New Data Provider` and that columns `updated`, `col1` and `col2` exist.

```js
const columns = ['col1', 'col2'];
const labels = $("New Data Provider.Rows").map(e => e.updated);
const datasets = [];

for (col of columns) {
	datasets.push({
		label: col,
		data: $("New Data Provider.Rows").map(e => e[col])
	});	
}

return {
	labels: labels,
	datasets: datasets
};
```