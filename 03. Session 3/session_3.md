C4TS R-Club - Session 2
================
Jason Pott
30/06/2019

In our [second
session](https://github.com/jasonpott/r4ds/blob/master/02.%20Session%202/session_2.md)
we covered - Setting up our environment - Working in projects and why
you should - Getting data into R - Manipulating data

Feel free to look back over the notes from that session, please come
back to me if you have any questions or need some clarification.

## Session 3

This session will cover the following functions within dplyr

  - select()  
  - group\_by()  
  - tally()  
  - mutate()  
  - transmute()
  - sumarise()

We will also create some tables

filter()

We covered this last time briefly, but it is worth refreshing. Filter
can help remove data that is erroneous or that which does not contribut
to an analysis. Operators include - \>= - \> - == - \!= - \< - \<= -
%in%

``` r
mtcars
```

    ##                      mpg cyl  disp  hp drat    wt  qsec vs am gear carb
    ## Mazda RX4           21.0   6 160.0 110 3.90 2.620 16.46  0  1    4    4
    ## Mazda RX4 Wag       21.0   6 160.0 110 3.90 2.875 17.02  0  1    4    4
    ## Datsun 710          22.8   4 108.0  93 3.85 2.320 18.61  1  1    4    1
    ## Hornet 4 Drive      21.4   6 258.0 110 3.08 3.215 19.44  1  0    3    1
    ## Hornet Sportabout   18.7   8 360.0 175 3.15 3.440 17.02  0  0    3    2
    ## Valiant             18.1   6 225.0 105 2.76 3.460 20.22  1  0    3    1
    ## Duster 360          14.3   8 360.0 245 3.21 3.570 15.84  0  0    3    4
    ## Merc 240D           24.4   4 146.7  62 3.69 3.190 20.00  1  0    4    2
    ## Merc 230            22.8   4 140.8  95 3.92 3.150 22.90  1  0    4    2
    ## Merc 280            19.2   6 167.6 123 3.92 3.440 18.30  1  0    4    4
    ## Merc 280C           17.8   6 167.6 123 3.92 3.440 18.90  1  0    4    4
    ## Merc 450SE          16.4   8 275.8 180 3.07 4.070 17.40  0  0    3    3
    ## Merc 450SL          17.3   8 275.8 180 3.07 3.730 17.60  0  0    3    3
    ## Merc 450SLC         15.2   8 275.8 180 3.07 3.780 18.00  0  0    3    3
    ## Cadillac Fleetwood  10.4   8 472.0 205 2.93 5.250 17.98  0  0    3    4
    ## Lincoln Continental 10.4   8 460.0 215 3.00 5.424 17.82  0  0    3    4
    ## Chrysler Imperial   14.7   8 440.0 230 3.23 5.345 17.42  0  0    3    4
    ## Fiat 128            32.4   4  78.7  66 4.08 2.200 19.47  1  1    4    1
    ## Honda Civic         30.4   4  75.7  52 4.93 1.615 18.52  1  1    4    2
    ## Toyota Corolla      33.9   4  71.1  65 4.22 1.835 19.90  1  1    4    1
    ## Toyota Corona       21.5   4 120.1  97 3.70 2.465 20.01  1  0    3    1
    ## Dodge Challenger    15.5   8 318.0 150 2.76 3.520 16.87  0  0    3    2
    ## AMC Javelin         15.2   8 304.0 150 3.15 3.435 17.30  0  0    3    2
    ## Camaro Z28          13.3   8 350.0 245 3.73 3.840 15.41  0  0    3    4
    ## Pontiac Firebird    19.2   8 400.0 175 3.08 3.845 17.05  0  0    3    2
    ## Fiat X1-9           27.3   4  79.0  66 4.08 1.935 18.90  1  1    4    1
    ## Porsche 914-2       26.0   4 120.3  91 4.43 2.140 16.70  0  1    5    2
    ## Lotus Europa        30.4   4  95.1 113 3.77 1.513 16.90  1  1    5    2
    ## Ford Pantera L      15.8   8 351.0 264 4.22 3.170 14.50  0  1    5    4
    ## Ferrari Dino        19.7   6 145.0 175 3.62 2.770 15.50  0  1    5    6
    ## Maserati Bora       15.0   8 301.0 335 3.54 3.570 14.60  0  1    5    8
    ## Volvo 142E          21.4   4 121.0 109 4.11 2.780 18.60  1  1    4    2

``` r
mtcars$gear
```

    ##  [1] 4 4 4 3 3 3 3 4 4 4 4 3 3 3 3 3 3 4 4 4 3 3 3 3 3 4 5 5 5 5 5 4

``` r
filter(mtcars, gear >= 4)
```

    ##     mpg cyl  disp  hp drat    wt  qsec vs am gear carb
    ## 1  21.0   6 160.0 110 3.90 2.620 16.46  0  1    4    4
    ## 2  21.0   6 160.0 110 3.90 2.875 17.02  0  1    4    4
    ## 3  22.8   4 108.0  93 3.85 2.320 18.61  1  1    4    1
    ## 4  24.4   4 146.7  62 3.69 3.190 20.00  1  0    4    2
    ## 5  22.8   4 140.8  95 3.92 3.150 22.90  1  0    4    2
    ## 6  19.2   6 167.6 123 3.92 3.440 18.30  1  0    4    4
    ## 7  17.8   6 167.6 123 3.92 3.440 18.90  1  0    4    4
    ## 8  32.4   4  78.7  66 4.08 2.200 19.47  1  1    4    1
    ## 9  30.4   4  75.7  52 4.93 1.615 18.52  1  1    4    2
    ## 10 33.9   4  71.1  65 4.22 1.835 19.90  1  1    4    1
    ## 11 27.3   4  79.0  66 4.08 1.935 18.90  1  1    4    1
    ## 12 26.0   4 120.3  91 4.43 2.140 16.70  0  1    5    2
    ## 13 30.4   4  95.1 113 3.77 1.513 16.90  1  1    5    2
    ## 14 15.8   8 351.0 264 4.22 3.170 14.50  0  1    5    4
    ## 15 19.7   6 145.0 175 3.62 2.770 15.50  0  1    5    6
    ## 16 15.0   8 301.0 335 3.54 3.570 14.60  0  1    5    8
    ## 17 21.4   4 121.0 109 4.11 2.780 18.60  1  1    4    2

``` r
data <- mtcars %>% 
  filter(gear >= 4)

data <- mtcars %>% 
  filter(gear <= 4)

data <- mtcars %>% 
  filter(gear == 4)

data <- mtcars %>% 
  filter(gear != 4)

data <- mtcars %>% 
  filter(!is.na(gear))
```

select() Use select to choose which column within a Dataframe should be
used. If you do not name a column within a select function it will be
dropped from the outoput. The order in which you write the coloumn names
is also the same as the order that they are outputted.

``` r
mtcars <- mtcars %>% 
  rownames_to_column()

mtcars
```

    ##                rowname  mpg cyl  disp  hp drat    wt  qsec vs am gear carb
    ## 1            Mazda RX4 21.0   6 160.0 110 3.90 2.620 16.46  0  1    4    4
    ## 2        Mazda RX4 Wag 21.0   6 160.0 110 3.90 2.875 17.02  0  1    4    4
    ## 3           Datsun 710 22.8   4 108.0  93 3.85 2.320 18.61  1  1    4    1
    ## 4       Hornet 4 Drive 21.4   6 258.0 110 3.08 3.215 19.44  1  0    3    1
    ## 5    Hornet Sportabout 18.7   8 360.0 175 3.15 3.440 17.02  0  0    3    2
    ## 6              Valiant 18.1   6 225.0 105 2.76 3.460 20.22  1  0    3    1
    ## 7           Duster 360 14.3   8 360.0 245 3.21 3.570 15.84  0  0    3    4
    ## 8            Merc 240D 24.4   4 146.7  62 3.69 3.190 20.00  1  0    4    2
    ## 9             Merc 230 22.8   4 140.8  95 3.92 3.150 22.90  1  0    4    2
    ## 10            Merc 280 19.2   6 167.6 123 3.92 3.440 18.30  1  0    4    4
    ## 11           Merc 280C 17.8   6 167.6 123 3.92 3.440 18.90  1  0    4    4
    ## 12          Merc 450SE 16.4   8 275.8 180 3.07 4.070 17.40  0  0    3    3
    ## 13          Merc 450SL 17.3   8 275.8 180 3.07 3.730 17.60  0  0    3    3
    ## 14         Merc 450SLC 15.2   8 275.8 180 3.07 3.780 18.00  0  0    3    3
    ## 15  Cadillac Fleetwood 10.4   8 472.0 205 2.93 5.250 17.98  0  0    3    4
    ## 16 Lincoln Continental 10.4   8 460.0 215 3.00 5.424 17.82  0  0    3    4
    ## 17   Chrysler Imperial 14.7   8 440.0 230 3.23 5.345 17.42  0  0    3    4
    ## 18            Fiat 128 32.4   4  78.7  66 4.08 2.200 19.47  1  1    4    1
    ## 19         Honda Civic 30.4   4  75.7  52 4.93 1.615 18.52  1  1    4    2
    ## 20      Toyota Corolla 33.9   4  71.1  65 4.22 1.835 19.90  1  1    4    1
    ## 21       Toyota Corona 21.5   4 120.1  97 3.70 2.465 20.01  1  0    3    1
    ## 22    Dodge Challenger 15.5   8 318.0 150 2.76 3.520 16.87  0  0    3    2
    ## 23         AMC Javelin 15.2   8 304.0 150 3.15 3.435 17.30  0  0    3    2
    ## 24          Camaro Z28 13.3   8 350.0 245 3.73 3.840 15.41  0  0    3    4
    ## 25    Pontiac Firebird 19.2   8 400.0 175 3.08 3.845 17.05  0  0    3    2
    ## 26           Fiat X1-9 27.3   4  79.0  66 4.08 1.935 18.90  1  1    4    1
    ## 27       Porsche 914-2 26.0   4 120.3  91 4.43 2.140 16.70  0  1    5    2
    ## 28        Lotus Europa 30.4   4  95.1 113 3.77 1.513 16.90  1  1    5    2
    ## 29      Ford Pantera L 15.8   8 351.0 264 4.22 3.170 14.50  0  1    5    4
    ## 30        Ferrari Dino 19.7   6 145.0 175 3.62 2.770 15.50  0  1    5    6
    ## 31       Maserati Bora 15.0   8 301.0 335 3.54 3.570 14.60  0  1    5    8
    ## 32          Volvo 142E 21.4   4 121.0 109 4.11 2.780 18.60  1  1    4    2

``` r
mpg <- select(mtcars, rowname, mpg, disp)

mpg <- mtcars %>% 
  select(rowname, mpg, disp, wt)

example <- select(mtcars, disp, everything())


example <- mtcars %>% 
  select(disp, everything())
```

group\_by()

This function allows for the creation of subgroups within the table and
allows you to perform actions of the grouped data. The use case for this
in healthcare is where you need to calculate a value for each individual
in a data set.

``` r
cylinders <- group_by(mtcars, cyl) %>% tally()

cylinders <- mtcars %>% 
  group_by(cyl) %>% 
  tally()
```

You can see here that on it’s own grouping by a variable doesn’t do much
but it you linj it with another function it starts to become a really
valuable tool for any analysis.

summarise()

Summarise can be used to calculate summary statistics for a whole table,
combining this with a group\_by allows for sub population summaries to
be calculated.

``` r
weight <- mtcars %>% 
  group_by(cyl) %>% 
  summarise(av_weight = mean(wt),
            sd_weigjt = sd(wt),
            med_weigh = median(wt)) %>% 
  kable("html") %>%
  kable_styling(bootstrap_options = "striped", full_width = F)
```

mutate()

Mutate allows the user to create new columns of calculated variables
within an existing data set. Here we will use an ifelse() statement to
assign arbitatry values to rows of data based on the following cyl
values:

8 = red 6 = blue 4 = green

The structure of an ifelse statement is as follows:

Ifelse(logical argument, Answer if true, Answer if false)

these can be nested within each other as shown below to create a deeper
logic.

an alternative to ifelse() is
[case\_when()](https://dplyr.tidyverse.org/reference/case_when.html)

``` r
mtcars$cyl
```

    ##  [1] 6 6 4 6 8 6 8 4 4 6 6 8 8 8 8 8 8 4 4 4 4 8 8 8 8 4 4 4 8 6 8 4

``` r
variables  <- mtcars %>% 
  mutate(color = ifelse(cyl == 4, "green",
                        ifelse(cyl == 6, "blue", "red")),
         owner = ifelse(color == "red", "banker", 
                        ifelse(color == "green", "UN worker", "Geographer"))) %>% 
  group_by(owner) %>% 
  tally() %>% 
  kable("html") %>%
  kable_styling(bootstrap_options = "striped", full_width = F)
```

transmute()

Transmute works in a similar way to mutate except values are not added
to a dataset they are calculated and output as a separate table.

``` r
t_variables  <- mtcars %>% 
  transmute(color = ifelse(cyl == 4, "green",
                        ifelse(cyl == 6, "blue", "red")),
         owner = ifelse(color == "red", "banker", 
                        ifelse(color == "green", "UN worker", "Geographer")),
         name = rowname) %>% 
  select(name, color, owner)
```

### Creating tables

In the above examples tables have been created by piping results to
kable() which is a function to create a table. The kableExtra package is
a nice package which allows the user to create formatted tables in latex
and html. The documentation can be found at the below link.

<https://haozhu233.github.io/kableExtra/awesome_table_in_html.html>

Next sessions:

The following sessions are going to be much more free flowing with the
aim that we use the time to help each others analysis progress. Where
there are specific topics that might be good to cover people can request
these and I will look at putting some materials together. For the next
session people should bring some data and tasks that they would like to
tackle and we can work alongside one another to make some progess.
