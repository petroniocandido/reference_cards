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
