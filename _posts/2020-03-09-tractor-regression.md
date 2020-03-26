---
  title: "Early Tractorization of Rural America"
  date: 2020-03-09
  tags: [EDA, regression]
  header:
    image: "../assets/images/tractor/tractorHeaderImg4.jpg"
  excerpt: "Data Science"
---

### Anchors

[Value Added by Manufacturing](#value-added-by-manufacturing)

## Overview

This research was a part of a greater project headed by Dr. William White and Dr. Richard Steckel of The Ohio State University's Department of Economics. The core focus of the project was to look at the ways education was affected by early tractorization and rural manufacturing.

## The Data
Much of the data came from Michale Haine's [ICPSR Study Number 2896](https://www.colgate.edu/about/directory/mhaines). However quite a bit of cleaning and formatting was required to create sets which allowed for our analysis.

## The Focus

This was broken down into several parts, atttempting to answer several different questions.

Each of these questions focused around rural counties based on RUCC codes. Highly urban areas were not of interest as they naturally would not contain much farming and thus tractorization would be minimal to non existent, manufacturing was already present in these areas and in general education was high relative to the rural communities.

1. Did early adoption of tractors lead to more manufacturing in these communities?
   1A. Did the injection of manufacturing in these rural communities have an effect on education?

2. Was there an increase in average education level in the counties which had early adoption of tractors.


## Value Added By Manufacturing

VAM is a metric that describes the how economy of a region, in this case a county, benefitted from the manufacturing industry within that space.
This data was sparse but in order to gain best high-level understanind as possible, I created a map with gradient to visualize counties with highest and lowest VAM across our selected time period. Below are comparitive maps, one will all counties availble, the other with urban counties removed.


<!-- 1929 ALL             |  1929 Rural
:-------------------------:|:-------------------------:
<embed src="{{ site.url }}{{ site.baseurl }}/assets/images/tractor/vam(1929-2007)/1929.pdf" type="application/pdf">  |  <embed src="{{ site.url }}{{ site.baseurl }}/assets/images/tractor/vam(1929-2007)/RUCC_adjusted/1929.pdf" type="application/pdf"> -->


<figure class="half">
    <a href="/assets/images/tractor/vam(1929-2007)/1929.pdf"><img src="/assets/images/tractor/vam(1929-2007)/1929.png"></a>
    <a href="/assets/images/tractor/vam(1929-2007)/RUCC_adjusted/1929.pdf"><img src="/assets/images/tractor/vam(1929-2007)/RUCC_adjusted/1929.png"></a>
    <figcaption>VAM 1929 All vs VAM 1929 Rural</figcaption>
</figure>



<!-- <img src="{{ site.url }}{{ site.baseurl }}/assets/images/tractor/vam(1929-2007)/1929.pdf" alt="1929"> <img src="{{ site.url }}{{ site.baseurl }}/assets/images/tractor/vam(1929-2007)/RUCC_adjusted/1929.pdf" alt="1929RUCC"> -->



Test Photo:

<img src="{{ site.url }}{{ site.baseurl}}/assets/images/tractor/TractorVsEduPlots/50_54.png" alt="test alt">
