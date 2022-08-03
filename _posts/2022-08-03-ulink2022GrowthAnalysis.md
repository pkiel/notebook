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
  output_file = paste0(Sys.Date(), "-",
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
to proceed forward with all our tests.

# Calcification Analysis

<img src="/notebook/images/ulinkGrowth2022/growth graphs-1.png" width="60%" style="display: block; margin: auto;" /><img src="/notebook/images/ulinkGrowth2022/growth graphs-2.png" width="60%" style="display: block; margin: auto;" />

Following April 15 (Weeky 5), the declining health of the corals
stabilized and began to split amongst treatment groups.

<img src="/notebook/images/ulinkGrowth2022/calcification graphs-1.png" width="60%" style="display: block; margin: auto;" /><img src="/notebook/images/ulinkGrowth2022/calcification graphs-2.png" width="60%" style="display: block; margin: auto;" />

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
0.307
</td>
<td style="text-align:center;">
0.140
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
0.560
</td>
<td style="text-align:center;">
0.257
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
-5.8211
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
-1.2348
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
<td style="text-align:center;">
treatment
</td>
<td style="text-align:center;">
LCO2-HCO2
</td>
<td style="text-align:center;">
0.0000
</td>
<td style="text-align:center;">
xxx
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
0.0001
</td>
<td style="text-align:center;">
xxx
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
0.0003
</td>
<td style="text-align:center;">
xxx
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
0.0009
</td>
<td style="text-align:center;">
xxx
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
0.0051
</td>
<td style="text-align:center;">
xx
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
0.0122
</td>
<td style="text-align:center;">
x
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
0.0797
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
0.6143
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
0.9514
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
0.9917
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
abc
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
bcd
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

The mean calcification rate in the HCO2 group was mean 0.307 (SD = 0.14)
mg/g/day, whereas the mean in the LCO2 group was 0.56 (SD = 0.257). A
Student two-samples t-test showed that the difference was statistically
significant, t(87) = -5.821, p &lt; 0.0001, d = -1.235. Thus, the ocean
acidification group saw on average a 45% reduction in calcification
rates.

## Powder Available

<img src="/notebook/images/ulinkGrowth2022/powder available-1.png" width="60%" style="display: block; margin: auto;" />

The amount of new aragonite precipated is visualized above. Horizontal
lines denote thresholds for tests: &gt;500mg = green (complete suite
including XRD), &gt;120 mg = orange (complete suite sans XRD), &gt;50mg
= red (TGA and isotope only).

# Linear Extension

<img src="/notebook/images/ulinkGrowth2022/LE graphs-1.png" width="60%" style="display: block; margin: auto;" /><img src="/notebook/images/ulinkGrowth2022/LE graphs-2.png" width="60%" style="display: block; margin: auto;" />

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
<td style="text-align:center;">
treatment:genotype
</td>
<td style="text-align:center;">
LCO2:SI-A-HCO2:SI-A
</td>
<td style="text-align:center;">
0.0012
</td>
<td style="text-align:center;">
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

<img src="/notebook/images/ulinkGrowth2022/total extension-1.png" width="60%" style="display: block; margin: auto;" />

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
