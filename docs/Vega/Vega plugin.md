
## Line Chart

```vega
{
  "width": 400,
  "height": 200,
  "data": [
    {
      "name": "table",
      "values": [
        { "x": 0, "y": 50 }, { "x": 1, "y": 0 },
        { "x": 2, "y": 30 }, { "x": 3, "y": 40 },
        { "x": 4, "y": 60 }, { "x": 5, "y": 25 }
      ]
    }
  ],
  "scales": [
    {
      "name": "x",
      "type": "point",
      "range": "width",
      "domain": { "data": "table", "field": "x" }
    },
    {
      "name": "y",
      "type": "linear",
      "range": "height",
      "domain": { "data": "table", "field": "y" }
    }
  ],
  "axes": [
    { "orient": "bottom", "scale": "x" },
    { "orient": "left", "scale": "y" }
  ],
  "marks": [
    {
      "type": "line",
      "from": { "data": "table" },
      "encode": {
        "enter": {
          "x": { "scale": "x", "field": "x" },
          "y": { "scale": "y", "field": "y" },
          "interpolate": { "value": "monotone" }
        }
      }
    }
  ]
}
```