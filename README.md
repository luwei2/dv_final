<html>
<script src='https://d3js.org/d3.v5.min.js'></script>
<style> circle {fill: lightblue; stroke: black;} </style>
<body onload='init()'>
<svg width=300 height=300>
</svg>
<script>
async function init() {
  const data = await d3.csv(
    'https://flunky.github.io/cars2017.csv');

  var x = d3.scaleLog()
    .domain([10, 150])
    .range([0, 200])
    .base(10);

  var y = d3.scaleLog()
    .domain([10, 150])
    .range([200, 0])
    .base(10);

  d3.select("svg").append("g")
  .attr("transform","translate(50,50)")
  .selectAll("circle").data(data)
  .enter().append("circle")
  .attr("cx", function(d){return x(parseFloat(d.AverageCityMPG));})
  .attr("cy", function(d){return y(parseFloat(d.AverageHighwayMPG));})
  .attr("r", function(d){return parseFloat(d.EngineCylinders)+2;})

  d3.select("svg").append("g").attr("transform","translate(50,50)")
  .call(d3.axisLeft(y).tickValues([10,20,50,100]).tickFormat(d3.format("~s")))
  d3.select("svg").append("g").attr("transform","translate(50,250)")
  .call(d3.axisBottom(x).tickValues([10,20,50,100]).tickFormat(d3.format("~s")))
}
</script>
</body>
</html>

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/luwei2/dv_final/settings). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://help.github.com/categories/github-pages-basics/) or [contact support](https://github.com/contact) and we’ll help you sort it out.
