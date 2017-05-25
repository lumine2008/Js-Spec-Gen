# ChartAxis Object (JavaScript API for Excel)

Represents a single axis in a chart.

## Properties

| Property	   | Type	|Description| Req. Set|
|:---------------|:--------|:----------|:----|
|baseUnit|string|Returns or sets the base unit for the specified category axis. Possible values are: `Days` Specifies the unit of time for chart axes and data series, in days.,`Months` Specifies the unit of time for chart axes and data series, in months.,`Years` Specifies the unit of time for chart axes and data series, in years.|[1.9](../requirement-sets/excel-api-requirement-sets.md)|
|categoryNames|string|Returns or sets all the category names for the specified axis, as a text array.|[1.9](../requirement-sets/excel-api-requirement-sets.md)|
|categoryType|string|Returns or sets the category axis type. Possible values are: `Automatic` Specifies the type of the category axis. Excel controls the axis type.,`TextAxis` Specifies the type of the category axis. Axis groups data by an arbitrary set of categories.,`DateAxis` Specifies the type of the category axis. Axis groups data on a time scale.|[1.9](../requirement-sets/excel-api-requirement-sets.md)|
|customDisplayUnit|double|Represents the custom axis display unit value.|[1.9](../requirement-sets/excel-api-requirement-sets.md)|
|displayUnit|string|Represents the axis display unit. Possible values are: `None` Default option. This will reset display unit to the axis, and set unit label invisible.,`Hundreds` This will set the axis in units of hundreds.,`Thousands` This will set the axis in units of thousands.,`TenThousands` This will set the axis in units of tens of thousands.,`HundredThousands` This will set the axis in units of hundreds of thousands.,`Millions` This will set the axis in units of millions.,`TenMillions` This will set the axis in units of tens of millions.,`HundredMillons` This will set the axis in units of hundreds of millions.,`Billions` This will set the axis in units of billions.,`Trillions` This will set the axis in units of trillions.,`Custom` This will set the axis in units of custom value.|[1.9](../requirement-sets/excel-api-requirement-sets.md)|
|majorUnit|object|Represents the interval between two major tick marks. Can be set to a numeric value or an empty string.  The returned value is always a number.|[1.1](../requirement-sets/excel-api-requirement-sets.md)|
|majorUnitScale|string|Returns or sets the major unit scale value for the category axis when the CategoryType property is set to TimeScale. Possible values are: `Days` Specifies the unit of time for chart axes and data series, in days.,`Months` Specifies the unit of time for chart axes and data series, in months.,`Years` Specifies the unit of time for chart axes and data series, in years.|[1.9](../requirement-sets/excel-api-requirement-sets.md)|
|maximum|object|Represents the maximum value on the value axis.  Can be set to a numeric value or an empty string (for automatic axis values).  The returned value is always a number.|[1.1](../requirement-sets/excel-api-requirement-sets.md)|
|minimum|object|Represents the minimum value on the value axis. Can be set to a numeric value or an empty string (for automatic axis values).  The returned value is always a number.|[1.1](../requirement-sets/excel-api-requirement-sets.md)|
|minorUnit|object|Represents the interval between two minor tick marks. "Can be set to a numeric value or an empty string (for automatic axis values). The returned value is always a number.|[1.1](../requirement-sets/excel-api-requirement-sets.md)|
|minorUnitScale|string|Returns or sets the minor unit scale value for the category axis when the CategoryType property is set to TimeScale. Possible values are: `Days` Specifies the unit of time for chart axes and data series, in days.,`Months` Specifies the unit of time for chart axes and data series, in months.,`Years` Specifies the unit of time for chart axes and data series, in years.|[1.9](../requirement-sets/excel-api-requirement-sets.md)|
|showDisplayUnitLabel|bool|Represents whether the axis display unit label is visible.|[1.9](../requirement-sets/excel-api-requirement-sets.md)|
|type|string|Represents the axis type. Read-only. Possible values are: `Category` Specifies the axis type. Axis displays categories.,`Value` Specifies the axis type. Axis displays values.,`SeriesAxis` Specifies the axis type. Axis displays data series.|[1.9](../requirement-sets/excel-api-requirement-sets.md)|

_See property access [examples.](#property-access-examples)_

## Relationships
| Relationship | Type	|Description| Req. Set|
|:---------------|:--------|:----------|:----|
|format|[ChartAxisFormat](chartaxisformat.md)|Represents the formatting of a chart object, which includes line and font formatting. Read-only.|[1.1](../requirement-sets/excel-api-requirement-sets.md)|
|majorGridlines|[ChartGridlines](chartgridlines.md)|Returns a gridlines object that represents the major gridlines for the specified axis. Read-only.|[1.1](../requirement-sets/excel-api-requirement-sets.md)|
|minorGridlines|[ChartGridlines](chartgridlines.md)|Returns a Gridlines object that represents the minor gridlines for the specified axis. Read-only.|[1.1](../requirement-sets/excel-api-requirement-sets.md)|
|title|[ChartAxisTitle](chartaxistitle.md)|Represents the axis title. Read-only.|[1.1](../requirement-sets/excel-api-requirement-sets.md)|

## Methods
None


## Method Details

### Property access examples
Get the `maximum` of Chart Axis from Chart1

```js
Excel.run(function (ctx) { 
	var chart = ctx.workbook.worksheets.getItem("Sheet1").charts.getItem("Chart1");	
	var axis = chart.axes.valueAxis;
	axis.load('maximum');
	return ctx.sync().then(function() {
			console.log(axis.maximum);
	});
}).catch(function(error) {
		console.log("Error: " + error);
		if (error instanceof OfficeExtension.Error) {
			console.log("Debug info: " + JSON.stringify(error.debugInfo));
		}
});
```

Set the  `maximum`,  `minimum`,  `majorunit`, `minorunit` of valueaxis. 

```js
Excel.run(function (ctx) { 
	var chart = ctx.workbook.worksheets.getItem("Sheet1").charts.getItem("Chart1");	
	chart.axes.valueAxis.maximum = 5;
	chart.axes.valueAxis.minimum = 0;
	chart.axes.valueAxis.majorUnit = 1;
	chart.axes.valueAxis.minorUnit = 0.2;
	return ctx.sync().then(function() {
			console.log("Axis Settings Changed");
	});
}).catch(function(error) {
		console.log("Error: " + error);
		if (error instanceof OfficeExtension.Error) {
			console.log("Debug info: " + JSON.stringify(error.debugInfo));
		}
});
```