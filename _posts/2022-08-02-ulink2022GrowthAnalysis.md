---
layout: post
title:  "Title"
author: "Patrick M Kiel"
date: '2022-08-02'
categories: [research]
description: "Description"
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

![](/notebook/images/ulinkGrowth2022/calcification%20graphs-1.png)<!-- -->![](/notebook/images/ulinkGrowth2022/calcification%20graphs-2.png)<!-- -->

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

<!-- -->

    ## # A tibble: 2 x 5
    ##   treatment variable     n  mean    sd
    ##   <chr>     <chr>    <dbl> <dbl> <dbl>
    ## 1 HCO2      dailyG      46 0.334 0.14 
    ## 2 LCO2      dailyG      43 0.568 0.249

    ## # A tibble: 1 x 9
    ##   .y.    group1 group2    n1    n2 statistic    df           p p.signif
    ##   <chr>  <chr>  <chr>  <int> <int>     <dbl> <dbl>       <dbl> <chr>   
    ## 1 dailyG HCO2   LCO2      46    43     -5.51    87 0.000000357 ****

    ## # A tibble: 1 x 7
    ##   .y.    group1 group2 effsize    n1    n2 magnitude
    ## * <chr>  <chr>  <chr>    <dbl> <int> <int> <ord>    
    ## 1 dailyG HCO2   LCO2     -1.17    46    43 large

    ##   Tukey multiple comparisons of means
    ##     95% family-wise confidence level
    ## 
    ## Fit: aov(formula = dailyG ~ genotype, data = .)
    ## 
    ## $genotype
    ##                       diff         lwr         upr     p adj
    ## Cheetos-B-AC-2 -0.37195774 -0.67738416 -0.06653133 0.0116575
    ## MB-C-AC-2      -0.19046974 -0.44167635  0.06073686 0.1930452
    ## SI-A-AC-2      -0.06758806 -0.31006126  0.17488514 0.8769675
    ## MB-C-Cheetos-B  0.18148800 -0.11941333  0.48238933 0.3803720
    ## SI-A-Cheetos-B  0.30436969  0.01072006  0.59801931 0.0397206
    ## SI-A-MB-C       0.12288169 -0.11386621  0.35962958 0.5113356

<table class=" lightable-classic" style='font-family: "Arial Narrow", "Source Sans Pro", sans-serif; margin-left: auto; margin-right: auto;'>
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

-   </td>
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

    -   </td>
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

        -   </td>
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

            -   </td>
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

                -   </td>
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

                    -   </td>
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
TukeyHSD Results of Anova
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
HCO2
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
HCO2
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
LCO2
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
HCO2
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
HCO2
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
LCO2
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
LCO2
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
LCO2
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
acidification group saw on average a 0% reduction in calcification
rates.

# Linear Extension

</div>
