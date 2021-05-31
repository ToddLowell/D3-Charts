# D3 Charts

This repo is a collection of my D3.js projects.

## Charts

- Scatterplot
- Bar Plot
- Line Plot

---

## .join( ) vs .enter( ), .merge( ), .exit( )

### .join( )

```js
const chartValues = svg
  .selectAll('g')
  .data(bins)
  .join('g');
```

### .join( ) allows entering, updating and exiting elements to be targeted individually 

```js
const chartValues = svg
  .selectAll('g')
  .data(bins)
  .join(
    (enter) => enter.append('g'),
    (update) => update,
    (exit) => exit.remove()
  );
```

### .enter( ), .merge( ), .exit( )

```js
// retrieve current points
let chartValues = svg.selectAll('g').data(bins);

// remove old points
chartValues.exit().remove();

// select new points
const newChartValues = chartValues.enter().append('g');

// update current points to include new points
chartValues = newChartValues.merge(chartValues);
```