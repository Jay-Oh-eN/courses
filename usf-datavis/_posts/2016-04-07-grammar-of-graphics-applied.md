---
title: Grammar of Graphics Applied
content_type: lab
---

<!-- <table class="lecture-vid">
<tr>
<td><a href="{{ site.baseurl }}/usf-datavis/slides/2016-03-29-visual-encodings.pdf"><img src="{{ site.baseurl }}/usf-datavis/slides/thumbs/2016-03-29-visual-encodings.png" /></a></td><td> <iframe  src="https://www.youtube.com/embed/6k3ZDjqr844" frameborder="0" allowfullscreen></iframe></td>
</tr>
</table>

[![]({{ site.baseurl }}/usf-datavis/boards/2016-03-29-visual-encodings.jpg)]({{ site.baseurl }}/usf-datavis/boards/2016-03-29-visual-encodings.jpg) -->

## Announcements

* project 1 due **Monday at 9am**, critique **still due Tuesday**
* Project 2 due the following **Tuesday, 4/19**
* Videos playlist organized, notes updated

## Notes

## Exercise: Inside AirBnB

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
 * https://stanford.edu/~mwaskom/software/seaborn/examples/simple_violinplots.html
6. To find potential features that correlate with the price, make a facet grid of linear regressions (price will always be the dependent variable).
 * https://stanford.edu/~mwaskom/software/seaborn/examples/anscombes_quartet.html
 * https://stanford.edu/~mwaskom/software/seaborn/examples/logistic_regression.html
 * https://stanford.edu/~mwaskom/software/seaborn/examples/multiple_regression.html

### Extra Credit

* Visualize map of average listing price vs. median rent ([CartoDB](https://cartodb.com/) is a quick and easy way to do this)
* Visualize price trend for neighborhood and AirbNB ave. listing price trend (which one comes first? causal analysis)
* Finding undervalued listings by running a multiple regression on the data. The listings with the largest negative residuals are potentially undervalued.

## Resources

### Examples

### References

* [A Layered Grammar of Graphics](http://byrneslab.net/classes/biol607/readings/wickham_layered-grammar.pdf)
* [D3: Data Driven Documents (original paper)](http://vis.stanford.edu/files/2011-D3-InfoVis.pdf)




