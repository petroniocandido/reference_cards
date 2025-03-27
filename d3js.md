# D3JS

| Method   |      Usage      |  Example |  
|---|---|---|
| `.select("selector")` |  elect the first element that matches in the DOM (from top to bottom) | `d3.select("p")` | 
| `.selectAll("selector")` |  selects ALL elements that match the selector | `d3.select("p")` | 
| `.attr()` |  Update selected element attribute | `d3.select("p").attr("name", "fred")` | 
| `..classed()` | Assigns or unassigns the specified CSS class names on the selected elements   |   `d3.select("p").classed("radio", true);` |
| `.style()`  | Updates the style property |    `d3.select("p").style("color", "blue");` |
| `.property()` | Used to set an element property |    `d3.select('input').property('value', 'hello world')` |
| `.text()`  | Updates selected element text content |    `d3.select('h1').text('Learning d3.js')` |
| `.html()` | Sets the inner HTML to the specified value on all selected elements |    `d3.select('div').html('h1>learning d3.js</h1>')` |
| `.append()`  | Appends a new element as the last child of the selected element |    `d3.select("div").append("p")` |
| `.insert()`  | Works the same as the `.append()` method, except you can specify another element to insert before |    `d3.select("div").insert("p", "h1")` |
| `.remove()`  | Removes selected element from the DOM  | `d3.select("div").remove("p")` |
