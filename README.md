
<!-- README.md is generated from README.Rmd. Please edit the README.Rmd file -->

# Lab report \#1

Follow the instructions posted at
<https://ds202-at-isu.github.io/labs.html> for the lab assignment. The
work is meant to be finished during the lab time, but you have time
until Monday evening to polish things.

Include your answers in this document (Rmd file). Make sure that it
knits properly (into the md file). Upload both the Rmd and the md file
to your repository.

All submissions to the github repo will be automatically uploaded for
grading once the due date is passed. Submit a link to your repository on
Canvas (only one submission per team) to signal to the instructors that
you are done with your submission.

inspect the first few lines of the data set:

what variables are there? of what type are the variables? what does each
variable mean? what do we expect their data range to be? is there a
variable of special interest or focus?

16 variables, mainly quantitative. Parcel ID character with ID.

Address property address in Ames, IA.

Style factor variable detailing the type of housing.

Occupancy factor variable of type of housing.

Sale Date date of sale.

Sale Price sales price (in US dollar).

Multi Sale logical value: was this sale part of a package?

YearBuilt integer value: year in which the house was built.

Acres acres of the lot.

TotalLivingArea (sf) total living area in square feet.

Bedrooms number of bedrooms.

FinishedBsmtArea (sf) total area of the finished basement in square
feet.

LotArea(sf) total lot area in square feet.

AC logical value: does the property have an AC?

FirePlace logical value: does the property have an fireplace?

Neighborhood factor variable - levels indicate neighborhood area in
Ames.

start the exploration with the main variable:

what is the range of the variable? draw a histogram for a numeric
variable or a bar chart, if the variable is categorical. what is the
general pattern? is there anything odd? follow-up on oddities: see 4
pick a variable that might be related to the main variable.

what is the range of that variable? plot. describe the pattern. what is
the relationship to the main variable? plot a scatterplot, boxplot or
facetted barcharts (dependening on the types of variables involved).
Describe overall pattern, does this variable describe any oddities
discovered in 3? Identify/follow-up on any oddities

example text

``` r
1 + 2
```

    ## [1] 3
