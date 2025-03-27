# D3JS

## Selecting elements and changing properties

| Method   |      Usage      |  Example |  
|---|---|---|
| `.select("selector")` |  elect the first element that matches in the DOM (from top to bottom) | `d3.select("p")` | 
| `.selectAll("selector")` |  selects ALL elements that match the selector | `d3.select("p")` | 
| `.attr("attribute", newvalue)` |  Update selected element attribute | `d3.select("p").attr("name", "fred")` | 
| `.classed()` | Assigns or unassigns the specified CSS class names on the selected elements   |   `d3.select("p").classed("radio", true);` |
| `.style()`  | Updates the style property |    `d3.select("p").style("color", "blue");` |
| `.property()` | Used to set an element property |    `d3.select('input').property('value', 'hello world')` |
| `.text()`  | Updates selected element text content |    `d3.select('h1').text('Learning d3.js')` |
| `.html()` | Sets the inner HTML to the specified value on all selected elements |    `d3.select('div').html('h1>learning d3.js</h1>')` |
| `.append()`  | Appends a new element as the last child of the selected element |    `d3.select("div").append("p")` |
| `.insert()`  | Works the same as the `.append()` method, except you can specify another element to insert before |    `d3.select("div").insert("p", "h1")` |
| `.remove()`  | Removes selected element from the DOM  | `d3.select("div").remove("p")` |


## Working with data

| Method   |      Usage      |  Example |  
|---|---|---|
| `.data(json)`  | join the specified data to the selected element(s) | `d3.selectAll(".d3_fruit").data(fruits).text((d) => d)` |
| `.join("element")`  |  appends, removes, and reorders elements as necessary to match the specified data. | `d3.selectAll("p").data(fruits).join("p").attr("class", "d3_fruit").text((d) => d)` |
| `.json("path/to/file.json")`  |  Read a json file and return the data. | `d3.json("/path/to/file.json").then((data) => {  console.log(data); })` |
| `.csv("path/to/file.csv")`  |  Read a csv file and return the data. | `d3.json("/path/to/file.json").then((data) => {  console.log(data); })` |
| `.xml("path/to/file.xml")`  |  Read a xml file and return the data. | `d3.json("/path/to/file.json").then((data) => {  console.log(data); })` |
| `.tsv("path/to/file.tsv")`  |  Read a tsv file and return the data. | `d3.json("/path/to/file.json").then((data) => {  console.log(data); })` |
| `.text("path/to/file.txt")`  |  Read a txt file and return the data. | `d3.json("/path/to/file.json").then((data) => {  console.log(data); })` |

## Scales

- The `d3.scale` function converts the input data raw values into visual values as pixels.
- `d3.scale` needs to be set with a domain and a range. The domain sets a LIMIT for the data we are trying to represent visually.

| Method   |      Usage      |  Example |  
|---|---|---|
| `.domain([min, max])`  | Range of visual display, in pixels | `d3.` |
| `.range([min, max])`  | Range of raw data | `d3.` |
| `.scaleLinear()`  | Linear map between range and domain | `y_scale = d3.scaleLinear().range([height, 0]); y_scale.domain([0, d3.max(data, (d) => d.Population)])` |
| `.scaleTime()`  | For working with data that represents dates | `d3.` |
| `.scaleBand()`  | For working with bar charts | `x_scale = d3.scaleBand().range([0, width]); x_scale.domain(data.map((d) => d.Name);` |
| `.scale()`  | General use scales | `d3.` |
| `.scaleOrdinal()`  |  | `const color = d3.scaleOrdinal().domain(colors.keys()).range(colors.values());` |
| `.`  |  | `d3.` |
| `.`  |  | `d3.` |

```
const width = 960, height = 500;

const x_scale = d3.scaleBand().range([0, width]).padding(0.1);
const y_scale = d3.scaleLinear().range([height, 0]);

const svg = d3.select("#d3_demo")
    .attr("width", width)
    .attr("height", height);

d3.json("https://raw.githubusercontent.com/iamspruce/intro-d3/main/nigeria-states.json")
    .then(({ data }) => {

     data.forEach((d) => (d.Population = +d.info.Population));

     // Scale the Domain
     x_scale.domain(data.map((d) => d.Name));
     y_scale.domain([0, d3.max(data, (d) => d.Population)]);

     // add the rectangles for the bar chart
     svg
      .selectAll("rect")
      .data(data)
      .join("rect")
      .attr("class", "bar")
      .attr("x", (d) => x_scale(d.Name))
      .attr("y", (d) => y_scale(d.Population))
      .attr("width", x_scale.bandwidth())
      .attr("height", (d) => height - y_scale(d.Population));
    });

```


## Axis

- The axis component renders human-readable reference marks for scales.
-  you only need to pass an existing d3.scale and then append it to a SVG
-  
| Method   |      Usage      |  Example |  
|---|---|---|
| `.axisTop(scale)`  | Top axis | `let bottom_axis = d3.axisBottom(scale); svg.append("g").call(bottom_axis); |
| `.axisBottom(scale)`  | Top axis | `let bottom_axis = d3.axisBottom(scale); svg.append("g").call(bottom_axis); |
| `.axisLeft(scale)`  | Top axis | `let bottom_axis = d3.axisBottom(scale); svg.append("g").call(bottom_axis); |
| `.axisRight(scale)`  | Top axis | `let bottom_axis = d3.axisBottom(scale); svg.append("g").call(bottom_axis); |


## Event Handling
-  add or remove event handlers to or from selected document elements
-  `.on("event",function)`

|  Event Type  | Description  |
|---|---|
| zoom  | selection is being panned and zoomed  |
| click  | selection got clicked  |
| mouseover  | mouse pointer moves over a selection  |
| mouseout  | mouse pointer leaves a slection  |
