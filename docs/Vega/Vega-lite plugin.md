## Horizontal bar chart

```vega-lite
{ "$schema": "https://vega.github.io/schema/vega-lite/v5.json", "description": "A bar chart with negative values. We can hide the axis domain line, and instead use a conditional grid color to draw a zero baseline.", "data": { "values": [ {"a": "A", "b": -28}, {"a": "B", "b": 55}, {"a": "C", "b": -33}, {"a": "D", "b": 91}, {"a": "E", "b": 81}, {"a": "F", "b": 53}, {"a": "G", "b": -19}, {"a": "H", "b": 87}, {"a": "I", "b": 52} ] }, "encoding": { "y": { "field": "a", "type": "nominal", "axis": { "domain": false, "ticks": false, "labelAngle": 0, "labelPadding": 4 } }, "x": { "field": "b", "type": "quantitative", "scale": {"padding": 20}, "axis": { "gridColor": { "condition": {"test": "datum.value === 0", "value": "black"}, "value": "#ddd" } } } }, "layer": [ {"mark": "bar"}, { "mark": { "type": "text", "align": {"expr": "datum.b < 0 ? 'right' : 'left'"}, "dx": {"expr": "datum.b < 0 ? -2 : 2"} }, "encoding": {"text": {"field": "b", "type": "quantitative"}} } ] }
```


## Histogram

```vega-lite
{ "$schema": "https://vega.github.io/schema/vega-lite/v5.json", "data": { "values": [ {"bin_start": 8, "bin_end": 10, "count": 7}, {"bin_start": 10, "bin_end": 12, "count": 29}, {"bin_start": 12, "bin_end": 14, "count": 71}, {"bin_start": 14, "bin_end": 16, "count": 127}, {"bin_start": 16, "bin_end": 18, "count": 94}, {"bin_start": 18, "bin_end": 20, "count": 54}, {"bin_start": 20, "bin_end": 22, "count": 17}, {"bin_start": 22, "bin_end": 24, "count": 5} ] }, "mark": "bar", "encoding": { "x": { "field": "bin_start", "bin": {"binned": true, "step": 2} }, "x2": {"field": "bin_end"}, "y": { "field": "count", "type": "quantitative" } } }
```

## Line Chart

```vega-lite
{ "$schema": "https://vega.github.io/schema/vega-lite/v5.json", "description": "Plots two functions using a generated sequence.", "width": 300, "height": 150, "data": { "sequence": { "start": 0, "stop": 12.7, "step": 0.1, "as": "x" } }, "transform": [ { "calculate": "sin(datum.x)", "as": "sin(x)" }, { "calculate": "cos(datum.x)", "as": "cos(x)" }, { "fold": ["sin(x)", "cos(x)"] } ], "mark": "line", "encoding": { "x": { "type": "quantitative", "field": "x" }, "y": { "field": "value", "type": "quantitative" }, "color": { "field": "key", "type": "nominal", "title": null } } }
```

## Grid of Bar Charts

```vega-lite
{ "$schema": "https://vega.github.io/schema/vega-lite/v5.json", "description": "A simple grid of bar charts to compare performance data.", "data": { "values": [ {"a": "a1", "b": "b1", "c": "x", "p": "0.14"}, {"a": "a1", "b": "b1", "c": "y", "p": "0.60"}, {"a": "a1", "b": "b1", "c": "z", "p": "0.03"}, {"a": "a1", "b": "b2", "c": "x", "p": "0.80"}, {"a": "a1", "b": "b2", "c": "y", "p": "0.38"}, {"a": "a1", "b": "b2", "c": "z", "p": "0.55"}, {"a": "a1", "b": "b3", "c": "x", "p": "0.11"}, {"a": "a1", "b": "b3", "c": "y", "p": "0.58"}, {"a": "a1", "b": "b3", "c": "z", "p": "0.79"}, {"a": "a2", "b": "b1", "c": "x", "p": "0.83"}, {"a": "a2", "b": "b1", "c": "y", "p": "0.87"}, {"a": "a2", "b": "b1", "c": "z", "p": "0.67"}, {"a": "a2", "b": "b2", "c": "x", "p": "0.97"}, {"a": "a2", "b": "b2", "c": "y", "p": "0.84"}, {"a": "a2", "b": "b2", "c": "z", "p": "0.90"}, {"a": "a2", "b": "b3", "c": "x", "p": "0.74"}, {"a": "a2", "b": "b3", "c": "y", "p": "0.64"}, {"a": "a2", "b": "b3", "c": "z", "p": "0.19"}, {"a": "a3", "b": "b1", "c": "x", "p": "0.57"}, {"a": "a3", "b": "b1", "c": "y", "p": "0.35"}, {"a": "a3", "b": "b1", "c": "z", "p": "0.49"}, {"a": "a3", "b": "b2", "c": "x", "p": "0.91"}, {"a": "a3", "b": "b2", "c": "y", "p": "0.38"}, {"a": "a3", "b": "b2", "c": "z", "p": "0.91"}, {"a": "a3", "b": "b3", "c": "x", "p": "0.99"}, {"a": "a3", "b": "b3", "c": "y", "p": "0.80"}, {"a": "a3", "b": "b3", "c": "z", "p": "0.37"} ] }, "width": 60, "height": {"step": 8}, "spacing": 5, "mark": "bar", "encoding": { "y": {"field": "c", "type": "nominal", "axis": null}, "x": { "field": "p", "type": "quantitative", "axis": {"format": "%"}, "title": null }, "color": { "field": "c", "type": "nominal", "legend": {"orient": "bottom", "titleOrient": "left"}, "title": "settings" }, "row": {"field": "a", "title": "Factor A", "header": {"labelAngle": 0}}, "column": {"field": "b", "title": "Factor B"} } }
```

## Stacked Bar Chart

```vega-lite
{ "$schema": "https://vega.github.io/schema/vega-lite/v5.json", "data": {"url": "assets/data/seattle-weather.csv"}, "mark": {"type": "bar", "cornerRadiusTopLeft": 3, "cornerRadiusTopRight": 3}, "encoding": { "x": {"timeUnit": "month", "field": "date", "type": "ordinal"}, "y": {"aggregate": "count"}, "color": {"field": "weather"} } }
```

## World Population

```vega-lite
{
  "$schema": "https://vega.github.io/schema/vega-lite/v5.json",
  "data": {
    "url": "/assets/data/population.csv",
    "format": {"type": "csv"},
    "filter": {"field": "Country Name", "equal": "Germany"}
  },
  "mark": "line",
  "encoding": {
    "x": {"field": "Year", "type": "temporal", "axis": {"title": "Year"}},
    "y": {"field": "Value", "type": "quantitative", "axis": {"title": "Population (in billions)"}, "scale": {"zero": false}}
  }
}

```

## Chart from file

```vega-lite 
{ "description": "A simple bar chart with embedded data.", "data": {"url" : "assets/charts/chart_basic_bar_chart.json"}, "mark": {"type": "bar", "tooltip": true}, "encoding": { "x": {"field": "a", "type": "nominal", "axis": {"labelAngle": 0}}, "y": {"field": "b", "type": "quantitative"} } } 
```

And much more you can find on the website.[^1]

[^1]: https://vega.github.io/vega-lite/examples/