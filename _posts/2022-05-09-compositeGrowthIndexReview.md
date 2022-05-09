---
layout: post
title: "*Acropora cervicornis* Composite Growth Index"
author: "Patrick Kiel"
date: '2022-05-09'
categories: [methods]
description: "Growth of the staghorn coral is measured in many different ways. Here I propose a composite indexing methodology to align disparate measurements to deduce genotype-specific influences on growth."
output:
  md_document:
    variant: gfm
    preserve_yaml: TRUE
knit: (function(inputFile, encoding) {
  rmarkdown::render(inputFile, 
  encoding = encoding, 
  output_file = paste0(Sys.Date(), "-",
                        gsub(pattern = "\\.Rmd$",
                              "", basename(inputFile))
                        ,".md"), 
  output_dir = "../_posts") })
always_allow_html: true
---

<style type="text/css">
caption {
      color: black;
      font-weight: bold;
      font-size: 1.2em;
}

.tocify-extend-page {
  height: 0 !important;
}
</style>
<script type="text/javascript">
function verify() {
  if (document.getElementById('password').value === 'acropora') {
    document.getElementById('HIDDENDIV').classList.remove("hidden"); 
    document.getElementById('credentials').classList.add("hidden"); // Hide the div containing the credentials
  } else {
    alert('Invalid Password! You cannot view this content.');
    password.setSelectionRange(0, password.value.length);
  }
  return false;
}
</script>
<style type="text/css">
.hidden {
  display: none;
}
</style>
<!-- The password box -->

<div id="credentials">

<input type="text" id="password" onkeydown="if (event.keyCode == 13) verify()" />
<br/>
<input id="button" type="button" value="Show Content" onclick="verify()" />

</div>

<!-- The content we want to show after password -->

<div id="HIDDENDIV" class="hidden" markdown="1">

# Overview

## Previous Studies

There exist **17** studies that have investigated the growth forms of
*Acropora cervicornis* at the genotype level which have been
incorporated into our database. These studies began with Diego Lirman
who analyzed genotype-specific differences in annual proportionate
growth (termed productivity in *Lirman et al. 2014*) across genotypes
within Diego’s Biscayne National Park nurseries and his work in the
Dominican Republic. Katie Lohr built upon this and analyzed 10 genotypes
for differences in total linear extension and calcification rate over a
13 month study of CRF genotypes (Lohr and Patterson 2017). At the same
time, Ford Drury analyzed the genotype niches in a genotype by
environment study (Dury, Manzello, Lirman 2017). Other studies did not
solely focus on differences among genotypes but their data analyzing
growth under OA, temperature stress, or a combination of the two shed
light on genotype-specific patterns. There has consistently been
genotypic patterns of growth throughout all of these studies. Through
the connection of each individual dataset, we can elucidate new,
overarching genotype-specific patterns of growth. Below is a table
summarizing the aforementioned and complementary studies that have
analyzed growth of genotyped *A. cervicornis*. The remaining tables
delve into the combined data of all these studies to begin to draw
patterns.

## Traits Table

``` r
#table describing traits
traitStats %>%
kbl(align = 'c',
    caption = "Table 1: Summary statistics for each unqiue trait, unit, and method combination.") %>%
  kable_classic() %>%
  row_spec(0, bold = T)
```

<table class=" lightable-classic" style="font-family: &quot;Arial Narrow&quot;, &quot;Source Sans Pro&quot;, sans-serif; margin-left: auto; margin-right: auto;">
<caption>
Table 1: Summary statistics for each unqiue trait, unit, and method
combination.
</caption>
<thead>
<tr>
<th style="text-align:center;font-weight: bold;">
trait
</th>
<th style="text-align:center;font-weight: bold;">
unit
</th>
<th style="text-align:center;font-weight: bold;">
method
</th>
<th style="text-align:center;font-weight: bold;">
mean
</th>
<th style="text-align:center;font-weight: bold;">
sd
</th>
<th style="text-align:center;font-weight: bold;">
min
</th>
<th style="text-align:center;font-weight: bold;">
max
</th>
<th style="text-align:center;font-weight: bold;">
n
</th>
<th style="text-align:center;font-weight: bold;">
datasets
</th>
<th style="text-align:center;font-weight: bold;">
genotypes
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:center;">
6-month colony volumetric growth
</td>
<td style="text-align:center;">
proportionate growth
</td>
<td style="text-align:center;">
3D photogrammetry
</td>
<td style="text-align:center;">
2.5333658
</td>
<td style="text-align:center;">
4.5160081
</td>
<td style="text-align:center;">
0.0377524
</td>
<td style="text-align:center;">
60.281553
</td>
<td style="text-align:center;">
293
</td>
<td style="text-align:center;">
3
</td>
<td style="text-align:center;">
17
</td>
</tr>
<tr>
<td style="text-align:center;">
6-month interstitial space growth
</td>
<td style="text-align:center;">
proportionate growth
</td>
<td style="text-align:center;">
3D photogrammetry
</td>
<td style="text-align:center;">
6.3103033
</td>
<td style="text-align:center;">
5.5360624
</td>
<td style="text-align:center;">
0.0692467
</td>
<td style="text-align:center;">
35.728773
</td>
<td style="text-align:center;">
135
</td>
<td style="text-align:center;">
1
</td>
<td style="text-align:center;">
10
</td>
</tr>
<tr>
<td style="text-align:center;">
6-month linear growth
</td>
<td style="text-align:center;">
proportionate growth
</td>
<td style="text-align:center;">
ruler
</td>
<td style="text-align:center;">
1.6449644
</td>
<td style="text-align:center;">
1.4264161
</td>
<td style="text-align:center;">
0.0133041
</td>
<td style="text-align:center;">
16.524444
</td>
<td style="text-align:center;">
2686
</td>
<td style="text-align:center;">
10
</td>
<td style="text-align:center;">
120
</td>
</tr>
<tr>
<td style="text-align:center;">
annual colony volumetric growth
</td>
<td style="text-align:center;">
annual proportionate growth
</td>
<td style="text-align:center;">
3D photogrammetry
</td>
<td style="text-align:center;">
6.5244687
</td>
<td style="text-align:center;">
8.1461205
</td>
<td style="text-align:center;">
0.3835854
</td>
<td style="text-align:center;">
63.974185
</td>
<td style="text-align:center;">
170
</td>
<td style="text-align:center;">
3
</td>
<td style="text-align:center;">
18
</td>
</tr>
<tr>
<td style="text-align:center;">
annual interstitial space growth
</td>
<td style="text-align:center;">
annual proportionate growth
</td>
<td style="text-align:center;">
3D photogrammetry
</td>
<td style="text-align:center;">
22.6691608
</td>
<td style="text-align:center;">
23.9115484
</td>
<td style="text-align:center;">
1.4555964
</td>
<td style="text-align:center;">
216.829571
</td>
<td style="text-align:center;">
123
</td>
<td style="text-align:center;">
1
</td>
<td style="text-align:center;">
10
</td>
</tr>
<tr>
<td style="text-align:center;">
annual linear growth
</td>
<td style="text-align:center;">
annual proportionate growth
</td>
<td style="text-align:center;">
ruler
</td>
<td style="text-align:center;">
6.6611193
</td>
<td style="text-align:center;">
5.8815492
</td>
<td style="text-align:center;">
0.0405556
</td>
<td style="text-align:center;">
59.211111
</td>
<td style="text-align:center;">
1583
</td>
<td style="text-align:center;">
9
</td>
<td style="text-align:center;">
81
</td>
</tr>
<tr>
<td style="text-align:center;">
colony volumetric SGR
</td>
<td style="text-align:center;">
% change day^-1
</td>
<td style="text-align:center;">
3D photogrammetry
</td>
<td style="text-align:center;">
0.5092050
</td>
<td style="text-align:center;">
0.1972331
</td>
<td style="text-align:center;">
0.0883920
</td>
<td style="text-align:center;">
1.376506
</td>
<td style="text-align:center;">
317
</td>
<td style="text-align:center;">
4
</td>
<td style="text-align:center;">
23
</td>
</tr>
<tr>
<td style="text-align:center;">
daily calcification
</td>
<td style="text-align:center;">
mg day^-1
</td>
<td style="text-align:center;">
buoyant weight
</td>
<td style="text-align:center;">
71.5996332
</td>
<td style="text-align:center;">
96.9861159
</td>
<td style="text-align:center;">
3.9540230
</td>
<td style="text-align:center;">
497.308997
</td>
<td style="text-align:center;">
266
</td>
<td style="text-align:center;">
5
</td>
<td style="text-align:center;">
32
</td>
</tr>
<tr>
<td style="text-align:center;">
dark calcification
</td>
<td style="text-align:center;">
µmol cm^-2 h^-1
</td>
<td style="text-align:center;">
alkalinity anomaly
</td>
<td style="text-align:center;">
0.6967946
</td>
<td style="text-align:center;">
0.2713945
</td>
<td style="text-align:center;">
0.0180000
</td>
<td style="text-align:center;">
1.594000
</td>
<td style="text-align:center;">
56
</td>
<td style="text-align:center;">
1
</td>
<td style="text-align:center;">
12
</td>
</tr>
<tr>
<td style="text-align:center;">
interstitial space SGR
</td>
<td style="text-align:center;">
% change day^-1
</td>
<td style="text-align:center;">
3D photogrammetry
</td>
<td style="text-align:center;">
0.7736615
</td>
<td style="text-align:center;">
0.2390515
</td>
<td style="text-align:center;">
0.2423776
</td>
<td style="text-align:center;">
1.520514
</td>
<td style="text-align:center;">
136
</td>
<td style="text-align:center;">
1
</td>
<td style="text-align:center;">
10
</td>
</tr>
<tr>
<td style="text-align:center;">
light calcification
</td>
<td style="text-align:center;">
µmol cm^-2 h^-1
</td>
<td style="text-align:center;">
alkalinity anomaly
</td>
<td style="text-align:center;">
0.8475254
</td>
<td style="text-align:center;">
0.2766803
</td>
<td style="text-align:center;">
0.3110000
</td>
<td style="text-align:center;">
1.594000
</td>
<td style="text-align:center;">
59
</td>
<td style="text-align:center;">
1
</td>
<td style="text-align:center;">
12
</td>
</tr>
<tr>
<td style="text-align:center;">
mass normalized daily calcification
</td>
<td style="text-align:center;">
mg day^-1 g^-1
</td>
<td style="text-align:center;">
buoyant weight
</td>
<td style="text-align:center;">
27.2406909
</td>
<td style="text-align:center;">
41.4262869
</td>
<td style="text-align:center;">
0.3450656
</td>
<td style="text-align:center;">
191.199153
</td>
<td style="text-align:center;">
244
</td>
<td style="text-align:center;">
4
</td>
<td style="text-align:center;">
27
</td>
</tr>
<tr>
<td style="text-align:center;">
SA normalized daily calcification
</td>
<td style="text-align:center;">
mg day^-1 cm^-2
</td>
<td style="text-align:center;">
buoyant weight
</td>
<td style="text-align:center;">
1.2370585
</td>
<td style="text-align:center;">
0.3665081
</td>
<td style="text-align:center;">
0.5407155
</td>
<td style="text-align:center;">
2.884992
</td>
<td style="text-align:center;">
105
</td>
<td style="text-align:center;">
2
</td>
<td style="text-align:center;">
13
</td>
</tr>
<tr>
<td style="text-align:center;">
specific growth rate
</td>
<td style="text-align:center;">
% change day^-1
</td>
<td style="text-align:center;">
ruler
</td>
<td style="text-align:center;">
0.5105088
</td>
<td style="text-align:center;">
0.2186303
</td>
<td style="text-align:center;">
0.0062386
</td>
<td style="text-align:center;">
1.597730
</td>
<td style="text-align:center;">
2867
</td>
<td style="text-align:center;">
11
</td>
<td style="text-align:center;">
122
</td>
</tr>
</tbody>
</table>

## Connecting Across Datasets

We can then look at the mean value of each metric for each genotype. The
columns have been ordered by their amount of data completeness. Columns
to the left of the vertical line describe linear extension, while
columns to the right of the line describe total calcification. Linear
extension includes TLE and volumetric methods for a total of 9 metrics,
and calcification metrics include buoyant weight and total alkalinity
anomaly methodologies for a total of 5 metrics. The large amounts of
missing data will force us to impute many data points.

``` r
  count_na <- function(x) sum(is.na(x))

  overlap <-   corals %>%
    filter(str_detect(filters, "(Bleach)|(OA)" ,negate = T)) %>%
    group_by(genotype, trait, unit, method) %>%
    summarise(mean = mean(value, na.rm = T)) %>%
    ungroup() %>%
    arrange(trait,desc(mean)) %>%
    select(-c(unit,method)) %>%
    pivot_wider(names_from = trait,
                values_from = mean) %>%
    #arrange by rows w/ least # of na
    mutate(count = apply(., 1, count_na)) %>%
    arrange(count) %>%
    select(-count)

  overlap <- relocate(overlap, overlap %>%
    select(-genotype) %>%
    summarise(across(everything(), ~ sum(is.na(.)))) %>%
    unlist %>% sort() %>%
    names(), .after = "genotype") %>%
    relocate(c(`daily calcification`,`mass normalized daily calcification`,
               `SA normalized daily calcification`:`light calcification`),
             .after=`interstitial space SGR`)

  kbl(overlap,
    align = 'c',
    digits = 2) %>%
  kable_classic() %>%
  row_spec(0, bold = T) %>%
  column_spec(11, extra_css = "border-left: 1px solid #673ab7;")
```

<table class=" lightable-classic" style="font-family: &quot;Arial Narrow&quot;, &quot;Source Sans Pro&quot;, sans-serif; margin-left: auto; margin-right: auto;">
<thead>
<tr>
<th style="text-align:center;font-weight: bold;">
genotype
</th>
<th style="text-align:center;font-weight: bold;">
specific growth rate
</th>
<th style="text-align:center;font-weight: bold;">
6-month linear growth
</th>
<th style="text-align:center;font-weight: bold;">
annual linear growth
</th>
<th style="text-align:center;font-weight: bold;">
colony volumetric SGR
</th>
<th style="text-align:center;font-weight: bold;">
annual colony volumetric growth
</th>
<th style="text-align:center;font-weight: bold;">
6-month colony volumetric growth
</th>
<th style="text-align:center;font-weight: bold;">
6-month interstitial space growth
</th>
<th style="text-align:center;font-weight: bold;">
annual interstitial space growth
</th>
<th style="text-align:center;font-weight: bold;">
interstitial space SGR
</th>
<th style="text-align:center;font-weight: bold;">
daily calcification
</th>
<th style="text-align:center;font-weight: bold;">
mass normalized daily calcification
</th>
<th style="text-align:center;font-weight: bold;">
SA normalized daily calcification
</th>
<th style="text-align:center;font-weight: bold;">
dark calcification
</th>
<th style="text-align:center;font-weight: bold;">
light calcification
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:center;">
ML41
</td>
<td style="text-align:center;">
0.40
</td>
<td style="text-align:center;">
1.32
</td>
<td style="text-align:center;">
3.96
</td>
<td style="text-align:center;">
0.45
</td>
<td style="text-align:center;">
4.09
</td>
<td style="text-align:center;">
2.31
</td>
<td style="text-align:center;">
6.34
</td>
<td style="text-align:center;">
16.72
</td>
<td style="text-align:center;">
0.80
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
22.02
</td>
<td style="text-align:center;">
1.85
</td>
<td style="text-align:center;">
1.13
</td>
<td style="text-align:center;">
0.91
</td>
<td style="text-align:center;">
0.82
</td>
</tr>
<tr>
<td style="text-align:center;">
ML7
</td>
<td style="text-align:center;">
0.36
</td>
<td style="text-align:center;">
0.99
</td>
<td style="text-align:center;">
3.48
</td>
<td style="text-align:center;">
0.53
</td>
<td style="text-align:center;">
7.25
</td>
<td style="text-align:center;">
1.88
</td>
<td style="text-align:center;">
6.93
</td>
<td style="text-align:center;">
32.14
</td>
<td style="text-align:center;">
0.86
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
34.82
</td>
<td style="text-align:center;">
2.51
</td>
<td style="text-align:center;">
1.25
</td>
<td style="text-align:center;">
0.74
</td>
<td style="text-align:center;">
0.88
</td>
</tr>
<tr>
<td style="text-align:center;">
ML62
</td>
<td style="text-align:center;">
0.56
</td>
<td style="text-align:center;">
2.10
</td>
<td style="text-align:center;">
4.88
</td>
<td style="text-align:center;">
0.49
</td>
<td style="text-align:center;">
6.67
</td>
<td style="text-align:center;">
1.73
</td>
<td style="text-align:center;">
7.52
</td>
<td style="text-align:center;">
30.94
</td>
<td style="text-align:center;">
0.83
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
9.57
</td>
<td style="text-align:center;">
1.90
</td>
<td style="text-align:center;">
0.98
</td>
<td style="text-align:center;">
0.48
</td>
<td style="text-align:center;">
0.84
</td>
</tr>
<tr>
<td style="text-align:center;">
ML50
</td>
<td style="text-align:center;">
0.51
</td>
<td style="text-align:center;">
1.86
</td>
<td style="text-align:center;">
5.62
</td>
<td style="text-align:center;">
0.43
</td>
<td style="text-align:center;">
6.05
</td>
<td style="text-align:center;">
1.55
</td>
<td style="text-align:center;">
6.68
</td>
<td style="text-align:center;">
30.46
</td>
<td style="text-align:center;">
0.74
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
10.98
</td>
<td style="text-align:center;">
2.34
</td>
<td style="text-align:center;">
1.25
</td>
<td style="text-align:center;">
0.84
</td>
<td style="text-align:center;">
0.73
</td>
</tr>
<tr>
<td style="text-align:center;">
ML31
</td>
<td style="text-align:center;">
0.43
</td>
<td style="text-align:center;">
1.86
</td>
<td style="text-align:center;">
4.40
</td>
<td style="text-align:center;">
0.35
</td>
<td style="text-align:center;">
2.73
</td>
<td style="text-align:center;">
1.54
</td>
<td style="text-align:center;">
6.41
</td>
<td style="text-align:center;">
16.42
</td>
<td style="text-align:center;">
0.71
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
20.17
</td>
<td style="text-align:center;">
2.05
</td>
<td style="text-align:center;">
1.13
</td>
<td style="text-align:center;">
0.92
</td>
<td style="text-align:center;">
0.87
</td>
</tr>
<tr>
<td style="text-align:center;">
ML3
</td>
<td style="text-align:center;">
0.43
</td>
<td style="text-align:center;">
1.70
</td>
<td style="text-align:center;">
4.55
</td>
<td style="text-align:center;">
0.44
</td>
<td style="text-align:center;">
5.13
</td>
<td style="text-align:center;">
1.51
</td>
<td style="text-align:center;">
5.77
</td>
<td style="text-align:center;">
19.12
</td>
<td style="text-align:center;">
0.71
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
9.66
</td>
<td style="text-align:center;">
2.02
</td>
<td style="text-align:center;">
1.09
</td>
<td style="text-align:center;">
0.75
</td>
<td style="text-align:center;">
0.71
</td>
</tr>
<tr>
<td style="text-align:center;">
ML44
</td>
<td style="text-align:center;">
0.43
</td>
<td style="text-align:center;">
1.15
</td>
<td style="text-align:center;">
4.51
</td>
<td style="text-align:center;">
0.50
</td>
<td style="text-align:center;">
6.35
</td>
<td style="text-align:center;">
1.31
</td>
<td style="text-align:center;">
4.37
</td>
<td style="text-align:center;">
17.44
</td>
<td style="text-align:center;">
0.70
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
21.41
</td>
<td style="text-align:center;">
2.10
</td>
<td style="text-align:center;">
1.20
</td>
<td style="text-align:center;">
0.65
</td>
<td style="text-align:center;">
0.99
</td>
</tr>
<tr>
<td style="text-align:center;">
ML1
</td>
<td style="text-align:center;">
0.45
</td>
<td style="text-align:center;">
1.50
</td>
<td style="text-align:center;">
3.80
</td>
<td style="text-align:center;">
0.43
</td>
<td style="text-align:center;">
4.63
</td>
<td style="text-align:center;">
1.30
</td>
<td style="text-align:center;">
3.98
</td>
<td style="text-align:center;">
17.74
</td>
<td style="text-align:center;">
0.76
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
15.87
</td>
<td style="text-align:center;">
1.32
</td>
<td style="text-align:center;">
1.36
</td>
<td style="text-align:center;">
0.64
</td>
<td style="text-align:center;">
0.67
</td>
</tr>
<tr>
<td style="text-align:center;">
ML13
</td>
<td style="text-align:center;">
0.46
</td>
<td style="text-align:center;">
1.29
</td>
<td style="text-align:center;">
3.42
</td>
<td style="text-align:center;">
0.35
</td>
<td style="text-align:center;">
2.94
</td>
<td style="text-align:center;">
1.13
</td>
<td style="text-align:center;">
6.73
</td>
<td style="text-align:center;">
19.49
</td>
<td style="text-align:center;">
0.78
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
7.12
</td>
<td style="text-align:center;">
1.54
</td>
<td style="text-align:center;">
0.92
</td>
<td style="text-align:center;">
0.65
</td>
<td style="text-align:center;">
0.87
</td>
</tr>
<tr>
<td style="text-align:center;">
ML36
</td>
<td style="text-align:center;">
0.39
</td>
<td style="text-align:center;">
0.95
</td>
<td style="text-align:center;">
3.66
</td>
<td style="text-align:center;">
0.49
</td>
<td style="text-align:center;">
5.82
</td>
<td style="text-align:center;">
1.70
</td>
<td style="text-align:center;">
7.94
</td>
<td style="text-align:center;">
23.95
</td>
<td style="text-align:center;">
0.85
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
</tr>
<tr>
<td style="text-align:center;">
M6
</td>
<td style="text-align:center;">
0.57
</td>
<td style="text-align:center;">
1.72
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
0.54
</td>
<td style="text-align:center;">
11.98
</td>
<td style="text-align:center;">
5.30
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
12.77
</td>
<td style="text-align:center;">
0.89
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
</tr>
<tr>
<td style="text-align:center;">
U41
</td>
<td style="text-align:center;">
0.70
</td>
<td style="text-align:center;">
5.52
</td>
<td style="text-align:center;">
13.29
</td>
<td style="text-align:center;">
0.54
</td>
<td style="text-align:center;">
5.30
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
159.83
</td>
<td style="text-align:center;">
65.67
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
</tr>
<tr>
<td style="text-align:center;">
K3
</td>
<td style="text-align:center;">
0.72
</td>
<td style="text-align:center;">
5.08
</td>
<td style="text-align:center;">
14.59
</td>
<td style="text-align:center;">
0.34
</td>
<td style="text-align:center;">
2.39
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
189.47
</td>
<td style="text-align:center;">
84.94
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
</tr>
<tr>
<td style="text-align:center;">
K2
</td>
<td style="text-align:center;">
0.68
</td>
<td style="text-align:center;">
4.51
</td>
<td style="text-align:center;">
15.98
</td>
<td style="text-align:center;">
0.32
</td>
<td style="text-align:center;">
2.54
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
199.95
</td>
<td style="text-align:center;">
84.65
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
</tr>
<tr>
<td style="text-align:center;">
U77
</td>
<td style="text-align:center;">
0.65
</td>
<td style="text-align:center;">
4.01
</td>
<td style="text-align:center;">
10.08
</td>
<td style="text-align:center;">
0.62
</td>
<td style="text-align:center;">
6.98
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
150.69
</td>
<td style="text-align:center;">
54.90
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
</tr>
<tr>
<td style="text-align:center;">
U44
</td>
<td style="text-align:center;">
0.63
</td>
<td style="text-align:center;">
3.64
</td>
<td style="text-align:center;">
11.19
</td>
<td style="text-align:center;">
0.45
</td>
<td style="text-align:center;">
4.26
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
123.64
</td>
<td style="text-align:center;">
47.16
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
</tr>
<tr>
<td style="text-align:center;">
ML34
</td>
<td style="text-align:center;">
0.58
</td>
<td style="text-align:center;">
2.12
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
12.38
</td>
<td style="text-align:center;">
2.10
</td>
<td style="text-align:center;">
1.07
</td>
<td style="text-align:center;">
0.57
</td>
<td style="text-align:center;">
0.85
</td>
</tr>
<tr>
<td style="text-align:center;">
Marker 9
</td>
<td style="text-align:center;">
0.56
</td>
<td style="text-align:center;">
1.67
</td>
<td style="text-align:center;">
8.89
</td>
<td style="text-align:center;">
0.53
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
1.80
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
</tr>
<tr>
<td style="text-align:center;">
U47
</td>
<td style="text-align:center;">
0.80
</td>
<td style="text-align:center;">
4.70
</td>
<td style="text-align:center;">
18.24
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
120.05
</td>
<td style="text-align:center;">
52.37
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
</tr>
<tr>
<td style="text-align:center;">
U73
</td>
<td style="text-align:center;">
0.82
</td>
<td style="text-align:center;">
4.61
</td>
<td style="text-align:center;">
19.55
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
137.15
</td>
<td style="text-align:center;">
46.89
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
</tr>
<tr>
<td style="text-align:center;">
U78
</td>
<td style="text-align:center;">
0.79
</td>
<td style="text-align:center;">
4.10
</td>
<td style="text-align:center;">
16.52
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
146.81
</td>
<td style="text-align:center;">
47.16
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
</tr>
<tr>
<td style="text-align:center;">
K1
</td>
<td style="text-align:center;">
0.79
</td>
<td style="text-align:center;">
3.93
</td>
<td style="text-align:center;">
15.47
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
90.84
</td>
<td style="text-align:center;">
34.87
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
</tr>
<tr>
<td style="text-align:center;">
K25
</td>
<td style="text-align:center;">
0.63
</td>
<td style="text-align:center;">
3.02
</td>
<td style="text-align:center;">
9.95
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
72.80
</td>
<td style="text-align:center;">
23.20
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
</tr>
<tr>
<td style="text-align:center;">
ML20
</td>
<td style="text-align:center;">
0.44
</td>
<td style="text-align:center;">
1.21
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
10.31
</td>
<td style="text-align:center;">
1.13
</td>
<td style="text-align:center;">
1.31
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
</tr>
<tr>
<td style="text-align:center;">
ML63
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
10.97
</td>
<td style="text-align:center;">
2.25
</td>
<td style="text-align:center;">
1.24
</td>
<td style="text-align:center;">
0.38
</td>
<td style="text-align:center;">
0.92
</td>
</tr>
<tr>
<td style="text-align:center;">
ML47
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
10.96
</td>
<td style="text-align:center;">
2.20
</td>
<td style="text-align:center;">
1.25
</td>
<td style="text-align:center;">
0.84
</td>
<td style="text-align:center;">
1.01
</td>
</tr>
<tr>
<td style="text-align:center;">
BC-G
</td>
<td style="text-align:center;">
0.33
</td>
<td style="text-align:center;">
0.76
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
0.61
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
2.52
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
</tr>
<tr>
<td style="text-align:center;">
Stagreef
</td>
<td style="text-align:center;">
0.44
</td>
<td style="text-align:center;">
1.13
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
0.63
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
2.49
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
</tr>
<tr>
<td style="text-align:center;">
Sunny Isles-F
</td>
<td style="text-align:center;">
0.40
</td>
<td style="text-align:center;">
1.00
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
0.56
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
2.02
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
</tr>
<tr>
<td style="text-align:center;">
BC-H
</td>
<td style="text-align:center;">
0.56
</td>
<td style="text-align:center;">
1.61
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
0.50
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
1.58
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
</tr>
<tr>
<td style="text-align:center;">
ML5
</td>
<td style="text-align:center;">
0.59
</td>
<td style="text-align:center;">
2.82
</td>
<td style="text-align:center;">
5.50
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
63.40
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
</tr>
<tr>
<td style="text-align:center;">
ML56
</td>
<td style="text-align:center;">
0.48
</td>
<td style="text-align:center;">
2.18
</td>
<td style="text-align:center;">
3.38
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
22.90
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
</tr>
<tr>
<td style="text-align:center;">
ML54
</td>
<td style="text-align:center;">
0.48
</td>
<td style="text-align:center;">
1.87
</td>
<td style="text-align:center;">
3.99
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
34.10
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
</tr>
<tr>
<td style="text-align:center;">
U25
</td>
<td style="text-align:center;">
0.26
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
1.63
</td>
<td style="text-align:center;">
0.61
</td>
<td style="text-align:center;">
5.38
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
</tr>
<tr>
<td style="text-align:center;">
FM20
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
0.59
</td>
<td style="text-align:center;">
16.16
</td>
<td style="text-align:center;">
8.02
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
</tr>
<tr>
<td style="text-align:center;">
B
</td>
<td style="text-align:center;">
0.78
</td>
<td style="text-align:center;">
3.61
</td>
<td style="text-align:center;">
18.89
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
</tr>
<tr>
<td style="text-align:center;">
DR-A
</td>
<td style="text-align:center;">
0.49
</td>
<td style="text-align:center;">
2.45
</td>
<td style="text-align:center;">
5.40
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
</tr>
<tr>
<td style="text-align:center;">
THIN
</td>
<td style="text-align:center;">
0.55
</td>
<td style="text-align:center;">
2.19
</td>
<td style="text-align:center;">
6.78
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
</tr>
<tr>
<td style="text-align:center;">
Acerv 1 (A-AC)
</td>
<td style="text-align:center;">
0.59
</td>
<td style="text-align:center;">
2.00
</td>
<td style="text-align:center;">
7.89
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
</tr>
<tr>
<td style="text-align:center;">
ELK
</td>
<td style="text-align:center;">
0.50
</td>
<td style="text-align:center;">
1.74
</td>
<td style="text-align:center;">
5.36
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
</tr>
<tr>
<td style="text-align:center;">
G1
</td>
<td style="text-align:center;">
0.49
</td>
<td style="text-align:center;">
1.66
</td>
<td style="text-align:center;">
5.27
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
</tr>
<tr>
<td style="text-align:center;">
Struggle Bus
</td>
<td style="text-align:center;">
0.52
</td>
<td style="text-align:center;">
1.66
</td>
<td style="text-align:center;">
9.27
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
</tr>
<tr>
<td style="text-align:center;">
Acerv 3 (C-AC)
</td>
<td style="text-align:center;">
0.55
</td>
<td style="text-align:center;">
1.63
</td>
<td style="text-align:center;">
7.82
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
</tr>
<tr>
<td style="text-align:center;">
Acerv 2 (B-AC)
</td>
<td style="text-align:center;">
0.54
</td>
<td style="text-align:center;">
1.61
</td>
<td style="text-align:center;">
5.26
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
</tr>
<tr>
<td style="text-align:center;">
Site 406
</td>
<td style="text-align:center;">
0.52
</td>
<td style="text-align:center;">
1.61
</td>
<td style="text-align:center;">
8.05
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
</tr>
<tr>
<td style="text-align:center;">
G16
</td>
<td style="text-align:center;">
0.55
</td>
<td style="text-align:center;">
1.58
</td>
<td style="text-align:center;">
6.75
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
</tr>
<tr>
<td style="text-align:center;">
TT (Thicket 3)
</td>
<td style="text-align:center;">
0.48
</td>
<td style="text-align:center;">
1.53
</td>
<td style="text-align:center;">
3.25
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
</tr>
<tr>
<td style="text-align:center;">
FM12
</td>
<td style="text-align:center;">
0.38
</td>
<td style="text-align:center;">
1.50
</td>
<td style="text-align:center;">
1.33
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
</tr>
<tr>
<td style="text-align:center;">
Acerv 5 (E-AC)
</td>
<td style="text-align:center;">
0.46
</td>
<td style="text-align:center;">
1.46
</td>
<td style="text-align:center;">
7.24
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
</tr>
<tr>
<td style="text-align:center;">
G17
</td>
<td style="text-align:center;">
0.54
</td>
<td style="text-align:center;">
1.43
</td>
<td style="text-align:center;">
6.39
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
</tr>
<tr>
<td style="text-align:center;">
ML4
</td>
<td style="text-align:center;">
0.42
</td>
<td style="text-align:center;">
1.38
</td>
<td style="text-align:center;">
3.82
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
</tr>
<tr>
<td style="text-align:center;">
U24
</td>
<td style="text-align:center;">
0.42
</td>
<td style="text-align:center;">
1.33
</td>
<td style="text-align:center;">
3.84
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
</tr>
<tr>
<td style="text-align:center;">
Steph’s
</td>
<td style="text-align:center;">
0.52
</td>
<td style="text-align:center;">
1.33
</td>
<td style="text-align:center;">
10.34
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
</tr>
<tr>
<td style="text-align:center;">
Trans 2
</td>
<td style="text-align:center;">
0.52
</td>
<td style="text-align:center;">
1.27
</td>
<td style="text-align:center;">
7.51
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
</tr>
<tr>
<td style="text-align:center;">
THICK
</td>
<td style="text-align:center;">
0.38
</td>
<td style="text-align:center;">
1.27
</td>
<td style="text-align:center;">
2.87
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
</tr>
<tr>
<td style="text-align:center;">
Grounding
</td>
<td style="text-align:center;">
0.45
</td>
<td style="text-align:center;">
1.26
</td>
<td style="text-align:center;">
5.07
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
</tr>
<tr>
<td style="text-align:center;">
G11
</td>
<td style="text-align:center;">
0.42
</td>
<td style="text-align:center;">
1.26
</td>
<td style="text-align:center;">
3.78
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
</tr>
<tr>
<td style="text-align:center;">
Dom’s Reef
</td>
<td style="text-align:center;">
0.57
</td>
<td style="text-align:center;">
1.25
</td>
<td style="text-align:center;">
9.31
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
</tr>
<tr>
<td style="text-align:center;">
G6
</td>
<td style="text-align:center;">
0.39
</td>
<td style="text-align:center;">
1.15
</td>
<td style="text-align:center;">
3.82
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
</tr>
<tr>
<td style="text-align:center;">
Cooper’s
</td>
<td style="text-align:center;">
0.45
</td>
<td style="text-align:center;">
1.12
</td>
<td style="text-align:center;">
4.53
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
</tr>
<tr>
<td style="text-align:center;">
Inshore
</td>
<td style="text-align:center;">
0.40
</td>
<td style="text-align:center;">
1.09
</td>
<td style="text-align:center;">
4.08
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
</tr>
<tr>
<td style="text-align:center;">
FM5
</td>
<td style="text-align:center;">
0.26
</td>
<td style="text-align:center;">
1.08
</td>
<td style="text-align:center;">
3.10
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
</tr>
<tr>
<td style="text-align:center;">
Trav’s Reef
</td>
<td style="text-align:center;">
0.54
</td>
<td style="text-align:center;">
1.05
</td>
<td style="text-align:center;">
7.62
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
</tr>
<tr>
<td style="text-align:center;">
FM7
</td>
<td style="text-align:center;">
0.25
</td>
<td style="text-align:center;">
1.05
</td>
<td style="text-align:center;">
1.97
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
</tr>
<tr>
<td style="text-align:center;">
Britt’s Reef
</td>
<td style="text-align:center;">
0.47
</td>
<td style="text-align:center;">
1.01
</td>
<td style="text-align:center;">
9.59
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
</tr>
<tr>
<td style="text-align:center;">
FM18
</td>
<td style="text-align:center;">
0.30
</td>
<td style="text-align:center;">
0.91
</td>
<td style="text-align:center;">
2.08
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
</tr>
<tr>
<td style="text-align:center;">
FM13
</td>
<td style="text-align:center;">
0.25
</td>
<td style="text-align:center;">
0.90
</td>
<td style="text-align:center;">
1.78
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
</tr>
<tr>
<td style="text-align:center;">
FM1
</td>
<td style="text-align:center;">
0.24
</td>
<td style="text-align:center;">
0.90
</td>
<td style="text-align:center;">
4.37
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
</tr>
<tr>
<td style="text-align:center;">
FM10
</td>
<td style="text-align:center;">
0.39
</td>
<td style="text-align:center;">
0.89
</td>
<td style="text-align:center;">
2.48
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
</tr>
<tr>
<td style="text-align:center;">
Almost Done
</td>
<td style="text-align:center;">
0.41
</td>
<td style="text-align:center;">
0.87
</td>
<td style="text-align:center;">
6.22
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
</tr>
<tr>
<td style="text-align:center;">
Ford’s Reef
</td>
<td style="text-align:center;">
0.52
</td>
<td style="text-align:center;">
0.86
</td>
<td style="text-align:center;">
10.78
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
</tr>
<tr>
<td style="text-align:center;">
G15
</td>
<td style="text-align:center;">
0.47
</td>
<td style="text-align:center;">
0.86
</td>
<td style="text-align:center;">
5.03
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
</tr>
<tr>
<td style="text-align:center;">
G2
</td>
<td style="text-align:center;">
0.42
</td>
<td style="text-align:center;">
0.85
</td>
<td style="text-align:center;">
4.38
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
</tr>
<tr>
<td style="text-align:center;">
Acerv 4 (D-AC)
</td>
<td style="text-align:center;">
0.54
</td>
<td style="text-align:center;">
0.84
</td>
<td style="text-align:center;">
7.05
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
</tr>
<tr>
<td style="text-align:center;">
MUTANT182
</td>
<td style="text-align:center;">
0.42
</td>
<td style="text-align:center;">
0.83
</td>
<td style="text-align:center;">
3.83
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
</tr>
<tr>
<td style="text-align:center;">
Alina-B
</td>
<td style="text-align:center;">
0.53
</td>
<td style="text-align:center;">
0.82
</td>
<td style="text-align:center;">
6.81
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
</tr>
<tr>
<td style="text-align:center;">
Alina-A
</td>
<td style="text-align:center;">
0.59
</td>
<td style="text-align:center;">
0.70
</td>
<td style="text-align:center;">
7.81
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
</tr>
<tr>
<td style="text-align:center;">
Big Bertha
</td>
<td style="text-align:center;">
0.45
</td>
<td style="text-align:center;">
0.70
</td>
<td style="text-align:center;">
5.20
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
</tr>
<tr>
<td style="text-align:center;">
Fowey
</td>
<td style="text-align:center;">
0.47
</td>
<td style="text-align:center;">
0.60
</td>
<td style="text-align:center;">
6.29
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
</tr>
<tr>
<td style="text-align:center;">
Navassa
</td>
<td style="text-align:center;">
0.33
</td>
<td style="text-align:center;">
0.59
</td>
<td style="text-align:center;">
2.34
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
</tr>
<tr>
<td style="text-align:center;">
B/B
</td>
<td style="text-align:center;">
0.38
</td>
<td style="text-align:center;">
0.58
</td>
<td style="text-align:center;">
2.94
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
</tr>
<tr>
<td style="text-align:center;">
Trans 1
</td>
<td style="text-align:center;">
0.38
</td>
<td style="text-align:center;">
0.56
</td>
<td style="text-align:center;">
4.82
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
</tr>
<tr>
<td style="text-align:center;">
FM9
</td>
<td style="text-align:center;">
0.35
</td>
<td style="text-align:center;">
0.54
</td>
<td style="text-align:center;">
2.27
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
</tr>
<tr>
<td style="text-align:center;">
G18
</td>
<td style="text-align:center;">
0.24
</td>
<td style="text-align:center;">
0.51
</td>
<td style="text-align:center;">
1.64
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
</tr>
<tr>
<td style="text-align:center;">
North Midchannel-A
</td>
<td style="text-align:center;">
0.68
</td>
<td style="text-align:center;">
0.49
</td>
<td style="text-align:center;">
9.07
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
</tr>
<tr>
<td style="text-align:center;">
W/Y
</td>
<td style="text-align:center;">
0.21
</td>
<td style="text-align:center;">
0.40
</td>
<td style="text-align:center;">
2.47
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
</tr>
<tr>
<td style="text-align:center;">
W/G
</td>
<td style="text-align:center;">
0.31
</td>
<td style="text-align:center;">
0.34
</td>
<td style="text-align:center;">
7.10
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
</tr>
<tr>
<td style="text-align:center;">
W/B
</td>
<td style="text-align:center;">
0.29
</td>
<td style="text-align:center;">
0.30
</td>
<td style="text-align:center;">
3.51
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
</tr>
<tr>
<td style="text-align:center;">
Sunny Isles-A
</td>
<td style="text-align:center;">
0.90
</td>
<td style="text-align:center;">
4.50
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
</tr>
<tr>
<td style="text-align:center;">
Stag-B
</td>
<td style="text-align:center;">
0.86
</td>
<td style="text-align:center;">
4.05
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
</tr>
<tr>
<td style="text-align:center;">
MB-C
</td>
<td style="text-align:center;">
0.86
</td>
<td style="text-align:center;">
3.90
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
</tr>
<tr>
<td style="text-align:center;">
MB-A
</td>
<td style="text-align:center;">
0.85
</td>
<td style="text-align:center;">
3.83
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
</tr>
<tr>
<td style="text-align:center;">
BC-8A
</td>
<td style="text-align:center;">
0.83
</td>
<td style="text-align:center;">
3.79
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
</tr>
<tr>
<td style="text-align:center;">
Cheetos-C
</td>
<td style="text-align:center;">
0.83
</td>
<td style="text-align:center;">
3.71
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
</tr>
<tr>
<td style="text-align:center;">
MB-B
</td>
<td style="text-align:center;">
0.78
</td>
<td style="text-align:center;">
3.39
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
</tr>
<tr>
<td style="text-align:center;">
Sunny Isles-C
</td>
<td style="text-align:center;">
0.78
</td>
<td style="text-align:center;">
3.38
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
</tr>
<tr>
<td style="text-align:center;">
Stag-A
</td>
<td style="text-align:center;">
0.78
</td>
<td style="text-align:center;">
3.31
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
</tr>
<tr>
<td style="text-align:center;">
BC-8B
</td>
<td style="text-align:center;">
0.79
</td>
<td style="text-align:center;">
3.30
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
</tr>
<tr>
<td style="text-align:center;">
Cheetos-D
</td>
<td style="text-align:center;">
0.74
</td>
<td style="text-align:center;">
3.15
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
</tr>
<tr>
<td style="text-align:center;">
BC-11
</td>
<td style="text-align:center;">
0.73
</td>
<td style="text-align:center;">
3.01
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
</tr>
<tr>
<td style="text-align:center;">
Tuna Jelly-B
</td>
<td style="text-align:center;">
0.79
</td>
<td style="text-align:center;">
2.95
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
</tr>
<tr>
<td style="text-align:center;">
MB-D
</td>
<td style="text-align:center;">
0.73
</td>
<td style="text-align:center;">
2.88
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
</tr>
<tr>
<td style="text-align:center;">
Sunny Isles-B
</td>
<td style="text-align:center;">
0.71
</td>
<td style="text-align:center;">
2.82
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
</tr>
<tr>
<td style="text-align:center;">
Sunny Isles-D
</td>
<td style="text-align:center;">
0.68
</td>
<td style="text-align:center;">
2.73
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
</tr>
<tr>
<td style="text-align:center;">
FM17
</td>
<td style="text-align:center;">
0.65
</td>
<td style="text-align:center;">
2.50
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
</tr>
<tr>
<td style="text-align:center;">
Tuna Jelly-A
</td>
<td style="text-align:center;">
0.71
</td>
<td style="text-align:center;">
2.46
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
</tr>
<tr>
<td style="text-align:center;">
Yung’s-B
</td>
<td style="text-align:center;">
0.66
</td>
<td style="text-align:center;">
2.45
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
</tr>
<tr>
<td style="text-align:center;">
Kelsey-1
</td>
<td style="text-align:center;">
0.63
</td>
<td style="text-align:center;">
2.38
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
</tr>
<tr>
<td style="text-align:center;">
Yung’s-A
</td>
<td style="text-align:center;">
0.62
</td>
<td style="text-align:center;">
2.36
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
</tr>
<tr>
<td style="text-align:center;">
Kelsey-2
</td>
<td style="text-align:center;">
0.63
</td>
<td style="text-align:center;">
2.33
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
</tr>
<tr>
<td style="text-align:center;">
BC-1
</td>
<td style="text-align:center;">
0.61
</td>
<td style="text-align:center;">
2.26
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
</tr>
<tr>
<td style="text-align:center;">
Cheetos-A
</td>
<td style="text-align:center;">
0.61
</td>
<td style="text-align:center;">
2.25
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
</tr>
<tr>
<td style="text-align:center;">
ML48
</td>
<td style="text-align:center;">
0.63
</td>
<td style="text-align:center;">
2.24
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
</tr>
<tr>
<td style="text-align:center;">
Site 211
</td>
<td style="text-align:center;">
0.56
</td>
<td style="text-align:center;">
1.64
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
</tr>
<tr>
<td style="text-align:center;">
FM15
</td>
<td style="text-align:center;">
0.26
</td>
<td style="text-align:center;">
1.62
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
</tr>
<tr>
<td style="text-align:center;">
MB
</td>
<td style="text-align:center;">
0.52
</td>
<td style="text-align:center;">
1.61
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
</tr>
<tr>
<td style="text-align:center;">
Govt Cut
</td>
<td style="text-align:center;">
0.55
</td>
<td style="text-align:center;">
1.58
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
</tr>
<tr>
<td style="text-align:center;">
Cheetos-B
</td>
<td style="text-align:center;">
0.42
</td>
<td style="text-align:center;">
1.37
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
</tr>
<tr>
<td style="text-align:center;">
ML14
</td>
<td style="text-align:center;">
0.50
</td>
<td style="text-align:center;">
1.35
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
</tr>
<tr>
<td style="text-align:center;">
FM16
</td>
<td style="text-align:center;">
0.32
</td>
<td style="text-align:center;">
1.34
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
</tr>
<tr>
<td style="text-align:center;">
Jons
</td>
<td style="text-align:center;">
0.45
</td>
<td style="text-align:center;">
1.26
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
</tr>
<tr>
<td style="text-align:center;">
FM3
</td>
<td style="text-align:center;">
0.22
</td>
<td style="text-align:center;">
0.80
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
</tr>
<tr>
<td style="text-align:center;">
FM11
</td>
<td style="text-align:center;">
0.22
</td>
<td style="text-align:center;">
0.80
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
</tr>
<tr>
<td style="text-align:center;">
FM19
</td>
<td style="text-align:center;">
0.24
</td>
<td style="text-align:center;">
0.47
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
</tr>
<tr>
<td style="text-align:center;">
ML38
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
3.66
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
43.80
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
</tr>
<tr>
<td style="text-align:center;">
ML43
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
2.59
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
29.97
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
</tr>
<tr>
<td style="text-align:center;">
ML11
</td>
<td style="text-align:center;">
0.25
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
1.01
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
</tr>
<tr>
<td style="text-align:center;">
M10
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
34.88
</td>
<td style="text-align:center;">
2.23
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
</tr>
<tr>
<td style="text-align:center;">
B8
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
22.40
</td>
<td style="text-align:center;">
1.32
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
</tr>
<tr>
<td style="text-align:center;">
M1
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
10.38
</td>
<td style="text-align:center;">
0.58
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
<td style="text-align:center;">
\-
</td>
</tr>
</tbody>
</table>

## Standardizing Scores

Because each of these metrics describe a different component of coral
growth and are measured on different scales, they cannot be directly
aggregated. Instead, we must first calculate standardized scores for
each metric prior to aligning disparate measurements. I chose to
standardize by calculating z-scores where the difference of each value
and the column mean is divided by the column’s standard deviation. Thus,
the column mean is now 0 and the standard deviation is 1. Each resulting
value indicates the amount of standard deviations about the mean for
that metric.

I then group together all linear extension metrics to calculate a
genotype’s average standard deviation about the mean and impute this
value for all missing linear extension metrics. I do the same for
calcification metrics. If no calcification or no linear extension
metrics exist for a particular genotype, then 0’s are imputed for all
calcification or no linear extension metrics, which signifies average
performance.

The table below shows the resulting standardized data with scores in
black indicating calculated z-scores, scores in blue indicating imputed
z-scores based on the other linear extension or calcification scores,
and scores in red indicating imputed scores of 0 if no linear extension
or calcification data was available.

``` r
std <- overlap %>%
  #scale existing values
  mutate(across(-1,~ as.numeric(scale(.))))

std <- std %>%
  #calculate the scaled col means
  # bind_rows(std %>%
  #             summarise(across(-1,
  #                              ~mean(.x, na.rm=T)))) %>%
  rowwise() %>%
  #calculate the LE and G Mean for each genotype
  mutate(LE.mean = mean(c_across(`specific growth rate`:`interstitial space SGR`),na.rm=T),
         G.mean = mean(c_across(`daily calcification`:`light calcification`),na.rm=T),
         #replace NaN with NA
         across(-1, ~replace(., is.nan(.), NA)),
  #impute LE values
  across(`specific growth rate`:`interstitial space SGR`, ~ coalesce(.,LE.mean)),
  #impute G Values
    across(`daily calcification`:`light calcification`,
           ~ coalesce(.,G.mean)),
  #if LE.mean | G.mean == NA, replace with the column mean i.e. 0
   across(-1, ~ case_when(is.na(.)~0,
                          TRUE ~ .))
  )

std %>%
  #color the cells based on their value
  mutate(across(-1,~round(.x,2)),
    across(-1,
          ~cell_spec(.x,
                              #IF value == column mean (0) THEN color red
                     color = case_when(.x == 0 ~ "red",
                              #IF value == LE.mean | G.mean THEN color blue
                                       .x == LE.mean | .x ==G.mean ~ "#1E90FF",
                                       TRUE ~ "black")))) %>%
  select(-c(LE.mean,G.mean)) %>%
kbl(align = 'c',
    digits = 2,
    escape = F) %>%
  kable_classic() %>%
  row_spec(0, bold = T)  %>%
  column_spec(11, extra_css = "border-left: 1px solid #673ab7;")
```

<table class=" lightable-classic" style="font-family: &quot;Arial Narrow&quot;, &quot;Source Sans Pro&quot;, sans-serif; margin-left: auto; margin-right: auto;">
<thead>
<tr>
<th style="text-align:center;font-weight: bold;">
genotype
</th>
<th style="text-align:center;font-weight: bold;">
specific growth rate
</th>
<th style="text-align:center;font-weight: bold;">
6-month linear growth
</th>
<th style="text-align:center;font-weight: bold;">
annual linear growth
</th>
<th style="text-align:center;font-weight: bold;">
colony volumetric SGR
</th>
<th style="text-align:center;font-weight: bold;">
annual colony volumetric growth
</th>
<th style="text-align:center;font-weight: bold;">
6-month colony volumetric growth
</th>
<th style="text-align:center;font-weight: bold;">
6-month interstitial space growth
</th>
<th style="text-align:center;font-weight: bold;">
annual interstitial space growth
</th>
<th style="text-align:center;font-weight: bold;">
interstitial space SGR
</th>
<th style="text-align:center;font-weight: bold;">
daily calcification
</th>
<th style="text-align:center;font-weight: bold;">
mass normalized daily calcification
</th>
<th style="text-align:center;font-weight: bold;">
SA normalized daily calcification
</th>
<th style="text-align:center;font-weight: bold;">
dark calcification
</th>
<th style="text-align:center;font-weight: bold;">
light calcification
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:center;">
ML41
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.73</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.49</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.57</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.39</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.54</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.01</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">0.06</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.89</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">0.45</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: black !important;">-0.6</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.68</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.33</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">1.26</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.22</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
ML7
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.95</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.77</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.68</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">0.43</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">0.39</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.26</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">0.53</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">1.51</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">1.41</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: black !important;">-0.39</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.66</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">0.61</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">0.25</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">0.3</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
ML62
</td>
<td style="text-align:center;">
<span style="     color: black !important;">0.24</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">0.17</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.35</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.01</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">0.22</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.35</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">0.99</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">1.33</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">0.92</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: black !important;">-0.8</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.68</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-1.42</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-1.27</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.06</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
ML50
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.06</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.02</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.17</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.7</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">0.04</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.45</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">0.33</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">1.25</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.59</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: black !important;">-0.78</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.67</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">0.65</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">0.86</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-1.11</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
ML31
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.52</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.02</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.46</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-1.53</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.94</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.46</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">0.11</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.94</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-1.1</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: black !important;">-0.63</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.68</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.31</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">1.31</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">0.19</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
ML3
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.53</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.16</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.43</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.6</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.23</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.47</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.39</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.52</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-1.07</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: black !important;">-0.8</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.68</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.63</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">0.28</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-1.33</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
ML44
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.53</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.63</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.43</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">0.07</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">0.12</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.59</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-1.51</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.78</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-1.22</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: #1E90FF !important;">-0.61</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.68</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">0.27</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.28</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">1.41</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
ML1
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.45</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.33</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.6</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.66</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.38</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.59</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-1.81</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.74</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.23</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: black !important;">-0.7</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.7</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">1.51</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.35</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-1.69</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
ML13
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.34</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.51</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.69</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-1.48</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.88</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.69</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">0.37</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.46</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">0.13</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: black !important;">-0.84</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.7</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-1.93</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.28</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">0.25</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
ML36
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.76</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.79</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.64</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.01</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.03</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.36</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">1.33</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">0.24</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">1.3</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
M6
</td>
<td style="text-align:center;">
<span style="     color: black !important;">0.27</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.15</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.82</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">0.48</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">1.78</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">1.7</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.82</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.82</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.82</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: black !important;">-0.75</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.72</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.73</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.73</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.73</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
U41
</td>
<td style="text-align:center;">
<span style="     color: black !important;">1.05</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">3.07</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">1.64</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">0.56</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.18</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.23</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.23</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.23</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.23</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: black !important;">1.68</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">1.57</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.63</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.63</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.63</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
K3
</td>
<td style="text-align:center;">
<span style="     color: black !important;">1.18</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">2.7</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">1.95</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-1.66</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-1.04</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.63</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.63</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.63</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.63</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: black !important;">2.17</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">2.25</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">2.21</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">2.21</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">2.21</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
K2
</td>
<td style="text-align:center;">
<span style="     color: black !important;">0.94</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">2.21</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">2.28</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-1.78</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.99</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.53</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.53</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.53</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.53</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: black !important;">2.34</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">2.24</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">2.29</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">2.29</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">2.29</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
U77
</td>
<td style="text-align:center;">
<span style="     color: black !important;">0.74</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">1.79</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">0.88</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">1.34</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">0.31</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.01</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.01</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.01</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.01</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: black !important;">1.53</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">1.19</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.36</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.36</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.36</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
U44
</td>
<td style="text-align:center;">
<span style="     color: black !important;">0.61</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">1.48</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">1.15</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.47</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.49</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.45</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.45</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.45</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.45</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: black !important;">1.08</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">0.92</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
ML34
</td>
<td style="text-align:center;">
<span style="     color: black !important;">0.35</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">0.2</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.28</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.28</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.28</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.28</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.28</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.28</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.28</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: black !important;">-0.76</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.68</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.73</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.75</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">0.03</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
Marker 9
</td>
<td style="text-align:center;">
<span style="     color: black !important;">0.2</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.19</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">0.6</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">0.45</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.15</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.31</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.15</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.15</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.15</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
U47
</td>
<td style="text-align:center;">
<span style="     color: black !important;">1.66</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">2.37</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">2.82</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">2.28</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">2.28</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">2.28</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">2.28</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">2.28</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">2.28</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: black !important;">1.02</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">1.1</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.06</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.06</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.06</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
U73
</td>
<td style="text-align:center;">
<span style="     color: black !important;">1.74</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">2.3</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">3.13</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">2.39</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">2.39</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">2.39</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">2.39</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">2.39</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">2.39</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: black !important;">1.3</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">0.91</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.11</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.11</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.11</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
U78
</td>
<td style="text-align:center;">
<span style="     color: black !important;">1.55</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">1.87</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">2.41</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.94</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.94</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.94</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.94</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.94</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.94</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: black !important;">1.46</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">0.92</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.19</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.19</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.19</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
K1
</td>
<td style="text-align:center;">
<span style="     color: black !important;">1.56</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">1.72</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">2.16</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.81</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.81</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.81</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.81</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.81</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.81</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: black !important;">0.54</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">0.48</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.51</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.51</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.51</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
K25
</td>
<td style="text-align:center;">
<span style="     color: black !important;">0.63</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">0.96</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">0.85</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.81</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.81</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.81</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.81</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.81</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.81</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: black !important;">0.24</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">0.07</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.16</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.16</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.16</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
ML20
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.51</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.58</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.54</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.54</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.54</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.54</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.54</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.54</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.54</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: black !important;">-0.79</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.71</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">1.12</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.13</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.13</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
ML63
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: black !important;">-0.78</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.67</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">0.56</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-1.9</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">0.66</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
ML47
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: black !important;">-0.78</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.67</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">0.63</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">0.86</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">1.57</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
BC-G
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-1.11</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.96</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.17</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">1.29</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.17</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">0.11</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.17</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.17</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.17</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
Stagreef
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.5</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.65</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.11</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">1.5</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.11</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">0.09</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.11</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.11</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.11</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
Sunny Isles-F
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.75</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.76</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.24</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">0.73</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.24</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.18</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.24</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.24</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.24</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
BC-H
</td>
<td style="text-align:center;">
<span style="     color: black !important;">0.2</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.24</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.09</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">0.12</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.09</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.43</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.09</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.09</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.09</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
ML5
</td>
<td style="text-align:center;">
<span style="     color: black !important;">0.38</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">0.78</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.2</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.32</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.32</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.32</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.32</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.32</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.32</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: #1E90FF !important;">0.09</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.09</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.09</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.09</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.09</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
ML56
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.24</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">0.24</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.7</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.23</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.23</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.23</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.23</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.23</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.23</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: #1E90FF !important;">-0.58</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.58</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.58</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.58</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.58</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
ML54
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.25</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.02</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.56</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.27</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.27</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.27</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.27</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.27</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.27</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: #1E90FF !important;">-0.4</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.4</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.4</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.4</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.4</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
U25
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-1.53</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.39</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-1.12</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">1.23</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.16</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.39</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.39</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.39</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.39</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
FM20
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">2.45</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">2.45</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">2.45</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">1.09</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">3</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">3.26</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">2.45</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">2.45</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">2.45</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
B
</td>
<td style="text-align:center;">
<span style="     color: black !important;">1.51</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">1.46</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">2.97</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.98</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.98</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.98</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.98</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.98</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.98</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
DR-A
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.17</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">0.47</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.22</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.03</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.03</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.03</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.03</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.03</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.03</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
THIN
</td>
<td style="text-align:center;">
<span style="     color: black !important;">0.19</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">0.25</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">0.1</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.18</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.18</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.18</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.18</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.18</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.18</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
Acerv 1 (A-AC)
</td>
<td style="text-align:center;">
<span style="     color: black !important;">0.41</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">0.09</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">0.36</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.29</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.29</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.29</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.29</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.29</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.29</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
ELK
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.12</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.13</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.23</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.16</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.16</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.16</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.16</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.16</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.16</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
G1
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.16</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.2</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.26</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.21</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.21</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.21</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.21</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.21</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.21</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
Struggle Bus
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.01</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.2</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">0.69</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.16</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.16</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.16</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.16</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.16</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.16</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
Acerv 3 (C-AC)
</td>
<td style="text-align:center;">
<span style="     color: black !important;">0.18</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.22</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">0.35</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.1</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.1</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.1</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.1</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.1</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.1</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
Acerv 2 (B-AC)
</td>
<td style="text-align:center;">
<span style="     color: black !important;">0.08</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.24</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.26</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.14</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.14</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.14</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.14</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.14</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.14</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
Site 406
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.03</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.24</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">0.4</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.04</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.04</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.04</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.04</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.04</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.04</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
G16
</td>
<td style="text-align:center;">
<span style="     color: black !important;">0.17</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.26</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">0.09</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
TT (Thicket 3)
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.25</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.3</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.73</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.43</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.43</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.43</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.43</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.43</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.43</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
FM12
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.83</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.33</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-1.19</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.78</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.78</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.78</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.78</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.78</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.78</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
Acerv 5 (E-AC)
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.38</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.37</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">0.21</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.18</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.18</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.18</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.18</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.18</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.18</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
G17
</td>
<td style="text-align:center;">
<span style="     color: black !important;">0.1</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.39</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">0.01</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.1</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.1</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.1</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.1</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.1</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.1</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
ML4
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.62</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.44</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.6</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.55</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.55</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.55</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.55</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.55</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.55</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
U24
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.62</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.47</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.59</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.56</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.56</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.56</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.56</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.56</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.56</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
Steph’s
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.47</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">0.94</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.16</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.16</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.16</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.16</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.16</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.16</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
Trans 2
</td>
<td style="text-align:center;">
<span style="     color: black !important;">0.01</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.53</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">0.28</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.08</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.08</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.08</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.08</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.08</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.08</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
THICK
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.83</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.53</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.82</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.73</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.73</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.73</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.73</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.73</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.73</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
Grounding
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.43</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.53</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.3</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.42</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.42</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.42</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.42</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.42</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.42</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
G11
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.63</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.54</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.61</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.59</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.59</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.59</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.59</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.59</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.59</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
Dom’s Reef
</td>
<td style="text-align:center;">
<span style="     color: black !important;">0.3</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.54</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">0.7</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.15</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.15</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.15</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.15</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.15</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.15</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
G6
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.76</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.63</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.6</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.66</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.66</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.66</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.66</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.66</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.66</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
Cooper’s
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.42</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.66</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.43</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.5</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.5</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.5</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.5</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.5</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.5</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
Inshore
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.7</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.68</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.54</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.64</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.64</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.64</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.64</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.64</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.64</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
FM5
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-1.57</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.69</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.77</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-1.01</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-1.01</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-1.01</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-1.01</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-1.01</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-1.01</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
Trav’s Reef
</td>
<td style="text-align:center;">
<span style="     color: black !important;">0.1</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.71</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">0.3</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.1</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.1</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.1</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.1</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.1</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.1</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
FM7
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-1.6</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.71</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-1.04</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-1.12</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-1.12</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-1.12</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-1.12</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-1.12</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-1.12</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
Britt’s Reef
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.32</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.75</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">0.77</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.1</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.1</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.1</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.1</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.1</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.1</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
FM18
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-1.33</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.83</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-1.01</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-1.06</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-1.06</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-1.06</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-1.06</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-1.06</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-1.06</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
FM13
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-1.63</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.84</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-1.08</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-1.18</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-1.18</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-1.18</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-1.18</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-1.18</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-1.18</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
FM1
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-1.65</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.84</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.47</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.99</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.99</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.99</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.99</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.99</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.99</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
FM10
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.76</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.85</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.91</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.84</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.84</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.84</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.84</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.84</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.84</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
Almost Done
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.68</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.86</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.03</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.52</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.52</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.52</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.52</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.52</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.52</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
Ford’s Reef
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.03</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.87</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">1.05</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.05</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.05</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.05</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.05</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.05</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.05</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
G15
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.3</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.87</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.31</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.49</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.49</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.49</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.49</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.49</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.49</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
G2
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.58</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.88</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.47</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.64</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.64</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.64</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.64</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.64</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.64</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
Acerv 4 (D-AC)
</td>
<td style="text-align:center;">
<span style="     color: black !important;">0.11</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.89</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">0.17</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.2</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.2</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.2</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.2</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.2</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.2</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
MUTANT182
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.6</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.9</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.6</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.7</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.7</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.7</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.7</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.7</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.7</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
Alina-B
</td>
<td style="text-align:center;">
<span style="     color: black !important;">0.03</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.91</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">0.11</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.26</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.26</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.26</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.26</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.26</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.26</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
Alina-A
</td>
<td style="text-align:center;">
<span style="     color: black !important;">0.38</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-1.01</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">0.35</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.1</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.1</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.1</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.1</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.1</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.1</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
Big Bertha
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.43</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-1.01</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.27</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.57</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.57</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.57</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.57</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.57</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.57</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
Fowey
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.31</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-1.1</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.01</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.47</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.47</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.47</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.47</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.47</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.47</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
Navassa
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-1.16</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-1.1</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.95</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-1.07</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-1.07</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-1.07</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-1.07</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-1.07</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-1.07</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
B/B
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.85</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-1.11</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.81</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.92</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.92</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.92</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.92</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.92</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.92</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
Trans 1
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.85</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-1.13</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.36</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.78</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.78</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.78</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.78</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.78</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.78</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
FM9
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-1.04</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-1.14</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.97</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-1.05</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-1.05</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-1.05</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-1.05</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-1.05</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-1.05</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
G18
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-1.65</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-1.17</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-1.12</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-1.31</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-1.31</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-1.31</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-1.31</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-1.31</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-1.31</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
North Midchannel-A
</td>
<td style="text-align:center;">
<span style="     color: black !important;">0.92</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-1.19</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">0.64</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.13</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.13</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.13</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.13</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.13</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.13</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
W/Y
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-1.85</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-1.27</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.92</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-1.34</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-1.34</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-1.34</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-1.34</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-1.34</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-1.34</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
W/G
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-1.26</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-1.31</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">0.18</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.8</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.8</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.8</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.8</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.8</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.8</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
W/B
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-1.4</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-1.35</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.67</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-1.14</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-1.14</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-1.14</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-1.14</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-1.14</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-1.14</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
Sunny Isles-A
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">2.2</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">2.2</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">2.2</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">2.2</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">2.2</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">2.2</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">2.2</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">2.2</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">2.2</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
Stag-B
</td>
<td style="text-align:center;">
<span style="     color: black !important;">1.97</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">1.83</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.9</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.9</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.9</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.9</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.9</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.9</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.9</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
MB-C
</td>
<td style="text-align:center;">
<span style="     color: black !important;">1.97</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">1.7</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.84</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.84</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.84</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.84</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.84</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.84</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.84</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
MB-A
</td>
<td style="text-align:center;">
<span style="     color: black !important;">1.91</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">1.64</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.78</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.78</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.78</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.78</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.78</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.78</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.78</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
BC-8A
</td>
<td style="text-align:center;">
<span style="     color: black !important;">1.81</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">1.61</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.71</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.71</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.71</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.71</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.71</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.71</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.71</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
Cheetos-C
</td>
<td style="text-align:center;">
<span style="     color: black !important;">1.81</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">1.54</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.68</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.68</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.68</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.68</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.68</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.68</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.68</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
MB-B
</td>
<td style="text-align:center;">
<span style="     color: black !important;">1.5</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">1.26</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.38</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.38</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.38</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.38</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.38</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.38</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.38</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
Sunny Isles-C
</td>
<td style="text-align:center;">
<span style="     color: black !important;">1.5</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">1.26</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.38</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.38</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.38</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.38</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.38</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.38</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.38</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
Stag-A
</td>
<td style="text-align:center;">
<span style="     color: black !important;">1.49</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">1.2</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.34</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.34</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.34</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.34</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.34</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.34</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.34</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
BC-8B
</td>
<td style="text-align:center;">
<span style="     color: black !important;">1.55</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">1.19</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.37</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.37</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.37</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.37</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.37</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.37</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.37</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
Cheetos-D
</td>
<td style="text-align:center;">
<span style="     color: black !important;">1.26</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">1.07</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.16</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.16</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.16</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.16</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.16</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.16</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.16</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
BC-11
</td>
<td style="text-align:center;">
<span style="     color: black !important;">1.24</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">0.95</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.09</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.09</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.09</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.09</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.09</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.09</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.09</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
Tuna Jelly-B
</td>
<td style="text-align:center;">
<span style="     color: black !important;">1.56</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">0.9</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.23</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.23</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.23</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.23</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.23</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.23</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.23</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
MB-D
</td>
<td style="text-align:center;">
<span style="     color: black !important;">1.22</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">0.83</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.03</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.03</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.03</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.03</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.03</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.03</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">1.03</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
Sunny Isles-B
</td>
<td style="text-align:center;">
<span style="     color: black !important;">1.13</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">0.79</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.96</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.96</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.96</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.96</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.96</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.96</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.96</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
Sunny Isles-D
</td>
<td style="text-align:center;">
<span style="     color: black !important;">0.93</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">0.71</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.82</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.82</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.82</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.82</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.82</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.82</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.82</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
FM17
</td>
<td style="text-align:center;">
<span style="     color: black !important;">0.73</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">0.52</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.62</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.62</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.62</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.62</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.62</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.62</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.62</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
Tuna Jelly-A
</td>
<td style="text-align:center;">
<span style="     color: black !important;">1.08</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">0.48</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.78</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.78</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.78</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.78</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.78</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.78</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.78</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
Yung’s-B
</td>
<td style="text-align:center;">
<span style="     color: black !important;">0.8</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">0.47</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.63</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.63</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.63</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.63</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.63</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.63</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.63</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
Kelsey-1
</td>
<td style="text-align:center;">
<span style="     color: black !important;">0.61</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">0.41</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.51</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.51</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.51</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.51</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.51</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.51</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.51</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
Yung’s-A
</td>
<td style="text-align:center;">
<span style="     color: black !important;">0.56</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">0.39</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.48</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.48</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.48</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.48</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.48</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.48</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.48</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
Kelsey-2
</td>
<td style="text-align:center;">
<span style="     color: black !important;">0.62</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">0.37</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.49</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.49</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.49</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.49</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.49</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.49</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.49</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
BC-1
</td>
<td style="text-align:center;">
<span style="     color: black !important;">0.52</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">0.31</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.41</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.41</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.41</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.41</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.41</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.41</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.41</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
Cheetos-A
</td>
<td style="text-align:center;">
<span style="     color: black !important;">0.49</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">0.3</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.4</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.4</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.4</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.4</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.4</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.4</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.4</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
ML48
</td>
<td style="text-align:center;">
<span style="     color: black !important;">0.64</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">0.29</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.47</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.47</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.47</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.47</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.47</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.47</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.47</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
Site 211
</td>
<td style="text-align:center;">
<span style="     color: black !important;">0.24</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.21</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.02</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.02</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.02</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.02</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.02</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.02</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">0.02</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
FM15
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-1.56</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.23</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.9</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.9</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.9</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.9</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.9</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.9</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.9</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
MB
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.04</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.24</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.14</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.14</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.14</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.14</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.14</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.14</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.14</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
Govt Cut
</td>
<td style="text-align:center;">
<span style="     color: black !important;">0.17</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.27</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.05</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.05</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.05</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.05</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.05</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.05</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.05</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
Cheetos-B
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.59</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.44</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.52</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.52</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.52</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.52</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.52</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.52</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.52</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
ML14
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.14</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.46</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.3</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.3</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.3</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.3</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.3</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.3</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.3</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
FM16
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-1.2</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.47</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.84</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.84</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.84</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.84</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.84</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.84</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.84</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
Jons
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.43</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.53</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.48</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.48</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.48</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.48</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.48</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.48</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.48</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
FM3
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-1.77</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.92</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-1.35</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-1.35</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-1.35</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-1.35</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-1.35</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-1.35</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-1.35</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
FM11
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-1.76</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.93</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-1.35</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-1.35</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-1.35</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-1.35</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-1.35</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-1.35</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-1.35</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
FM19
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-1.64</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-1.2</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-1.42</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-1.42</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-1.42</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-1.42</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-1.42</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-1.42</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-1.42</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
ML38
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.64</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.64</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.64</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.64</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.64</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.64</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.64</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.64</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.64</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: #1E90FF !important;">-0.24</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.24</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.24</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.24</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.24</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
ML43
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.89</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.89</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.89</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.89</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.89</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.89</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.89</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.89</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.89</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: #1E90FF !important;">-0.47</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.47</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.47</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.47</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.47</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
ML11
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-1.6</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-1.43</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-1.26</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-1.43</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-1.43</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-1.43</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-1.43</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-1.43</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-1.43</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
M10
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: black !important;">-0.39</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.67</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.53</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.53</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.53</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
B8
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: black !important;">-0.59</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.7</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.65</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.65</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.65</span>
</td>
</tr>
<tr>
<td style="text-align:center;">
M1
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;">
<span style="     color: red !important;">0</span>
</td>
<td style="text-align:center;border-left: 1px solid #673ab7;">
<span style="     color: black !important;">-0.79</span>
</td>
<td style="text-align:center;">
<span style="     color: black !important;">-0.73</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.76</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.76</span>
</td>
<td style="text-align:center;">
<span style="     color: #1E90FF !important;">-0.76</span>
</td>
</tr>
</tbody>
</table>

-   Note: Some genotypes (ML38, ML43, Sunny Isles-A) may have an entire
    row highlighted in blue suggesting all data is imputed. However,
    this is an artifact of my conditional formatting and not accurate.
    One or two of the actual, calculated z-scores is the same as the row
    mean and is being incorrectly colored. Decided not to spend
    unnecessary time figuring this out and made this quick note instead.

# Composite Growth Index

Now that we have standardized scores for 14 different metrics, we can
compare and align metrics into a single, composite index to understand
relative genotype performance.

## Methods

First, I group the growth metrics into their two large determinants of
linear extension and calcification and calculate the mean standardized
score for each of these determinants of growth.

Then, I individually weight the linear extension and calcification
scores. The derivation of the two distinct weights is explained below.
The two weights add to 1.

Finally, the two weighted values are added together for a finalized
score. For genotypes that only have linear extension data or
calcification data, the resulting score is just the weighed linear
extension or calcification score. Since average performance has a score
of 0 and the two determinants of growth are independently weighed with
the sum of the weights equaling 1, the finalized score should best
encapsulate true growth rates and permit ranking of relative genotype
performance.

This process assumes there is no genotype-effect on density, which is
supported by Kuffner et al. (2017) who demonstrated for this species a
genotype-specific calcification rate but a plastic density based on its
nursery grow out structure.

### Derivation of Weights

Weights were determined by characteristic growth of the species, a
common practice in calicification budgets of coral reefs. Briefly,
calcification is the product of densification and linear extension, and
is the total metric we are trying to describe. We have metrics that
measure calcification through buoyant weight or total alkalinity anomaly
measurements. We also have various determinations of linear extension as
it is a common metric captured in the field, but this rapid growth is
biased by the quick growing branch tips which is only about 24.6% of the
coral’s volume, with the other 75.4% of the coral growing at a rate 10%
of the branch tips (data aggregated by Perry Reef Budget, see citations
within).

The formula for calculating the gross calcification of a branching *A.
cervicornis* is:
*G* = (*l* × *c*<sub>*a*</sub> × *P* × *ρ*) + ((*l* − *c*<sub>*a*</sub> × *l*) × 0.1 × *P* × *ρ*)
where

1.  *G* = total gross calcification of the two terms
    *g*/*c**m*<sup>2</sup>/*y**r* *or* *g*/*c**m*<sup>2</sup>/*d**a**y*
2.  *l* = the initial length of the coral in cm
3.  *c*<sub>*a*</sub> = proportion of colony fast-growing axial tips
    (0.246)
4.  *P* = relative linear extension of the coral *y**r*<sup> − 1</sup>
    *or* *d**a**y*<sup> − 1</sup> (termed productivity in Lirman et
    al. 2014)
5.  *ρ* = the average density of the coral in *g*/*c**m*<sup>3</sup>

As you can see, the first term is for the fast linear extension of the
branches, and the second term is for the growth of the remaining portion
of the colony, growing at a rate 10% of the branch tips. We can combine
the constant terms and simplify the equation to:

*G* = (0.246 × *Q*) + (0.754 × 0.1 × *Q*)
where Q is the terms *l* × *P* × *ρ* combined. Thus the ratio of linear
extension to gross calcification is:
$$
\\frac{\\text{LE}}{ G} = \\frac{0.246}{0.0754 + 0.246} = \\frac{0.246}{0.3214} = 0.7654
$$

Therefore, by measuring linear extension you are describing only 76.54%
of the colony growth, while if you measure the calcification, you are
describing 100% of the colony’s growth. Our goal is to have these
percentages converted to weights which add to 1 to provide simple
understanding and calculating of weighted arithmetic means.

0.7654*x* + *x* = 1 → 1.7654*x* = 1 → *x* = 1/1.7654 ≈ 0.57

Finally, our weighting for calcification measurements take the weight of
0.57 and linear extension measurements take the weight of 1-0.57 or
0.43.

![image-weighting-breakdown](/notebook/images/compositeGrowth/circleWeights_composite.png)

## Lets Graph It Out

``` r
normalizedStats <- std %>%
    select(-c(LE.mean,G.mean)) %>%
  pivot_longer(-genotype,
               names_to = "metric",
               values_to = "score")

normalizedStats.LE <- normalizedStats %>%
              filter(metric %in% c('6-month linear growth',
                                  'annual linear growth',
                 'specific growth rate', 'colony volumetric SGR',
                 '6-month colony volumetric growth',
                 'annual colony volumetric growth',
                 '6-month interstitial space growth',
                 'annual interstitial space growth',
                 'interstitial space SGR')) %>%
              group_by(genotype) %>%
              summarise(score = mean(score, na.rm=T)*0.43)
normalizedStats.G <- normalizedStats %>%
            filter(!metric %in% c('6-month linear growth',
                                 'annual linear growth',
                 'specific growth rate', 'colony volumetric SGR',
                 '6-month colony volumetric growth',
                 'annual colony volumetric growth',
                 '6-month interstitial space growth',
                 'annual interstitial space growth',
                 'interstitial space SGR')) %>%
              group_by(genotype) %>%
              summarise(score = mean(score, na.rm=T)*0.57)

normalizedStats <- full_join(
  normalizedStats.G,
  normalizedStats.LE,
  by = "genotype") %>%
  mutate(score=score.x + score.y) %>%
  select(genotype,score) %>%
  arrange(desc(score))

normalizedStats %>%
  mutate(rank = row_number(),
         tercile = ntile(desc(score),3)) %>%
  kbl(align = 'c',
    digits = 3) %>%
  kable_classic() %>%
  row_spec(0, bold = T)
```

<table class=" lightable-classic" style="font-family: &quot;Arial Narrow&quot;, &quot;Source Sans Pro&quot;, sans-serif; margin-left: auto; margin-right: auto;">
<thead>
<tr>
<th style="text-align:center;font-weight: bold;">
genotype
</th>
<th style="text-align:center;font-weight: bold;">
score
</th>
<th style="text-align:center;font-weight: bold;">
rank
</th>
<th style="text-align:center;font-weight: bold;">
tercile
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:center;">
U73
</td>
<td style="text-align:center;">
1.658
</td>
<td style="text-align:center;">
1
</td>
<td style="text-align:center;">
1
</td>
</tr>
<tr>
<td style="text-align:center;">
U47
</td>
<td style="text-align:center;">
1.587
</td>
<td style="text-align:center;">
2
</td>
<td style="text-align:center;">
1
</td>
</tr>
<tr>
<td style="text-align:center;">
K2
</td>
<td style="text-align:center;">
1.536
</td>
<td style="text-align:center;">
3
</td>
<td style="text-align:center;">
1
</td>
</tr>
<tr>
<td style="text-align:center;">
K3
</td>
<td style="text-align:center;">
1.530
</td>
<td style="text-align:center;">
4
</td>
<td style="text-align:center;">
1
</td>
</tr>
<tr>
<td style="text-align:center;">
U78
</td>
<td style="text-align:center;">
1.515
</td>
<td style="text-align:center;">
5
</td>
<td style="text-align:center;">
1
</td>
</tr>
<tr>
<td style="text-align:center;">
U41
</td>
<td style="text-align:center;">
1.455
</td>
<td style="text-align:center;">
6
</td>
<td style="text-align:center;">
1
</td>
</tr>
<tr>
<td style="text-align:center;">
U77
</td>
<td style="text-align:center;">
1.210
</td>
<td style="text-align:center;">
7
</td>
<td style="text-align:center;">
1
</td>
</tr>
<tr>
<td style="text-align:center;">
K1
</td>
<td style="text-align:center;">
1.072
</td>
<td style="text-align:center;">
8
</td>
<td style="text-align:center;">
1
</td>
</tr>
<tr>
<td style="text-align:center;">
FM20
</td>
<td style="text-align:center;">
1.054
</td>
<td style="text-align:center;">
9
</td>
<td style="text-align:center;">
1
</td>
</tr>
<tr>
<td style="text-align:center;">
Sunny Isles-A
</td>
<td style="text-align:center;">
0.946
</td>
<td style="text-align:center;">
10
</td>
<td style="text-align:center;">
1
</td>
</tr>
<tr>
<td style="text-align:center;">
B
</td>
<td style="text-align:center;">
0.851
</td>
<td style="text-align:center;">
11
</td>
<td style="text-align:center;">
1
</td>
</tr>
<tr>
<td style="text-align:center;">
Stag-B
</td>
<td style="text-align:center;">
0.817
</td>
<td style="text-align:center;">
12
</td>
<td style="text-align:center;">
1
</td>
</tr>
<tr>
<td style="text-align:center;">
MB-C
</td>
<td style="text-align:center;">
0.790
</td>
<td style="text-align:center;">
13
</td>
<td style="text-align:center;">
1
</td>
</tr>
<tr>
<td style="text-align:center;">
U44
</td>
<td style="text-align:center;">
0.765
</td>
<td style="text-align:center;">
14
</td>
<td style="text-align:center;">
1
</td>
</tr>
<tr>
<td style="text-align:center;">
MB-A
</td>
<td style="text-align:center;">
0.764
</td>
<td style="text-align:center;">
15
</td>
<td style="text-align:center;">
1
</td>
</tr>
<tr>
<td style="text-align:center;">
BC-8A
</td>
<td style="text-align:center;">
0.736
</td>
<td style="text-align:center;">
16
</td>
<td style="text-align:center;">
1
</td>
</tr>
<tr>
<td style="text-align:center;">
Cheetos-C
</td>
<td style="text-align:center;">
0.721
</td>
<td style="text-align:center;">
17
</td>
<td style="text-align:center;">
1
</td>
</tr>
<tr>
<td style="text-align:center;">
MB-B
</td>
<td style="text-align:center;">
0.594
</td>
<td style="text-align:center;">
18
</td>
<td style="text-align:center;">
1
</td>
</tr>
<tr>
<td style="text-align:center;">
Sunny Isles-C
</td>
<td style="text-align:center;">
0.593
</td>
<td style="text-align:center;">
19
</td>
<td style="text-align:center;">
1
</td>
</tr>
<tr>
<td style="text-align:center;">
BC-8B
</td>
<td style="text-align:center;">
0.588
</td>
<td style="text-align:center;">
20
</td>
<td style="text-align:center;">
1
</td>
</tr>
<tr>
<td style="text-align:center;">
Stag-A
</td>
<td style="text-align:center;">
0.578
</td>
<td style="text-align:center;">
21
</td>
<td style="text-align:center;">
1
</td>
</tr>
<tr>
<td style="text-align:center;">
Tuna Jelly-B
</td>
<td style="text-align:center;">
0.528
</td>
<td style="text-align:center;">
22
</td>
<td style="text-align:center;">
1
</td>
</tr>
<tr>
<td style="text-align:center;">
Cheetos-D
</td>
<td style="text-align:center;">
0.499
</td>
<td style="text-align:center;">
23
</td>
<td style="text-align:center;">
1
</td>
</tr>
<tr>
<td style="text-align:center;">
BC-11
</td>
<td style="text-align:center;">
0.471
</td>
<td style="text-align:center;">
24
</td>
<td style="text-align:center;">
1
</td>
</tr>
<tr>
<td style="text-align:center;">
MB-D
</td>
<td style="text-align:center;">
0.442
</td>
<td style="text-align:center;">
25
</td>
<td style="text-align:center;">
1
</td>
</tr>
<tr>
<td style="text-align:center;">
K25
</td>
<td style="text-align:center;">
0.439
</td>
<td style="text-align:center;">
26
</td>
<td style="text-align:center;">
1
</td>
</tr>
<tr>
<td style="text-align:center;">
Sunny Isles-B
</td>
<td style="text-align:center;">
0.411
</td>
<td style="text-align:center;">
27
</td>
<td style="text-align:center;">
1
</td>
</tr>
<tr>
<td style="text-align:center;">
Sunny Isles-D
</td>
<td style="text-align:center;">
0.351
</td>
<td style="text-align:center;">
28
</td>
<td style="text-align:center;">
1
</td>
</tr>
<tr>
<td style="text-align:center;">
Tuna Jelly-A
</td>
<td style="text-align:center;">
0.336
</td>
<td style="text-align:center;">
29
</td>
<td style="text-align:center;">
1
</td>
</tr>
<tr>
<td style="text-align:center;">
Yung’s-B
</td>
<td style="text-align:center;">
0.273
</td>
<td style="text-align:center;">
30
</td>
<td style="text-align:center;">
1
</td>
</tr>
<tr>
<td style="text-align:center;">
FM17
</td>
<td style="text-align:center;">
0.267
</td>
<td style="text-align:center;">
31
</td>
<td style="text-align:center;">
1
</td>
</tr>
<tr>
<td style="text-align:center;">
Kelsey-1
</td>
<td style="text-align:center;">
0.219
</td>
<td style="text-align:center;">
32
</td>
<td style="text-align:center;">
1
</td>
</tr>
<tr>
<td style="text-align:center;">
Kelsey-2
</td>
<td style="text-align:center;">
0.212
</td>
<td style="text-align:center;">
33
</td>
<td style="text-align:center;">
1
</td>
</tr>
<tr>
<td style="text-align:center;">
Yung’s-A
</td>
<td style="text-align:center;">
0.206
</td>
<td style="text-align:center;">
34
</td>
<td style="text-align:center;">
1
</td>
</tr>
<tr>
<td style="text-align:center;">
ML48
</td>
<td style="text-align:center;">
0.200
</td>
<td style="text-align:center;">
35
</td>
<td style="text-align:center;">
1
</td>
</tr>
<tr>
<td style="text-align:center;">
ML5
</td>
<td style="text-align:center;">
0.187
</td>
<td style="text-align:center;">
36
</td>
<td style="text-align:center;">
1
</td>
</tr>
<tr>
<td style="text-align:center;">
ML47
</td>
<td style="text-align:center;">
0.184
</td>
<td style="text-align:center;">
37
</td>
<td style="text-align:center;">
1
</td>
</tr>
<tr>
<td style="text-align:center;">
BC-1
</td>
<td style="text-align:center;">
0.178
</td>
<td style="text-align:center;">
38
</td>
<td style="text-align:center;">
1
</td>
</tr>
<tr>
<td style="text-align:center;">
Cheetos-A
</td>
<td style="text-align:center;">
0.170
</td>
<td style="text-align:center;">
39
</td>
<td style="text-align:center;">
1
</td>
</tr>
<tr>
<td style="text-align:center;">
Acerv 1 (A-AC)
</td>
<td style="text-align:center;">
0.124
</td>
<td style="text-align:center;">
40
</td>
<td style="text-align:center;">
1
</td>
</tr>
<tr>
<td style="text-align:center;">
ML7
</td>
<td style="text-align:center;">
0.090
</td>
<td style="text-align:center;">
41
</td>
<td style="text-align:center;">
1
</td>
</tr>
<tr>
<td style="text-align:center;">
THIN
</td>
<td style="text-align:center;">
0.077
</td>
<td style="text-align:center;">
42
</td>
<td style="text-align:center;">
1
</td>
</tr>
<tr>
<td style="text-align:center;">
Struggle Bus
</td>
<td style="text-align:center;">
0.069
</td>
<td style="text-align:center;">
43
</td>
<td style="text-align:center;">
1
</td>
</tr>
<tr>
<td style="text-align:center;">
Steph’s
</td>
<td style="text-align:center;">
0.067
</td>
<td style="text-align:center;">
44
</td>
<td style="text-align:center;">
1
</td>
</tr>
<tr>
<td style="text-align:center;">
Dom’s Reef
</td>
<td style="text-align:center;">
0.066
</td>
<td style="text-align:center;">
45
</td>
<td style="text-align:center;">
2
</td>
</tr>
<tr>
<td style="text-align:center;">
Marker 9
</td>
<td style="text-align:center;">
0.065
</td>
<td style="text-align:center;">
46
</td>
<td style="text-align:center;">
2
</td>
</tr>
<tr>
<td style="text-align:center;">
North Midchannel-A
</td>
<td style="text-align:center;">
0.054
</td>
<td style="text-align:center;">
47
</td>
<td style="text-align:center;">
2
</td>
</tr>
<tr>
<td style="text-align:center;">
Stagreef
</td>
<td style="text-align:center;">
0.047
</td>
<td style="text-align:center;">
48
</td>
<td style="text-align:center;">
2
</td>
</tr>
<tr>
<td style="text-align:center;">
Acerv 3 (C-AC)
</td>
<td style="text-align:center;">
0.044
</td>
<td style="text-align:center;">
49
</td>
<td style="text-align:center;">
2
</td>
</tr>
<tr>
<td style="text-align:center;">
Ford’s Reef
</td>
<td style="text-align:center;">
0.020
</td>
<td style="text-align:center;">
50
</td>
<td style="text-align:center;">
2
</td>
</tr>
<tr>
<td style="text-align:center;">
Site 406
</td>
<td style="text-align:center;">
0.018
</td>
<td style="text-align:center;">
51
</td>
<td style="text-align:center;">
2
</td>
</tr>
<tr>
<td style="text-align:center;">
ML36
</td>
<td style="text-align:center;">
0.013
</td>
<td style="text-align:center;">
52
</td>
<td style="text-align:center;">
2
</td>
</tr>
<tr>
<td style="text-align:center;">
DR-A
</td>
<td style="text-align:center;">
0.012
</td>
<td style="text-align:center;">
53
</td>
<td style="text-align:center;">
2
</td>
</tr>
<tr>
<td style="text-align:center;">
Site 211
</td>
<td style="text-align:center;">
0.007
</td>
<td style="text-align:center;">
54
</td>
<td style="text-align:center;">
2
</td>
</tr>
<tr>
<td style="text-align:center;">
G16
</td>
<td style="text-align:center;">
0.000
</td>
<td style="text-align:center;">
55
</td>
<td style="text-align:center;">
2
</td>
</tr>
<tr>
<td style="text-align:center;">
Govt Cut
</td>
<td style="text-align:center;">
-0.021
</td>
<td style="text-align:center;">
56
</td>
<td style="text-align:center;">
2
</td>
</tr>
<tr>
<td style="text-align:center;">
Trans 2
</td>
<td style="text-align:center;">
-0.034
</td>
<td style="text-align:center;">
57
</td>
<td style="text-align:center;">
2
</td>
</tr>
<tr>
<td style="text-align:center;">
BC-H
</td>
<td style="text-align:center;">
-0.038
</td>
<td style="text-align:center;">
58
</td>
<td style="text-align:center;">
2
</td>
</tr>
<tr>
<td style="text-align:center;">
G17
</td>
<td style="text-align:center;">
-0.041
</td>
<td style="text-align:center;">
59
</td>
<td style="text-align:center;">
2
</td>
</tr>
<tr>
<td style="text-align:center;">
Alina-A
</td>
<td style="text-align:center;">
-0.041
</td>
<td style="text-align:center;">
60
</td>
<td style="text-align:center;">
2
</td>
</tr>
<tr>
<td style="text-align:center;">
Britt’s Reef
</td>
<td style="text-align:center;">
-0.043
</td>
<td style="text-align:center;">
61
</td>
<td style="text-align:center;">
2
</td>
</tr>
<tr>
<td style="text-align:center;">
Trav’s Reef
</td>
<td style="text-align:center;">
-0.045
</td>
<td style="text-align:center;">
62
</td>
<td style="text-align:center;">
2
</td>
</tr>
<tr>
<td style="text-align:center;">
Acerv 2 (B-AC)
</td>
<td style="text-align:center;">
-0.059
</td>
<td style="text-align:center;">
63
</td>
<td style="text-align:center;">
2
</td>
</tr>
<tr>
<td style="text-align:center;">
MB
</td>
<td style="text-align:center;">
-0.060
</td>
<td style="text-align:center;">
64
</td>
<td style="text-align:center;">
2
</td>
</tr>
<tr>
<td style="text-align:center;">
M6
</td>
<td style="text-align:center;">
-0.067
</td>
<td style="text-align:center;">
65
</td>
<td style="text-align:center;">
2
</td>
</tr>
<tr>
<td style="text-align:center;">
ELK
</td>
<td style="text-align:center;">
-0.069
</td>
<td style="text-align:center;">
66
</td>
<td style="text-align:center;">
2
</td>
</tr>
<tr>
<td style="text-align:center;">
BC-G
</td>
<td style="text-align:center;">
-0.072
</td>
<td style="text-align:center;">
67
</td>
<td style="text-align:center;">
2
</td>
</tr>
<tr>
<td style="text-align:center;">
Acerv 5 (E-AC)
</td>
<td style="text-align:center;">
-0.076
</td>
<td style="text-align:center;">
68
</td>
<td style="text-align:center;">
2
</td>
</tr>
<tr>
<td style="text-align:center;">
Acerv 4 (D-AC)
</td>
<td style="text-align:center;">
-0.087
</td>
<td style="text-align:center;">
69
</td>
<td style="text-align:center;">
2
</td>
</tr>
<tr>
<td style="text-align:center;">
G1
</td>
<td style="text-align:center;">
-0.088
</td>
<td style="text-align:center;">
70
</td>
<td style="text-align:center;">
2
</td>
</tr>
<tr>
<td style="text-align:center;">
Sunny Isles-F
</td>
<td style="text-align:center;">
-0.103
</td>
<td style="text-align:center;">
71
</td>
<td style="text-align:center;">
2
</td>
</tr>
<tr>
<td style="text-align:center;">
Alina-B
</td>
<td style="text-align:center;">
-0.111
</td>
<td style="text-align:center;">
72
</td>
<td style="text-align:center;">
2
</td>
</tr>
<tr>
<td style="text-align:center;">
ML14
</td>
<td style="text-align:center;">
-0.130
</td>
<td style="text-align:center;">
73
</td>
<td style="text-align:center;">
2
</td>
</tr>
<tr>
<td style="text-align:center;">
ML50
</td>
<td style="text-align:center;">
-0.136
</td>
<td style="text-align:center;">
74
</td>
<td style="text-align:center;">
2
</td>
</tr>
<tr>
<td style="text-align:center;">
U25
</td>
<td style="text-align:center;">
-0.169
</td>
<td style="text-align:center;">
75
</td>
<td style="text-align:center;">
2
</td>
</tr>
<tr>
<td style="text-align:center;">
Grounding
</td>
<td style="text-align:center;">
-0.180
</td>
<td style="text-align:center;">
76
</td>
<td style="text-align:center;">
2
</td>
</tr>
<tr>
<td style="text-align:center;">
TT (Thicket 3)
</td>
<td style="text-align:center;">
-0.184
</td>
<td style="text-align:center;">
77
</td>
<td style="text-align:center;">
2
</td>
</tr>
<tr>
<td style="text-align:center;">
Fowey
</td>
<td style="text-align:center;">
-0.203
</td>
<td style="text-align:center;">
78
</td>
<td style="text-align:center;">
2
</td>
</tr>
<tr>
<td style="text-align:center;">
Jons
</td>
<td style="text-align:center;">
-0.208
</td>
<td style="text-align:center;">
79
</td>
<td style="text-align:center;">
2
</td>
</tr>
<tr>
<td style="text-align:center;">
ML34
</td>
<td style="text-align:center;">
-0.210
</td>
<td style="text-align:center;">
80
</td>
<td style="text-align:center;">
2
</td>
</tr>
<tr>
<td style="text-align:center;">
G15
</td>
<td style="text-align:center;">
-0.212
</td>
<td style="text-align:center;">
81
</td>
<td style="text-align:center;">
2
</td>
</tr>
<tr>
<td style="text-align:center;">
ML41
</td>
<td style="text-align:center;">
-0.214
</td>
<td style="text-align:center;">
82
</td>
<td style="text-align:center;">
2
</td>
</tr>
<tr>
<td style="text-align:center;">
Cooper’s
</td>
<td style="text-align:center;">
-0.216
</td>
<td style="text-align:center;">
83
</td>
<td style="text-align:center;">
2
</td>
</tr>
<tr>
<td style="text-align:center;">
Cheetos-B
</td>
<td style="text-align:center;">
-0.223
</td>
<td style="text-align:center;">
84
</td>
<td style="text-align:center;">
2
</td>
</tr>
<tr>
<td style="text-align:center;">
Almost Done
</td>
<td style="text-align:center;">
-0.225
</td>
<td style="text-align:center;">
85
</td>
<td style="text-align:center;">
2
</td>
</tr>
<tr>
<td style="text-align:center;">
ML4
</td>
<td style="text-align:center;">
-0.238
</td>
<td style="text-align:center;">
86
</td>
<td style="text-align:center;">
2
</td>
</tr>
<tr>
<td style="text-align:center;">
U24
</td>
<td style="text-align:center;">
-0.241
</td>
<td style="text-align:center;">
87
</td>
<td style="text-align:center;">
2
</td>
</tr>
<tr>
<td style="text-align:center;">
ML63
</td>
<td style="text-align:center;">
-0.243
</td>
<td style="text-align:center;">
88
</td>
<td style="text-align:center;">
3
</td>
</tr>
<tr>
<td style="text-align:center;">
Big Bertha
</td>
<td style="text-align:center;">
-0.245
</td>
<td style="text-align:center;">
89
</td>
<td style="text-align:center;">
3
</td>
</tr>
<tr>
<td style="text-align:center;">
ML44
</td>
<td style="text-align:center;">
-0.249
</td>
<td style="text-align:center;">
90
</td>
<td style="text-align:center;">
3
</td>
</tr>
<tr>
<td style="text-align:center;">
G11
</td>
<td style="text-align:center;">
-0.254
</td>
<td style="text-align:center;">
91
</td>
<td style="text-align:center;">
3
</td>
</tr>
<tr>
<td style="text-align:center;">
Inshore
</td>
<td style="text-align:center;">
-0.275
</td>
<td style="text-align:center;">
92
</td>
<td style="text-align:center;">
3
</td>
</tr>
<tr>
<td style="text-align:center;">
G2
</td>
<td style="text-align:center;">
-0.277
</td>
<td style="text-align:center;">
93
</td>
<td style="text-align:center;">
3
</td>
</tr>
<tr>
<td style="text-align:center;">
G6
</td>
<td style="text-align:center;">
-0.285
</td>
<td style="text-align:center;">
94
</td>
<td style="text-align:center;">
3
</td>
</tr>
<tr>
<td style="text-align:center;">
ML31
</td>
<td style="text-align:center;">
-0.293
</td>
<td style="text-align:center;">
95
</td>
<td style="text-align:center;">
3
</td>
</tr>
<tr>
<td style="text-align:center;">
MUTANT182
</td>
<td style="text-align:center;">
-0.300
</td>
<td style="text-align:center;">
96
</td>
<td style="text-align:center;">
3
</td>
</tr>
<tr>
<td style="text-align:center;">
M10
</td>
<td style="text-align:center;">
-0.301
</td>
<td style="text-align:center;">
97
</td>
<td style="text-align:center;">
3
</td>
</tr>
<tr>
<td style="text-align:center;">
ML20
</td>
<td style="text-align:center;">
-0.307
</td>
<td style="text-align:center;">
98
</td>
<td style="text-align:center;">
3
</td>
</tr>
<tr>
<td style="text-align:center;">
THICK
</td>
<td style="text-align:center;">
-0.313
</td>
<td style="text-align:center;">
99
</td>
<td style="text-align:center;">
3
</td>
</tr>
<tr>
<td style="text-align:center;">
ML62
</td>
<td style="text-align:center;">
-0.332
</td>
<td style="text-align:center;">
100
</td>
<td style="text-align:center;">
3
</td>
</tr>
<tr>
<td style="text-align:center;">
Trans 1
</td>
<td style="text-align:center;">
-0.335
</td>
<td style="text-align:center;">
101
</td>
<td style="text-align:center;">
3
</td>
</tr>
<tr>
<td style="text-align:center;">
FM12
</td>
<td style="text-align:center;">
-0.337
</td>
<td style="text-align:center;">
102
</td>
<td style="text-align:center;">
3
</td>
</tr>
<tr>
<td style="text-align:center;">
W/G
</td>
<td style="text-align:center;">
-0.343
</td>
<td style="text-align:center;">
103
</td>
<td style="text-align:center;">
3
</td>
</tr>
<tr>
<td style="text-align:center;">
ML54
</td>
<td style="text-align:center;">
-0.345
</td>
<td style="text-align:center;">
104
</td>
<td style="text-align:center;">
3
</td>
</tr>
<tr>
<td style="text-align:center;">
FM16
</td>
<td style="text-align:center;">
-0.359
</td>
<td style="text-align:center;">
105
</td>
<td style="text-align:center;">
3
</td>
</tr>
<tr>
<td style="text-align:center;">
FM10
</td>
<td style="text-align:center;">
-0.362
</td>
<td style="text-align:center;">
106
</td>
<td style="text-align:center;">
3
</td>
</tr>
<tr>
<td style="text-align:center;">
B8
</td>
<td style="text-align:center;">
-0.369
</td>
<td style="text-align:center;">
107
</td>
<td style="text-align:center;">
3
</td>
</tr>
<tr>
<td style="text-align:center;">
FM15
</td>
<td style="text-align:center;">
-0.385
</td>
<td style="text-align:center;">
108
</td>
<td style="text-align:center;">
3
</td>
</tr>
<tr>
<td style="text-align:center;">
B/B
</td>
<td style="text-align:center;">
-0.397
</td>
<td style="text-align:center;">
109
</td>
<td style="text-align:center;">
3
</td>
</tr>
<tr>
<td style="text-align:center;">
ML38
</td>
<td style="text-align:center;">
-0.409
</td>
<td style="text-align:center;">
110
</td>
<td style="text-align:center;">
3
</td>
</tr>
<tr>
<td style="text-align:center;">
FM1
</td>
<td style="text-align:center;">
-0.424
</td>
<td style="text-align:center;">
111
</td>
<td style="text-align:center;">
3
</td>
</tr>
<tr>
<td style="text-align:center;">
ML56
</td>
<td style="text-align:center;">
-0.432
</td>
<td style="text-align:center;">
112
</td>
<td style="text-align:center;">
3
</td>
</tr>
<tr>
<td style="text-align:center;">
M1
</td>
<td style="text-align:center;">
-0.433
</td>
<td style="text-align:center;">
113
</td>
<td style="text-align:center;">
3
</td>
</tr>
<tr>
<td style="text-align:center;">
FM5
</td>
<td style="text-align:center;">
-0.433
</td>
<td style="text-align:center;">
114
</td>
<td style="text-align:center;">
3
</td>
</tr>
<tr>
<td style="text-align:center;">
FM9
</td>
<td style="text-align:center;">
-0.451
</td>
<td style="text-align:center;">
115
</td>
<td style="text-align:center;">
3
</td>
</tr>
<tr>
<td style="text-align:center;">
FM18
</td>
<td style="text-align:center;">
-0.455
</td>
<td style="text-align:center;">
116
</td>
<td style="text-align:center;">
3
</td>
</tr>
<tr>
<td style="text-align:center;">
Navassa
</td>
<td style="text-align:center;">
-0.460
</td>
<td style="text-align:center;">
117
</td>
<td style="text-align:center;">
3
</td>
</tr>
<tr>
<td style="text-align:center;">
FM7
</td>
<td style="text-align:center;">
-0.481
</td>
<td style="text-align:center;">
118
</td>
<td style="text-align:center;">
3
</td>
</tr>
<tr>
<td style="text-align:center;">
W/B
</td>
<td style="text-align:center;">
-0.490
</td>
<td style="text-align:center;">
119
</td>
<td style="text-align:center;">
3
</td>
</tr>
<tr>
<td style="text-align:center;">
ML1
</td>
<td style="text-align:center;">
-0.496
</td>
<td style="text-align:center;">
120
</td>
<td style="text-align:center;">
3
</td>
</tr>
<tr>
<td style="text-align:center;">
FM13
</td>
<td style="text-align:center;">
-0.508
</td>
<td style="text-align:center;">
121
</td>
<td style="text-align:center;">
3
</td>
</tr>
<tr>
<td style="text-align:center;">
G18
</td>
<td style="text-align:center;">
-0.565
</td>
<td style="text-align:center;">
122
</td>
<td style="text-align:center;">
3
</td>
</tr>
<tr>
<td style="text-align:center;">
ML3
</td>
<td style="text-align:center;">
-0.571
</td>
<td style="text-align:center;">
123
</td>
<td style="text-align:center;">
3
</td>
</tr>
<tr>
<td style="text-align:center;">
W/Y
</td>
<td style="text-align:center;">
-0.578
</td>
<td style="text-align:center;">
124
</td>
<td style="text-align:center;">
3
</td>
</tr>
<tr>
<td style="text-align:center;">
FM11
</td>
<td style="text-align:center;">
-0.578
</td>
<td style="text-align:center;">
125
</td>
<td style="text-align:center;">
3
</td>
</tr>
<tr>
<td style="text-align:center;">
FM3
</td>
<td style="text-align:center;">
-0.580
</td>
<td style="text-align:center;">
126
</td>
<td style="text-align:center;">
3
</td>
</tr>
<tr>
<td style="text-align:center;">
FM19
</td>
<td style="text-align:center;">
-0.611
</td>
<td style="text-align:center;">
127
</td>
<td style="text-align:center;">
3
</td>
</tr>
<tr>
<td style="text-align:center;">
ML13
</td>
<td style="text-align:center;">
-0.616
</td>
<td style="text-align:center;">
128
</td>
<td style="text-align:center;">
3
</td>
</tr>
<tr>
<td style="text-align:center;">
ML11
</td>
<td style="text-align:center;">
-0.616
</td>
<td style="text-align:center;">
129
</td>
<td style="text-align:center;">
3
</td>
</tr>
<tr>
<td style="text-align:center;">
ML43
</td>
<td style="text-align:center;">
-0.648
</td>
<td style="text-align:center;">
130
</td>
<td style="text-align:center;">
3
</td>
</tr>
</tbody>
</table>

``` r
composite <- normalizedStats %>%
  left_join(overlap %>%
  pivot_longer(-genotype,
               names_to = "metric",
               values_to = "score",
               values_drop_na = T) %>%
  group_by(genotype) %>%
  summarise(metrics = length(unique(metric)),
            type = case_when(
              all(metric %in% c('6-month linear growth',
                      'annual linear growth',
                      'specific growth rate', 'colony volumetric SGR',
                      '6-month colony volumetric growth',
                      'annual colony volumetric growth',
                      '6-month interstitial space growth',
                      'annual interstitial space growth',
                      'interstitial space SGR')) == T ~ 'LE',
              all(!metric %in% c('6-month linear growth',
                      'annual linear growth',
                      'specific growth rate', 'colony volumetric SGR',
                      '6-month colony volumetric growth',
                      'annual colony volumetric growth',
                      '6-month interstitial space growth',
                      'annual interstitial space growth',
                      'interstitial space SGR')) == T ~ 'G',
              TRUE ~ 'Both')),
  by = "genotype")

composite %>%
  ggplot(aes(x= score, y=metrics, color=type)) +
  geom_point(position = "jitter") +
  #circle around the type-score cluster
  annotate("path",
   x=1.3+0.7*cos(seq(0,2*pi,length.out=100)),
   y=6.1+2.2*sin(seq(0,2*pi,length.out=100)),
   size=2) +
  #circle around the type-metric cluster
  annotate("path",
   x=-0.2+0.6*cos(seq(0,2*pi,length.out=100)),
   y=14+0.9*sin(seq(0,2*pi,length.out=100)),
   size=2,
   color = "#673ab7") +
  scale_x_continuous(limits = c(-1.5,2),
                     breaks = seq(-1,2,by=1),
                     minor_breaks = seq(-1,2,by=0.5)) +
  labs(title="Comparison of Composite Score and the Number/Type of Metrics") +
  theme_bw()
```

![](/notebook/images/compositeGrowth/graphs%20of%20norm%20stats-1.png)<!-- -->

There is a cluster of the type of metric and the number of metrics
(purple), which makes sense as if there are two types of metrics
represented, then there is a high likelihood that both calcification and
linear extension metrics are represented. However, there is no
clustering of the number of metrics and the score. Finally, there is
slight clustering of the type of metric and the score (black), with
genotypes that have both metrics represented being on average higher
than genotypes represented by linear extension or calcification metrics
alone.

### Statistical Tests

``` r
composite %>%
  aov(metrics~type, data=.) %>%
TukeyHSD() %>%
  tidy() %>%
  select(-c(term,null.value)) %>%
  kbl(align = 'c',
    digits = 3,
    caption = "Comparison of the number of metrics as a function of the classified type (purple). Both denotes linear extension and calcification metrics are represented in the composite index.") %>%
  kable_classic() %>%
  row_spec(0, bold = T)
```

<table class=" lightable-classic" style="font-family: &quot;Arial Narrow&quot;, &quot;Source Sans Pro&quot;, sans-serif; margin-left: auto; margin-right: auto;">
<caption>
Comparison of the number of metrics as a function of the classified type
(purple). Both denotes linear extension and calcification metrics are
represented in the composite index.
</caption>
<thead>
<tr>
<th style="text-align:center;font-weight: bold;">
contrast
</th>
<th style="text-align:center;font-weight: bold;">
estimate
</th>
<th style="text-align:center;font-weight: bold;">
conf.low
</th>
<th style="text-align:center;font-weight: bold;">
conf.high
</th>
<th style="text-align:center;font-weight: bold;">
adj.p.value
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:center;">
G-Both
</td>
<td style="text-align:center;">
-4.985
</td>
<td style="text-align:center;">
-7.476
</td>
<td style="text-align:center;">
-2.494
</td>
<td style="text-align:center;">
0.000
</td>
</tr>
<tr>
<td style="text-align:center;">
LE-Both
</td>
<td style="text-align:center;">
-5.430
</td>
<td style="text-align:center;">
-6.542
</td>
<td style="text-align:center;">
-4.318
</td>
<td style="text-align:center;">
0.000
</td>
</tr>
<tr>
<td style="text-align:center;">
LE-G
</td>
<td style="text-align:center;">
-0.445
</td>
<td style="text-align:center;">
-2.790
</td>
<td style="text-align:center;">
1.901
</td>
<td style="text-align:center;">
0.895
</td>
</tr>
</tbody>
</table>

``` r
composite %>%
  lm(score~metrics, data=.) %>%
  summary() %>%
  tidy()%>%
  kbl(align = 'c',
    digits = 3,
    caption = "Comparison of the composite index as a function of the number of metrics repesented.") %>%
  kable_classic() %>%
  row_spec(0, bold = T)
```

<table class=" lightable-classic" style="font-family: &quot;Arial Narrow&quot;, &quot;Source Sans Pro&quot;, sans-serif; margin-left: auto; margin-right: auto;">
<caption>
Comparison of the composite index as a function of the number of metrics
repesented.
</caption>
<thead>
<tr>
<th style="text-align:center;font-weight: bold;">
term
</th>
<th style="text-align:center;font-weight: bold;">
estimate
</th>
<th style="text-align:center;font-weight: bold;">
std.error
</th>
<th style="text-align:center;font-weight: bold;">
statistic
</th>
<th style="text-align:center;font-weight: bold;">
p.value
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:center;">
(Intercept)
</td>
<td style="text-align:center;">
0.066
</td>
<td style="text-align:center;">
0.074
</td>
<td style="text-align:center;">
0.886
</td>
<td style="text-align:center;">
0.377
</td>
</tr>
<tr>
<td style="text-align:center;">
metrics
</td>
<td style="text-align:center;">
-0.005
</td>
<td style="text-align:center;">
0.015
</td>
<td style="text-align:center;">
-0.347
</td>
<td style="text-align:center;">
0.729
</td>
</tr>
</tbody>
</table>

``` r
composite %>%
  aov(score~type, data=.) %>%
  TukeyHSD() %>%
  tidy() %>%
  select(-c(term,null.value)) %>%
  kbl(align = 'c',
    digits = 3,
    caption = "Comparison of the composite index as a function of the classified type (black). Both denotes linear extension and calcification metrics are represented in the composite index.") %>%
  kable_classic() %>%
  row_spec(0, bold = T)
```

<table class=" lightable-classic" style="font-family: &quot;Arial Narrow&quot;, &quot;Source Sans Pro&quot;, sans-serif; margin-left: auto; margin-right: auto;">
<caption>
Comparison of the composite index as a function of the classified type
(black). Both denotes linear extension and calcification metrics are
represented in the composite index.
</caption>
<thead>
<tr>
<th style="text-align:center;font-weight: bold;">
contrast
</th>
<th style="text-align:center;font-weight: bold;">
estimate
</th>
<th style="text-align:center;font-weight: bold;">
conf.low
</th>
<th style="text-align:center;font-weight: bold;">
conf.high
</th>
<th style="text-align:center;font-weight: bold;">
adj.p.value
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:center;">
G-Both
</td>
<td style="text-align:center;">
-0.518
</td>
<td style="text-align:center;">
-1.105
</td>
<td style="text-align:center;">
0.069
</td>
<td style="text-align:center;">
0.095
</td>
</tr>
<tr>
<td style="text-align:center;">
LE-Both
</td>
<td style="text-align:center;">
-0.292
</td>
<td style="text-align:center;">
-0.554
</td>
<td style="text-align:center;">
-0.030
</td>
<td style="text-align:center;">
0.025
</td>
</tr>
<tr>
<td style="text-align:center;">
LE-G
</td>
<td style="text-align:center;">
0.226
</td>
<td style="text-align:center;">
-0.327
</td>
<td style="text-align:center;">
0.778
</td>
<td style="text-align:center;">
0.598
</td>
</tr>
</tbody>
</table>

### Analysis

We can then dive into the 9 clustered (black) genotypes which are
driving this statistically significant difference (have a score &gt;0.5
and have both metrics represented). They all happen to be CRF genotypes
used by Katie Lohr in her PhD work at UF and Dan Paradis in his masters
work at Auburn. This data is distinguished as only having a few data
points in an Auburn lab for buoyant weight measurements while all other
measurements come from the field and inshore patch reefs. Katie Lohr
measured the linear extension and calcification of the corals in a CRF
nursery and is the main driver of why these corals are classified as
‘Both’.

``` r
corals %>% 
  filter(genotype %in% (composite %>%
                            filter(score>0.5&type=='Both') %>%
                            pull(genotype))) %>%
  select(genotype, datafile_name, location_name) %>%
  distinct() %>%
  arrange(genotype) %>%
    kbl(align = 'c',
    digits = 3) %>%
  kable_classic() %>%
  row_spec(0, bold = T)
```

<table class=" lightable-classic" style="font-family: &quot;Arial Narrow&quot;, &quot;Source Sans Pro&quot;, sans-serif; margin-left: auto; margin-right: auto;">
<thead>
<tr>
<th style="text-align:center;font-weight: bold;">
genotype
</th>
<th style="text-align:center;font-weight: bold;">
datafile\_name
</th>
<th style="text-align:center;font-weight: bold;">
location\_name
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:center;">
K1
</td>
<td style="text-align:center;">
Paradis2019
</td>
<td style="text-align:center;">
Auburn Lab
</td>
</tr>
<tr>
<td style="text-align:center;">
K1
</td>
<td style="text-align:center;">
LohrPatterson2017
</td>
<td style="text-align:center;">
CRF Tavenier Nursery
</td>
</tr>
<tr>
<td style="text-align:center;">
K2
</td>
<td style="text-align:center;">
LohrPatterson2017
</td>
<td style="text-align:center;">
CRF Tavenier Nursery
</td>
</tr>
<tr>
<td style="text-align:center;">
K2
</td>
<td style="text-align:center;">
Lohr2020
</td>
<td style="text-align:center;">
U4 Patch
</td>
</tr>
<tr>
<td style="text-align:center;">
K2
</td>
<td style="text-align:center;">
Lohr2020
</td>
<td style="text-align:center;">
U14 Patch
</td>
</tr>
<tr>
<td style="text-align:center;">
K3
</td>
<td style="text-align:center;">
LohrPatterson2017
</td>
<td style="text-align:center;">
CRF Tavenier Nursery
</td>
</tr>
<tr>
<td style="text-align:center;">
K3
</td>
<td style="text-align:center;">
Lohr2020
</td>
<td style="text-align:center;">
U4 Patch
</td>
</tr>
<tr>
<td style="text-align:center;">
U41
</td>
<td style="text-align:center;">
LohrPatterson2017
</td>
<td style="text-align:center;">
CRF Tavenier Nursery
</td>
</tr>
<tr>
<td style="text-align:center;">
U41
</td>
<td style="text-align:center;">
Lohr2020
</td>
<td style="text-align:center;">
U4 Patch
</td>
</tr>
<tr>
<td style="text-align:center;">
U41
</td>
<td style="text-align:center;">
Lohr2020
</td>
<td style="text-align:center;">
U14 Patch
</td>
</tr>
<tr>
<td style="text-align:center;">
U44
</td>
<td style="text-align:center;">
LohrPatterson2017
</td>
<td style="text-align:center;">
CRF Tavenier Nursery
</td>
</tr>
<tr>
<td style="text-align:center;">
U44
</td>
<td style="text-align:center;">
Lohr2020
</td>
<td style="text-align:center;">
U4 Patch
</td>
</tr>
<tr>
<td style="text-align:center;">
U47
</td>
<td style="text-align:center;">
LohrPatterson2017
</td>
<td style="text-align:center;">
CRF Tavenier Nursery
</td>
</tr>
<tr>
<td style="text-align:center;">
U73
</td>
<td style="text-align:center;">
LohrPatterson2017
</td>
<td style="text-align:center;">
CRF Tavenier Nursery
</td>
</tr>
<tr>
<td style="text-align:center;">
U77
</td>
<td style="text-align:center;">
LohrPatterson2017
</td>
<td style="text-align:center;">
CRF Tavenier Nursery
</td>
</tr>
<tr>
<td style="text-align:center;">
U77
</td>
<td style="text-align:center;">
Lohr2020
</td>
<td style="text-align:center;">
U4 Patch
</td>
</tr>
<tr>
<td style="text-align:center;">
U77
</td>
<td style="text-align:center;">
Lohr2020
</td>
<td style="text-align:center;">
U14 Patch
</td>
</tr>
<tr>
<td style="text-align:center;">
U78
</td>
<td style="text-align:center;">
LohrPatterson2017
</td>
<td style="text-align:center;">
CRF Tavenier Nursery
</td>
</tr>
</tbody>
</table>

This leads me to believe that the composite growth index is not
sensitive to data comprised only of calcification or linear extension
metrics, rather, the index is sensitive to evenness of sampling effort
where a few high growth values in a single metric may skew the composite
score. While this dampens the robustness of our index as it stands
today, the index will become more robust over time with the inclusion of
more datasets from the lab and field.

To support this conclusion, I am recalculating the composite growth
index. However, for this index, the calcification data for Katie Lohr’s
work is removed. This calcification data was obtained by collecting the
buoyant weight of corals grown in a coral nursery and dominates the
buoyant weight metrics as all other buoyant weight growth measured
corals grown in a lab where growth rates are typically much less than
that of a nursery. Thus, these genotypes will now only be classified as
linear extension. I am then recreating the exact plot and tables from
above on this data subset.

``` r
corals_sub <- corals %>%
  filter(datafile_name!='LohrPatterson2017') %>%
  bind_rows(.,corals %>% 
              filter(datafile_name=='LohrPatterson2017' &
                       !trait %in% c('daily calcification','mass normalized daily calcification')))

overlap_sub <-   corals_sub %>%
    filter(str_detect(filters, "(Bleach)|(OA)" ,negate = T)) %>%
    group_by(genotype, trait, unit, method) %>%
    summarise(mean = mean(value, na.rm = T)) %>%
    ungroup() %>%
    arrange(trait,desc(mean)) %>%
    select(-c(unit,method)) %>%
    pivot_wider(names_from = trait,
                values_from = mean) %>%
    #arrange by rows w/ least # of na
    mutate(count = apply(., 1, count_na)) %>%
    arrange(count) %>%
    select(-count)

  overlap_sub <- relocate(overlap_sub, overlap_sub %>%
    select(-genotype) %>%
    summarise(across(everything(), ~ sum(is.na(.)))) %>%
    unlist %>% sort() %>%
    names(), .after = "genotype") %>%
    relocate(c(`daily calcification`,`mass normalized daily calcification`,
               `SA normalized daily calcification`:`light calcification`),
             .after=`interstitial space SGR`)
  
  std_sub <- overlap_sub %>%
  #scale existing values
  mutate(across(-1,~ as.numeric(scale(.))))

std_sub <- std_sub %>%
  rowwise() %>%
  #calculate the LE and G Mean for each genotype
  mutate(LE.mean = mean(c_across(`specific growth rate`:`interstitial space SGR`),na.rm=T),
         G.mean = mean(c_across(`daily calcification`:`light calcification`),na.rm=T),
         #replace NaN with NA
         across(-1, ~replace(., is.nan(.), NA)),
  #impute LE values
  across(`specific growth rate`:`interstitial space SGR`, ~ coalesce(.,LE.mean)),
  #impute G Values
    across(`daily calcification`:`light calcification`,
           ~ coalesce(.,G.mean)),
  #if LE.mean | G.mean == NA, replace with the column mean i.e. 0
   across(-1, ~ case_when(is.na(.)~0,
                          TRUE ~ .))
  )

normalizedStats_sub <- std_sub %>%
    select(-c(LE.mean,G.mean)) %>%
  pivot_longer(-genotype,
               names_to = "metric",
               values_to = "score")

normalizedStats.LE_sub <- normalizedStats_sub %>%
              filter(metric %in% c('6-month linear growth',
                                  'annual linear growth',
                 'specific growth rate', 'colony volumetric SGR',
                 '6-month colony volumetric growth',
                 'annual colony volumetric growth',
                 '6-month interstitial space growth',
                 'annual interstitial space growth',
                 'interstitial space SGR')) %>%
              group_by(genotype) %>%
              summarise(score = mean(score, na.rm=T)*0.43)
normalizedStats.G_sub <- normalizedStats_sub %>%
            filter(!metric %in% c('6-month linear growth',
                                 'annual linear growth',
                 'specific growth rate', 'colony volumetric SGR',
                 '6-month colony volumetric growth',
                 'annual colony volumetric growth',
                 '6-month interstitial space growth',
                 'annual interstitial space growth',
                 'interstitial space SGR')) %>%
              group_by(genotype) %>%
              summarise(score = mean(score, na.rm=T)*0.57)

normalizedStats_sub <- full_join(
  normalizedStats.G_sub,
  normalizedStats.LE_sub,
  by = "genotype") %>%
  mutate(score=score.x + score.y) %>%
  select(genotype,score) %>%
  arrange(desc(score))

composite_sub <- normalizedStats_sub %>%
  left_join(overlap_sub %>%
  pivot_longer(-genotype,
               names_to = "metric",
               values_to = "score",
               values_drop_na = T) %>%
  group_by(genotype) %>%
  summarise(metrics = length(unique(metric)),
            type = case_when(
              all(metric %in% c('6-month linear growth',
                      'annual linear growth',
                      'specific growth rate', 'colony volumetric SGR',
                      '6-month colony volumetric growth',
                      'annual colony volumetric growth',
                      '6-month interstitial space growth',
                      'annual interstitial space growth',
                      'interstitial space SGR')) == T ~ 'LE',
              all(!metric %in% c('6-month linear growth',
                      'annual linear growth',
                      'specific growth rate', 'colony volumetric SGR',
                      '6-month colony volumetric growth',
                      'annual colony volumetric growth',
                      '6-month interstitial space growth',
                      'annual interstitial space growth',
                      'interstitial space SGR')) == T ~ 'G',
              TRUE ~ 'Both')),
  by = "genotype")

composite_sub %>%
  ggplot(aes(x= score, y=metrics, color=type)) +
  geom_point(position = "jitter") +
  scale_x_continuous(limits = c(-1.5,2),
                     breaks = seq(-1,2,by=1),
                     minor_breaks = seq(-1,2,by=0.5)) +
  labs(title="Missing Lohr (2017) Calcification Data") +
  theme_bw()
```

![](/notebook/images/compositeGrowth/remove%20Lohr%20G%20data-1.png)<!-- -->

``` r
composite_sub %>%
  aov(score~type, data=.) %>%
  TukeyHSD() %>%
  tidy() %>%
  select(-c(term,null.value)) %>%
  kbl(align = 'c',
    digits = 3,
    caption = "Comparison of the composite index as a function of the classified type. Both denotes linear extension and calcification metrics are represented in the composite index. Calcification data from Lohr (2017) has been removed.") %>%
  kable_classic() %>%
  row_spec(0, bold = T)
```

<table class=" lightable-classic" style="font-family: &quot;Arial Narrow&quot;, &quot;Source Sans Pro&quot;, sans-serif; margin-left: auto; margin-right: auto;">
<caption>
Comparison of the composite index as a function of the classified type.
Both denotes linear extension and calcification metrics are represented
in the composite index. Calcification data from Lohr (2017) has been
removed.
</caption>
<thead>
<tr>
<th style="text-align:center;font-weight: bold;">
contrast
</th>
<th style="text-align:center;font-weight: bold;">
estimate
</th>
<th style="text-align:center;font-weight: bold;">
conf.low
</th>
<th style="text-align:center;font-weight: bold;">
conf.high
</th>
<th style="text-align:center;font-weight: bold;">
adj.p.value
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:center;">
G-Both
</td>
<td style="text-align:center;">
-0.106
</td>
<td style="text-align:center;">
-0.634
</td>
<td style="text-align:center;">
0.422
</td>
<td style="text-align:center;">
0.882
</td>
</tr>
<tr>
<td style="text-align:center;">
LE-Both
</td>
<td style="text-align:center;">
-0.030
</td>
<td style="text-align:center;">
-0.296
</td>
<td style="text-align:center;">
0.236
</td>
<td style="text-align:center;">
0.960
</td>
</tr>
<tr>
<td style="text-align:center;">
LE-G
</td>
<td style="text-align:center;">
0.076
</td>
<td style="text-align:center;">
-0.402
</td>
<td style="text-align:center;">
0.554
</td>
<td style="text-align:center;">
0.925
</td>
</tr>
</tbody>
</table>

We can then compare the new index rankings with the old index rankings
after the removal of Lohr (2017). We can see these few data points
heavily weighed these genotypes.

``` r
composite %>%
  full_join(composite_sub,
            suffix = c(".old",".new"),
            by="genotype") %>%
  arrange(desc(score.old)) %>%
  filter(score.old>0.5&type.old=='Both') %>%
    kbl(align = 'c',
    digits = 3,
    caption = "Comparison of the composite index before and after filtering Lohr (2017).") %>%
  kable_classic() %>%
  row_spec(0, bold = T)
```

<table class=" lightable-classic" style="font-family: &quot;Arial Narrow&quot;, &quot;Source Sans Pro&quot;, sans-serif; margin-left: auto; margin-right: auto;">
<caption>
Comparison of the composite index before and after filtering Lohr
(2017).
</caption>
<thead>
<tr>
<th style="text-align:center;font-weight: bold;">
genotype
</th>
<th style="text-align:center;font-weight: bold;">
score.old
</th>
<th style="text-align:center;font-weight: bold;">
metrics.old
</th>
<th style="text-align:center;font-weight: bold;">
type.old
</th>
<th style="text-align:center;font-weight: bold;">
score.new
</th>
<th style="text-align:center;font-weight: bold;">
metrics.new
</th>
<th style="text-align:center;font-weight: bold;">
type.new
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:center;">
U73
</td>
<td style="text-align:center;">
1.658
</td>
<td style="text-align:center;">
5
</td>
<td style="text-align:center;">
Both
</td>
<td style="text-align:center;">
1.027
</td>
<td style="text-align:center;">
3
</td>
<td style="text-align:center;">
LE
</td>
</tr>
<tr>
<td style="text-align:center;">
U47
</td>
<td style="text-align:center;">
1.587
</td>
<td style="text-align:center;">
5
</td>
<td style="text-align:center;">
Both
</td>
<td style="text-align:center;">
0.982
</td>
<td style="text-align:center;">
3
</td>
<td style="text-align:center;">
LE
</td>
</tr>
<tr>
<td style="text-align:center;">
K2
</td>
<td style="text-align:center;">
1.536
</td>
<td style="text-align:center;">
7
</td>
<td style="text-align:center;">
Both
</td>
<td style="text-align:center;">
0.229
</td>
<td style="text-align:center;">
5
</td>
<td style="text-align:center;">
LE
</td>
</tr>
<tr>
<td style="text-align:center;">
K3
</td>
<td style="text-align:center;">
1.530
</td>
<td style="text-align:center;">
7
</td>
<td style="text-align:center;">
Both
</td>
<td style="text-align:center;">
0.269
</td>
<td style="text-align:center;">
5
</td>
<td style="text-align:center;">
LE
</td>
</tr>
<tr>
<td style="text-align:center;">
U78
</td>
<td style="text-align:center;">
1.515
</td>
<td style="text-align:center;">
5
</td>
<td style="text-align:center;">
Both
</td>
<td style="text-align:center;">
0.836
</td>
<td style="text-align:center;">
3
</td>
<td style="text-align:center;">
LE
</td>
</tr>
<tr>
<td style="text-align:center;">
U41
</td>
<td style="text-align:center;">
1.455
</td>
<td style="text-align:center;">
7
</td>
<td style="text-align:center;">
Both
</td>
<td style="text-align:center;">
0.528
</td>
<td style="text-align:center;">
5
</td>
<td style="text-align:center;">
LE
</td>
</tr>
<tr>
<td style="text-align:center;">
U77
</td>
<td style="text-align:center;">
1.210
</td>
<td style="text-align:center;">
7
</td>
<td style="text-align:center;">
Both
</td>
<td style="text-align:center;">
0.435
</td>
<td style="text-align:center;">
5
</td>
<td style="text-align:center;">
LE
</td>
</tr>
<tr>
<td style="text-align:center;">
K1
</td>
<td style="text-align:center;">
1.072
</td>
<td style="text-align:center;">
5
</td>
<td style="text-align:center;">
Both
</td>
<td style="text-align:center;">
0.382
</td>
<td style="text-align:center;">
5
</td>
<td style="text-align:center;">
Both
</td>
</tr>
<tr>
<td style="text-align:center;">
U44
</td>
<td style="text-align:center;">
0.765
</td>
<td style="text-align:center;">
7
</td>
<td style="text-align:center;">
Both
</td>
<td style="text-align:center;">
0.195
</td>
<td style="text-align:center;">
5
</td>
<td style="text-align:center;">
LE
</td>
</tr>
</tbody>
</table>

In conclusion, I believe the composite growth index can align the
datasets and metrics within AcDC to best describe relative performance.
While the index is not without its flaws, the robustness will only
increase over time with the inclusion of more traits and datasets. By
using the temporal, experimental, and location filters, one can further
increase the robustness of the index. For instance, one can remove lab
or field data using the filters to achieve the filtering of the Lohr
(2017) calcification data.

# Standardized Metric

To compare these rankings to individually derived metrics, please check
out the other report.

</div>
