# D3JS

## Selecting elements and changing properties
- https://d3js.org/d3-selection/selecting
- https://d3js.org/d3-selection/modifying
- 
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
- https://d3js.org/d3-selection/joining
- https://d3js.org/d3-selection/control-flow
- 
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
- https://d3js.org/d3-scale
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
- https://d3js.org/d3-axis
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
- https://d3js.org/d3-selection/events
-  add or remove event handlers to or from selected document elements
-  `.on("event",function)`

|  Event Type  | Description  |
|---|---|
| zoom  | selection is being panned and zoomed  |
| click  | selection got clicked  |
| mouseover  | mouse pointer moves over a selection  |
| mouseout  | mouse pointer leaves a slection  |

## Formatting Numbers and Time

- `d3.format("format")` customize number formatting. Ex: `const formatter = d3.format(".1f"); console.print(formatter(0.1 ))`
- https://d3js.org/d3-format
- https://d3js.org/d3-time-format

## SVG Elements
| Element   |      Usage      |  Example |  
|---|---|---|
|`<a>`| creates a hyperlink to other web pages, files, locations in the same page, email addresses, or any other URL..|` `|
|`<g>`| a container used to group other SVG elements, and its attributes are inherited by its children.|` `|
|`<circle>`| draw circles based on a center point and a radius.|` <circle cx="50" cy="50" r="50" />`|
|`<ellipse>`|  create ellipses based on a center coordinate, and both their x and y radius.|` <ellipse cx="100" cy="50" rx="100" ry="50" />`|
|`<line>`|  create a line connecting two points.|` line x1="0" y1="80" x2="100" y2="20" stroke="black" />`|
|`<polygon>`|  defines a closed shape consisting of a set of connected straight line segments. The last point is connected to the first point.|`<polygon points="100,100 150,25 150,75 200,0" fill="none" stroke="black" /> `|
|`<rect>`|  draws rectangles, defined by their position, width, and height. The rectangles may have their corners rounded.|` <rect x="120" width="100" height="100" rx="15" />`|
|`<text>`|  draws a graphics element consisting of text.|`<text x="65" y="55" class="Rrrrr">Grumpy!</text> `|
|`<polyline>`| creates straight lines connecting several points.|`<polyline points="100,100 150,25 150,75 200,0" fill="none" stroke="black" /> `|


## SVG Atributes
| Attribute   |      Usage      |  Example |  
|---|---|---|
|`transform`| defines a list of transform definitions that are applied to an element and the element's children.|` matrix(a,b,c,d,e,f), translate(<x> [<y>]), scale(<x> [<y>]), rotate(<a> [<x> <y>])`|
|`fill`|  the color used to paint the element.|` `|
|`cx`| defines the x-axis coordinate of a center point.|` `|
|`cy`| defines the y-axis coordinate of a center point.|` `|
|`r`| defines the radius of a circle.|` `|
|`rx`| defines a radius on the x-axis.|` `|
|`ry`| defines a radius on the y-axis.|` `|
|`x, x1, x2`| defines the x-axis coordinate of an object, or the x-coordinates of objects that require more than one point.|` `|
|`y, y1, y2`| defines the x-axis coordinate of an object, or the x-coordinates of objects that require more than one point.|` `|
|`points`| defines a list of points. Each point is defined by a pair of number representing a X and a Y coordinate in the user coordinate system.|` `|

