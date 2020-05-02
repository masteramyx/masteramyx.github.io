---
title: "2020-04-05-formula-one"
author: "Kyle Amyx"
date: "5/1/2020"
output: 
  html_document:
    keep_md: true
---



## R Markdown

This is an R Markdown document. Markdown is a simple formatting syntax for authoring HTML, PDF, and MS Word documents. For more details on using R Markdown see <http://rmarkdown.rstudio.com>.

When you click the **Knit** button a document will be generated that includes both content as well as the output of any embedded R code chunks within the document. You can embed an R code chunk like this:



```r
8*8
```

```
## [1] 64
```


```r
circuits = read.csv("Data(1950_2017)/circuits.csv")
races = read.csv("Data(1950_2017)/races.csv")
```

```
## Warning in scan(file = file, what = what, sep = sep, quote = quote, dec =
## dec, : embedded nul(s) found in input
```

```r
results = read.csv("Data(1950_2017)/results.csv")
drivers = read.csv("Data(1950_2017)/drivers.csv")
```



```r
summary(circuits)
```

```
##    circuitId        circuitRef                             name   
##  Min.   : 1   adelaide   : 1   A1-Ring                       : 1  
##  1st Qu.:19   ain-diab   : 1   Adelaide Street Circuit       : 1  
##  Median :37   aintree    : 1   Ain Diab                      : 1  
##  Mean   :37   albert_park: 1   Aintree                       : 1  
##  3rd Qu.:55   americas   : 1   Albert Park Grand Prix Circuit: 1  
##  Max.   :73   anderstorp : 1   Aut\xcc_dromo do Estoril      : 1  
##               (Other)    :67   (Other)                       :67  
##        location     country        lat              lng          
##  Barcelona : 2   USA    :11   Min.   :-37.85   Min.   :-118.189  
##  California: 2   France : 7   1st Qu.: 33.58   1st Qu.:  -9.394  
##  Spielburg : 2   Spain  : 6   Median : 41.37   Median :   3.931  
##  Abu Dhabi : 1   UK     : 4   Mean   : 33.87   Mean   :   1.723  
##  Adelaide  : 1   Austria: 3   3rd Qu.: 47.22   3rd Qu.:  14.765  
##  Anderstorp: 1   Belgium: 3   Max.   : 57.27   Max.   : 144.968  
##  (Other)   :64   (Other):39                                      
##       alt    
##  Min.   :10  
##  1st Qu.:10  
##  Median :10  
##  Mean   :10  
##  3rd Qu.:10  
##  Max.   :10  
##  NA's   :72  
##                                                                   url    
##  http://en.wikipedia.org/wiki/A1-Ring                               : 1  
##  http://en.wikipedia.org/wiki/Adelaide_Street_Circuit               : 1  
##  http://en.wikipedia.org/wiki/Ain-Diab_Circuit                      : 1  
##  http://en.wikipedia.org/wiki/Aintree_Motor_Racing_Circuit          : 1  
##  http://en.wikipedia.org/wiki/Aut%C3%B3dromo_do_Estoril             : 1  
##  http://en.wikipedia.org/wiki/Aut%C3%B3dromo_Hermanos_Rodr%C3%ADguez: 1  
##  (Other)                                                            :67
```


```r
summary(races)
```

```
##      raceId          year          round          circuitId    
##  Min.   :   1   Min.   :1950   Min.   : 1.000   Min.   : 1.00  
##  1st Qu.: 250   1st Qu.:1974   1st Qu.: 4.000   1st Qu.: 9.00  
##  Median : 499   Median :1990   Median : 8.000   Median :18.00  
##  Mean   : 500   Mean   :1989   Mean   : 8.234   Mean   :21.76  
##  3rd Qu.: 748   3rd Qu.:2005   3rd Qu.:12.000   3rd Qu.:30.00  
##  Max.   :1009   Max.   :2018   Max.   :21.000   Max.   :73.00  
##                                                                
##                  name             date           time    
##  British Grand Prix: 69   1950-05-13:  1           :731  
##  Italian Grand Prix: 69   1950-05-21:  1   12:00:00:118  
##  Monaco Grand Prix : 65   1950-05-30:  1   14:00:00: 28  
##  Belgian Grand Prix: 63   1950-06-04:  1   06:00:00: 20  
##  German Grand Prix : 63   1950-06-18:  1   13:00:00: 14  
##  French Grand Prix : 59   1950-07-02:  1   16:00:00: 12  
##  (Other)           :609   (Other)   :991   (Other) : 74  
##                                                    url     
##  http://en.wikipedia.org/wiki/1950_Belgian_Grand_Prix:  1  
##  http://en.wikipedia.org/wiki/1950_British_Grand_Prix:  1  
##  http://en.wikipedia.org/wiki/1950_French_Grand_Prix :  1  
##  http://en.wikipedia.org/wiki/1950_Indianapolis_500  :  1  
##  http://en.wikipedia.org/wiki/1950_Italian_Grand_Prix:  1  
##  http://en.wikipedia.org/wiki/1950_Monaco_Grand_Prix :  1  
##  (Other)                                             :991
```


```r
summary(results)
```

```
##     resultId         raceId         driverId     constructorId   
##  Min.   :    1   Min.   :  1.0   Min.   :  1.0   Min.   :  1.00  
##  1st Qu.: 5945   1st Qu.:273.0   1st Qu.: 55.0   1st Qu.:  6.00  
##  Median :11889   Median :478.0   Median :154.0   Median : 25.00  
##  Mean   :11889   Mean   :487.2   Mean   :226.5   Mean   : 46.28  
##  3rd Qu.:17833   3rd Qu.:718.0   3rd Qu.:314.0   3rd Qu.: 57.00  
##  Max.   :23781   Max.   :988.0   Max.   :843.0   Max.   :210.00  
##                                                                  
##      number            grid          position       positionText 
##  Min.   :  0.00   Min.   : 0.00   Min.   : 1.000   R      :8517  
##  1st Qu.:  7.00   1st Qu.: 5.00   1st Qu.: 4.000   F      :1368  
##  Median : 15.00   Median :11.00   Median : 7.000   3      : 986  
##  Mean   : 16.97   Mean   :11.27   Mean   : 7.782   4      : 986  
##  3rd Qu.: 23.00   3rd Qu.:17.00   3rd Qu.:11.000   2      : 984  
##  Max.   :208.00   Max.   :34.00   Max.   :33.000   5      : 982  
##  NA's   :6                        NA's   :10550    (Other):9954  
##  positionOrder       points            laps              time      
##  Min.   : 1.00   Min.   : 0.000   Min.   :  0.00           :17773  
##  1st Qu.: 7.00   1st Qu.: 0.000   1st Qu.: 20.00   +8:22.19:    5  
##  Median :13.00   Median : 0.000   Median : 52.00   +1:29.6 :    4  
##  Mean   :13.08   Mean   : 1.601   Mean   : 45.27   0.7     :    4  
##  3rd Qu.:19.00   3rd Qu.: 1.000   3rd Qu.: 66.00   46.2    :    4  
##  Max.   :39.00   Max.   :50.000   Max.   :200.00   5.7     :    4  
##                                                    (Other) : 5983  
##   milliseconds        fastestLap         rank       fastestLapTime 
##  Min.   : 1474899   Min.   : 2.00   Min.   : 0.0           :18394  
##  1st Qu.: 5442948   1st Qu.:29.00   1st Qu.: 5.0    01:17.2:   28  
##  Median : 5859428   Median :44.00   Median :11.0    01:16.5:   27  
##  Mean   : 6303313   Mean   :41.06   Mean   :10.6    01:16.8:   26  
##  3rd Qu.: 6495440   3rd Qu.:53.00   3rd Qu.:16.0    01:28.0:   26  
##  Max.   :15090540   Max.   :78.00   Max.   :24.0    01:19.1:   24  
##  NA's   :17774      NA's   :18394   NA's   :18246   (Other): 5252  
##  fastestLapSpeed    statusId     
##         :18394   Min.   :  1.00  
##  189.423:    3   1st Qu.:  1.00  
##  195.933:    3   Median : 11.00  
##  196.785:    3   Mean   : 18.24  
##  200.091:    3   3rd Qu.: 16.00  
##  201.33 :    3   Max.   :136.00  
##  (Other): 5368
```


```r
summary(drivers)
```

```
##     driverId         driverRef       number           code    
##  Min.   :  1.0   abate    :  1   Min.   : 2.00          :757  
##  1st Qu.:211.2   abecassis:  1   1st Qu.:10.25   BIA    :  2  
##  Median :421.5   acheson  :  1   Median :21.50   HAR    :  2  
##  Mean   :421.5   adamich  :  1   Mean   :30.50   MAG    :  2  
##  3rd Qu.:631.8   adams    :  1   3rd Qu.:38.25   VER    :  2  
##  Max.   :843.0   ader     :  1   Max.   :99.00   ALB    :  1  
##                  (Other)  :836   NA's   :804     (Other): 76  
##     forename         surname            dob         nationality 
##  John   : 14   Taylor    :  5   02/10/1921:  2   British  :162  
##  Mike   : 14   Wilson    :  4   04/09/1920:  2   American :157  
##  Peter  : 13   Brabham   :  3   05/05/1932:  2   Italian  : 99  
##  Bill   : 11   Brown     :  3   06/06/1923:  2   French   : 73  
##  Tony   : 11   Fittipaldi:  3   06/10/1918:  2   German   : 49  
##  Bob    : 10   Hill      :  3   12/12/1946:  2   Brazilian: 31  
##  (Other):769   (Other)   :821   (Other)   :830   (Other)  :271  
##                                                           url     
##                                                             :  1  
##  http://en.wikipedia.org/wiki/%C3%89lie_Bayol               :  1  
##  http://en.wikipedia.org/wiki/%C3%89ric_Bernard             :  1  
##  http://en.wikipedia.org/wiki/%C3%89rik_Comas               :  1  
##  http://en.wikipedia.org/wiki/%C3%93scar_Alfredo_G%C3%A1lvez:  1  
##  http://en.wikipedia.org/wiki/A.J._Foyt                     :  1  
##  (Other)                                                    :836
```

## Including Plots

You can also embed plots, for example:

![](2020-04-05-formula-one_files/figure-html/pressure-1.png)<!-- -->![](2020-04-05-formula-one_files/figure-html/pressure-2.png)<!-- -->

Note that the `echo = FALSE` parameter was added to the code chunk to prevent printing of the R code that generated the plot.

