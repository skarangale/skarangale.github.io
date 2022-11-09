---
name: Homework 10
tools: [Python, HTML, vega-lite, altair]
image: assets/pngs/cars.png
description: This is a "showcase" project that uses vega-lite for interactive viz!
custom_js:
  - vega.min
  - vega-lite.min
  - vega-embed.min
  - justcharts
---


### 1. Interactive visual using altair in python


<vegachart schema-url="{{ site.baseurl }}/assets/json/altair_buildings_chart.json" style="width: 100%"></vegachart>


<!-- these are written in a combo of html and liquid --> 

<div class="left">
{% include elements/button.html link="https://raw.githubusercontent.com/UIUC-iSchool-DataViz/is445_bcubcg_fall2022/main/data/building_inventory.csv" text="The Data" %}
</div>

<div class="right">
{% include elements/button.html link="https://github.com/jnaiman/online_cv_public/blob/main/python_notebooks/test_generate_plots.ipynb" text="The Analysis" %}
</div>

### Explanation
The above dashboard is an interactive dashboard which was made by combining two visuals. These two visuals were made using the altair library in python. The right visual is scatter plot which shows the average number of floors in the buildings constructed throughout the years. The scatter plot has the year constructed on the X-axis and the average number of floors on the Y-axis. The color shade of the different data points on the scatter plot is determined by the square footage of the buildings in each year. There was no particular color chosen for the scatter plot and we left it on default which is blue. The x-axis value which is 'Year constructed' has the type 'temporal (T)' as it is date(year) data. The y-axis value which is 'average of total floors' is 'quantitative (Q)' because it is numeric data. The column 'square footage' which is used in the color property has the type 'quantitative (Q)' because it is numeric data.

The left visual is a bar chart which shows the different status available for the buildings and the number of buildings in each status. The 'building status' is on the x-axis and has the type 'nominal (N)' as it is a string data which is unordered. The number of buildings on the y-axis was found using the count() function which takes the count of buildings under each status using the 'building status' column. Each status of the buildings in the chart has a separate color assigned to it by default by using the color() function in altair. The 'building status' column is used to decide the colors for the different status. Both the charts have tooltips which help the viewer check the individual data values. This was achieved using the tooltip() function in altair.

Finally, both these charts were combined together using the operator for hconcat after making the charts interactive. Inorder to make the charts interactive, we used the selection_interval() function in altair which was used to select an interval from the scatter plot. This interval was then used to obtain the different status of buildings which existed in that particular year interval on the adjacent bar chart. To achieve this, we used the transform_filter() altair property in the bar chart which filters out the data depending on the interval selected on the scatter plot.

We did not use the colormap function in both our plots here because we didn't feel its need to explain our data.


### 2. Bar plot made using vega-lite and altair which shows the number of buildings built according to the usage description.

<vegachart schema-url="{{ site.baseurl }}/assets/json/altair_vega_bar.json" style="width: 100%"></vegachart>

<!-- these are written in a combo of html and liquid --> 

<div class="left">
{% include elements/button.html link="https://raw.githubusercontent.com/UIUC-iSchool-DataViz/is445_bcubcg_fall2022/main/data/building_inventory.csv" text="The Data" %}
</div>

<div class="right">
{% include elements/button.html link="https://github.com/jnaiman/online_cv_public/blob/main/python_notebooks/test_generate_plots.ipynb" text="The Analysis" %}
</div>

### Explanation

This above visual is a simple bar chart which was made using vega-lite in altair. Inorder to use the vega-lite script in altair, we used the Chart.from_dict() function and changed the manner in which comments are mentioned in the code. The bar chart shows us the different usage descriptions for the buildings constructed and the number of buildings built for the different use. The encodings() function in vega-lite was used to mention the x and the y- axis. The x-axis in the bar chart is the 'usage description' which has the type 'nominal' as it is a string data which is unordered. The y-axis in the bar chart is the 'number of buildings' which is obtained by using the aggregate function count. The number of buildings on the y-axis has the type 'quantitative' as it is numeric data. We have used the transform function in vega-lite which has a filter function which gave us the ability to decide the usage descriptions we wanted to include on the x-axis. We didn't choose to use the 'unusual' string under the column 'usage description'. We used the mark function in vega-lite to define the chart type which is bar and the color was chosen as red randomly. We did not use the colormap function here because we didn't feel its need to explain our data.

