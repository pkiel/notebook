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

<img src="/notebook/images/ulinkGrowth2022/diel pot-1.png" width="90%" style="display: block; margin: auto;" />

The peaks in the standard deviation are almost certainly caused by
aquarium cleaning days when corals are removed into a separate bath and
the sensors are capped causing logging errors. CO2 injection is turned
off during these times so the aquariums themselves are not experiencing
the conditions that the logged data are suggesting. The following graph
filters out these spiked values which were programmatically identified
by occurring during scheduled cleaning times and affecting multiple
aquariums at once since cleaning occurred at the same time for all
aquariums.

<img src="/notebook/images/ulinkGrowth2022/cleaned diel plot-1.png" width="90%" style="display: block; margin: auto;" />

Variability is still present, but the extreme spikes caused by cleaning
have been removed. Thus, any variability that remains is due to durafet
error or experimental variability that affected the corals. For example,
the durafet for T15 had much higher variability than the other
aquariums. However, I believe this to be negligible.

## Carbonate Chemistry Data

500mL water samples were collected every Tuesday for analysis of the
complete carbonate chemistry suite.

### Time of Day

The bottles were not taken at exactly the same time of day, and thus the
programmed variability will be apart of the variability of each sample
along with sampling error, durafet error altering amount of CO2 injected
into aquaria (shown above in the LabView data), etc.

<img src="/notebook/images/ulinkGrowth2022/unnamed-chunk-3-1.png" width="90%" style="display: block; margin: auto;" />

Sampling time had a mean of around 10a. 3 sampling times were taken
after 12p with one sampling time around 4:20p

## Carb Parameters

<table class=" lightable-classic" style="font-family: &quot;Arial Narrow&quot;, &quot;Source Sans Pro&quot;, sans-serif; margin-left: auto; margin-right: auto;">
<caption>
Aquarium Conditions. Means ± SEM
</caption>
<thead>
<tr>
<th style="text-align:center;font-weight: bold;">
tank
</th>
<th style="text-align:center;font-weight: bold;">
sal
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
34.45 ± 0.65
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
34.38 ± 0.66
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
34.44 ± 0.65
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
34.40 ± 0.67
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
Significance of Parameters
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
sal
</td>
<td style="text-align:center;">
treatment
</td>
<td style="text-align:center;">
1
</td>
<td style="text-align:center;">
0.040
</td>
<td style="text-align:center;">
0.040
</td>
<td style="text-align:center;">
0.007
</td>
<td style="text-align:center;">
0.933
</td>
<td style="text-align:center;">
NS
</td>
</tr>
<tr>
<td style="text-align:center;">
sal
</td>
<td style="text-align:center;">
treatment:tank
</td>
<td style="text-align:center;">
2
</td>
<td style="text-align:center;">
0.003
</td>
<td style="text-align:center;">
0.002
</td>
<td style="text-align:center;">
0.000
</td>
<td style="text-align:center;">
1.000
</td>
<td style="text-align:center;">
NS
</td>
</tr>
<tr>
<td style="text-align:center;">
sal
</td>
<td style="text-align:center;">
Residuals
</td>
<td style="text-align:center;">
48
</td>
<td style="text-align:center;">
269.036
</td>
<td style="text-align:center;">
5.605
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

Salinity, temperature, and total alkalinity were not significantly
different between treatments or within treatments (p&gt;&gt;0.05). DIC,
pCO2, and
*Ω*<sub>*A**r*</sub>
(p&lt;0.001) were significantly different between treatment, but not
between aquariums (p&gt;&gt;0.05). In other words, our system
reproducibly altered the carbonate chemistry parameters with high
precision.

# Calcification Analysis

<img src="/notebook/images/ulinkGrowth2022/growth graphs-1.png" width="90%" style="display: block; margin: auto;" /><img src="/notebook/images/ulinkGrowth2022/growth graphs-2.png" width="90%" style="display: block; margin: auto;" />

Following April 15 (Weeky 5), the declining health of the corals
stabilized and began to split amongst treatment groups.

<img src="/notebook/images/ulinkGrowth2022/calcification graphs-1.png" width="90%" style="display: block; margin: auto;" /><img src="/notebook/images/ulinkGrowth2022/calcification graphs-2.png" width="90%" style="display: block; margin: auto;" /><img src="/notebook/images/ulinkGrowth2022/calcification graphs-3.png" width="90%" style="display: block; margin: auto;" />

There is some obvious genet-specific responses.

1.  Cheetos-B calcification rate was nearly identical across HCO2 and
    LCO2 groups. This genet also had high initial mortality and the
    worst survivorship rate throughout the experiment. It is entirely
    possible that this genotype did not do well in the aquariums and its
    diminished calcification rate is an effect of overall health and not
    treatment.

2.  SI-A and AC-2 had the highest average calcification rates and there
    was no significant difference between these two genotypes. However,
    when you look at the effect of treatment within these genotypes
    (sensitivity), there is significant differences between them.

3.  When looking at just controls, the only significant different
    genotype is Cheetos-B. Thus, there is a difference in sensitivity to
    OA but no observable differences in ambient conditions.

4.  The relative rankings extracted from the ol’ AcDC are SI-A \~
    MB-C &gt; AC-2 &gt; Cheetos-B. The data collected here fits within
    that framework, yet reveals intraspecifc differences in
    sensitivities similar to Enochs et al. (2018). Genet identities are
    unknown for that paper though.

<table class=" lightable-classic" style="font-family: &quot;Arial Narrow&quot;, &quot;Source Sans Pro&quot;, sans-serif; margin-left: auto; margin-right: auto;">
<caption>
Means of Treatment
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
46
</td>
<td style="text-align:center;">
0.316
</td>
<td style="text-align:center;">
0.139
</td>
</tr>
<tr>
<td style="text-align:center;">
LCO2
</td>
<td style="text-align:center;">
43
</td>
<td style="text-align:center;">
0.569
</td>
<td style="text-align:center;">
0.237
</td>
</tr>
</tbody>
</table>
<table class=" lightable-classic" style="font-family: &quot;Arial Narrow&quot;, &quot;Source Sans Pro&quot;, sans-serif; margin-left: auto; margin-right: auto;">
<caption>
Stats of Treatment
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
dailyG
</td>
<td style="text-align:center;">
HCO2
</td>
<td style="text-align:center;">
LCO2
</td>
<td style="text-align:center;">
46
</td>
<td style="text-align:center;">
43
</td>
<td style="text-align:center;">
-6.1944
</td>
<td style="text-align:center;">
87
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
Effect Size of Treatment
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
dailyG
</td>
<td style="text-align:center;">
HCO2
</td>
<td style="text-align:center;">
LCO2
</td>
<td style="text-align:center;">
-1.314
</td>
<td style="text-align:center;">
46
</td>
<td style="text-align:center;">
43
</td>
<td style="text-align:center;">
large
</td>
</tr>
</tbody>
</table>
<table class=" lightable-classic" style="font-family: &quot;Arial Narrow&quot;, &quot;Source Sans Pro&quot;, sans-serif; margin-left: auto; margin-right: auto;">
<caption>
TukeyHSD Results of Anova
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
genotype
</td>
<td style="text-align:center;font-weight: bold;color: white !important;background-color: red !important;">
SI-A-Cheetos-B
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
genotype
</td>
<td style="text-align:center;font-weight: bold;color: white !important;background-color: red !important;">
Cheetos-B-AC-2
</td>
<td style="text-align:center;font-weight: bold;color: white !important;background-color: red !important;">
0.0004
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
0.0004
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
0.0039
</td>
<td style="text-align:center;font-weight: bold;color: white !important;background-color: red !important;">
xx
</td>
</tr>
<tr>
<td style="text-align:center;">
genotype
</td>
<td style="text-align:center;">
MB-C-Cheetos-B
</td>
<td style="text-align:center;">
0.1103
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
0.3339
</td>
<td style="text-align:center;">
NS
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
0.5634
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
LCO2:Cheetos-B-HCO2:Cheetos-B
</td>
<td style="text-align:center;">
0.9741
</td>
<td style="text-align:center;">
NS
</td>
</tr>
</tbody>
</table>
<table class=" lightable-classic" style="font-family: &quot;Arial Narrow&quot;, &quot;Source Sans Pro&quot;, sans-serif; margin-left: auto; margin-right: auto;">
<caption>
Significance Letter Groups
</caption>
<thead>
<tr>
<th style="text-align:left;font-weight: bold;">
</th>
<th style="text-align:center;font-weight: bold;">
treatment
</th>
<th style="text-align:center;font-weight: bold;">
genotype
</th>
<th style="text-align:center;font-weight: bold;">
significance
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:left;">
3
</td>
<td style="text-align:center;">
HCO2
</td>
<td style="text-align:center;">
Cheetos-B
</td>
<td style="text-align:center;">
a
</td>
</tr>
<tr>
<td style="text-align:left;">
5
</td>
<td style="text-align:center;">
HCO2
</td>
<td style="text-align:center;">
MB-C
</td>
<td style="text-align:center;">
a
</td>
</tr>
<tr>
<td style="text-align:left;">
4
</td>
<td style="text-align:center;">
LCO2
</td>
<td style="text-align:center;">
Cheetos-B
</td>
<td style="text-align:center;">
ab
</td>
</tr>
<tr>
<td style="text-align:left;">
1
</td>
<td style="text-align:center;">
HCO2
</td>
<td style="text-align:center;">
AC-2
</td>
<td style="text-align:center;">
ab
</td>
</tr>
<tr>
<td style="text-align:left;">
7
</td>
<td style="text-align:center;">
HCO2
</td>
<td style="text-align:center;">
SI-A
</td>
<td style="text-align:center;">
bc
</td>
</tr>
<tr>
<td style="text-align:left;">
6
</td>
<td style="text-align:center;">
LCO2
</td>
<td style="text-align:center;">
MB-C
</td>
<td style="text-align:center;">
cd
</td>
</tr>
<tr>
<td style="text-align:left;">
8
</td>
<td style="text-align:center;">
LCO2
</td>
<td style="text-align:center;">
SI-A
</td>
<td style="text-align:center;">
cd
</td>
</tr>
<tr>
<td style="text-align:left;">
2
</td>
<td style="text-align:center;">
LCO2
</td>
<td style="text-align:center;">
AC-2
</td>
<td style="text-align:center;">
d
</td>
</tr>
</tbody>
</table>

The mean calcification rate in the HCO2 group was mean 0.316 (SD =
0.139) mg/g/day, whereas the mean in the LCO2 group was 0.569 (SD =
0.237). A Student two-samples t-test showed that the difference was
statistically significant, t(87) = -6.194, p &lt; 0.0001, d = -1.314.
Thus, the ocean acidification group saw on average a 44% reduction in
calcification rates.

## Tank Effects

We saw above that tank conditions were significantly different among
treatment groups, but not individual aquariums within treatment. We also
saw that calcification rates were significantly different among
treatment groups. Here I am analyzing tank effects on the calcification
rate and investigating if calcification rates were significantly
different between aquariums within the same treatment group.

<img src="/notebook/images/ulinkGrowth2022/tank effects graph-1.png" width="90%" style="display: block; margin: auto;" /><img src="/notebook/images/ulinkGrowth2022/tank effects graph-2.png" width="90%" style="display: block; margin: auto;" />

### Tank Effects Statistics

<table class=" lightable-classic" style="font-family: &quot;Arial Narrow&quot;, &quot;Source Sans Pro&quot;, sans-serif; margin-left: auto; margin-right: auto;">
<caption>
Significance testing of tank effect on calcification
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
dailyG
</td>
<td style="text-align:center;">
13
</td>
<td style="text-align:center;">
15
</td>
<td style="text-align:center;">
24
</td>
<td style="text-align:center;">
22
</td>
<td style="text-align:center;">
-0.482
</td>
<td style="text-align:center;">
42.209
</td>
<td style="text-align:center;">
0.632
</td>
<td style="text-align:center;">
0.632
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
dailyG
</td>
<td style="text-align:center;">
14
</td>
<td style="text-align:center;">
16
</td>
<td style="text-align:center;">
22
</td>
<td style="text-align:center;">
21
</td>
<td style="text-align:center;">
1.456
</td>
<td style="text-align:center;">
40.856
</td>
<td style="text-align:center;">
0.153
</td>
<td style="text-align:center;">
0.153
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
calcification rates. Including this random effect decreased the AIC from
66 to 31 as compared to a fixed-effects only model, and therefore the
random tank effect should be included for analysis.

As a reminder, here is the fixed effects model as shown above:

``` r
modFixed <- totalGrowth %>%
  aov(dailyG ~ genotype*treatment, data=.)

modFixed %>%
  summary()
```

    ##                    Df Sum Sq Mean Sq F value   Pr(>F)    
    ## genotype            3 0.9975  0.3325  13.298 3.86e-07 ***
    ## treatment           1 1.2904  1.2904  51.605 2.97e-10 ***
    ## genotype:treatment  3 0.3311  0.1104   4.413  0.00631 ** 
    ## Residuals          81 2.0254  0.0250                     
    ## ---
    ## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1

Here is the mixed effects model with the tank identity set as a random
factor to give each tank its own, random intercept. Notice, including
the random effects decreases the absolute value of the AIC. Therefore,
this new model better describes the data.

``` r
modRandom <- totalGrowth %>%
  lmerTest::lmer(dailyG ~ genotype * treatment + (1|tank),
                 data=.)
modRandom %>%
  anova()
```

    ## Type III Analysis of Variance Table with Satterthwaite's method
    ##                     Sum Sq Mean Sq NumDF  DenDF F value    Pr(>F)    
    ## genotype           0.96092 0.32031     3 79.039 13.2105 4.486e-07 ***
    ## treatment          0.49517 0.49517     1  2.061 20.4225  0.043159 *  
    ## genotype:treatment 0.32747 0.10916     3 79.039  4.5019  0.005729 ** 
    ## ---
    ## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1

``` r
AIC(modFixed, modRandom)
```

    ##           df       AIC
    ## modFixed   9 -66.10356
    ## modRandom 10 -30.71757

Tukey post-hoc analysis of the mixed effects model:

<table class=" lightable-classic" style="font-family: &quot;Arial Narrow&quot;, &quot;Source Sans Pro&quot;, sans-serif; margin-left: auto; margin-right: auto;">
<caption>
Pairwise comparison of genotypes’ sensitivity to OA
</caption>
<thead>
<tr>
<th style="text-align:center;font-weight: bold;">
pairwise
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
adj.p.value
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:center;font-weight: bold;color: white !important;background-color: red !important;">
(AC-2 HCO2) - (AC-2 LCO2)
</td>
<td style="text-align:center;font-weight: bold;color: white !important;background-color: red !important;">
-0.3942
</td>
<td style="text-align:center;font-weight: bold;color: white !important;background-color: red !important;">
0.0741
</td>
<td style="text-align:center;font-weight: bold;color: white !important;background-color: red !important;">
-5.3202
</td>
<td style="text-align:center;font-weight: bold;color: white !important;background-color: red !important;">
0.0066
</td>
</tr>
<tr>
<td style="text-align:center;">
(Cheetos-B HCO2) - (Cheetos-B LCO2)
</td>
<td style="text-align:center;">
-0.0820
</td>
<td style="text-align:center;">
0.0903
</td>
<td style="text-align:center;">
-0.9082
</td>
<td style="text-align:center;">
0.9815
</td>
</tr>
<tr>
<td style="text-align:center;font-weight: bold;color: white !important;background-color: red !important;">
(MB-C HCO2) - (MB-C LCO2)
</td>
<td style="text-align:center;font-weight: bold;color: white !important;background-color: red !important;">
-0.3045
</td>
<td style="text-align:center;font-weight: bold;color: white !important;background-color: red !important;">
0.0751
</td>
<td style="text-align:center;font-weight: bold;color: white !important;background-color: red !important;">
-4.0544
</td>
<td style="text-align:center;font-weight: bold;color: white !important;background-color: red !important;">
0.0333
</td>
</tr>
<tr>
<td style="text-align:center;">
(SI-A HCO2) - (SI-A LCO2)
</td>
<td style="text-align:center;">
-0.1365
</td>
<td style="text-align:center;">
0.0708
</td>
<td style="text-align:center;">
-1.9281
</td>
<td style="text-align:center;">
0.5701
</td>
</tr>
</tbody>
</table>

Pattern is the same as above with the fixed effects. Significance has
decreased (p values increased) for AC-2 and MB-C, suggesting that there
was some variability between tanks in the same treatment (T13 v T15 and
T14 v T16) but that this within treatment variability was not
significant enough to change our conclusions. Thus, we fail to reject
our null hypothesis that there are significant differences between
individual genotype’s susceptibility to OA.

## Powder Available

<img src="/notebook/images/ulinkGrowth2022/powder available-1.png" width="90%" style="display: block; margin: auto;" />

The amount of new aragonite precipated is visualized above. Horizontal
lines denote thresholds for tests: &gt;500mg = green (complete suite
including XRD), &gt;120 mg = orange (complete suite sans XRD), &gt;50mg
= red (TGA and isotope only).

# Linear Extension

<img src="/notebook/images/ulinkGrowth2022/LE graphs-1.png" width="90%" style="display: block; margin: auto;" /><img src="/notebook/images/ulinkGrowth2022/LE graphs-2.png" width="90%" style="display: block; margin: auto;" /><img src="/notebook/images/ulinkGrowth2022/LE graphs-3.png" width="90%" style="display: block; margin: auto;" />

<table class=" lightable-classic" style="font-family: &quot;Arial Narrow&quot;, &quot;Source Sans Pro&quot;, sans-serif; margin-left: auto; margin-right: auto;">
<caption>
Means of Treatment
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
45
</td>
<td style="text-align:center;">
0.005
</td>
<td style="text-align:center;">
0.004
</td>
</tr>
<tr>
<td style="text-align:center;">
LCO2
</td>
<td style="text-align:center;">
39
</td>
<td style="text-align:center;">
0.006
</td>
<td style="text-align:center;">
0.004
</td>
</tr>
</tbody>
</table>
<table class=" lightable-classic" style="font-family: &quot;Arial Narrow&quot;, &quot;Source Sans Pro&quot;, sans-serif; margin-left: auto; margin-right: auto;">
<caption>
Stats of Treatment
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
45
</td>
<td style="text-align:center;">
39
</td>
<td style="text-align:center;">
-1.5559
</td>
<td style="text-align:center;">
82
</td>
<td style="text-align:center;">
0.124
</td>
<td style="text-align:center;">
ns
</td>
</tr>
</tbody>
</table>
<table class=" lightable-classic" style="font-family: &quot;Arial Narrow&quot;, &quot;Source Sans Pro&quot;, sans-serif; margin-left: auto; margin-right: auto;">
<caption>
Effect Size of Treatment
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
-0.3404
</td>
<td style="text-align:center;">
45
</td>
<td style="text-align:center;">
39
</td>
<td style="text-align:center;">
small
</td>
</tr>
</tbody>
</table>
<table class=" lightable-classic" style="font-family: &quot;Arial Narrow&quot;, &quot;Source Sans Pro&quot;, sans-serif; margin-left: auto; margin-right: auto;">
<caption>
TukeyHSD Results of Anova
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
treatment:genotype
</td>
<td style="text-align:center;font-weight: bold;color: white !important;background-color: red !important;">
LCO2:SI-A-HCO2:SI-A
</td>
<td style="text-align:center;font-weight: bold;color: white !important;background-color: red !important;">
0.0012
</td>
<td style="text-align:center;font-weight: bold;color: white !important;background-color: red !important;">
xx
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
0.0943
</td>
<td style="text-align:center;">
NS
</td>
</tr>
<tr>
<td style="text-align:center;">
genotype
</td>
<td style="text-align:center;">
MB-C-Cheetos-B
</td>
<td style="text-align:center;">
0.3472
</td>
<td style="text-align:center;">
NS
</td>
</tr>
<tr>
<td style="text-align:center;">
genotype
</td>
<td style="text-align:center;">
SI-A-MB-C
</td>
<td style="text-align:center;">
0.4989
</td>
<td style="text-align:center;">
NS
</td>
</tr>
<tr>
<td style="text-align:center;">
genotype
</td>
<td style="text-align:center;">
Cheetos-B-AC-2
</td>
<td style="text-align:center;">
0.5543
</td>
<td style="text-align:center;">
NS
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
0.7510
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
0.9477
</td>
<td style="text-align:center;">
NS
</td>
</tr>
<tr>
<td style="text-align:center;">
genotype
</td>
<td style="text-align:center;">
SI-A-Cheetos-B
</td>
<td style="text-align:center;">
0.9671
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
LCO2:Cheetos-B-HCO2:Cheetos-B
</td>
<td style="text-align:center;">
1.0000
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
<table class=" lightable-classic" style="font-family: &quot;Arial Narrow&quot;, &quot;Source Sans Pro&quot;, sans-serif; margin-left: auto; margin-right: auto;">
<caption>
Significance Letter Groups
</caption>
<thead>
<tr>
<th style="text-align:left;font-weight: bold;">
</th>
<th style="text-align:center;font-weight: bold;">
treatment
</th>
<th style="text-align:center;font-weight: bold;">
genotype
</th>
<th style="text-align:center;font-weight: bold;">
significance
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:left;">
7
</td>
<td style="text-align:center;">
HCO2
</td>
<td style="text-align:center;">
SI-A
</td>
<td style="text-align:center;">
a
</td>
</tr>
<tr>
<td style="text-align:left;">
4
</td>
<td style="text-align:center;">
LCO2
</td>
<td style="text-align:center;">
Cheetos-B
</td>
<td style="text-align:center;">
ab
</td>
</tr>
<tr>
<td style="text-align:left;">
3
</td>
<td style="text-align:center;">
HCO2
</td>
<td style="text-align:center;">
Cheetos-B
</td>
<td style="text-align:center;">
ab
</td>
</tr>
<tr>
<td style="text-align:left;">
2
</td>
<td style="text-align:center;">
LCO2
</td>
<td style="text-align:center;">
AC-2
</td>
<td style="text-align:center;">
ab
</td>
</tr>
<tr>
<td style="text-align:left;">
6
</td>
<td style="text-align:center;">
LCO2
</td>
<td style="text-align:center;">
MB-C
</td>
<td style="text-align:center;">
ab
</td>
</tr>
<tr>
<td style="text-align:left;">
5
</td>
<td style="text-align:center;">
HCO2
</td>
<td style="text-align:center;">
MB-C
</td>
<td style="text-align:center;">
ab
</td>
</tr>
<tr>
<td style="text-align:left;">
1
</td>
<td style="text-align:center;">
HCO2
</td>
<td style="text-align:center;">
AC-2
</td>
<td style="text-align:center;">
b
</td>
</tr>
<tr>
<td style="text-align:left;">
8
</td>
<td style="text-align:center;">
LCO2
</td>
<td style="text-align:center;">
SI-A
</td>
<td style="text-align:center;">
b
</td>
</tr>
</tbody>
</table>

The mean linear extension rate in the HCO2 group was mean 0.005 (SD =
0.004) mm/cm/day, whereas the mean in the LCO2 group was 0.006 (SD =
0.004). A Student two-samples t-test showed that the difference was not
statistically significant, t(82) = -1.556, p =0.124, d = -0.34.

## Tank Effects

<img src="/notebook/images/ulinkGrowth2022/LE tank effects-1.png" width="90%" style="display: block; margin: auto;" />

<table class=" lightable-classic" style="font-family: &quot;Arial Narrow&quot;, &quot;Source Sans Pro&quot;, sans-serif; margin-left: auto; margin-right: auto;">
<caption>
Significance testing of tank effect on Linear Extension Rates
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
prod
</td>
<td style="text-align:center;">
13
</td>
<td style="text-align:center;">
15
</td>
<td style="text-align:center;">
23
</td>
<td style="text-align:center;">
22
</td>
<td style="text-align:center;">
-0.911
</td>
<td style="text-align:center;">
38.599
</td>
<td style="text-align:center;">
0.368
</td>
<td style="text-align:center;">
0.368
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
prod
</td>
<td style="text-align:center;">
14
</td>
<td style="text-align:center;">
16
</td>
<td style="text-align:center;">
21
</td>
<td style="text-align:center;">
18
</td>
<td style="text-align:center;">
1.227
</td>
<td style="text-align:center;">
34.931
</td>
<td style="text-align:center;">
0.228
</td>
<td style="text-align:center;">
0.228
</td>
<td style="text-align:center;">
ns
</td>
</tr>
</tbody>
</table>

    ## # A tibble: 1 x 4
    ##   term               contrast            adj.p.value significance
    ##   <chr>              <chr>                     <dbl> <chr>       
    ## 1 treatment:genotype LCO2:SI-A-HCO2:SI-A      0.0012 xx

    ## Type III Analysis of Variance Table with Satterthwaite's method
    ##                        Sum Sq    Mean Sq NumDF  DenDF F value  Pr(>F)   
    ## genotype           4.3893e-05 1.4631e-05     3 74.015  1.1832 0.32200   
    ## treatment          1.7696e-05 1.7696e-05     1  2.059  1.4311 0.35119   
    ## genotype:treatment 2.1560e-04 7.1866e-05     3 74.015  5.8119 0.00127 **
    ## ---
    ## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1

<table class=" lightable-classic" style="font-family: &quot;Arial Narrow&quot;, &quot;Source Sans Pro&quot;, sans-serif; margin-left: auto; margin-right: auto;">
<caption>
Pairwise comparison of genotypes’ sensitivity to OA
</caption>
<thead>
<tr>
<th style="text-align:center;font-weight: bold;">
pairwise
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
adj.p.value
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:center;">
(AC-2 HCO2) - (AC-2 LCO2)
</td>
<td style="text-align:center;">
0.0017
</td>
<td style="text-align:center;">
0.0015
</td>
<td style="text-align:center;">
1.1114
</td>
<td style="text-align:center;">
0.9453
</td>
</tr>
<tr>
<td style="text-align:center;">
(Cheetos-B HCO2) - (Cheetos-B LCO2)
</td>
<td style="text-align:center;">
0.0004
</td>
<td style="text-align:center;">
0.0019
</td>
<td style="text-align:center;">
0.1980
</td>
<td style="text-align:center;">
1.0000
</td>
</tr>
<tr>
<td style="text-align:center;">
(MB-C HCO2) - (MB-C LCO2)
</td>
<td style="text-align:center;">
0.0000
</td>
<td style="text-align:center;">
0.0015
</td>
<td style="text-align:center;">
0.0210
</td>
<td style="text-align:center;">
1.0000
</td>
</tr>
<tr>
<td style="text-align:center;font-weight: bold;color: white !important;background-color: red !important;">
(SI-A HCO2) - (SI-A LCO2)
</td>
<td style="text-align:center;font-weight: bold;color: white !important;background-color: red !important;">
-0.0062
</td>
<td style="text-align:center;font-weight: bold;color: white !important;background-color: red !important;">
0.0015
</td>
<td style="text-align:center;font-weight: bold;color: white !important;background-color: red !important;">
-4.1839
</td>
<td style="text-align:center;font-weight: bold;color: white !important;background-color: red !important;">
0.0117
</td>
</tr>
</tbody>
</table>

    ##           df       AIC
    ## modFixed   9 -700.8051
    ## modRandom 10 -604.1854

AIC tells us the mixed effects model better describes the data. Post-hoc
testing further tells us that indeed SI-A’s linear extension rates were
significantly different between treatments (p&lt;0.05), yet all other
genotype’s were not.

<img src="/notebook/images/ulinkGrowth2022/total extension-1.png" width="90%" style="display: block; margin: auto;" />

# Takeaways and Next Steps

Overall growth was less than hoped for. However, there is enough new
skeleton for nearly all the powder tests that we want to conduct: FTIR,
TGA, boron isotopes, and Raman. There is enough powder to run XRD on
some samples from genotypes AC-2 (OA=2, control=8) and SI-A (control=5)
and a single sample of Cheetos-B. The lack of even replication though
may preclude analysis of XRD. For nanoindentation tests, we should have
enough new growth to run on a majority of samples.

Linear extension was measured by maximum vertical height as measured
with calipers. We additionally have initial 3d scans of all corals and
post 3d scans of a subset of 48 corals (n=3 per genotype per tank). From
this data, we can extract surface area to volume ratios and see how this
changed among genotypes and treatments. This analysis still needs to be
done. We can also more accurately measure total linear extension of the
corals which may have curving or branching morphologies.

## Plating of Tissue

Among control corals, I visually noticed significant plating of tissue
and a veneer of aragonite above the acrylic tags. This was almost
completely absent in OA corals. I can take photos of each coral and
calculate surface area of plating.

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
