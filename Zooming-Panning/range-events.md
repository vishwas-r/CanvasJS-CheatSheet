## rangeChanging & rangeChanged

[rangeChanging](https://canvasjs.com/docs/charts/chart-options/range-changing/) and [rangeChanged](https://canvasjs.com/docs/charts/chart-options/range-changed/) are events related to the viewport range in CanvasJS charts, but they serve different purposes:

### rangeChanging:
* Triggered: Just before the range of the chart is about to be changed, before rendering takes place.
* Use: Useful for modifying chart options based on the new range before the chart updates. You can access details about the new range (minimum and maximum values) through the event object.
* Note: Changes made to chart options within the rangeChanging event handler **do not require calling the render method` afterwards.

### rangeChanged:
* Triggered: After the chart has been rendered with the updated viewport range.
* Use: Suitable for tasks that need to react to the finalized change in the range, such as:
  * Updating external data based on the new range.
  * Triggering other actions or calculations dependent on the new range.
* Note: If you need to update the chart itself based on the new range, you need to call the render method within the rangeChanged event handler.

| Feature      | rangeChanging                            | rangeChanged                                            |
|--------------|------------------------------------------|---------------------------------------------------------|
| Triggered    | Before rendering, with new range details | After rendering, with finalized range                   |
| Use          | Modify chart options based on new range  | React to finalized range change                         |
| Update Chart | Not required within the event handler    | Requires calling render method within the event handler |

##### Note:
* Events are triggered only for manual changes (zoom/pan/reset) performed via mouse/pointer and not for programmatic changes using viewportMinimum and viewportMaximum.
* `dynamicUpdate` option in StockChart can influence how often these events are triggered.