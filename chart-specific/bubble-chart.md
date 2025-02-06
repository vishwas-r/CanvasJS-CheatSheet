# CanvasJS Bubble Chart Cheatsheet
Bubble charts are used to visualize three dimensions of data: x, y, and z (size of the bubble).

### Key Bubble Chart Properties
**Data Point Properties**
- `x`: X-axis value.
- `y`: Y-axis value.
- `z`: Size of the bubble (third dimension).
- `color`: Custom color for the bubble.
- `name`: Name/title of the bubble (displayed in tooltips/legends).
- `markerType`: Customize the marker shape ("circle", "square", "triangle", etc.).
- `markerColor`: Customize the marker color.

**Series Properties**
- `type`: Set to "bubble".
- `showInLegend`: Show/hide the series in the legend (default: false).
- `toolTipContent`: Customize tooltip content (e.g., "{name}: {x}, {y}, {z}").

### Customizing Bubbles
Customize individual bubbles using dataPoints:
```
dataPoints: [
  { x: 10, y: 45, z: 20, color: "red", name: "Bubble 1", markerType: "square" },
  { x: 20, y: 14, z: 30, color: "blue", name: "Bubble 2", markerType: "triangle" },
  { x: 30, y: 20, z: 40, color: "green", name: "Bubble 3", markerType: "circle" }
]
```

### Tooltip Customization
Customize tooltips to display additional information:
```
data: [{
  type: "bubble",
  toolTipContent: "<b>{name}</b><br>X: {x}<br>Y: {y}<br>Size: {z}",
  dataPoints: [
    { x: 10, y: 45, z: 20, name: "Point 1" },
    { x: 20, y: 14, z: 30, name: "Point 2" }
  ]
}]
```
