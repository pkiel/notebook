---
layout: post
title:  "Langdon OA Corals"
author: "Patrick M Kiel"
date: '2022-06-28'
categories: [research]
description: "Skeletal density analysis of Acropora cervicornis reared under ocean acidification and control experiment conditions."
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

<!-- The password box -->

<div id="credentials">

<input type="text" id="password" onkeydown="if (event.keyCode == 13) verify()" />
<br/>
<input id="button" type="button" value="Show Content" onclick="verify()" />

</div>

<!-- The content we want to show after password -->

<div id="HIDDENDIV" class="hidden" markdown="1">

# Overview

Here, I analyze the 11 coral skeletons grown under OA and ambient
conditions. I first investigate the vertical extension and calcification
data collected by the Langdon Lab, and then I look at the response of
skeletal density to OA treatment. I further compare analyses at
different thresholding, different scales of segmentation, and the
different metrics I could standardize densities to facilitate “apples to
apples” comparisons.

To remove genotype-specific variability from the analysis, a subset of 8
genetically distinct corals is selected with 4 corals each in the
acidified group and the control group. The remaining 3 corals, all of
genotype ‘P-Lirman’ and in the control group, are then compared to the
other control corals to piece apart genotypic influence on skeletal bulk
densities.

# Linear Growth Analysis

![](/notebook/images/LangdonCorals/unnamed-chunk-3-1.png)<!-- -->![](/notebook/images/LangdonCorals/unnamed-chunk-3-2.png)<!-- -->![](/notebook/images/LangdonCorals/unnamed-chunk-3-3.png)<!-- -->![](/notebook/images/LangdonCorals/unnamed-chunk-3-4.png)<!-- -->![](/notebook/images/LangdonCorals/unnamed-chunk-3-5.png)<!-- -->

## Statistical Testing

#### Growth

![](/notebook/images/LangdonCorals/unnamed-chunk-4-1.png)<!-- -->

    ## # A tibble: 2 x 4
    ##   treatment variable statistic     p
    ##   <chr>     <chr>        <dbl> <dbl>
    ## 1 HCO2      growth       0.998 0.995
    ## 2 LCO2      growth       0.980 0.902

    ## # A tibble: 1 x 5
    ##     df1   df2 statistic     p variable
    ##   <int> <int>     <dbl> <dbl> <chr>   
    ## 1     1     6      1.32 0.294 growth

<table class=" lightable-classic" style="font-family: &quot;Arial Narrow&quot;, &quot;Source Sans Pro&quot;, sans-serif; margin-left: auto; margin-right: auto;">
<caption>
T-Test Results of Vertical Extension
</caption>
<thead>
<tr>
<th style="text-align:center;font-weight: bold;">
.y.
</th>
<th style="text-align:center;font-weight: bold;">
group1
</th>
<th style="text-align:center;font-weight: bold;">
group2
</th>
<th style="text-align:center;font-weight: bold;">
n1
</th>
<th style="text-align:center;font-weight: bold;">
n2
</th>
<th style="text-align:center;font-weight: bold;">
statistic
</th>
<th style="text-align:center;font-weight: bold;">
df
</th>
<th style="text-align:center;font-weight: bold;">
p
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:center;">
growth
</td>
<td style="text-align:center;">
HCO2
</td>
<td style="text-align:center;">
LCO2
</td>
<td style="text-align:center;">
4
</td>
<td style="text-align:center;">
4
</td>
<td style="text-align:center;">
2.083
</td>
<td style="text-align:center;">
6
</td>
<td style="text-align:center;">
0.082
</td>
</tr>
</tbody>
</table>
<table class=" lightable-classic" style="font-family: &quot;Arial Narrow&quot;, &quot;Source Sans Pro&quot;, sans-serif; margin-left: auto; margin-right: auto;">
<caption>
Effect Size Results of Vertical Extension
</caption>
<thead>
<tr>
<th style="text-align:center;font-weight: bold;">
.y.
</th>
<th style="text-align:center;font-weight: bold;">
group1
</th>
<th style="text-align:center;font-weight: bold;">
group2
</th>
<th style="text-align:center;font-weight: bold;">
effsize
</th>
<th style="text-align:center;font-weight: bold;">
n1
</th>
<th style="text-align:center;font-weight: bold;">
n2
</th>
<th style="text-align:center;font-weight: bold;">
magnitude
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:center;">
growth
</td>
<td style="text-align:center;">
HCO2
</td>
<td style="text-align:center;">
LCO2
</td>
<td style="text-align:center;">
1.473
</td>
<td style="text-align:center;">
4
</td>
<td style="text-align:center;">
4
</td>
<td style="text-align:center;">
large
</td>
</tr>
</tbody>
</table>

The mean growth in the HCO2 group was 35.43 mm (SD = 9.77mm), whereas
the mean in LCO2 group was 23.69mm (SD = 5.63mm). A Student’s
two-samples t-test showed that the difference was **not** statistically
significant, t(6) = 2.083, p &gt; 0.05, d = 1.473. Due to the small
sample size, a type 2 error might be happening where we are accepting
the null hypothesis. Further, the different number of days and times of
the year when corals were observed obfuscates any conclusions.

#### Productivity

Using the productivity (growth standardized to initial size) metric from
Lirman *et al.* 2014.
![](/notebook/images/LangdonCorals/unnamed-chunk-5-1.png)<!-- -->

    ## # A tibble: 2 x 4
    ##   treatment variable     statistic     p
    ##   <chr>     <chr>            <dbl> <dbl>
    ## 1 HCO2      productivity     0.962 0.794
    ## 2 LCO2      productivity     0.978 0.890

    ## # A tibble: 1 x 5
    ##     df1   df2 statistic     p variable    
    ##   <int> <int>     <dbl> <dbl> <chr>       
    ## 1     1     6   0.00748 0.934 productivity

<table class=" lightable-classic" style="font-family: &quot;Arial Narrow&quot;, &quot;Source Sans Pro&quot;, sans-serif; margin-left: auto; margin-right: auto;">
<caption>
T-Test Results of Vertical Extension
</caption>
<thead>
<tr>
<th style="text-align:center;font-weight: bold;">
.y.
</th>
<th style="text-align:center;font-weight: bold;">
group1
</th>
<th style="text-align:center;font-weight: bold;">
group2
</th>
<th style="text-align:center;font-weight: bold;">
n1
</th>
<th style="text-align:center;font-weight: bold;">
n2
</th>
<th style="text-align:center;font-weight: bold;">
statistic
</th>
<th style="text-align:center;font-weight: bold;">
df
</th>
<th style="text-align:center;font-weight: bold;">
p
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:center;">
prod
</td>
<td style="text-align:center;">
HCO2
</td>
<td style="text-align:center;">
LCO2
</td>
<td style="text-align:center;">
4
</td>
<td style="text-align:center;">
4
</td>
<td style="text-align:center;">
-1.125
</td>
<td style="text-align:center;">
6
</td>
<td style="text-align:center;">
0.304
</td>
</tr>
</tbody>
</table>
<table class=" lightable-classic" style="font-family: &quot;Arial Narrow&quot;, &quot;Source Sans Pro&quot;, sans-serif; margin-left: auto; margin-right: auto;">
<caption>
Effect Size Results of Vertical Extension
</caption>
<thead>
<tr>
<th style="text-align:center;font-weight: bold;">
.y.
</th>
<th style="text-align:center;font-weight: bold;">
group1
</th>
<th style="text-align:center;font-weight: bold;">
group2
</th>
<th style="text-align:center;font-weight: bold;">
effsize
</th>
<th style="text-align:center;font-weight: bold;">
n1
</th>
<th style="text-align:center;font-weight: bold;">
n2
</th>
<th style="text-align:center;font-weight: bold;">
magnitude
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:center;">
prod
</td>
<td style="text-align:center;">
HCO2
</td>
<td style="text-align:center;">
LCO2
</td>
<td style="text-align:center;">
-0.796
</td>
<td style="text-align:center;">
4
</td>
<td style="text-align:center;">
4
</td>
<td style="text-align:center;">
moderate
</td>
</tr>
</tbody>
</table>

The mean productivity in the HCO2 group was 0.04 mm (SD = 0.01mm),
whereas the mean in LCO2 group was 0.05mm (SD = 0.01mm). A Student’s
two-samples t-test showed that the difference was **not** statistically
significant, t(6) = -1.125, p &gt; 0.05, d = -0.796.

#### Number of Days

<table class=" lightable-classic" style="font-family: &quot;Arial Narrow&quot;, &quot;Source Sans Pro&quot;, sans-serif; margin-left: auto; margin-right: auto;">
<caption>
T-Test Results of Vertical Extension
</caption>
<thead>
<tr>
<th style="text-align:center;font-weight: bold;">
.y.
</th>
<th style="text-align:center;font-weight: bold;">
group1
</th>
<th style="text-align:center;font-weight: bold;">
group2
</th>
<th style="text-align:center;font-weight: bold;">
n1
</th>
<th style="text-align:center;font-weight: bold;">
n2
</th>
<th style="text-align:center;font-weight: bold;">
statistic
</th>
<th style="text-align:center;font-weight: bold;">
df
</th>
<th style="text-align:center;font-weight: bold;">
p
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:center;">
days
</td>
<td style="text-align:center;">
HCO2
</td>
<td style="text-align:center;">
LCO2
</td>
<td style="text-align:center;">
4
</td>
<td style="text-align:center;">
4
</td>
<td style="text-align:center;">
4.154
</td>
<td style="text-align:center;">
3.905
</td>
<td style="text-align:center;">
0.015
</td>
</tr>
</tbody>
</table>
<table class=" lightable-classic" style="font-family: &quot;Arial Narrow&quot;, &quot;Source Sans Pro&quot;, sans-serif; margin-left: auto; margin-right: auto;">
<caption>
Effect Size Results of Vertical Extension
</caption>
<thead>
<tr>
<th style="text-align:center;font-weight: bold;">
.y.
</th>
<th style="text-align:center;font-weight: bold;">
group1
</th>
<th style="text-align:center;font-weight: bold;">
group2
</th>
<th style="text-align:center;font-weight: bold;">
effsize
</th>
<th style="text-align:center;font-weight: bold;">
n1
</th>
<th style="text-align:center;font-weight: bold;">
n2
</th>
<th style="text-align:center;font-weight: bold;">
magnitude
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:center;">
days
</td>
<td style="text-align:center;">
HCO2
</td>
<td style="text-align:center;">
LCO2
</td>
<td style="text-align:center;">
2.938
</td>
<td style="text-align:center;">
4
</td>
<td style="text-align:center;">
4
</td>
<td style="text-align:center;">
large
</td>
</tr>
</tbody>
</table>

The mean days in experiment of the HCO2 group was 195 days (SD = 45.7),
whereas the mean in LCO2 group was 93 days (SD = NA). A Welch’s
two-samples t-test showed that the difference was statistically
significant, t(3.91) = 4.15, p &lt; 0.05, d = 2.938.

Due to the different number of days, I am trimming the observation of
the OA corals to approximately equal the number of days of the control
corals.

![](/notebook/images/LangdonCorals/unnamed-chunk-7-1.png)<!-- -->![](/notebook/images/LangdonCorals/unnamed-chunk-7-2.png)<!-- -->

# Calcification Analysis

Calcification rates were determined by weekly measurements of buoyant
weight. Mass gained during the experiment was standardized to initial
mass.

![](/notebook/images/LangdonCorals/unnamed-chunk-8-1.png)<!-- -->![](/notebook/images/LangdonCorals/unnamed-chunk-8-2.png)<!-- -->

The data becomes a little messy between December and February near the
end of the experiment with most of this mess centered around January
10th, 2022. Further, the different number of days and times of year as
seen in linear extension data is present here and continues to muddle
conclusions. Regardless, calcification is net positive by taking the
difference in mass from the final and initial measurements.

![](/notebook/images/LangdonCorals/unnamed-chunk-9-1.png)<!-- -->![](/notebook/images/LangdonCorals/unnamed-chunk-9-2.png)<!-- -->

Due to the different number of days, I am trimming the observation of
the OA corals to approximately equal the number of days of the control
corals.

![](/notebook/images/LangdonCorals/unnamed-chunk-10-1.png)<!-- -->![](/notebook/images/LangdonCorals/unnamed-chunk-10-2.png)<!-- -->

## Statistical Testing

![](/notebook/images/LangdonCorals/unnamed-chunk-11-1.png)<!-- -->

    ## # A tibble: 2 x 4
    ##   treatment variable statistic     p
    ##   <chr>     <chr>        <dbl> <dbl>
    ## 1 HCO2      G            0.909 0.479
    ## 2 LCO2      G            0.962 0.792

    ## # A tibble: 1 x 5
    ##     df1   df2 statistic     p variable
    ##   <int> <int>     <dbl> <dbl> <chr>   
    ## 1     1     6     0.290 0.610 G

<table class=" lightable-classic" style="font-family: &quot;Arial Narrow&quot;, &quot;Source Sans Pro&quot;, sans-serif; margin-left: auto; margin-right: auto;">
<caption>
T-Test Results of Vertical Extension
</caption>
<thead>
<tr>
<th style="text-align:center;font-weight: bold;">
.y.
</th>
<th style="text-align:center;font-weight: bold;">
group1
</th>
<th style="text-align:center;font-weight: bold;">
group2
</th>
<th style="text-align:center;font-weight: bold;">
n1
</th>
<th style="text-align:center;font-weight: bold;">
n2
</th>
<th style="text-align:center;font-weight: bold;">
statistic
</th>
<th style="text-align:center;font-weight: bold;">
df
</th>
<th style="text-align:center;font-weight: bold;">
p
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:center;">
G
</td>
<td style="text-align:center;">
HCO2
</td>
<td style="text-align:center;">
LCO2
</td>
<td style="text-align:center;">
4
</td>
<td style="text-align:center;">
4
</td>
<td style="text-align:center;">
-3.79
</td>
<td style="text-align:center;">
6
</td>
<td style="text-align:center;">
0.009
</td>
</tr>
</tbody>
</table>
<table class=" lightable-classic" style="font-family: &quot;Arial Narrow&quot;, &quot;Source Sans Pro&quot;, sans-serif; margin-left: auto; margin-right: auto;">
<caption>
Effect Size Results of Vertical Extension
</caption>
<thead>
<tr>
<th style="text-align:center;font-weight: bold;">
.y.
</th>
<th style="text-align:center;font-weight: bold;">
group1
</th>
<th style="text-align:center;font-weight: bold;">
group2
</th>
<th style="text-align:center;font-weight: bold;">
effsize
</th>
<th style="text-align:center;font-weight: bold;">
n1
</th>
<th style="text-align:center;font-weight: bold;">
n2
</th>
<th style="text-align:center;font-weight: bold;">
magnitude
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:center;">
G
</td>
<td style="text-align:center;">
HCO2
</td>
<td style="text-align:center;">
LCO2
</td>
<td style="text-align:center;">
-2.68
</td>
<td style="text-align:center;">
4
</td>
<td style="text-align:center;">
4
</td>
<td style="text-align:center;">
large
</td>
</tr>
</tbody>
</table>

The mean calcification rate in the HCO2 group was 4.85 mg/g/day (SD =
0.77), whereas the mean in LCO2 group was 7.42 mg/g/day (SD = 1.12). A
Student’s two-samples t-test showed that the difference was
statistically significant, t(6) = -3.79, p &lt; 0.01, d = -2.68.

![](/notebook/images/LangdonCorals/unnamed-chunk-12-1.png)<!-- -->

    ## # A tibble: 2 x 4
    ##   treatment variable statistic     p
    ##   <chr>     <chr>        <dbl> <dbl>
    ## 1 HCO2      days         0.917 0.521
    ## 2 LCO2      days         0.810 0.121

    ## # A tibble: 1 x 5
    ##     df1   df2 statistic     p variable
    ##   <int> <int>     <dbl> <dbl> <chr>   
    ## 1     1     6     0.962 0.365 days

<table class=" lightable-classic" style="font-family: &quot;Arial Narrow&quot;, &quot;Source Sans Pro&quot;, sans-serif; margin-left: auto; margin-right: auto;">
<caption>
T-Test Results of Vertical Extension
</caption>
<thead>
<tr>
<th style="text-align:center;font-weight: bold;">
.y.
</th>
<th style="text-align:center;font-weight: bold;">
group1
</th>
<th style="text-align:center;font-weight: bold;">
group2
</th>
<th style="text-align:center;font-weight: bold;">
n1
</th>
<th style="text-align:center;font-weight: bold;">
n2
</th>
<th style="text-align:center;font-weight: bold;">
statistic
</th>
<th style="text-align:center;font-weight: bold;">
df
</th>
<th style="text-align:center;font-weight: bold;">
p
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:center;">
days
</td>
<td style="text-align:center;">
HCO2
</td>
<td style="text-align:center;">
LCO2
</td>
<td style="text-align:center;">
4
</td>
<td style="text-align:center;">
4
</td>
<td style="text-align:center;">
3.651
</td>
<td style="text-align:center;">
6
</td>
<td style="text-align:center;">
0.011
</td>
</tr>
</tbody>
</table>
<table class=" lightable-classic" style="font-family: &quot;Arial Narrow&quot;, &quot;Source Sans Pro&quot;, sans-serif; margin-left: auto; margin-right: auto;">
<caption>
Effect Size Results of Vertical Extension
</caption>
<thead>
<tr>
<th style="text-align:center;font-weight: bold;">
.y.
</th>
<th style="text-align:center;font-weight: bold;">
group1
</th>
<th style="text-align:center;font-weight: bold;">
group2
</th>
<th style="text-align:center;font-weight: bold;">
effsize
</th>
<th style="text-align:center;font-weight: bold;">
n1
</th>
<th style="text-align:center;font-weight: bold;">
n2
</th>
<th style="text-align:center;font-weight: bold;">
magnitude
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:center;">
days
</td>
<td style="text-align:center;">
HCO2
</td>
<td style="text-align:center;">
LCO2
</td>
<td style="text-align:center;">
2.582
</td>
<td style="text-align:center;">
4
</td>
<td style="text-align:center;">
4
</td>
<td style="text-align:center;">
large
</td>
</tr>
</tbody>
</table>

The mean days in experiment of the HCO2 group was 242.5 days (SD =
74.44), whereas the mean in LCO2 group was 96.75 days (SD = 28.85). A
Student’s two-samples t-test showed that the difference was
statistically significant, t(6) = 3.65, p &lt; 0.05, d = 2.582.

# Growth Data Summarized

In summary, standardized vertical extension data was not signifcantly
different among treatment groups. However, calcification rates were
significantly different, with acidified groups having significantly less
calcification rates.

Most importantly, the length of observation was significantly different
with control corals observed in the experiment significantly less than
acidified treatment corals. This is critical for phenotypically plastic
corals such as *A. cervicornis* (Kuffner *et al.* 2017), where the
corals’ morphology and bulk density will be shaped by its environment
over short amounts of time. Thus, the longer exposure of corals in lab
conditions will artificially increase its bulk density compared to
corals held in the lab over much shorter time frames. This is because
nursery grown corals grow in the midwater column and are highly porous
compared to corals grown in a lab which are affixed to a tag and held
stationary in an aquarium. Over time, the density will increase, and the
amount of this density increase is directly proportional to time in the
lab and any experimental conditions (acidified treatment). Since there
is a difference in these two variables (length of time and
control/treatment), we are unable to parse apart the relative
significance of each of these factors, particularly with the small
sample size present.

# Skeletal Density Analysis

![Segmentation of
CT-Scan](/notebook/images/LangdonCorals/ctSegmentation.jpg)

Skeletal density of the corals was measured by CT scanning with a
Siemens Somatom Volume Zoom CT scanner at a resolution of
0.1mm scan<sup> − 1</sup>. The three dimensional reconstruction was
digitally bisected using the software Amira (ThermoFischer Scientific)
at the distance of new growth from the most distal slice of the apical
branch. Materials were first assigned ‘Old Growth’ (red) and ‘New
Growth’ (blue), where ‘Old Growth’ denotes the portion of the skeleton
that was present at the beginning of the experiment and ‘New Growth’
denotes the portion of the skeleton that is grown under treatment
conditions. The ‘New Growth’ section was then further segmented into
‘apical’ (purple) and ‘distal’ (green), where ‘apical’ and ‘distal’
denote 7.5mm sections of new growth. These standardized subsections
permit additional analyses of the skeletal densities. Finally, ‘Old
Growth’ and ‘New Growth’ were combined to do bulk scale analyses on the
complete coral.

Because coral growth has vertical and lateral components, the ‘Old
Growth’ material contains the initial skeleton and laterally grown
calcium carbonate. However, we are unable to accurately parse apart
these two growth forms in this material. Thus, ‘New Growth’, or the
portion of the skeleton that grew above the maximum height of the
initial skeleton, is the only section of the coral we can accurately
analyze for treatment effect on skeletal density.

Bisected Slice = Distal Slice − \[(*H*<sub>*f*</sub> − *H*<sub>*i*</sub>) \* 10\]
where *H* is measured in mm, and slices represent 0.1mm of the
skeleton’s reconstruction.

Then, holes were filled of the reconstruction to enclose the volume of
the skeleton to be comparable with methods that determine skeletal
density using the buoyant weight technique of wax sealed coral
fragments. Finally, the mean brightness of the entire volume of new
growth was converted to real-world skeletal density using aragonite
density phantoms.

Two different material thresholds were selected for further comparison.
The lab standard is to use -250, but I additionally tested -800 to
prevent the clipping of low brightness data that may occur near the
columella, apical tip, and the edge of the thecas. The result is the
increased volume of the reconstruction and a slight increase in the
brightness cumulative sum count, resulting in a overall reduction in
average determined density. I compare the different values of the new
growth at each of these thresholds in more depth below.

## Old Growth v New Growth

<table class=" lightable-classic" style="font-family: &quot;Arial Narrow&quot;, &quot;Source Sans Pro&quot;, sans-serif; margin-left: auto; margin-right: auto;">
<caption>
Density of bisected coral skeletons in g/cm^3, analyzed at standard -250
thresholding
</caption>
<thead>
<tr>
<th style="text-align:center;font-weight: bold;">
coral
</th>
<th style="text-align:center;font-weight: bold;">
treatment
</th>
<th style="text-align:center;font-weight: bold;">
Coral
</th>
<th style="text-align:center;font-weight: bold;">
NewGrowth
</th>
<th style="text-align:center;font-weight: bold;">
OldGrowth
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:center;">
108b
</td>
<td style="text-align:center;">
HCO2
</td>
<td style="text-align:center;">
1.941
</td>
<td style="text-align:center;">
1.741
</td>
<td style="text-align:center;">
2.023
</td>
</tr>
<tr>
<td style="text-align:center;">
157
</td>
<td style="text-align:center;">
HCO2
</td>
<td style="text-align:center;">
1.789
</td>
<td style="text-align:center;">
1.700
</td>
<td style="text-align:center;">
1.866
</td>
</tr>
<tr>
<td style="text-align:center;">
187b
</td>
<td style="text-align:center;">
HCO2
</td>
<td style="text-align:center;">
1.661
</td>
<td style="text-align:center;">
1.432
</td>
<td style="text-align:center;">
1.755
</td>
</tr>
<tr>
<td style="text-align:center;">
271b
</td>
<td style="text-align:center;">
LCO2
</td>
<td style="text-align:center;">
1.501
</td>
<td style="text-align:center;">
1.168
</td>
<td style="text-align:center;">
1.590
</td>
</tr>
<tr>
<td style="text-align:center;">
433b
</td>
<td style="text-align:center;">
HCO2
</td>
<td style="text-align:center;">
2.015
</td>
<td style="text-align:center;">
1.537
</td>
<td style="text-align:center;">
2.087
</td>
</tr>
<tr>
<td style="text-align:center;">
439b
</td>
<td style="text-align:center;">
LCO2
</td>
<td style="text-align:center;">
1.779
</td>
<td style="text-align:center;">
1.520
</td>
<td style="text-align:center;">
1.818
</td>
</tr>
<tr>
<td style="text-align:center;">
456b
</td>
<td style="text-align:center;">
LCO2
</td>
<td style="text-align:center;">
1.632
</td>
<td style="text-align:center;">
1.457
</td>
<td style="text-align:center;">
1.672
</td>
</tr>
<tr>
<td style="text-align:center;">
496
</td>
<td style="text-align:center;">
LCO2
</td>
<td style="text-align:center;">
1.617
</td>
<td style="text-align:center;">
1.362
</td>
<td style="text-align:center;">
1.656
</td>
</tr>
</tbody>
</table>

![](/notebook/images/LangdonCorals/unnamed-chunk-13-1.png)<!-- -->

Across all materials, corals grown under LCO2 (control) are less dense
than treatment corals. Further, New Growth is less dense than Old Growth
which makes sense as the Old Growth contains the initial skeleton
present at the beginning of the experiment with the addition of lateral
thickening. Further, New Growth contains the fast growing apical branch
which is less dense than the basal portion of the colony.

The decreased density in control corals compared to acidified corals is
surprising, and does not agree with previous OA literature (Tambutte *et
al.* 2015; Mollica *et al.* 2018). One interpretation is that the
treatment group had significant effect on both the vertical extension
and the lateral thickening of coral growth, and thus treatment effect is
apparent in both the ‘New Growth’ and ‘Old Growth’ materials. As
mentioned before, this was to be expected, however we cannot parse apart
skeleton grown under treatment conditions in the Old Growth section.
**More likely, the differences in density is a factor of the amount of
time held in the experiment.**

### Statistical Testing

![](/notebook/images/LangdonCorals/unnamed-chunk-14-1.png)<!-- -->

    ## # A tibble: 6 x 5
    ##   treatment material  variable statistic     p
    ##   <chr>     <chr>     <chr>        <dbl> <dbl>
    ## 1 HCO2      Coral     density      0.963 0.796
    ## 2 HCO2      NewGrowth density      0.923 0.555
    ## 3 HCO2      OldGrowth density      0.950 0.719
    ## 4 LCO2      Coral     density      0.960 0.782
    ## 5 LCO2      NewGrowth density      0.939 0.651
    ## 6 LCO2      OldGrowth density      0.916 0.512

    ## # A tibble: 3 x 6
    ##   material    df1   df2 statistic     p variable
    ##   <chr>     <int> <int>     <dbl> <dbl> <chr>   
    ## 1 Coral         1     6    1.16   0.323 density 
    ## 2 NewGrowth     1     6    0.0137 0.911 density 
    ## 3 OldGrowth     1     6    1.95   0.212 density

<table class=" lightable-classic" style="font-family: &quot;Arial Narrow&quot;, &quot;Source Sans Pro&quot;, sans-serif; margin-left: auto; margin-right: auto;">
<caption>
Student’s T-Test Results of Standardized Density of Both Materials
</caption>
<thead>
<tr>
<th style="text-align:center;font-weight: bold;">
material
</th>
<th style="text-align:center;font-weight: bold;">
.y.
</th>
<th style="text-align:center;font-weight: bold;">
group1
</th>
<th style="text-align:center;font-weight: bold;">
group2
</th>
<th style="text-align:center;font-weight: bold;">
n1
</th>
<th style="text-align:center;font-weight: bold;">
n2
</th>
<th style="text-align:center;font-weight: bold;">
statistic
</th>
<th style="text-align:center;font-weight: bold;">
df
</th>
<th style="text-align:center;font-weight: bold;">
p
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:center;">
Coral
</td>
<td style="text-align:center;">
density
</td>
<td style="text-align:center;">
HCO2
</td>
<td style="text-align:center;">
LCO2
</td>
<td style="text-align:center;">
4
</td>
<td style="text-align:center;">
4
</td>
<td style="text-align:center;">
2.248
</td>
<td style="text-align:center;">
6
</td>
<td style="text-align:center;">
0.066
</td>
</tr>
<tr>
<td style="text-align:center;">
NewGrowth
</td>
<td style="text-align:center;">
density
</td>
<td style="text-align:center;">
HCO2
</td>
<td style="text-align:center;">
LCO2
</td>
<td style="text-align:center;">
4
</td>
<td style="text-align:center;">
4
</td>
<td style="text-align:center;">
2.146
</td>
<td style="text-align:center;">
6
</td>
<td style="text-align:center;">
0.076
</td>
</tr>
<tr>
<td style="text-align:center;">
OldGrowth
</td>
<td style="text-align:center;">
density
</td>
<td style="text-align:center;">
HCO2
</td>
<td style="text-align:center;">
LCO2
</td>
<td style="text-align:center;">
4
</td>
<td style="text-align:center;">
4
</td>
<td style="text-align:center;">
2.783
</td>
<td style="text-align:center;">
6
</td>
<td style="text-align:center;">
0.032
</td>
</tr>
</tbody>
</table>
<table class=" lightable-classic" style="font-family: &quot;Arial Narrow&quot;, &quot;Source Sans Pro&quot;, sans-serif; margin-left: auto; margin-right: auto;">
<caption>
Effect Size Results of Standardized Density of Both Materials
</caption>
<thead>
<tr>
<th style="text-align:center;font-weight: bold;">
.y.
</th>
<th style="text-align:center;font-weight: bold;">
group1
</th>
<th style="text-align:center;font-weight: bold;">
group2
</th>
<th style="text-align:center;font-weight: bold;">
effsize
</th>
<th style="text-align:center;font-weight: bold;">
material
</th>
<th style="text-align:center;font-weight: bold;">
n1
</th>
<th style="text-align:center;font-weight: bold;">
n2
</th>
<th style="text-align:center;font-weight: bold;">
magnitude
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:center;">
density
</td>
<td style="text-align:center;">
HCO2
</td>
<td style="text-align:center;">
LCO2
</td>
<td style="text-align:center;">
1.589
</td>
<td style="text-align:center;">
Coral
</td>
<td style="text-align:center;">
4
</td>
<td style="text-align:center;">
4
</td>
<td style="text-align:center;">
large
</td>
</tr>
<tr>
<td style="text-align:center;">
density
</td>
<td style="text-align:center;">
HCO2
</td>
<td style="text-align:center;">
LCO2
</td>
<td style="text-align:center;">
1.518
</td>
<td style="text-align:center;">
NewGrowth
</td>
<td style="text-align:center;">
4
</td>
<td style="text-align:center;">
4
</td>
<td style="text-align:center;">
large
</td>
</tr>
<tr>
<td style="text-align:center;">
density
</td>
<td style="text-align:center;">
HCO2
</td>
<td style="text-align:center;">
LCO2
</td>
<td style="text-align:center;">
1.968
</td>
<td style="text-align:center;">
OldGrowth
</td>
<td style="text-align:center;">
4
</td>
<td style="text-align:center;">
4
</td>
<td style="text-align:center;">
large
</td>
</tr>
</tbody>
</table>

A Student’s two-samples t-test only showed statistically significant
differences for the OldGrowth material, t(6) = 2.783, p &lt; 0.05, d =
1.968. The New Growth material and the complete coral was just outside
our significance threshold. There exist three interpretations: 1) The
skeletons were significantly different prior to the experiment and the
treatment did not alter the densities, or 2) the control treatment
precluded the lateral thickening of the corals while maintaining the
linear extension as evidenced by the similiar producitivty values and
densities of new growth, yet old growth (existing + latral thickening)
was diminished. This interpretation would be characteristic of growth
patterns seen in the literature for acidified groups, and not ambient
control groups. Or 3) the increase in density (although only significant
at the old growth) is a factor of the length of time in the treatment
with the theory explained above. Again, it is important to place these
interpretations alongside the small samples size.

## Thresholding Differences

As mentioned in the overview, the lab standard for analysis of coral CT
Scans is to set the lower threshold limit at -250. This clips some
brightness data and shrinks the calculated volume of the reconstruction
with the benefit of definitively selecting coral material only and not
air or other non-coral material. Since we are exploring low density
growth patterns in a controlled experiment, I sought to forgoe the
benefits of the conservative thresholding and employed a liberal
thresholding of -800.

Here, I am comparing the different determinations of the two settings.
In the image below you can see two identical slices at the different
thresholding limits. It is barely noticeable at this scale to the naked
eye, but there is slightly more material included in the -800
thresholding with the width of the columella being less than the width
of the columella in the -250. Thus, the increased thresholding permits
the region of interest (skeletal material) to penetrate into this low
density portion of the skeleton.

![CT-Scan Analysis Threshold
Compare](/notebook/images/LangdonCorals/thresholdCompare.jpg)

<table class=" lightable-classic" style="font-family: &quot;Arial Narrow&quot;, &quot;Source Sans Pro&quot;, sans-serif; margin-left: auto; margin-right: auto;">
<caption>
Average % Differences between -800 and -250 Thresholding
</caption>
<thead>
<tr>
<th style="text-align:center;font-weight: bold;">
metric
</th>
<th style="text-align:center;font-weight: bold;">
mean
</th>
<th style="text-align:center;font-weight: bold;">
sd
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:center;">
density
</td>
<td style="text-align:center;">
-14.0
</td>
<td style="text-align:center;">
5.0
</td>
</tr>
<tr>
<td style="text-align:center;">
volume
</td>
<td style="text-align:center;">
17.2
</td>
<td style="text-align:center;">
7.1
</td>
</tr>
</tbody>
</table>

On average, the -800 thresholded reconstruction has a volume 17.2%
greater than the -250 reconstruction by including more low density
material, resulting in an average determined density 14% less than the
-250 reconstruction. This lines up well with our theory of segmentation.
Certainly, a -250 reconstruction should not be compared to a -800
reconstruction, but the variability between the two is fairly uniform
among the group.

With that in mind, I will proceed with the -800 reconstruction and
subseciton out materials in the New Growth material. These densities
will be differen than the New Growth shown above and will only be
compared to other -800 reconstructions.

## Subsectioning New Growth

![](/notebook/images/LangdonCorals/unnamed-chunk-16-1.png)<!-- -->

### Statistical Testing

![](/notebook/images/LangdonCorals/unnamed-chunk-17-1.png)<!-- -->

    ## # A tibble: 8 x 5
    ##   treatment material  variable statistic     p
    ##   <chr>     <fct>     <chr>        <dbl> <dbl>
    ## 1 HCO2      NewGrowth density      0.881 0.343
    ## 2 HCO2      apical    density      0.959 0.775
    ## 3 HCO2      remainder density      0.879 0.333
    ## 4 HCO2      distal    density      0.897 0.415
    ## 5 LCO2      NewGrowth density      0.982 0.911
    ## 6 LCO2      apical    density      0.864 0.273
    ## 7 LCO2      remainder density      0.841 0.198
    ## 8 LCO2      distal    density      0.963 0.800

    ## # A tibble: 4 x 6
    ##   material    df1   df2 statistic      p variable
    ##   <fct>     <int> <int>     <dbl>  <dbl> <chr>   
    ## 1 NewGrowth     1     6      4.81 0.0708 density 
    ## 2 apical        1     6      3.93 0.0948 density 
    ## 3 remainder     1     6      7.54 0.0335 density 
    ## 4 distal        1     6     12.3  0.0127 density

<table class=" lightable-classic" style="font-family: &quot;Arial Narrow&quot;, &quot;Source Sans Pro&quot;, sans-serif; margin-left: auto; margin-right: auto;">
<caption>
Student’s T-Test Results of Standardized Density of Both Materials
</caption>
<thead>
<tr>
<th style="text-align:center;font-weight: bold;">
material
</th>
<th style="text-align:center;font-weight: bold;">
.y.
</th>
<th style="text-align:center;font-weight: bold;">
group1
</th>
<th style="text-align:center;font-weight: bold;">
group2
</th>
<th style="text-align:center;font-weight: bold;">
n1
</th>
<th style="text-align:center;font-weight: bold;">
n2
</th>
<th style="text-align:center;font-weight: bold;">
statistic
</th>
<th style="text-align:center;font-weight: bold;">
df
</th>
<th style="text-align:center;font-weight: bold;">
p
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:center;">
NewGrowth
</td>
<td style="text-align:center;">
density
</td>
<td style="text-align:center;">
HCO2
</td>
<td style="text-align:center;">
LCO2
</td>
<td style="text-align:center;">
4
</td>
<td style="text-align:center;">
4
</td>
<td style="text-align:center;">
2.486
</td>
<td style="text-align:center;">
4.354
</td>
<td style="text-align:center;">
0.063
</td>
</tr>
<tr>
<td style="text-align:center;">
apical
</td>
<td style="text-align:center;">
density
</td>
<td style="text-align:center;">
HCO2
</td>
<td style="text-align:center;">
LCO2
</td>
<td style="text-align:center;">
4
</td>
<td style="text-align:center;">
4
</td>
<td style="text-align:center;">
1.087
</td>
<td style="text-align:center;">
4.614
</td>
<td style="text-align:center;">
0.330
</td>
</tr>
<tr>
<td style="text-align:center;">
remainder
</td>
<td style="text-align:center;">
density
</td>
<td style="text-align:center;">
HCO2
</td>
<td style="text-align:center;">
LCO2
</td>
<td style="text-align:center;">
4
</td>
<td style="text-align:center;">
4
</td>
<td style="text-align:center;">
2.608
</td>
<td style="text-align:center;">
3.988
</td>
<td style="text-align:center;">
0.060
</td>
</tr>
<tr>
<td style="text-align:center;">
distal
</td>
<td style="text-align:center;">
density
</td>
<td style="text-align:center;">
HCO2
</td>
<td style="text-align:center;">
LCO2
</td>
<td style="text-align:center;">
4
</td>
<td style="text-align:center;">
4
</td>
<td style="text-align:center;">
2.914
</td>
<td style="text-align:center;">
4.132
</td>
<td style="text-align:center;">
0.042
</td>
</tr>
</tbody>
</table>
<table class=" lightable-classic" style="font-family: &quot;Arial Narrow&quot;, &quot;Source Sans Pro&quot;, sans-serif; margin-left: auto; margin-right: auto;">
<caption>
Effect Size Results of Standardized Density of Both Materials
</caption>
<thead>
<tr>
<th style="text-align:center;font-weight: bold;">
.y.
</th>
<th style="text-align:center;font-weight: bold;">
group1
</th>
<th style="text-align:center;font-weight: bold;">
group2
</th>
<th style="text-align:center;font-weight: bold;">
effsize
</th>
<th style="text-align:center;font-weight: bold;">
material
</th>
<th style="text-align:center;font-weight: bold;">
n1
</th>
<th style="text-align:center;font-weight: bold;">
n2
</th>
<th style="text-align:center;font-weight: bold;">
magnitude
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:center;">
density
</td>
<td style="text-align:center;">
HCO2
</td>
<td style="text-align:center;">
LCO2
</td>
<td style="text-align:center;">
1.758
</td>
<td style="text-align:center;">
NewGrowth
</td>
<td style="text-align:center;">
4
</td>
<td style="text-align:center;">
4
</td>
<td style="text-align:center;">
large
</td>
</tr>
<tr>
<td style="text-align:center;">
density
</td>
<td style="text-align:center;">
HCO2
</td>
<td style="text-align:center;">
LCO2
</td>
<td style="text-align:center;">
0.769
</td>
<td style="text-align:center;">
apical
</td>
<td style="text-align:center;">
4
</td>
<td style="text-align:center;">
4
</td>
<td style="text-align:center;">
moderate
</td>
</tr>
<tr>
<td style="text-align:center;">
density
</td>
<td style="text-align:center;">
HCO2
</td>
<td style="text-align:center;">
LCO2
</td>
<td style="text-align:center;">
1.844
</td>
<td style="text-align:center;">
remainder
</td>
<td style="text-align:center;">
4
</td>
<td style="text-align:center;">
4
</td>
<td style="text-align:center;">
large
</td>
</tr>
<tr>
<td style="text-align:center;">
density
</td>
<td style="text-align:center;">
HCO2
</td>
<td style="text-align:center;">
LCO2
</td>
<td style="text-align:center;">
2.061
</td>
<td style="text-align:center;">
distal
</td>
<td style="text-align:center;">
4
</td>
<td style="text-align:center;">
4
</td>
<td style="text-align:center;">
large
</td>
</tr>
</tbody>
</table>

A Welch’s two-sample t-test only showed statistically significant
differences for the distal material, t(4.13) = 2.91, p &lt; 0.05, d =
2.061. The remainder material and the new growth material analyzed as a
whole was just outside our significance threshold, and the apical
matrial was highly variable and not significantly different, p &gt;
0.33. Thus, from the distal to apical regions of the new growth,
variability within treatment group increases and the ability to detect
treatment effect decreases. This falls in line with our understanding of
coral growth in the highly variable, fast growing apical tips. Further,
this closely aligns with the prior analysis of new growth v old growth,
where new growth was not signifcantly different between control and
treatment, but old growth was different between the groups. Finally, the
trend of denser skeletons in the control group compared to the treatment
group aligns with the previous analysis with the likely cause being the
amount of days grown in the lab.

## Estimating Mass Gain

Calcification can also be determined by multiplying the volume of the
new growth section by the average density of this material. We can
compare this calculated mass to to the buoyant weight data. We can
further see which thresholding has a better fit with the buoyant weight
data to add to our comparison of thesholding differnces.

![](/notebook/images/LangdonCorals/unnamed-chunk-18-1.png)<!-- -->

    ## 
    ## Call:
    ## lm(formula = calcMass ~ newMass, data = newMass)
    ## 
    ## Residuals:
    ##     Min      1Q  Median      3Q     Max 
    ## -0.6187 -0.3328 -0.1018  0.2494  1.0180 
    ## 
    ## Coefficients:
    ##             Estimate Std. Error t value Pr(>|t|)  
    ## (Intercept)   0.3837     0.3522   1.089   0.2943  
    ## newMass       0.3078     0.1332   2.312   0.0365 *
    ## ---
    ## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
    ## 
    ## Residual standard error: 0.4958 on 14 degrees of freedom
    ## Multiple R-squared:  0.2762, Adjusted R-squared:  0.2246 
    ## F-statistic: 5.344 on 1 and 14 DF,  p-value: 0.03653

![](/notebook/images/LangdonCorals/unnamed-chunk-18-2.png)<!-- -->

Multiplying ct scan density and volume underestimates the derived mass
gain as compared to buoyant weight data. To some extent, this was to be
expected. Calcification takes place not only in the new growth, but also
in the lateral thickening of the old growth section which was not
included in the CT Scan derived mass. Except for one data point which
nearly has a 1:1 relationship (85%), the other 7 corals have their
calculated mass gain at about 43% of mass gain as measured by buoyant
weight.

There was no observable difference in calculation of mass between the
250 and 800 thresholded reconstructions. Again, this was to be expected
as calculated gain in mass is the product of volume and density. The two
different reconstructions have nearly equal and opposite determinations
of each, balacing out the equation and resulting in nearly similar mass;
(vol<sub>250</sub> &lt; vol<sub>800</sub>, *ρ*<sub>250</sub> &gt; *ρ*<sub>800</sub>, mass<sub>250</sub> ≈ mass<sub>800</sub>,

## Standardization Metrics

### Number of Days in Treatment

Due to the different number of days in treatment and control groups, I
am tempted to standardize the density of the corals to its number of
days in treatment. This should standardize the number of days an
individual coral was able to fill in its skeleton in the laboratory at
its specified treatment.

There are multiple caveats: 1) we have already sectoned out the new
growth in the treatment, 2) units will be expressed in density/days
which is an arbitrary unit without a real-world meaning, and 3) the
range of the days are fairly large (&gt;150 days difference between
group means), and the data may just be incomparable.

![](/notebook/images/LangdonCorals/unnamed-chunk-19-1.png)<!-- -->![](/notebook/images/LangdonCorals/unnamed-chunk-19-2.png)<!-- -->

Nevertheless, here is the data standardized to the number of days in
treatment.

![](/notebook/images/LangdonCorals/unnamed-chunk-20-1.png)<!-- -->![](/notebook/images/LangdonCorals/unnamed-chunk-20-2.png)<!-- -->

Now, there are significant differences with LCO2 corals being denser
than OA corals. However, the differences across sectioned materials and
different thresholds is nearly uniform, suggesting that the driving
force is not the difference in densities of each material (as shown
above in the normal data and backed with theory), but rather the
standardizing metric. Furher, the differences reflect the boxplot above
showing the difference in number of days

I conclude that standardizing to the number of days in treatment is not
an appropriate metric.

### Initial Height of Coral

Just as we standardized total vertical extension to initial height of
the coral, we can standardize density of the coral to its initial
height. However, this shares many of the same caveats from above, namely
that density/height is an arbitrary, potentially meaningless unit.

![](/notebook/images/LangdonCorals/unnamed-chunk-21-1.png)<!-- -->![](/notebook/images/LangdonCorals/unnamed-chunk-21-2.png)<!-- -->![](/notebook/images/LangdonCorals/unnamed-chunk-21-3.png)<!-- -->![](/notebook/images/LangdonCorals/unnamed-chunk-21-4.png)<!-- -->

    ## # A tibble: 3 x 9
    ##   material  .y.     group1 group2    n1    n2 statistic    df     p
    ## * <chr>     <chr>   <chr>  <chr>  <int> <int>     <dbl> <dbl> <dbl>
    ## 1 Coral     density HCO2   LCO2       4     4      1.42     6 0.206
    ## 2 NewGrowth density HCO2   LCO2       4     4      1.25     6 0.257
    ## 3 OldGrowth density HCO2   LCO2       4     4      1.52     6 0.18

    ## # A tibble: 4 x 9
    ##   material  .y.     group1 group2    n1    n2 statistic    df     p
    ## * <fct>     <chr>   <chr>  <chr>  <int> <int>     <dbl> <dbl> <dbl>
    ## 1 NewGrowth density HCO2   LCO2       4     4     1.34      6 0.229
    ## 2 apical    density HCO2   LCO2       4     4     0.979     6 0.366
    ## 3 remainder density HCO2   LCO2       4     4     1.38      6 0.216
    ## 4 distal    density HCO2   LCO2       4     4     1.39      6 0.215

Here, we see the same initial pattern with OA corals generally more
dense than control corals. However, significant differences between any
material has been lost. HCO2 corals had more variable initial height but
the mean value did not differ significantly.

### Initial Mass of Coral

Same concept, but using initial mass to standardize just as we did for
calcification.

![](/notebook/images/LangdonCorals/unnamed-chunk-22-1.png)<!-- -->![](/notebook/images/LangdonCorals/unnamed-chunk-22-2.png)<!-- -->![](/notebook/images/LangdonCorals/unnamed-chunk-22-3.png)<!-- -->![](/notebook/images/LangdonCorals/unnamed-chunk-22-4.png)<!-- -->

    ## # A tibble: 3 x 9
    ##   material  .y.     group1 group2    n1    n2 statistic    df      p
    ## * <chr>     <chr>   <chr>  <chr>  <int> <int>     <dbl> <dbl>  <dbl>
    ## 1 Coral     density HCO2   LCO2       4     4      2.14     6 0.076 
    ## 2 NewGrowth density HCO2   LCO2       4     4      1.68     6 0.145 
    ## 3 OldGrowth density HCO2   LCO2       4     4      2.29     6 0.0622

    ## # A tibble: 4 x 9
    ##   material  .y.     group1 group2    n1    n2 statistic    df     p
    ## * <fct>     <chr>   <chr>  <chr>  <int> <int>     <dbl> <dbl> <dbl>
    ## 1 NewGrowth density HCO2   LCO2       4     4      1.73     6 0.134
    ## 2 apical    density HCO2   LCO2       4     4      1.22     6 0.267
    ## 3 remainder density HCO2   LCO2       4     4      1.74     6 0.132
    ## 4 distal    density HCO2   LCO2       4     4      1.81     6 0.12

Again, the same initial pattern with significant differences between any
material lost.

# Genotype Variability

Finally, it is important to compare the variability of the population to
the variability of a genoype within that population to begin to
understand genotype-specific sensitivities. Here, I compare 3 ramets of
P-Lirman grown under LCO2 conditions and compare it to all LCO2 corals

![](/notebook/images/LangdonCorals/unnamed-chunk-23-1.png)<!-- -->![](/notebook/images/LangdonCorals/unnamed-chunk-23-2.png)<!-- -->

    ## # A tibble: 3 x 6
    ## # Groups:   material [3]
    ##   material  threshold statistic p.value parameter method                        
    ##   <chr>         <dbl>     <dbl>   <dbl>     <dbl> <chr>                         
    ## 1 Coral           250      2.70   0.260         2 Bartlett test of homogeneity ~
    ## 2 NewGrowth       250      2.65   0.266         2 Bartlett test of homogeneity ~
    ## 3 OldGrowth       250      2.55   0.279         2 Bartlett test of homogeneity ~

![](/notebook/images/LangdonCorals/unnamed-chunk-23-3.png)<!-- -->

    ##   Tukey multiple comparisons of means
    ##     95% family-wise confidence level
    ## 
    ## Fit: aov(formula = density ~ genotype, data = .)
    ## 
    ## $genotype
    ##                                  diff          lwr        upr     p adj
    ## P-Lirman-Everything Else   0.25151849  0.040800773 0.46223621 0.0156768
    ## total pop-Everything Else  0.15266046 -0.008427085 0.31374800 0.0666405
    ## total pop-P-Lirman        -0.09885804 -0.278558712 0.08084264 0.3864274

From this data, there are significant differences of skeletal density
among the genotype P-Lirman as compared to the rest of the population
(p&lt;0.05). However, when grouped together, there is no difference of
P-Lirman (p=0.386). This could suggest that there is significant
genotypic variability, shown here with only 3 corals compared to the 8
other corals. Certainly, more analysis needs to be done.

</div>
