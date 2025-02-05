# CanvasJS Line Charts Cheatsheet

### Supported Line Chart Types
| Chart Type | `type` Value |
| ---------- |:------------:|
| Line       | "line"       |
| Spline     | "spline"     |
| Step Line  | "stepLine"   |

### Customizing Line Appearance
```
dataSeries: {
    lineThickness: 3, // Adjust thickness
    lineColor: "#4CAF50", // Custom line color
    lineDashType: "dash" // Options: solid, dash, dot, dashDot
}

```

### Adding Markers
```
dataSeries: {
    markerType: "triangle", // Options: circle, square, cross, triangle
    markerSize: 10, // Adjust size
    markerColor: "red" //Change Color
}
```

### Tooltips & Legends
```
toolTip: { shared: true },
legend: { cursor: "pointer", itemclick: toggleDataSeries }
```

### Multi-Series Line Chart
```
data: [
    { type: "line", name: "Series 1", showInLegend: true, dataPoints: [...] },
    { type: "line", name: "Series 2", showInLegend: true, dataPoints: [...] }
]
```

### Secondary Y-Axis
```
axisY2: { title: "Expenses", lineColor: "red", tickColor: "red", labelFontColor: "red" },
data: [
    { type: "line", name: "Sales", dataPoints: [...] },
    { type: "line", name: "Expenses", dataPoints: [...], axisYType: "secondary" }
]
```

### Enabling Data Labels
```
dataSeries: {
    indexLabel: "{y}",
    indexLabelFontSize: 14
}
```