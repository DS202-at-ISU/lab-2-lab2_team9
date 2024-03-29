
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

Since this is on housing sales, sale price is likely a variable of
interest.

16 variables, mainly quantitative. Parcel ID \#Used to answer required
questions \#summary(ames\[“Parcel ID”\]) character with ID. Type:
Character Length: 6935 (No Range values)

Address property address in Ames, IA. \#Used to answer required
questions \#summary(ames\[“Parcel ID”\]) Type: character Length: 6935
(No Range values)

Style factor variable detailing the type of housing. \#Used to Answer
required questions \#summary(ames\[’Style”\]) Type: character 1 Story
Frame: 3732 2 Story Frame: 1456 1 1/2 Story Frame: 711 Split Level
Frame: 215 Split Foyer Frame: 156 Other: 218 NA: 447

Occupancy factor variable of type of housing. Type:Character \#Used to
answer required question \#summary(ames\[“Occupancy”\]) Condominium: 711
Single-Family/Owner occupied: 4711 Townhouse: 745 Two-Family Conversion:
139 NA’s: 447

Sale Date date of sale. Type: Date library(classdata) ames
range(ames\$‘Sale Date’)

Sale Price sales price (in US dollar). Type: Intger Data range is 0 -
20,500,000.

Multi Sale Sales that include mulitple properties/houses Type: character

YearBuilt integer value: year in which the house was built. Type: Date
range(ames\$‘YearBuilt’)

Acres acres of the lot. Type: Float range(ames\$‘Acres’)

TotalLivingArea (sf) total living area in square feet. Type: Integer
range(ames\$‘TotalLivingArea (sf)’)

Bedrooms number of bedrooms. Type: integer Range: 0-10

FinishedBsmtArea (sf) total area of the finished basement in square
feet. Type: float range(ames\$‘FinishedBsmtArea (sf)’)

LotArea(sf) total lot area in square feet. Quantitative- Range is
between zero and 523228.

AC logical value: does the property have an AC? Expected- Yes or no,
range- binary

FirePlace logical value: does the property have an fireplace? Expected
yes or not, range- it is binary

Neighborhood factor variable - levels indicate neighborhood area in
Ames. Not continuous, contains the specific neighborhood codes for the
house sold range- These are descrete values even though they are numbers

3.  start the exploration with the main variable:

what is the range of the variable? draw a histogram for a numeric
variable or a bar chart, if the variable is categorical. what is the
general pattern? is there anything odd? follow-up on oddities: see 4

``` r
library(classdata)
library(ggplot2)

ames
```

    ## # A tibble: 6,935 × 16
    ##    `Parcel ID` Address     Style Occupancy `Sale Date` `Sale Price` `Multi Sale`
    ##    <chr>       <chr>       <fct> <fct>     <date>             <dbl> <chr>       
    ##  1 0903202160  1024 RIDGE… 1 1/… Single-F… 2022-08-12        181900 <NA>        
    ##  2 0907428215  4503 TWAIN… 1 St… Condomin… 2022-08-04        127100 <NA>        
    ##  3 0909428070  2030 MCCAR… 1 St… Single-F… 2022-08-15             0 <NA>        
    ##  4 0923203160  3404 EMERA… 1 St… Townhouse 2022-08-09        245000 <NA>        
    ##  5 0520440010  4507 EVERE… <NA>  <NA>      2022-08-03        449664 <NA>        
    ##  6 0907275030  4512 HEMIN… 2 St… Single-F… 2022-08-16        368000 <NA>        
    ##  7 0535105180  511 25TH S… 1 St… Single-F… 2022-08-03             0 <NA>        
    ##  8 0907428446  4510 TWAIN… 1 St… Condomin… 2022-08-16        110000 <NA>        
    ##  9 0527301030  3409 EISEN… 1 St… Single-F… 2022-08-08        350000 <NA>        
    ## 10 0531363050  5426 KANSA… 1 St… Single-F… 2022-08-03        242000 <NA>        
    ## # ℹ 6,925 more rows
    ## # ℹ 9 more variables: YearBuilt <dbl>, Acres <dbl>,
    ## #   `TotalLivingArea (sf)` <dbl>, Bedrooms <dbl>,
    ## #   `FinishedBsmtArea (sf)` <dbl>, `LotArea(sf)` <dbl>, AC <chr>,
    ## #   FirePlace <chr>, Neighborhood <fct>

``` r
range(ames$`Sale Price`)
```

    ## [1]        0 20500000

``` r
ggplot(ames,
       aes(x = `Sale Price`)) +
  geom_histogram()
```

    ## `stat_bin()` using `bins = 30`. Pick better value with `binwidth`.

![](README_files/figure-gfm/unnamed-chunk-1-1.png)<!-- --> Most houses
are on the lower end of the range, with a couple outliers in the upper
millions. The data is skewed right and unimodal. This makes sense since
there is an expected bottom to housing prices but mansions and large
estates are expected to break the general trend when compared to average
suburban housing. Several houses also have a sale price of zero, which
may be an entry error.

what is the range of that variable? plot. describe the pattern. what is
the relationship to the main variable? plot a scatterplot, boxplot or
facetted barcharts (dependening on the types of variables involved).
Describe overall pattern, does this variable describe any oddities
discovered in 3? Identify/follow-up on any oddities

4.  pick a variable that might be related to the main variable. what is
    the range of that variable? plot. describe the pattern. what is the
    relationship to the main variable? plot a scatterplot, boxplot or
    facetted barcharts (dependening on the types of variables involved).
    Describe overall pattern, does this variable describe any oddities
    discovered in 3? Identify/follow-up on any oddities.

5.  Cameron Kraklio- Square feet compared to sale price

``` r
library(classdata)
library(ggplot2)

ames
```

    ## # A tibble: 6,935 × 16
    ##    `Parcel ID` Address     Style Occupancy `Sale Date` `Sale Price` `Multi Sale`
    ##    <chr>       <chr>       <fct> <fct>     <date>             <dbl> <chr>       
    ##  1 0903202160  1024 RIDGE… 1 1/… Single-F… 2022-08-12        181900 <NA>        
    ##  2 0907428215  4503 TWAIN… 1 St… Condomin… 2022-08-04        127100 <NA>        
    ##  3 0909428070  2030 MCCAR… 1 St… Single-F… 2022-08-15             0 <NA>        
    ##  4 0923203160  3404 EMERA… 1 St… Townhouse 2022-08-09        245000 <NA>        
    ##  5 0520440010  4507 EVERE… <NA>  <NA>      2022-08-03        449664 <NA>        
    ##  6 0907275030  4512 HEMIN… 2 St… Single-F… 2022-08-16        368000 <NA>        
    ##  7 0535105180  511 25TH S… 1 St… Single-F… 2022-08-03             0 <NA>        
    ##  8 0907428446  4510 TWAIN… 1 St… Condomin… 2022-08-16        110000 <NA>        
    ##  9 0527301030  3409 EISEN… 1 St… Single-F… 2022-08-08        350000 <NA>        
    ## 10 0531363050  5426 KANSA… 1 St… Single-F… 2022-08-03        242000 <NA>        
    ## # ℹ 6,925 more rows
    ## # ℹ 9 more variables: YearBuilt <dbl>, Acres <dbl>,
    ## #   `TotalLivingArea (sf)` <dbl>, Bedrooms <dbl>,
    ## #   `FinishedBsmtArea (sf)` <dbl>, `LotArea(sf)` <dbl>, AC <chr>,
    ## #   FirePlace <chr>, Neighborhood <fct>

``` r
range(ames$`TotalLivingArea (sf)`)
```

    ## [1] NA NA

``` r
ggplot(ames,
       aes(x = `TotalLivingArea (sf)`, y = `Sale Price`)) +
  geom_point()
```

    ## Warning: Removed 447 rows containing missing values (`geom_point()`).

![](README_files/figure-gfm/unnamed-chunk-2-1.png)<!-- --> It is a
linear positive relationship. There are several outliers with small
living areas but high prices. This could be due to a high lot area (like
a farm house). This helps to explain the outliers that we saw earlier as
they both have high sale price.

4.  Olivia Riniker - YearBuilt compares to the sale Price

``` r
library(classdata)
library(ggplot2)
range(ames$`YearBuilt`)
```

    ## [1] NA NA

``` r
# restrictnig data so it is more readable 
ames_filtered <- ames %>%
  filter(YearBuilt > 1879 )
ggplot(ames_filtered, aes(x = `YearBuilt`, y = `Sale Price`)) + geom_point()
```

![](README_files/figure-gfm/unnamed-chunk-3-1.png)<!-- -->

The Data has a linearly positive relationship. There are outliers that
were indicating a house built in the year 0 so logically i removed them
from the data being analysed. The outliers that you can see in the
scatter plot I believe indicate mansions that were built in the early
2000 due to the high listing prices around 20 million dollars.

4.  Gabriel Wright- Acres to sales price

``` r
library(classdata)

library(ggplot2)
ames
```

    ## # A tibble: 6,935 × 16
    ##    `Parcel ID` Address     Style Occupancy `Sale Date` `Sale Price` `Multi Sale`
    ##    <chr>       <chr>       <fct> <fct>     <date>             <dbl> <chr>       
    ##  1 0903202160  1024 RIDGE… 1 1/… Single-F… 2022-08-12        181900 <NA>        
    ##  2 0907428215  4503 TWAIN… 1 St… Condomin… 2022-08-04        127100 <NA>        
    ##  3 0909428070  2030 MCCAR… 1 St… Single-F… 2022-08-15             0 <NA>        
    ##  4 0923203160  3404 EMERA… 1 St… Townhouse 2022-08-09        245000 <NA>        
    ##  5 0520440010  4507 EVERE… <NA>  <NA>      2022-08-03        449664 <NA>        
    ##  6 0907275030  4512 HEMIN… 2 St… Single-F… 2022-08-16        368000 <NA>        
    ##  7 0535105180  511 25TH S… 1 St… Single-F… 2022-08-03             0 <NA>        
    ##  8 0907428446  4510 TWAIN… 1 St… Condomin… 2022-08-16        110000 <NA>        
    ##  9 0527301030  3409 EISEN… 1 St… Single-F… 2022-08-08        350000 <NA>        
    ## 10 0531363050  5426 KANSA… 1 St… Single-F… 2022-08-03        242000 <NA>        
    ## # ℹ 6,925 more rows
    ## # ℹ 9 more variables: YearBuilt <dbl>, Acres <dbl>,
    ## #   `TotalLivingArea (sf)` <dbl>, Bedrooms <dbl>,
    ## #   `FinishedBsmtArea (sf)` <dbl>, `LotArea(sf)` <dbl>, AC <chr>,
    ## #   FirePlace <chr>, Neighborhood <fct>

``` r
range(ames$'Acres')
```

    ## [1] NA NA

``` r
#Cannot have a range due to minimum value being zero
ggplot(ames,
       aes(x = `Acres`, y = `Sale Price`)) +
  geom_point()
```

    ## Warning: Removed 89 rows containing missing values (`geom_point()`).

![](README_files/figure-gfm/unnamed-chunk-4-1.png)<!-- --> Graph
displays a postiive linear relationship where the more acres a property
has the sale price tends to be higher. There are a few properties that
would be considered outliers and are most likely due to expensive houses
in high population cities.

``` r
data("ames")
ames_data <- ames
?ames
```

    ## starting httpd help server ... done

``` r
library(ggplot2)
```

``` r
ggplot(ames_data, aes(x = Acres, y = `Sale Price`)) +
  geom_point() +
  scale_y_continuous(labels = scales::dollar_format(prefix = "$"), limits = c(70000, 1000000)) +
  labs(title = "Scatter Plot of Sale Price vs Acres",
       x = "Acres",
       y = "Sale Price")
```

    ## Warning: Removed 2898 rows containing missing values (`geom_point()`).

![](README_files/figure-gfm/unnamed-chunk-6-1.png)<!-- -->

``` r
ggplot(ames_data, aes(x = `TotalLivingArea (sf)`, y = `Sale Price`)) +
  geom_point() +
  scale_y_continuous(labels = scales::dollar_format(prefix = "$"), limits = c(70000, 1000000)) +
  labs(title = "Scatter Plot of Sale Price vs Total Living Area",
       x = "Total Living Area (sf)",
       y = "Sale Price")
```

    ## Warning: Removed 3114 rows containing missing values (`geom_point()`).

![](README_files/figure-gfm/unnamed-chunk-7-1.png)<!-- -->

``` r
ggplot(ames_data, aes(x = Bedrooms, y = `Sale Price`)) +
  geom_point() +
  scale_y_continuous(labels = scales::dollar_format(prefix = "$"), limits = c(70000, 1000000)) +
  labs(title = "Scatter Plot of Sale Price vs Bedrooms",
       x = "Bedrooms",
       y = "Sale Price")
```

    ## Warning: Removed 3114 rows containing missing values (`geom_point()`).

![](README_files/figure-gfm/unnamed-chunk-8-1.png)<!-- -->

``` r
ggplot(ames_data, aes(x = `FinishedBsmtArea (sf)`, y = `Sale Price`)) +
  geom_point() +
  scale_y_continuous(labels = scales::dollar_format(prefix = "$"), limits = c(70000, 1000000)) +
  labs(title = "Scatter Plot of Sale Price vs Finished Basement Area",
       x = "Finished Basement Area (sf)",
       y = "Sale Price")
```

    ## Warning: Removed 4254 rows containing missing values (`geom_point()`).

![](README_files/figure-gfm/unnamed-chunk-9-1.png)<!-- -->

-The scatter plots are all mostly linear. The bedrroms visual is harder
to read since its basically a catagorical variable. However the
strongest coorelation of sales price lies with Finished basement area
(sf). The relationship is very linear and has a positive trend upwards.
