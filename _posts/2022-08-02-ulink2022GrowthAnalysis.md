---
layout: post
title:  "ULink 2022 Genotype x OA Growth Analysis"
author: "Patrick M Kiel"
date: '2022-08-02'
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

# Calcification Analysis

<img src="/notebook/images/ulinkGrowth2022/calcification graphs-1.png" width="40%" style="display: block; margin: auto;" /><img src="/notebook/images/ulinkGrowth2022/calcification graphs-2.png" width="40%" style="display: block; margin: auto;" />

There is some obvious genet-specific responses.

1.  Cheetos-B calcification rate was nearly identical across HCO2 and
    LCO2 groups. This genet also had high initial mortality and the
    worst survivorship rate throughout the experiment. It is entirely
    possible that this genotype did not do well in the aquariums and its
    diminished calcification rate is an effect of overall health and not
    treatment.

2.  SI-A and AC-2 had the highest average calcification rates and there
    was no significant difference between these two genotypes.

3.  When looking at just controls, the only significant different
    genotype is Cheetos-B. Thus, there is a difference in sensitivity to
    OA but no observable differences in ambient conditions.

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
variable
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
dailyG
</td>
<td style="text-align:center;">
46
</td>
<td style="text-align:center;">
0.334
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
dailyG
</td>
<td style="text-align:center;">
43
</td>
<td style="text-align:center;">
0.568
</td>
<td style="text-align:center;">
0.249
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
-5.512
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
-1.1692
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
\*\*\*
</td>
</tr>
<tr>
<td style="text-align:center;">
treatment:genotype
</td>
<td style="text-align:center;">
HCO2:Cheetos-B-LCO2:AC-2
</td>
<td style="text-align:center;">
0.0000
</td>
<td style="text-align:center;">
\*\*\*
</td>
</tr>
<tr>
<td style="text-align:center;">
treatment:genotype
</td>
<td style="text-align:center;">
HCO2:MB-C-LCO2:AC-2
</td>
<td style="text-align:center;">
0.0000
</td>
<td style="text-align:center;">
\*\*\*
</td>
</tr>
<tr>
<td style="text-align:center;">
treatment:genotype
</td>
<td style="text-align:center;">
LCO2:SI-A-HCO2:Cheetos-B
</td>
<td style="text-align:center;">
0.0000
</td>
<td style="text-align:center;">
\*\*\*
</td>
</tr>
<tr>
<td style="text-align:center;">
treatment:genotype
</td>
<td style="text-align:center;">
LCO2:SI-A-HCO2:MB-C
</td>
<td style="text-align:center;">
0.0000
</td>
<td style="text-align:center;">
\*\*\*
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
0.0004
</td>
<td style="text-align:center;">
\*\*\*
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
0.0004
</td>
<td style="text-align:center;">
\*\*\*
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
0.0008
</td>
<td style="text-align:center;">
\*\*\*
</td>
</tr>
<tr>
<td style="text-align:center;">
treatment:genotype
</td>
<td style="text-align:center;">
LCO2:Cheetos-B-LCO2:AC-2
</td>
<td style="text-align:center;">
0.0020
</td>
<td style="text-align:center;">
\*\*
</td>
</tr>
<tr>
<td style="text-align:center;">
treatment:genotype
</td>
<td style="text-align:center;">
LCO2:SI-A-HCO2:AC-2
</td>
<td style="text-align:center;">
0.0051
</td>
<td style="text-align:center;">
\*\*
</td>
</tr>
<tr>
<td style="text-align:center;">
treatment:genotype
</td>
<td style="text-align:center;">
LCO2:SI-A-LCO2:Cheetos-B
</td>
<td style="text-align:center;">
0.0151
</td>
<td style="text-align:center;">
\*
</td>
</tr>
<tr>
<td style="text-align:center;">
treatment:genotype
</td>
<td style="text-align:center;">
HCO2:SI-A-LCO2:AC-2
</td>
<td style="text-align:center;">
0.0156
</td>
<td style="text-align:center;">
\*
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
0.0161
</td>
<td style="text-align:center;">
\*
</td>
</tr>
<tr>
<td style="text-align:center;">
treatment:genotype
</td>
<td style="text-align:center;">
LCO2:MB-C-HCO2:Cheetos-B
</td>
<td style="text-align:center;">
0.0184
</td>
<td style="text-align:center;">
\*
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
0.0235
</td>
<td style="text-align:center;">
\*
</td>
</tr>
<tr>
<td style="text-align:center;">
genotype
</td>
<td style="text-align:center;">
MB-C-AC-2
</td>
<td style="text-align:center;">
0.0303
</td>
<td style="text-align:center;">
\*
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
0.1224
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
HCO2:SI-A-HCO2:Cheetos-B
</td>
<td style="text-align:center;">
0.1424
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
LCO2:MB-C-LCO2:AC-2
</td>
<td style="text-align:center;">
0.1772
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
HCO2:SI-A-HCO2:MB-C
</td>
<td style="text-align:center;">
0.1870
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
LCO2:MB-C-LCO2:Cheetos-B
</td>
<td style="text-align:center;">
0.4524
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
0.4535
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
LCO2:MB-C-HCO2:AC-2
</td>
<td style="text-align:center;">
0.4956
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
LCO2:SI-A-LCO2:MB-C
</td>
<td style="text-align:center;">
0.6427
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
HCO2:Cheetos-B-HCO2:AC-2
</td>
<td style="text-align:center;">
0.6949
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
HCO2:MB-C-HCO2:AC-2
</td>
<td style="text-align:center;">
0.8038
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
HCO2:SI-A-LCO2:Cheetos-B
</td>
<td style="text-align:center;">
0.8788
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
HCO2:SI-A-HCO2:AC-2
</td>
<td style="text-align:center;">
0.9546
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
LCO2:SI-A-LCO2:AC-2
</td>
<td style="text-align:center;">
0.9799
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
0.9799
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
HCO2:SI-A-LCO2:MB-C
</td>
<td style="text-align:center;">
0.9844
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
HCO2:MB-C-LCO2:Cheetos-B
</td>
<td style="text-align:center;">
0.9948
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
0.9987
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
LCO2:Cheetos-B-HCO2:AC-2
</td>
<td style="text-align:center;">
0.9998
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
HCO2:MB-C-HCO2:Cheetos-B
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
genotype
</th>
<th style="text-align:center;font-weight: bold;">
emmean
</th>
<th style="text-align:center;font-weight: bold;">
SE
</th>
<th style="text-align:center;font-weight: bold;">
df
</th>
<th style="text-align:center;font-weight: bold;">
lower.CL
</th>
<th style="text-align:center;font-weight: bold;">
upper.CL
</th>
<th style="text-align:center;font-weight: bold;">
.group
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:left;">
3
</td>
<td style="text-align:center;">
Cheetos-B
</td>
<td style="text-align:center;">
0.2348
</td>
<td style="text-align:center;">
0.0589
</td>
<td style="text-align:center;">
81
</td>
<td style="text-align:center;">
0.1177
</td>
<td style="text-align:center;">
0.3519
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
MB-C
</td>
<td style="text-align:center;">
0.2553
</td>
<td style="text-align:center;">
0.0533
</td>
<td style="text-align:center;">
81
</td>
<td style="text-align:center;">
0.1494
</td>
<td style="text-align:center;">
0.3613
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
Cheetos-B
</td>
<td style="text-align:center;">
0.3232
</td>
<td style="text-align:center;">
0.0721
</td>
<td style="text-align:center;">
81
</td>
<td style="text-align:center;">
0.1797
</td>
<td style="text-align:center;">
0.4667
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
AC-2
</td>
<td style="text-align:center;">
0.3641
</td>
<td style="text-align:center;">
0.0490
</td>
<td style="text-align:center;">
81
</td>
<td style="text-align:center;">
0.2666
</td>
<td style="text-align:center;">
0.4615
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
SI-A
</td>
<td style="text-align:center;">
0.4404
</td>
<td style="text-align:center;">
0.0490
</td>
<td style="text-align:center;">
81
</td>
<td style="text-align:center;">
0.3429
</td>
<td style="text-align:center;">
0.5379
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
MB-C
</td>
<td style="text-align:center;">
0.5047
</td>
<td style="text-align:center;">
0.0510
</td>
<td style="text-align:center;">
81
</td>
<td style="text-align:center;">
0.4033
</td>
<td style="text-align:center;">
0.6061
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
SI-A
</td>
<td style="text-align:center;">
0.6276
</td>
<td style="text-align:center;">
0.0472
</td>
<td style="text-align:center;">
81
</td>
<td style="text-align:center;">
0.5337
</td>
<td style="text-align:center;">
0.7215
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
AC-2
</td>
<td style="text-align:center;">
0.6952
</td>
<td style="text-align:center;">
0.0533
</td>
<td style="text-align:center;">
81
</td>
<td style="text-align:center;">
0.5892
</td>
<td style="text-align:center;">
0.8011
</td>
<td style="text-align:center;">
d
</td>
</tr>
</tbody>
</table>

The mean calcification rate in the HCO2 group was mean 0.334 (SD = 0.14)
mg/g/day, whereas the mean in the LCO2 group was 0.568 (SD = 0.249). A
Student two-samples t-test showed that the difference was statistically
significant, t(87) = -5.512, p &lt; 0.0001, d = -1.169. Thus, the ocean
acidification group saw on average a 41% reduction in calcification
rates.

# Linear Extension

</div>
