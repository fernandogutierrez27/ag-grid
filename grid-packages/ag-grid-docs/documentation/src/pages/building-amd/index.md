---
title: "Using ag-Grid with AMD"
---

We walk through the main steps required when using ag-Grid with AMD.

## Initialise Project

```bash
mkdir ag-grid-amd
cd ag-grid-amd
npm init --yes
```

## Install Dependencies

```bash
npm i --save ag-grid-community

# or, if using Enterprise features
npm i --save ag-grid-enterprise
```

## Create Application

Our application will be a very simple one:

```js
requirejs.config({
    baseUrl: '../node_modules',
    paths: {
        'agGrid': 'ag-grid-community/dist/ag-grid-community.amd.min', // for community features
        // 'agGrid': 'ag-grid-enterprise/dist/ag-grid-enterprise.amd.min',   // for enterprise features
    }
});

requirejs(['agGrid'], function (agGrid) {
    var columnDefs = [
        {headerName: "Make", field: "make"},
        {headerName: "Model", field: "model"},
        {headerName: "Price", field: "price"}
    ];

    // specify the data
    var rowData = [
        {make: "Toyota", model: "Celica", price: 35000},
        {make: "Ford", model: "Mondeo", price: 32000},
        {make: "Porsche", model: "Boxter", price: 72000}
    ];

    // let the grid know which columns and what data to use
    var gridOptions = {
        columnDefs: columnDefs,
        rowData: rowData
    };

    var gridDiv = document.querySelector('#myGrid');
    new agGrid.Grid(gridDiv, gridOptions);
});
```

```html
<!DOCTYPE html>
<html>
<head>
    <script data-main="app" src="https://cdnjs.cloudflare.com/ajax/libs/require.js/2.3.6/require.js"></script>
</head>
<body>
    <div id="myGrid" style="height: 200px;width: 600px" class="ag-theme-alpine"></div>
</body>
</html>
```

Now we can either serve the HTML file above which will result in the following grid.

<img-caption src="building-amdresources/ts-grid.png" alt="Datagrid" constrained="true"></image-caption>

## Example Code

The code for this example can be found on [GitHub](git@github.com:seanlandsman/ag-grid-amd-example.git).
