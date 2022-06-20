---
layout: post
title:  "Langdon OA Corals"
author: "Patrick M Kiel"
date: '2022-06-20'
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


<script type="text/javascript">
function verify() {
  if (document.getElementById('password').value === 'acidification') {
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
img {
    display: block;
    max-width: 50%;
    margin: 0 auto 1rem;
    border-radius: 5px;
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

Here, I analyze the 10 coral skeletons grown under OA and ambient
conditions. I investigate the response of skeletal density to OA
treatment and begin to look at genotype variability within the control
group.

# Linear Growth Analysis

![](/notebook/images/unnamed-chunk-1-1.png)<!-- -->![](/notebook/images/unnamed-chunk-1-2.png)<!-- -->![](/notebook/images/unnamed-chunk-1-3.png)<!-- -->

## Statistical Testing

![](/notebook/images/unnamed-chunk-2-1.png)<!-- -->

    ## # A tibble: 2 x 4
    ##   treatment variable statistic      p
    ##   <chr>     <chr>        <dbl>  <dbl>
    ## 1 HCO2      growth       0.998 0.995 
    ## 2 LCO2      growth       0.816 0.0818

    ## # A tibble: 1 x 4
    ##     df1   df2 statistic      p
    ##   <int> <int>     <dbl>  <dbl>
    ## 1     1     8      5.34 0.0496

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
6
</td>
<td style="text-align:center;">
2.629
</td>
<td style="text-align:center;">
3.382
</td>
<td style="text-align:center;">
0.069
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
1.832
</td>
<td style="text-align:center;">
4
</td>
<td style="text-align:center;">
6
</td>
<td style="text-align:center;">
large
</td>
</tr>
</tbody>
</table>

We cannot assume homogeneity of variance as p &lt; 0.05 for the Levene
Test (p=0.0496). So we’ll use the Welch’s T test.

The mean growth in the HCO2 group was 35.43 mm (SD = 9.77mm), whereas
the mean in LCO2 group was 22.2mm (SD = 3mm). A Welch’s two-samples
t-test showed that the difference was **not** statistically significant,
t(3.38) = 2.629, p &gt; 0.05, d = 1.832.

When this growth data is standardized to initial height (Lirman *et al.*
2014), there is definitely no observable differences (p&gt;0.7).

# Skeletal Density Analysis

![Segmentation of CT-Scan](/notebook/images/ctSegmentation.jpg)

Skeletal density of the corals was measured by CT scanning with a
Siemens Somatom Volume Zoom CT scanner at a resolution of
0.1mm scan<sup> − 1</sup>. The three dimensional reconstruction was
digitally bisected using the software Amira (ThermoFischer Scientific)
at the distance of new growth from the most distal slice of the apical
branch. Materials were assigned ‘Old Growth’ (red) and ‘New Growth’
(blue), where ‘Old Growth’ denotes the portion of the skeleton that was
present at the beginning of the experiment and ‘New Growth’ denotes the
portion of the skeleton that is grown under treatment conditions.
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

<table class=" lightable-classic" style="font-family: &quot;Arial Narrow&quot;, &quot;Source Sans Pro&quot;, sans-serif; margin-left: auto; margin-right: auto;">
<caption>
Density of bisected coral skeletons in g/cm^3
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
1.432
</td>
<td style="text-align:center;">
1.755
</td>
</tr>
<tr>
<td style="text-align:center;">
313
</td>
<td style="text-align:center;">
LCO2
</td>
<td style="text-align:center;">
1.620
</td>
<td style="text-align:center;">
2.006
</td>
</tr>
<tr>
<td style="text-align:center;">
421b
</td>
<td style="text-align:center;">
LCO2
</td>
<td style="text-align:center;">
1.567
</td>
<td style="text-align:center;">
1.884
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
1.457
</td>
<td style="text-align:center;">
1.672
</td>
</tr>
<tr>
<td style="text-align:center;">
464
</td>
<td style="text-align:center;">
LCO2
</td>
<td style="text-align:center;">
1.661
</td>
<td style="text-align:center;">
1.960
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
1.362
</td>
<td style="text-align:center;">
1.656
</td>
</tr>
</tbody>
</table>

![](/notebook/images/unnamed-chunk-3-1.png)<!-- -->![](/notebook/images/unnamed-chunk-3-2.png)<!-- -->

New Growth is less dense than Old Growth which makes sense as the Old
Growth contains the initial skeleton present at the beginning of the
experiment with the addition of lateral thickening. Further, New Growth
contains the fast growing apical branch which is less dense than the
basal portion of the colony.

There is, however, an interesting trend of corals grown under LCO2 (or
control) treatments being less dense than corals grown under HCO2. This
trend is apparent for both New Growth and Old Growth. One interpretation
is that the treatment group had significant effect on both the vertical
extension and the lateral thickening of coral growth, and thus treatment
effect is apparent in both the ‘New Growth’ and ‘Old Growth’ materials.
As mentioned before, this was to be expected, however we cannot parse
apart skeleton grown under treatment conditions in the Old Growth
section.

It is important to remember that the skeletal density is also a factor
of the coral’s growth and not solely its treatment group. Therefore, we
should standardize the density to a metric reflective of the coral’s
influence on its density to subtract the variability of the coral’s
growth from its treatment effect. When this is done, we begin to see
significant differences in standardized skeletal density among treatment
groups both in the New Growth and Old Growth materials.

## Statistical Testing

### Both Materials

![](/notebook/images/unnamed-chunk-4-1.png)<!-- -->

    ## # A tibble: 2 x 4
    ##   treatment variable    statistic     p
    ##   <chr>     <chr>           <dbl> <dbl>
    ## 1 HCO2      density.std     0.947 0.686
    ## 2 LCO2      density.std     0.898 0.150

    ## # A tibble: 1 x 4
    ##     df1   df2 statistic       p
    ##   <int> <int>     <dbl>   <dbl>
    ## 1     1    18      8.91 0.00795

<table class=" lightable-classic" style="font-family: &quot;Arial Narrow&quot;, &quot;Source Sans Pro&quot;, sans-serif; margin-left: auto; margin-right: auto;">
<caption>
Welch’s T-Test Results of Standardized Density of Both Materials
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
density.std
</td>
<td style="text-align:center;">
HCO2
</td>
<td style="text-align:center;">
LCO2
</td>
<td style="text-align:center;">
8
</td>
<td style="text-align:center;">
12
</td>
<td style="text-align:center;">
-4.628
</td>
<td style="text-align:center;">
17.168
</td>
<td style="text-align:center;">
0
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
1.974
</td>
<td style="text-align:center;">
8
</td>
<td style="text-align:center;">
12
</td>
<td style="text-align:center;">
large
</td>
</tr>
</tbody>
</table>

The mean standardized density in the HCO2 group was 0.01 (SD = 0),
whereas the mean in LCO2 group was 0.02 (SD = 0). A Welch’s two-samples
t-test showed that the difference was statistically significant,
t(17.17) = -4.628, p &lt; 0.001, d = 1.974.

### New Growth

Now, let’s just analyze the new growth material.

![](/notebook/images/unnamed-chunk-5-1.png)<!-- -->

    ## # A tibble: 2 x 4
    ##   treatment variable    statistic      p
    ##   <chr>     <chr>           <dbl>  <dbl>
    ## 1 HCO2      density.std     0.943 0.674 
    ## 2 LCO2      density.std     0.794 0.0522

    ## # A tibble: 1 x 4
    ##     df1   df2 statistic        p
    ##   <int> <int>     <dbl>    <dbl>
    ## 1     1     8      32.8 0.000440

<table class=" lightable-classic" style="font-family: &quot;Arial Narrow&quot;, &quot;Source Sans Pro&quot;, sans-serif; margin-left: auto; margin-right: auto;">
<caption>
Welch’s T-Test Results of Standardized Density of New Growth
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
density.std
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
6
</td>
<td style="text-align:center;">
-3.615
</td>
<td style="text-align:center;">
6.713
</td>
<td style="text-align:center;">
0.009
</td>
</tr>
</tbody>
</table>
<table class=" lightable-classic" style="font-family: &quot;Arial Narrow&quot;, &quot;Source Sans Pro&quot;, sans-serif; margin-left: auto; margin-right: auto;">
<caption>
Effect Size Results of Standardized Density of New Growth
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
1.832
</td>
<td style="text-align:center;">
4
</td>
<td style="text-align:center;">
6
</td>
<td style="text-align:center;">
large
</td>
</tr>
</tbody>
</table>

When looking at just the new growth, the mean standardized density in
the HCO2 group was 0.01 (SD = 0), whereas the mean in LCO2 group was
0.01 (SD = 0). A Welch’s two-samples t-test showed that the difference
was statistically significant, t(6.71) = -3.62, p &lt; 0.01, d = 1.832.

# Genotype Variability

Finally, it is important to compare the variability of the population to
the variability of a genoype within that population to begin to
understand genotype-specific sensitivities. Here, I compare 3 ramets of
P-Lirman grown under LCO2 conditions and compare it to all LCO2 corals

![](/notebook/images/unnamed-chunk-6-1.png)<!-- -->

    ## 
    ##  Bartlett test of homogeneity of variances
    ## 
    ## data:  density.std by genotype
    ## Bartlett's K-squared = 5.9302, df = 1, p-value = 0.01488

From this data, the variance of standardized skeletal density among the
genotype P-Lirman is certainly less than the variance of the population,
and there is a statistically significant difference between these two
groups’ variances. However, I am shying away from making any claims of
genotypic variability due to the small sample sizes and lack of genotype
replication throughout the experiment design.

</div>
