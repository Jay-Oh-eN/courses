---
title: Grammar of Graphics Applied
content_type: lab
boards: ["2016-04-07-gog", "2016-04-07-polar-area"]
youtube: eS-BvoXfnNw
---

<iframe src="https://www.youtube.com/embed/{{ page.youtube }}" frameborder="0" allowfullscreen></iframe>

{% for board in page.boards %}
[![]({{ site.baseurl }}/usf-datavis/boards/{{ board }}.jpg)]({{ site.baseurl }}/usf-datavis/boards/{{ board }}.jpg)
{% endfor %}

## Announcements

* project 1 due **Monday at 9am**, critique **still due Tuesday**
* Project 2 due the following **Tuesday, 4/19**
* Videos playlist organized, notes updated

## Notes

[![](http://r4ds.had.co.nz/images/visualization-grammar-3.png)](http://r4ds.had.co.nz/visualize.html)
([source: Hadley Wickham](http://r4ds.had.co.nz/visualize.html))

[Live coding Jupyter notebook](https://github.com/Jay-Oh-eN/courses/blob/gh-pages/notebooks/2016-04-07-grammar-of-graphics.ipynb)

### Why?

[![Anscomb's Quartet](https://upload.wikimedia.org/wikipedia/commons/thumb/e/ec/Anscombe%27s_quartet_3.svg/500px-Anscombe%27s_quartet_3.svg.png)](https://en.wikipedia.org/wiki/Anscombe%27s_quartet)

### [EDA Techniques](https://en.wikipedia.org/wiki/Exploratory_data_analysis#Techniques)

* Box plot
* Histogram
* Run chart
* Pareto chart
* Scatter plot
* Stem-and-leaf plot
* Parallel coordinates
* Odds ratio
* Multidimensional scaling
* Principal component analysis
* Interactive versions of these plots

### Where we Came From

* We call him Tukey ([EDA](http://www.amazon.com/Exploratory-Data-Analysis-John-Tukey/dp/0201076160): 1977)
* William S. Cleveland ([Elements of Graphing Data](http://www.amazon.com/Elements-Graphing-Data-William-Cleveland/dp/0963488414/ref=pd_bxgy_14_img_3?ie=UTF8&refRID=1G5YRC8PTS1BRNYWAYC8): 1985, [Visualizing Data](http://www.amazon.com/Visualizing-Data-William-S-Cleveland/dp/0963488406/ref=pd_bxgy_14_img_2?ie=UTF8&refRID=1G5YRC8PTS1BRNYWAYC8): 1993)
* Leland Wilkinson ([Grammar of Graphics](http://www.springer.com/us/book/9780387245447): 1999)
* Hadley Wickham ([A Layered Grammar of Graphics](http://byrneslab.net/classes/biol607/readings/wickham_layered-grammar.pdf): 2010)

### GoG Applied

> On the spectrum between visual encodings and chart types

* A Grammar: The fundamental principles or rules of an art or science
    * provides insight into the composition of complicated graphics
    * understand diverse range of graphics
    * inform us on what a good graphic looks like
* Wilkinson vs Layered
* Implementations:
    * ggplot2
    * Protovis
    * Vega
    * (kinda) D3
* Data vs Aesthetic
* Components (can change each in relative isolation)
    * layers: data -> aesthetic mapping, stat transform, geom, position
        * different "view" of the same data
    * scale
    * coordinate system
    * Faceting

#### Examples

* Python Libraries
    * Lightning-Viz (we will come back to this)
    * Bokeh (powerful but complex)
    * bqplot (just the right abstraction, but a little beta)

```sh
pip install bokeh # conda install bokeh

python -c "import bokeh.sampledata; bokeh.sampledata.download()"
```

* Histogram: binning stat + bar geom

```r
ggplot(data = diamonds, mapping = aes(price)) +
    layer(geom = "bar", stat = "bin",
    mapping = aes(y = ..count..))
```

* Coxcomb plot: bar chart + polar coordinates

### Poll: Which chart is best?

### Exploratory vs. Explanatory

* Which tools are best for each?

#### Exploratory

* Trade flexibility and for speed: more rapid iteration (time to insight)
    * many charts, each take seconds
* integration with data processing environment (i.e. R or Python)
    * query (filter, subset, facet) and transform (aggregate)
    * can we have our cake and eat it too?
* Visual aesthetic not (as) important
* Fast iteration: less flexible charts, but quicker
    * Many charts, minutes per chart
* embedded with data analysis environment
    * query (filter, facet, subset)
    * transform (group, aggregate, etc.)

#### Explanatory

* Optimize for communication efficiency (time to interpretation)
* Custom, flexible, and interactive visual representations
    * single chart, takes days
* multiple reader problem
    * reader driven
    * drill down (next week)
* novice reader problem
    * author driven (next week)
    * don't have context you have
* distillation
* many reader and novice problem
    * interactivity
    * drill down to "teach"

## Exercise: Inside AirBnB

[solution notebook](https://github.com/Jay-Oh-eN/courses/blob/gh-pages/notebooks/2016-04-07-airbnb-eda.ipynb)

For this lab's exercise we are going to answer a few questions about AirBnB listings to get a better understanding of how to perform EDA in Python. Spurred by [Prop F](https://ballotpedia.org/City_of_San_Francisco_Initiative_to_Restrict_Short-Term_Rentals,_Proposition_F_(November_2015)) in San Francisco, imagine you are the mayor of your respective city and need to decide what impact AirBnB has had on your own housing situation. We will use visualization to both better understand our own city and potentially communicate these findings to the public at large.

__You will work in pairs and submit your work at the end of the class as a secret gist link.__

### The Cities

Each pair will work with a different cities data:

* 18 cities
    * Toronto
    * Austin
    * Boston
    * Chicago
    * LA
    * Berlin
    * Athens
    * London
    * DC
    * Sydney
    * Seattle
    * Santa Cruz
    * San Diego
    * Portland
    * Paris
    * Oakland
    * NYC
    * New Orleans

### Questions

#### Initial EDA with `pandas`

1. Download the data for your assigned city (`listings.csv` summary information): http://insideairbnb.com/get-the-data.html
2. Using pandas answer the following questions with summary statistics (just numbers, no charts):
    * How many neighborhoods?
    * Most common `room_type`
    * Neighborhood with the most # of listings
    * User with the most # of listings
    * Most expensive neighborhood (median price)
    * Listing with most # of reviews
3. Time to visualize! Using `pandas` (and matplotlib) create a visualization of each of the following:
 * Distribution of `room_type` (for entire city)
 * Histogram of # of listings per neighborhood
 * Histogram of # of listings for each user
 * City wide distribution of listing price
 * Distribution of median listing price per neighborhood
 * Histogram of number of reviews per listing
4. In an effort to find potential correlations (or outliers) you want a little bit more fine grained loot at the data. Create a scatterplot matrix of the data for your city. [http://pandas.pydata.org/pandas-docs/stable/visualization.html#visualization-scatter-matrix](http://pandas.pydata.org/pandas-docs/stable/visualization.html#visualization-scatter-matrix)
5. What impact would a Prof F like policy have on your city? 

 > Prop F would have removed all listings that are the `Entire Home` and available for more than 75 days per year

6. What would AirBnB's revenue loss have been from a passing of Prop F? Calculate revenue from the `reviews_per_month`, `availability_365`, and `price` for each listing.

#### Advanced plots with `seaborn`

5. Make a violin plot of the price distribution of each neighborhood. If your city has a large number of neighborhoods plot the 10 with the most listing.
 * [Seaborn: Violinplots](https://stanford.edu/~mwaskom/software/seaborn/examples/simple_violinplots.html)
6. To find potential features that correlate with the price, make a facet grid of linear regressions (price will always be the dependent variable).
 * [Seaborn: Anscombe's Quartet Regression](https://stanford.edu/~mwaskom/software/seaborn/examples/anscombes_quartet.html)
 * [Seaborn: Logistic Regression](https://stanford.edu/~mwaskom/software/seaborn/examples/logistic_regression.html)
 * [Seaborn: Multiple Regression](https://stanford.edu/~mwaskom/software/seaborn/examples/multiple_regression.html)

### Extra Credit

* Visualize map of average listing price vs. median rent ([CartoDB](https://cartodb.com/) is a quick and easy way to do this)
* Visualize price trend for neighborhood and AirbNB ave. listing price trend (which one comes first? causal analysis)
* Finding undervalued listings by running a multiple regression on the data. The listings with the largest negative residuals are potentially undervalued.

## Resources

### Tools

* [R for Data Science: Data Visualization](http://r4ds.had.co.nz/visualize.html)
* Bokeh
    * [Quick Start](http://bokeh.pydata.org/en/latest/docs/user_guide/quickstart.html)
    * [Plotting with Basic Glyphs](http://bokeh.pydata.org/en/latest/docs/user_guide/plotting.html)
    * [Making High Level Charts](http://bokeh.pydata.org/en/latest/docs/user_guide/charts.html)
    * [Adding Interacitons](http://bokeh.pydata.org/en/0.11.1/docs/user_guide/interaction.html)
    * [Configuring Plot Tools](http://bokeh.pydata.org/en/0.11.1/docs/user_guide/tools.html#setting-tool-visuals)
    * [Leveraging Other Libraries](http://bokeh.pydata.org/en/0.11.1/docs/user_guide/compat.html)
* [Pandas Visualization](http://pandas.pydata.org/pandas-docs/stable/visualization.html)
* [Seaborn Gallery](https://stanford.edu/~mwaskom/software/seaborn/examples/index.html)   
* [`bqplot`](https://github.com/bloomberg/bqplot)
* [Vega](http://vega.github.io/vega/)

### Examples

* [Elijah Meeks: Brushable Radial Chart](https://bl.ocks.org/emeeks/2fffa9abe50ac97603c7)
* [Bokeh: Gallery](http://bokeh.pydata.org/en/0.11.1/docs/gallery.html)
* [Bokeh: Stacked Bar](http://bokeh.pydata.org/en/latest/docs/gallery/stacked_bar_chart.html)
* [Bokeh: Histogram Chart](http://bokeh.pydata.org/en/0.8.1/docs/gallery/histograms_chart.html)
* [Bokeh: Distributions Histograms](http://bokeh.pydata.org/en/0.11.1/docs/gallery/histogram.html)
* [ggplot (from yHat) Gallery](http://ggplot.yhathq.com/docs/index.html)

### References

* [A Layered Grammar of Graphics](http://byrneslab.net/classes/biol607/readings/wickham_layered-grammar.pdf)
* [D3: Data Driven Documents (original paper)](http://vis.stanford.edu/files/2011-D3-InfoVis.pdf)
* Kernel Density Estimation
    * [Histograms and Kernel Density Estimation (KDE)](http://www.mglerner.com/blog/?p=28)
    * [An Introduction to Kernel Density Estimation](http://www.mvstat.net/tduong/research/seminars/seminar-2001-05/)
    * [Kernel Density Estimation in Python](https://jakevdp.github.io/blog/2013/12/01/kernel-density-estimation/)
    * [What's wrong with Kernel Density?](http://andrewgelman.com/2009/11/25/whats_wrong_wit/)
* [Ballotpedia: Prof F](https://ballotpedia.org/City_of_San_Francisco_Initiative_to_Restrict_Short-Term_Rentals,_Proposition_F_(November_2015))
