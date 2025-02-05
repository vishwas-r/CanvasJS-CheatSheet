# CanvasJS-CheatSheet

### Basic Setup
Include CanvasJS Library
```
<script src="https://cdn.canvasjs.com/canvasjs.min.js"></script>
```

Basic HTML Structure
```
<div id="chartContainer" style="height: 300px; width: 100%;"></div>
```

### Creating a Chart
```
//Initialize the chart
var chart = new CanvasJS.Chart("chartContainer", {
    animationEnabled: true, // Enable animations
    title: {
        text: "Chart Title" // Chart title
    },
    axisX: {
        title: "X-Axis Title" // X-axis title
    },
    axisY: {
        title: "Y-Axis Title" // Y-axis title
    },
    data: [{ // Data series
        type: "column", // Chart type
        dataPoints: [ // Data points
            { label: "Category 1", y: 10 },
            { label: "Category 2", y: 15 },
            { label: "Category 3", y: 25 }
        ]
    }]
});

// Render the chart
chart.render();
```

### Chart Types
Common Chart Types
- ```type: "line"``` - Line Chart
- ```type: "column"``` - Column Chart
- ```type: "bar"``` - Bar Chart
- ```type: "pie"``` - Pie Chart
- ```type: "area"``` - Area Chart
- ```type: "spline"``` - Spline Chart
- ```type: "scatter"``` - Scatter Chart
- ```type: "bubble"``` - Bubble Chart

### Data Points
DataPoint Structure
```
dataPoints: [
    { label: "Category 1", y: 10 },
    { label: "Category 2", y: 20, color: "red" }, // Custom color
    { label: "Category 3", y: 30, indexLabel: "Highest" } // Index label
]
```

Dynamic Data Points
```
var dataPoints = [];
for (var i = 0; i < 10; i++) {
    dataPoints.push({ label: "Point " + i, y: Math.random() * 100 });
}
```

### Customization
Axis Customization
```
axisX: {
    title: "X-Axis",
    interval: 1, // Interval between labels
    labelAngle: -45, // Rotate labels
    gridThickness: 1 // Grid line thickness
},
axisY: {
    title: "Y-Axis",
    includeZero: true // Include zero in the scale
}
```

Legend Customization
```
legend: {
    cursor: "pointer", // Change cursor on hover
    itemclick: function (e) {
        // Toggle data series visibility on legend click
        if (typeof (e.dataSeries.visible) === "undefined" || e.dataSeries.visible) {
            e.dataSeries.visible = false;
        } else {
            e.dataSeries.visible = true;
        }
        chart.render();
    }
}
```

Tooltip Customization
```
toolTip: {
    shared: true, // Shared tooltip for multiple series
    content: "{label}: {y}" // Custom tooltip content
}
```

### Advanced Features
Multiple Data Series
```
data: [
    {
        type: "column",
        name: "Series 1",
        dataPoints: [{ label: "A", y: 10 }, { label: "B", y: 20 }]
    },
    {
        type: "line",
        name: "Series 2",
        dataPoints: [{ label: "A", y: 15 }, { label: "B", y: 25 }]
    }
]
```

Dynamic Updates
```
function updateChart() {
    var newDataPoint = { label: "New Point", y: Math.random() * 100 };
    chart.options.data[0].dataPoints.push(newDataPoint);
    chart.render();
}
```

Export Chart as Image
```
chart.exportChart({ format: "png" }); // Options: "png", "jpg"
```

### Event Handling
Data Point Click Event
```
data: [{
    type: "column",
    dataPoints: [{ label: "A", y: 10, click: function(e) { alert("Clicked!"); } }]
}]
```

### Useful Methods
- Render/update the chart - ```chart.render()```
- Destroy the chart instance - ```chart.destroy()```
- Export the chart as image - ```chart.exportChart(options)```
- Add data points dynamically - ```chart.data[seriesIndex].addTo(dataPoints, {y: 29, label: "Apple" })```

### Example: Line Chart with Dynamic Data
```
var chart = new CanvasJS.Chart("chartContainer", {
    title: { text: "Dynamic Line Chart" },
    data: [{
        type: "line",
        dataPoints: []
    }]
});

var xVal = 0;
var updateInterval = 1000; // Update every second
var dataLength = 20; // Number of data points to show

function updateChart() {
    var yVal = Math.random() * 100;
    chart.options.data[0].dataPoints.push({ x: xVal, y: yVal });
    if (chart.options.data[0].dataPoints.length > dataLength) {
        chart.options.data[0].dataPoints.shift();
    }
    xVal++;
    chart.render();
}
setInterval(updateChart, updateInterval);
```