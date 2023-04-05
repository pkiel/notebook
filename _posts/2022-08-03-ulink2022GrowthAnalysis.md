---
layout: post
title:  "ULink 2022 Genotype x OA Growth Analysis"
author: "Patrick M Kiel"
date: '2022-08-03'
categories: [research]
description: "Growth analysis of corals in the University of Miami ULINK Genotype x ocean acidifcation experiment to test for mechanisms of resilience to global change within the critically endangered Acropora cervicornis."
output:
  md_document:
    variant: gfm
    preserve_yaml: TRUE
knit: (function(inputFile, encoding) {
  rmarkdown::render(inputFile, 
  encoding = encoding, 
  output_file = paste0("2022-08-03-",
                        gsub(pattern = "\\.Rmd$",
                              "", basename(inputFile))
                        ,".md"), 
  output_dir = "../_posts") })
always_allow_html: true
---

<script type="text/javascript">
window.onload = function() {
    //query string in the password
    const urlParams = new URLSearchParams(window.location.search);
    const pass = urlParams.get('pass')
    document.getElementById("password").value = pass;
};


function verify() {
  <!-- set the password here -->
  if (document.getElementById('password').value === 'ulink') {
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
/*Change content Display */
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

<!-- Place all chunks, text, etc here as you would a normal RMarkdown document -->

# Overview

Here I review the growth we have observed in our experiment. The total
growth was less than we anticipated, but we still produced enough new
skeleton with significant differences in growth rates and sensitivities
to proceed forward with most of our tests.

# Treatment Conditions

## Labview Data

<h5>
Figure 1. 10-minute averaged ERL Log
</h5>

<img src="/notebook/images/ulinkGrowth2022/diel plot-1.png" width="90%" style="display: block; margin: auto;" />

The peaks in the standard deviation are almost certainly caused by
aquarium cleaning days when corals are removed into a separate bath and
the sensors are capped causing logging errors. CO2 injection is turned
off during these times so the aquariums themselves are not experiencing
the conditions that the logged data are suggesting. The following graph
filters out these spiked values which were programmatically identified
by occurring during scheduled cleaning times and affecting multiple
aquariums at once since cleaning occurred at the same time for all
aquariums.

<h5>
Figure 2. Cleaned 10-minute Averaged ERL Log
</h5>

<img src="/notebook/images/ulinkGrowth2022/cleaned diel plot-1.png" width="90%" style="display: block; margin: auto;" />

Variability is still present, but the extreme spikes caused by cleaning
have been removed. Thus, any variability that remains is due to durafet
error or experimental variability that affected the corals. For example,
the durafet for T15 had much higher variability than the other
aquariums. However, I believe this to be negligible as values are not
spiking out of the treatment groups.

## Carbonate Chemistry Data

500mL water samples were collected every Tuesday for analysis of the
complete carbonate chemistry suite.

### Time of Day

The bottles were not taken at exactly the same time of day (my fault).
Therefore there will be enhanced variability of these stats since our
diel variability is in action.

<h5>
Figure 3. Times of Aquarium Bottle Sampling
</h5>

<img src="/notebook/images/ulinkGrowth2022/todSampling-1.png" width="90%" style="display: block; margin: auto;" />

Sampling time had a mean of around 10a. 3 sampling times were taken
after 12p with one sampling time around 4:20p

## Carb Parameters

<table class=" lightable-classic" style="font-family: &quot;Arial Narrow&quot;, &quot;Source Sans Pro&quot;, sans-serif; margin-left: auto; margin-right: auto;">
<caption>
Table 1: Aquarium Conditions. Means ± SEM
</caption>
<thead>
<tr>
<th style="text-align:center;font-weight: bold;">
tank
</th>
<th style="text-align:center;font-weight: bold;">
temp
</th>
<th style="text-align:center;font-weight: bold;">
TA
</th>
<th style="text-align:center;font-weight: bold;">
DIC
</th>
<th style="text-align:center;font-weight: bold;">
pCO2
</th>
<th style="text-align:center;font-weight: bold;">
omega
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:center;">
T13
</td>
<td style="text-align:center;">
27.05 ± 0.02
</td>
<td style="text-align:center;">
2301.01 ± 21.14
</td>
<td style="text-align:center;">
2126.64 ± 22.78
</td>
<td style="text-align:center;">
835.70 ± 36.22
</td>
<td style="text-align:center;">
2.19 ± 0.07
</td>
</tr>
<tr>
<td style="text-align:center;">
T14
</td>
<td style="text-align:center;">
27.05 ± 0.02
</td>
<td style="text-align:center;">
2300.12 ± 21.34
</td>
<td style="text-align:center;">
2000.13 ± 21.73
</td>
<td style="text-align:center;">
426.93 ± 14.74
</td>
<td style="text-align:center;">
3.46 ± 0.08
</td>
</tr>
<tr>
<td style="text-align:center;">
T15
</td>
<td style="text-align:center;">
27.04 ± 0.02
</td>
<td style="text-align:center;">
2303.84 ± 21.56
</td>
<td style="text-align:center;">
2119.24 ± 24.84
</td>
<td style="text-align:center;">
848.20 ± 99.62
</td>
<td style="text-align:center;">
2.31 ± 0.18
</td>
</tr>
<tr>
<td style="text-align:center;">
T16
</td>
<td style="text-align:center;">
27.07 ± 0.02
</td>
<td style="text-align:center;">
2297.52 ± 21.47
</td>
<td style="text-align:center;">
2004.24 ± 23.57
</td>
<td style="text-align:center;">
442.12 ± 17.83
</td>
<td style="text-align:center;">
3.38 ± 0.08
</td>
</tr>
</tbody>
</table>

## Statistics

<table class=" lightable-classic" style="font-family: &quot;Arial Narrow&quot;, &quot;Source Sans Pro&quot;, sans-serif; margin-left: auto; margin-right: auto;">
<caption>
Table 2: Significance of Parameters
</caption>
<thead>
<tr>
<th style="text-align:center;">
parameter
</th>
<th style="text-align:center;">
term
</th>
<th style="text-align:center;">
df
</th>
<th style="text-align:center;">
sumsq
</th>
<th style="text-align:center;">
meansq
</th>
<th style="text-align:center;">
statistic
</th>
<th style="text-align:center;">
p.value
</th>
<th style="text-align:center;">
significance
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:center;">
temp
</td>
<td style="text-align:center;">
treatment
</td>
<td style="text-align:center;">
1
</td>
<td style="text-align:center;">
0.003
</td>
<td style="text-align:center;">
0.003
</td>
<td style="text-align:center;">
1.007
</td>
<td style="text-align:center;">
0.321
</td>
<td style="text-align:center;">
NS
</td>
</tr>
<tr>
<td style="text-align:center;">
temp
</td>
<td style="text-align:center;">
treatment:tank
</td>
<td style="text-align:center;">
2
</td>
<td style="text-align:center;">
0.004
</td>
<td style="text-align:center;">
0.002
</td>
<td style="text-align:center;">
0.636
</td>
<td style="text-align:center;">
0.534
</td>
<td style="text-align:center;">
NS
</td>
</tr>
<tr>
<td style="text-align:center;">
temp
</td>
<td style="text-align:center;">
Residuals
</td>
<td style="text-align:center;">
48
</td>
<td style="text-align:center;">
0.167
</td>
<td style="text-align:center;">
0.003
</td>
<td style="text-align:center;">
NA
</td>
<td style="text-align:center;">
NA
</td>
<td style="text-align:center;">
NS
</td>
</tr>
<tr>
<td style="text-align:center;">
TA
</td>
<td style="text-align:center;">
treatment
</td>
<td style="text-align:center;">
1
</td>
<td style="text-align:center;">
169.020
</td>
<td style="text-align:center;">
169.020
</td>
<td style="text-align:center;">
0.028
</td>
<td style="text-align:center;">
0.867
</td>
<td style="text-align:center;">
NS
</td>
</tr>
<tr>
<td style="text-align:center;">
TA
</td>
<td style="text-align:center;">
treatment:tank
</td>
<td style="text-align:center;">
2
</td>
<td style="text-align:center;">
96.270
</td>
<td style="text-align:center;">
48.135
</td>
<td style="text-align:center;">
0.008
</td>
<td style="text-align:center;">
0.992
</td>
<td style="text-align:center;">
NS
</td>
</tr>
<tr>
<td style="text-align:center;">
TA
</td>
<td style="text-align:center;">
Residuals
</td>
<td style="text-align:center;">
48
</td>
<td style="text-align:center;">
285247.509
</td>
<td style="text-align:center;">
5942.656
</td>
<td style="text-align:center;">
NA
</td>
<td style="text-align:center;">
NA
</td>
<td style="text-align:center;">
NS
</td>
</tr>
<tr>
<td style="text-align:center;font-weight: bold;color: white !important;background-color: red !important;">
DIC
</td>
<td style="text-align:center;font-weight: bold;color: white !important;background-color: red !important;">
treatment
</td>
<td style="text-align:center;font-weight: bold;color: white !important;background-color: red !important;">
1
</td>
<td style="text-align:center;font-weight: bold;color: white !important;background-color: red !important;">
189577.501
</td>
<td style="text-align:center;font-weight: bold;color: white !important;background-color: red !important;">
189577.501
</td>
<td style="text-align:center;font-weight: bold;color: white !important;background-color: red !important;">
26.960
</td>
<td style="text-align:center;font-weight: bold;color: white !important;background-color: red !important;">
0.000
</td>
<td style="text-align:center;font-weight: bold;color: white !important;background-color: red !important;">
xxx
</td>
</tr>
<tr>
<td style="text-align:center;">
DIC
</td>
<td style="text-align:center;">
treatment:tank
</td>
<td style="text-align:center;">
2
</td>
<td style="text-align:center;">
465.459
</td>
<td style="text-align:center;">
232.730
</td>
<td style="text-align:center;">
0.033
</td>
<td style="text-align:center;">
0.967
</td>
<td style="text-align:center;">
NS
</td>
</tr>
<tr>
<td style="text-align:center;">
DIC
</td>
<td style="text-align:center;">
Residuals
</td>
<td style="text-align:center;">
48
</td>
<td style="text-align:center;">
337526.642
</td>
<td style="text-align:center;">
7031.805
</td>
<td style="text-align:center;">
NA
</td>
<td style="text-align:center;">
NA
</td>
<td style="text-align:center;">
NS
</td>
</tr>
<tr>
<td style="text-align:center;font-weight: bold;color: white !important;background-color: red !important;">
pCO2
</td>
<td style="text-align:center;font-weight: bold;color: white !important;background-color: red !important;">
treatment
</td>
<td style="text-align:center;font-weight: bold;color: white !important;background-color: red !important;">
1
</td>
<td style="text-align:center;font-weight: bold;color: white !important;background-color: red !important;">
2157966.567
</td>
<td style="text-align:center;font-weight: bold;color: white !important;background-color: red !important;">
2157966.567
</td>
<td style="text-align:center;font-weight: bold;color: white !important;background-color: red !important;">
56.404
</td>
<td style="text-align:center;font-weight: bold;color: white !important;background-color: red !important;">
0.000
</td>
<td style="text-align:center;font-weight: bold;color: white !important;background-color: red !important;">
xxx
</td>
</tr>
<tr>
<td style="text-align:center;">
pCO2
</td>
<td style="text-align:center;">
treatment:tank
</td>
<td style="text-align:center;">
2
</td>
<td style="text-align:center;">
2513.434
</td>
<td style="text-align:center;">
1256.717
</td>
<td style="text-align:center;">
0.033
</td>
<td style="text-align:center;">
0.968
</td>
<td style="text-align:center;">
NS
</td>
</tr>
<tr>
<td style="text-align:center;">
pCO2
</td>
<td style="text-align:center;">
Residuals
</td>
<td style="text-align:center;">
48
</td>
<td style="text-align:center;">
1836441.545
</td>
<td style="text-align:center;">
38259.199
</td>
<td style="text-align:center;">
NA
</td>
<td style="text-align:center;">
NA
</td>
<td style="text-align:center;">
NS
</td>
</tr>
<tr>
<td style="text-align:center;font-weight: bold;color: white !important;background-color: red !important;">
omega
</td>
<td style="text-align:center;font-weight: bold;color: white !important;background-color: red !important;">
treatment
</td>
<td style="text-align:center;font-weight: bold;color: white !important;background-color: red !important;">
1
</td>
<td style="text-align:center;font-weight: bold;color: white !important;background-color: red !important;">
17.735
</td>
<td style="text-align:center;font-weight: bold;color: white !important;background-color: red !important;">
17.735
</td>
<td style="text-align:center;font-weight: bold;color: white !important;background-color: red !important;">
109.739
</td>
<td style="text-align:center;font-weight: bold;color: white !important;background-color: red !important;">
0.000
</td>
<td style="text-align:center;font-weight: bold;color: white !important;background-color: red !important;">
xxx
</td>
</tr>
<tr>
<td style="text-align:center;">
omega
</td>
<td style="text-align:center;">
treatment:tank
</td>
<td style="text-align:center;">
2
</td>
<td style="text-align:center;">
0.135
</td>
<td style="text-align:center;">
0.068
</td>
<td style="text-align:center;">
0.418
</td>
<td style="text-align:center;">
0.661
</td>
<td style="text-align:center;">
NS
</td>
</tr>
<tr>
<td style="text-align:center;">
omega
</td>
<td style="text-align:center;">
Residuals
</td>
<td style="text-align:center;">
48
</td>
<td style="text-align:center;">
7.757
</td>
<td style="text-align:center;">
0.162
</td>
<td style="text-align:center;">
NA
</td>
<td style="text-align:center;">
NA
</td>
<td style="text-align:center;">
NS
</td>
</tr>
</tbody>
</table>

Temperature and total alkalinity were not significantly different
between treatments or within treatments (p\>\>0.05). DIC, pCO2, and
$$\Omega_{Ar}$$ (p\<0.001) were significantly different between
treatment, but not between aquariums within treatment (p\>\>0.05). In
other words, our system reproducibly altered the carbonate chemistry
parameters with high precision.

# Calcification Analysis

<h5>
Figure 4. Avg Daily Growth by (A) Treatment and (B) Genotype
</h5>

<img src="/notebook/images/ulinkGrowth2022/calcification graphs-1.png" width="90%" style="display: block; margin: auto;" />

<table class=" lightable-classic" style="font-family: &quot;Arial Narrow&quot;, &quot;Source Sans Pro&quot;, sans-serif; margin-left: auto; margin-right: auto;">
<caption>
Table 2: Means of Treatment
</caption>
<thead>
<tr>
<th style="text-align:center;font-weight: bold;">
treatment
</th>
<th style="text-align:center;font-weight: bold;">
n
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
HCO2
</td>
<td style="text-align:center;">
37
</td>
<td style="text-align:center;">
0.081
</td>
<td style="text-align:center;">
0.027
</td>
</tr>
<tr>
<td style="text-align:center;">
LCO2
</td>
<td style="text-align:center;">
37
</td>
<td style="text-align:center;">
0.126
</td>
<td style="text-align:center;">
0.028
</td>
</tr>
</tbody>
</table>
<table class=" lightable-classic" style="font-family: &quot;Arial Narrow&quot;, &quot;Source Sans Pro&quot;, sans-serif; margin-left: auto; margin-right: auto;">
<caption>
Table 3: Stats of Treatment
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
<th style="text-align:center;font-weight: bold;">
p.signif
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
37
</td>
<td style="text-align:center;">
37
</td>
<td style="text-align:center;">
-7.0659
</td>
<td style="text-align:center;">
72
</td>
<td style="text-align:center;">
0
</td>
<td style="text-align:center;">
\*\*\*\*
</td>
</tr>
</tbody>
</table>
<table class=" lightable-classic" style="font-family: &quot;Arial Narrow&quot;, &quot;Source Sans Pro&quot;, sans-serif; margin-left: auto; margin-right: auto;">
<caption>
Table 4: Effect Size of Treatment
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
-1.6428
</td>
<td style="text-align:center;">
37
</td>
<td style="text-align:center;">
37
</td>
<td style="text-align:center;">
large
</td>
</tr>
</tbody>
</table>
<table class=" lightable-classic" style="font-family: &quot;Arial Narrow&quot;, &quot;Source Sans Pro&quot;, sans-serif; margin-left: auto; margin-right: auto;">
<caption>
Table 5: TukeyHSD Results of Anova
</caption>
<thead>
<tr>
<th style="text-align:center;font-weight: bold;">
term
</th>
<th style="text-align:center;font-weight: bold;">
contrast
</th>
<th style="text-align:center;font-weight: bold;">
adj.p.value
</th>
<th style="text-align:center;font-weight: bold;">
significance
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:center;font-weight: bold;color: white !important;background-color: red !important;">
treatment
</td>
<td style="text-align:center;font-weight: bold;color: white !important;background-color: red !important;">
LCO2-HCO2
</td>
<td style="text-align:center;font-weight: bold;color: white !important;background-color: red !important;">
0.0000
</td>
<td style="text-align:center;font-weight: bold;color: white !important;background-color: red !important;">
xxx
</td>
</tr>
<tr>
<td style="text-align:center;font-weight: bold;color: white !important;background-color: red !important;">
treatment:genotype
</td>
<td style="text-align:center;font-weight: bold;color: white !important;background-color: red !important;">
LCO2:AC-2-HCO2:AC-2
</td>
<td style="text-align:center;font-weight: bold;color: white !important;background-color: red !important;">
0.0000
</td>
<td style="text-align:center;font-weight: bold;color: white !important;background-color: red !important;">
xxx
</td>
</tr>
<tr>
<td style="text-align:center;font-weight: bold;color: white !important;background-color: red !important;">
treatment:genotype
</td>
<td style="text-align:center;font-weight: bold;color: white !important;background-color: red !important;">
LCO2:MB-C-HCO2:MB-C
</td>
<td style="text-align:center;font-weight: bold;color: white !important;background-color: red !important;">
0.0000
</td>
<td style="text-align:center;font-weight: bold;color: white !important;background-color: red !important;">
xxx
</td>
</tr>
<tr>
<td style="text-align:center;font-weight: bold;color: white !important;background-color: red !important;">
genotype
</td>
<td style="text-align:center;font-weight: bold;color: white !important;background-color: red !important;">
SI-A-MB-C
</td>
<td style="text-align:center;font-weight: bold;color: white !important;background-color: red !important;">
0.0001
</td>
<td style="text-align:center;font-weight: bold;color: white !important;background-color: red !important;">
xxx
</td>
</tr>
<tr>
<td style="text-align:center;">
genotype
</td>
<td style="text-align:center;">
SI-A-AC-2
</td>
<td style="text-align:center;">
0.1385
</td>
<td style="text-align:center;">
NS
</td>
</tr>
<tr>
<td style="text-align:center;">
treatment:genotype
</td>
<td style="text-align:center;">
LCO2:SI-A-HCO2:SI-A
</td>
<td style="text-align:center;">
0.4558
</td>
<td style="text-align:center;">
NS
</td>
</tr>
</tbody>
</table>

The mean calcification rate in the HCO2 group was mean 0.081 (SD =
0.027) mg/ $$cm^2$$ /day, whereas the mean in the LCO2 group was 0.126
(SD = 0.028). A Student two-samples t-test showed that the difference
was statistically significant, t(72) = -7.066, p \< 0.0001, d = -1.643.
Thus, the ocean acidification group saw on average a 36% reduction in
calcification rates. The effects, however, were not even across the
genotypes (Table 5).

## Tank Effects

We saw above that tank conditions were significantly different among
treatment groups, but not individual aquariums within treatment. We also
saw that calcification rates were significantly different among
treatment groups. Here I am analyzing tank effects on the calcification
rate and investigating if calcification rates were significantly
different between aquariums within the same treatment group. This will
dictate whether we need to include tank as a random intercept in our
ANOVA models.

<h5>
Figure 5. Avg Daily Growth by Tank and Treatment
</h5>

<img src="/notebook/images/ulinkGrowth2022/tank effects graph-1.png" width="90%" style="display: block; margin: auto;" />

### Tank Effects Statistics

<table class=" lightable-classic" style="font-family: &quot;Arial Narrow&quot;, &quot;Source Sans Pro&quot;, sans-serif; margin-left: auto; margin-right: auto;">
<caption>
Table 6: Significance testing of treatment effect on calcification,
using t test
</caption>
<thead>
<tr>
<th style="text-align:center;font-weight: bold;">
treatment
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
<th style="text-align:center;font-weight: bold;">
p.adj
</th>
<th style="text-align:center;font-weight: bold;">
p.adj.signif
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:center;">
HCO2
</td>
<td style="text-align:center;">
G
</td>
<td style="text-align:center;">
13
</td>
<td style="text-align:center;">
15
</td>
<td style="text-align:center;">
19
</td>
<td style="text-align:center;">
18
</td>
<td style="text-align:center;">
0.991
</td>
<td style="text-align:center;">
34.650
</td>
<td style="text-align:center;">
0.329
</td>
<td style="text-align:center;">
0.329
</td>
<td style="text-align:center;">
ns
</td>
</tr>
<tr>
<td style="text-align:center;">
LCO2
</td>
<td style="text-align:center;">
G
</td>
<td style="text-align:center;">
14
</td>
<td style="text-align:center;">
16
</td>
<td style="text-align:center;">
19
</td>
<td style="text-align:center;">
18
</td>
<td style="text-align:center;">
1.074
</td>
<td style="text-align:center;">
34.937
</td>
<td style="text-align:center;">
0.290
</td>
<td style="text-align:center;">
0.290
</td>
<td style="text-align:center;">
ns
</td>
</tr>
</tbody>
</table>

No observable differences of mean calcification rate when comparing
within treatment groups.

### Mixed Effects Model

Here I created a mixed effects model model to account for the lack of
independence brought upon by having multiple corals grown in the same
tank and the possible tank-specific effects that may have affected
calcification rates. Including this random effect increased the AIC from
-354 to -352 as compared to a fixed-effects only model, and therefore I
will not include random tank effects in my analysis.

As a reminder, here is the fixed effects model as shown above:

``` r
modFixed <- totalGrowth %>%
  aov(G ~ genotype*treatment, data=.)

modFixed %>%
  summary()
```

                   Df  Sum Sq Mean Sq F value   Pr(>F)    

genotype 2 0.01374 0.00687 17.46 7.61e-07 *** treatment 1 0.03956
0.03956 100.54 4.89e-15 *** genotype:treatment 2 0.01169 0.00584 14.85
4.46e-06 \*\*\* Residuals 68 0.02676 0.00039  
— Signif. codes: 0 ‘***’ 0.001 ’**’ 0.01 ’*’ 0.05 ‘.’ 0.1 ’ ’ 1

Here is the mixed effects model with the tank identity set as a random
factor to give each tank its own, random intercept. Notice, including
the random effects decreases the absolute value of the AIC. Therefore,
this new model better describes the data.

``` r
modRandom <- totalGrowth %>%
  lmerTest::lmer(G ~ genotype * treatment + (1|tank),
                 data=.)
modRandom %>%
  anova() %>%
  tidy() %>%
  kbl()
```

<table>
<thead>
<tr>
<th style="text-align:left;">
term
</th>
<th style="text-align:right;">
sumsq
</th>
<th style="text-align:right;">
meansq
</th>
<th style="text-align:right;">
NumDF
</th>
<th style="text-align:right;">
DenDF
</th>
<th style="text-align:right;">
statistic
</th>
<th style="text-align:right;">
p.value
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:left;">
genotype
</td>
<td style="text-align:right;">
0.0167813
</td>
<td style="text-align:right;">
0.0083906
</td>
<td style="text-align:right;">
2
</td>
<td style="text-align:right;">
66.206864
</td>
<td style="text-align:right;">
21.46841
</td>
<td style="text-align:right;">
0.0000001
</td>
</tr>
<tr>
<td style="text-align:left;">
treatment
</td>
<td style="text-align:right;">
0.0340982
</td>
<td style="text-align:right;">
0.0340982
</td>
<td style="text-align:right;">
1
</td>
<td style="text-align:right;">
2.012228
</td>
<td style="text-align:right;">
87.24428
</td>
<td style="text-align:right;">
0.0110507
</td>
</tr>
<tr>
<td style="text-align:left;">
genotype:treatment
</td>
<td style="text-align:right;">
0.0116516
</td>
<td style="text-align:right;">
0.0058258
</td>
<td style="text-align:right;">
2
</td>
<td style="text-align:right;">
66.206864
</td>
<td style="text-align:right;">
14.90602
</td>
<td style="text-align:right;">
0.0000045
</td>
</tr>
</tbody>
</table>

``` r
#redefining modRandom w/ REML=F for AIC comparison
modRandom <- totalGrowth %>%
  lmerTest::lmer(G ~ genotype * treatment + (1|tank), REML = F,
                 data=.)

AIC(modFixed, modRandom) %>%
  kbl()
```

<table>
<thead>
<tr>
<th style="text-align:left;">
</th>
<th style="text-align:right;">
df
</th>
<th style="text-align:right;">
AIC
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:left;">
modFixed
</td>
<td style="text-align:right;">
7
</td>
<td style="text-align:right;">
-362.4413
</td>
</tr>
<tr>
<td style="text-align:left;">
modRandom
</td>
<td style="text-align:right;">
8
</td>
<td style="text-align:right;">
-360.4413
</td>
</tr>
</tbody>
</table>
<!-- Tukey post-hoc analysis of the mixed effects model: -->
<!-- ```{r random mixed effects table} -->
<!-- emmeans(modRandom, list(pairwise ~genotype*treatment), -->
<!--         adjust = "tukey")[[2]] %>% -->
<!--   broom::tidy() %>% -->
<!--   filter(`1` %in% pairwiseString) %>% -->
<!--   select(-c(term,df)) %>% -->
<!--   rename(pairwise=`1`) %>% -->
<!--   kbl(align = 'c', -->
<!--     digits = 4, -->
<!--     caption = "Table 8: Pairwise comparison of genotypes' sensitivity to OA", -->
<!--     escape=F) %>% -->
<!--   kable_classic() %>% -->
<!--   row_spec(0, bold = T) %>% -->
<!--   row_spec(c(1,3), -->
<!--          bold = T, -->
<!--          color = "white", -->
<!--          background = "red") -->
<!-- ``` -->
<!-- Pattern is the same as above with the fixed effects. Significance has decreased (p values increased) for AC-2 and MB-C, suggesting that there was some variability between tanks in the same treatment (T13 v T15 and T14 v T16) but that this within treatment variability was not significant enough to change our conclusions. Thus, we fail to reject our null hypothesis that there are significant differences between individual genotype's susceptibility to OA. -->

## Powder Available

<h5>
Figure 6. Amount of New CaCO3 Precipitated
</h5>

<img src="/notebook/images/ulinkGrowth2022/powder available-1.png" width="90%" style="display: block; margin: auto;" />

The amount of new aragonite precipated is visualized above. Horizontal
lines denote thresholds for tests: \>500mg = green (complete suite
including XRD), \>120 mg = orange (complete suite sans XRD), \>50mg =
red (TGA and isotope only).

# Linear Extension

<h5>
Figure 7. Avg Daily Linear Extension by Treatment
</h5>
<img src="/notebook/images/ulinkGrowth2022/LE graphs-1.png" width="90%" style="display: block; margin: auto;" />
<h5>
Figure 8. Avg Daily Linear Extension by Treatment and Aquarium
</h5>
<img src="/notebook/images/ulinkGrowth2022/LE graphs-2.png" width="90%" style="display: block; margin: auto;" />
<h5>
Figure 9. Avg Daily Linar Extension by Genotype and Treatment
</h5>

<img src="/notebook/images/ulinkGrowth2022/LE graphs-3.png" width="90%" style="display: block; margin: auto;" />

Such large variability in that SI-A ambient group.

<table class=" lightable-classic" style="font-family: &quot;Arial Narrow&quot;, &quot;Source Sans Pro&quot;, sans-serif; margin-left: auto; margin-right: auto;">
<caption>
Table 7:Means of Treatment
</caption>
<thead>
<tr>
<th style="text-align:center;font-weight: bold;">
treatment
</th>
<th style="text-align:center;font-weight: bold;">
n
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
HCO2
</td>
<td style="text-align:center;">
37
</td>
<td style="text-align:center;">
0.011
</td>
<td style="text-align:center;">
0.003
</td>
</tr>
<tr>
<td style="text-align:center;">
LCO2
</td>
<td style="text-align:center;">
36
</td>
<td style="text-align:center;">
0.012
</td>
<td style="text-align:center;">
0.004
</td>
</tr>
</tbody>
</table>
<table class=" lightable-classic" style="font-family: &quot;Arial Narrow&quot;, &quot;Source Sans Pro&quot;, sans-serif; margin-left: auto; margin-right: auto;">
<caption>
Table 8: Stats of Treatment
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
<th style="text-align:center;font-weight: bold;">
p.signif
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
37
</td>
<td style="text-align:center;">
36
</td>
<td style="text-align:center;">
-0.4283
</td>
<td style="text-align:center;">
71
</td>
<td style="text-align:center;">
0.67
</td>
<td style="text-align:center;">
ns
</td>
</tr>
</tbody>
</table>
<table class=" lightable-classic" style="font-family: &quot;Arial Narrow&quot;, &quot;Source Sans Pro&quot;, sans-serif; margin-left: auto; margin-right: auto;">
<caption>
Table 9: Effect Size of Treatment
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
-0.1003
</td>
<td style="text-align:center;">
37
</td>
<td style="text-align:center;">
36
</td>
<td style="text-align:center;">
negligible
</td>
</tr>
</tbody>
</table>
<table class=" lightable-classic" style="font-family: &quot;Arial Narrow&quot;, &quot;Source Sans Pro&quot;, sans-serif; margin-left: auto; margin-right: auto;">
<caption>
Table 10: TukeyHSD Results of Anova
</caption>
<thead>
<tr>
<th style="text-align:center;font-weight: bold;">
term
</th>
<th style="text-align:center;font-weight: bold;">
contrast
</th>
<th style="text-align:center;font-weight: bold;">
adj.p.value
</th>
<th style="text-align:center;font-weight: bold;">
significance
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:center;font-weight: bold;color: white !important;background-color: red !important;">
genotype
</td>
<td style="text-align:center;font-weight: bold;color: white !important;background-color: red !important;">
SI-A-MB-C
</td>
<td style="text-align:center;font-weight: bold;color: white !important;background-color: red !important;">
0.0218
</td>
<td style="text-align:center;font-weight: bold;color: white !important;background-color: red !important;">
x
</td>
</tr>
<tr>
<td style="text-align:center;">
genotype
</td>
<td style="text-align:center;">
SI-A-AC-2
</td>
<td style="text-align:center;">
0.1599
</td>
<td style="text-align:center;">
NS
</td>
</tr>
<tr>
<td style="text-align:center;">
treatment
</td>
<td style="text-align:center;">
LCO2-HCO2
</td>
<td style="text-align:center;">
0.6562
</td>
<td style="text-align:center;">
NS
</td>
</tr>
<tr>
<td style="text-align:center;">
treatment:genotype
</td>
<td style="text-align:center;">
LCO2:SI-A-HCO2:SI-A
</td>
<td style="text-align:center;">
0.6948
</td>
<td style="text-align:center;">
NS
</td>
</tr>
<tr>
<td style="text-align:center;">
treatment:genotype
</td>
<td style="text-align:center;">
LCO2:AC-2-HCO2:AC-2
</td>
<td style="text-align:center;">
0.9697
</td>
<td style="text-align:center;">
NS
</td>
</tr>
<tr>
<td style="text-align:center;">
treatment:genotype
</td>
<td style="text-align:center;">
LCO2:MB-C-HCO2:MB-C
</td>
<td style="text-align:center;">
1.0000
</td>
<td style="text-align:center;">
NS
</td>
</tr>
</tbody>
</table>

The mean linear extension rate in the HCO2 group was mean 0.011 (SD =
0.003) mm/cm/day, whereas the mean in the LCO2 group was 0.012 (SD =
0.004). A Student two-samples t-test showed that the difference was not
statistically significant, t(71) = -0.428, p =0.124, d = -0.1.

<!-- ## Tank Effects -->
<!-- ```{r LE tank effects} -->
<!-- capFig("Avg Daily Linear Extension by Treatment and Aquarium") -->
<!-- height %>% -->
<!--    mutate(tank = case_when(tank == 13 ~ "13 HCO2", -->
<!--                           tank == 14 ~ "14 LCO2", -->
<!--                           tank == 15 ~ "15 HCO2", -->
<!--                           tank == 16 ~ "16 LCO2")) %>% -->
<!--   ggplot(aes(genotype, prod, fill=tank)) + -->
<!--   geom_boxplot() + -->
<!--   scale_fill_manual(values = manLegend) + -->
<!--   labs(x = "Treatment", -->
<!--        y = "Avg Daily LE Rate (mm/cm/day)") + -->
<!--   theme_classic() -->
<!-- ``` -->
<!-- ```{r LE Tank effects stats} -->
<!-- height %>% -->
<!--   group_by(treatment) %>% -->
<!--   t_test(data=.,formula = prod ~ tank) %>% -->
<!--     kbl(align = 'c', -->
<!--     digits = 3, -->
<!--     caption = "Table 14: Significance testing of tank effect on Linear Extension Rates") %>% -->
<!--   kable_classic() %>% -->
<!--   row_spec(0, bold = T) -->
<!-- modFixed <- height %>% -->
<!--   aov(prod ~ treatment*genotype, -->
<!--                  data=.)  -->
<!-- modFixed %>% TukeyHSD() %>% -->
<!--   broom::tidy() %>% -->
<!--   filter(contrast %in% c('LCO2:SI-A-HCO2:SI-A')) %>% -->
<!--   select(term,contrast,adj.p.value) %>% -->
<!--   mutate(significance = case_when(adj.p.value <0.001 ~ "xxx", -->
<!--                                   adj.p.value <0.01 ~ "xx", -->
<!--                                   adj.p.value <0.05 ~ "x", -->
<!--                                   TRUE ~ "NS"), -->
<!--          adj.p.value = round(adj.p.value, digits=4)) %>% -->
<!--   arrange(adj.p.value) -->
<!-- modRandom <- height %>% -->
<!--   lmerTest::lmer(prod ~ genotype * treatment + (1|tank), -->
<!--                  data=.) -->
<!-- modRandom %>% -->
<!--   anova() -->
<!-- emmeans(modRandom, list(pairwise ~genotype*treatment), -->
<!--         adjust = "tukey")[[2]] %>% -->
<!--   broom::tidy() %>% -->
<!--   filter(`1` %in% pairwiseString) %>% -->
<!--   select(-c(term,df)) %>% -->
<!--   rename(pairwise=`1`) %>% -->
<!--   kbl(align = 'c', -->
<!--     digits = 4, -->
<!--     caption = "Table 15:Pairwise comparison of genotypes' sensitivity to OA", -->
<!--     escape=F) %>% -->
<!--   kable_classic() %>% -->
<!--   row_spec(0, bold = T) %>% -->
<!--   row_spec(4, -->
<!--          bold = T, -->
<!--          color = "white", -->
<!--          background = "red") -->
<!-- AIC(modFixed, modRandom) -->
<!-- ``` -->
<!-- AIC tells us the mixed effects model better describes the data. Post-hoc testing further tells us that indeed SI-A's linear extension rates were significantly different between treatments (p<0.05), yet all other genotype's were not. -->
<!-- ```{r total extension} -->
<!-- capFig("Amount of New Skeleton and Mean New LE (Red Line)") -->
<!-- height %>% -->
<!--   ggplot(aes(x=genotype, y=LE)) + -->
<!--   geom_point(aes(color=treatment)) + -->
<!--   scale_y_continuous(limits = c(0,30)) + -->
<!--   geom_hline(yintercept = mean(height$LE), -->
<!--              color="red") + -->
<!--   labs(y = "Linear Extension (mm)") + -->
<!--   theme_classic() -->
<!-- ``` -->

# Takeaways and Next Steps

Overall growth was less than hoped for. However, there is enough new
skeleton for nearly all the powder tests that we want to conduct: FTIR,
TGA, boron isotopes, and Raman.For nanoindentation tests, we should have
enough new growth to run on a majority of samples.

Linear extension was measured by maximum vertical height as measured
with calipers. We additionally have initial 3d scans of all corals and
post 3d scans of a subset of 48 corals (n=3 per genotype per tank). From
this data, we can extract surface area to volume ratios and see how this
changed among genotypes and treatments. This analysis still needs to be
done.

## CT Scanning

The micro-ct scan is currently out of service. We can use the large
ct-scanner to determine bulk density. The scanner has a resolution of
0.1mm/scan so we can measure the density of the new growth. This growth
is isolated to the highly variable apical tips which may cause some
problems.
<a href="https://patrickmkiel.com/notebook/research/LangdonSkeletonAnalysis/?pass=acidification" target="_blank">See
this post which discusses the ct-scanning analysis of apical tips done
on Langdon’s OA corals.</a>

</div>
