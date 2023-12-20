---
layout: post
title:  "Initial MAT Growth Rates"
author: "Patrick M Kiel"
date: '2023-12-20'
categories: [research]
description: "Investigating the initial MAT growth rates from the >1 month of buoyant weight data."
output:
  md_document:
    variant: gfm
    preserve_yaml: TRUE
knit: (function(inputFile, encoding) {
  rmarkdown::render(inputFile, 
  encoding = encoding, 
  output_file = paste0('2023-12-20', "-",
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
  if (document.getElementById('password').value === 'frankencoral') {
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
img {
margin: 0 auto;
}

table {
    width: 90%;
    border: 0px solid #fff;
    border-collapse: collapse;
    overflow-x: auto;
    margin: 0 auto;
    display: block;
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

Below is a quick analysis of the growth rates from the mineral accretion
technology (MAT) experiment. After initial kinks were ironed out, there
was about one month of growth data recorded weekly, from November 14 to
December 15.

Since some abiotic precipitate was knocked loose during each weighing
session generating non-linear growth, I used the mass change between
consecutive weighing sessions to calculate a daily growth rate for each
week. This analysis method may require me to revisit the statistics
since I am artificially inflating the n for each group (e.g., there’s
only 8 corals per group per tank, but I have about about 30 daily growth
rates when combining multiple weighing sessions). A
repeated-measurements anova design is more appropriate for this type of
analysis. However, I would expect this revised analysis to increase
p-values, further supporting my conclusions (i.e. lack of statistically
significant differences between groups).

# Controls

## How did control acrylic corals grow?

<h5>
Figure 1. Acrylic Controls Daily Mass Gain
</h5>
<img src="/notebook/images/MATinitGrowth/acrylic-growth-1.png" width="90%" style="display: block; margin: auto;" />
<h5>
Figure 2. Acrylic Controls Daily Mass Gain by Tank
</h5>
<img src="/notebook/images/MATinitGrowth/acrylic-growth-2.png" width="90%" style="display: block; margin: auto;" />
<h5>
Figure 3. Acrylic Controls Standardized Daily Growth Rate by Tank
</h5>

<img src="/notebook/images/MATinitGrowth/acrylic-growth-3.png" width="90%" style="display: block; margin: auto;" />
The average daily increase in mass of the control corals growing on an
inert, acrylic plug was 6.702 mg/day, 95% CI\[5.963, 7.44\].

We can further initial-mass standardize these growth rates to the the
initial mass of each fragment since I don’t have the surface areas just
yet, i.e. Figure 3 above, to produce an average daily growth rate of
3.75 mg/day/ initial g, 95% CI\[3.331, 4.17\]. The same conclusions are
drawn regardless of the standardization chosen, likely because the
corals are evenly mixed and of the approximate same size.

## How did the control MAT plugs abiotically grow?

<h5>
Figure 4. All MAT Controls Daily Mass Gain by Date
</h5>
<img src="/notebook/images/MATinitGrowth/control-growth-1.png" width="90%" style="display: block; margin: auto;" />
<h5>
Figure 5. Filtered MAT Controls Daily Mass Gain by Date
</h5>
<img src="/notebook/images/MATinitGrowth/control-growth-2.png" width="90%" style="display: block; margin: auto;" />
<h5>
Figure 6. Filtered MAT Controls Daily Mass Gain by Tank
</h5>
<img src="/notebook/images/MATinitGrowth/control-growth-3.png" width="90%" style="display: block; margin: auto;" />Table 1.
Tukey Multiple Comparisons Output
<table>
<thead>
<tr>
<th style="text-align:left;">
term
</th>
<th style="text-align:left;">
contrast
</th>
<th style="text-align:right;">
null.value
</th>
<th style="text-align:right;">
estimate
</th>
<th style="text-align:right;">
conf.low
</th>
<th style="text-align:right;">
conf.high
</th>
<th style="text-align:right;">
adj.p.value
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:left;">
tank
</td>
<td style="text-align:left;">
6-5
</td>
<td style="text-align:right;">
0
</td>
<td style="text-align:right;">
8.044183
</td>
<td style="text-align:right;">
-2.102672
</td>
<td style="text-align:right;">
18.191037
</td>
<td style="text-align:right;">
0.1531608
</td>
</tr>
<tr>
<td style="text-align:left;">
tank
</td>
<td style="text-align:left;">
7-5
</td>
<td style="text-align:right;">
0
</td>
<td style="text-align:right;">
6.184415
</td>
<td style="text-align:right;">
-3.078353
</td>
<td style="text-align:right;">
15.447184
</td>
<td style="text-align:right;">
0.2743877
</td>
</tr>
<tr>
<td style="text-align:left;">
tank
</td>
<td style="text-align:left;">
8-5
</td>
<td style="text-align:right;">
0
</td>
<td style="text-align:right;">
7.413559
</td>
<td style="text-align:right;">
-3.930969
</td>
<td style="text-align:right;">
18.758087
</td>
<td style="text-align:right;">
0.2915231
</td>
</tr>
<tr>
<td style="text-align:left;">
tank
</td>
<td style="text-align:left;">
7-6
</td>
<td style="text-align:right;">
0
</td>
<td style="text-align:right;">
-1.859767
</td>
<td style="text-align:right;">
-11.122536
</td>
<td style="text-align:right;">
7.403001
</td>
<td style="text-align:right;">
0.9428549
</td>
</tr>
<tr>
<td style="text-align:left;">
tank
</td>
<td style="text-align:left;">
8-6
</td>
<td style="text-align:right;">
0
</td>
<td style="text-align:right;">
-0.630624
</td>
<td style="text-align:right;">
-11.975152
</td>
<td style="text-align:right;">
10.713904
</td>
<td style="text-align:right;">
0.9986310
</td>
</tr>
<tr>
<td style="text-align:left;">
tank
</td>
<td style="text-align:left;">
8-7
</td>
<td style="text-align:right;">
0
</td>
<td style="text-align:right;">
1.229143
</td>
<td style="text-align:right;">
-9.332038
</td>
<td style="text-align:right;">
11.790324
</td>
<td style="text-align:right;">
0.9878626
</td>
</tr>
</tbody>
</table>

On the cathodes, we experienced a problem I term “electro-pop”. This is
when the calcium carbonate precipitate, growing at the interface of the
cathode and water, pushed off the coral or glue from the cathode. When
this happened, I scraped off some of the precipitate, rescored the top
of the cathode, and reglued the coral. The mass is thus altered not only
by coral growth and abiotic mineral accretion, but also by the removal
of old precipitate and the addition of new glue. I labeled these mass
changes as “reglued” and filtered them from the analysis.

Additionally, towards the end of this growth period the precipitate grew
so much that it was blocking electrical contact between the ring
terminal and the bottom of the cathode. It was visible when this
occurred since there was no longer production of hydrogen gas bubbles. I
fixed this by removing a small amount of abiotic precipitate and
cleaning the ring terminals. This small removal was approximately even
for all MAT controls and corals. While this small removal will result in
a slight decreased growth rate, these decrease should be even for both
MAT controls and corals and therefore should not impact the conclusions.
I labeled these dates as “no electric” and filtered them from the
analysis.

The average daily abiotic growth rate of the steel cathodes was 34.047
mg/day, 95% CI\[31.287, 36.808\]. There is no significant difference in
the growth rates of these MAT controls when performing a Tukey multiple
comparisons of means ($\alpha = 0.05$). These abiotic growth rates need
to be taken into account when looking at the growth rates of the MAT
corals since this abiotic growth is on average 27.345 mg more or 408%
more than just the growth of the corals on the inert acrylic plugs.

I did not present a mass-standardized growth rate here because the
relationship is identical to the daily mass gain graph (Figure 5).

# MAT Corals

We will first look at the total MAT growth and then subtract out this
average MAT growth per tank for the corals to see how they perform
against the combination of the bare cathode and acrylic controls. This
is the basis of our investigation: do corals grown with MAT grow faster
than controls after accounting for the abiotic precipitate.

## How did the MAT corals grow?

<h5>
Figure 7. All MAT Corals by Tank and Date
</h5>
<img src="/notebook/images/MATinitGrowth/mat-corals-1.png" width="90%" style="display: block; margin: auto;" />
<h5>
Figure 8. Filtered MAT Corals by Tank and Date
</h5>
<img src="/notebook/images/MATinitGrowth/mat-corals-2.png" width="90%" style="display: block; margin: auto;" />
<h5>
Figure 9. Filterd MAT Corals by Tank
</h5>
<img src="/notebook/images/MATinitGrowth/mat-corals-3.png" width="90%" style="display: block; margin: auto;" />
<h5>
Figure 10. Filtered MAT Corals’ Standardized Daily Growth Rate by Tank
</h5>
<img src="/notebook/images/MATinitGrowth/mat-corals-4.png" width="90%" style="display: block; margin: auto;" />Table
2. Tukey Multiple Groups Comparisons
<table>
<thead>
<tr>
<th style="text-align:left;">
term
</th>
<th style="text-align:left;">
contrast
</th>
<th style="text-align:right;">
null.value
</th>
<th style="text-align:right;">
estimate
</th>
<th style="text-align:right;">
conf.low
</th>
<th style="text-align:right;">
conf.high
</th>
<th style="text-align:right;">
adj.p.value
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:left;">
tank
</td>
<td style="text-align:left;">
6-5
</td>
<td style="text-align:right;">
0
</td>
<td style="text-align:right;">
-6.364825
</td>
<td style="text-align:right;">
-15.370687
</td>
<td style="text-align:right;">
2.641038
</td>
<td style="text-align:right;">
0.2590354
</td>
</tr>
<tr>
<td style="text-align:left;">
tank
</td>
<td style="text-align:left;">
7-5
</td>
<td style="text-align:right;">
0
</td>
<td style="text-align:right;">
-4.113326
</td>
<td style="text-align:right;">
-12.422919
</td>
<td style="text-align:right;">
4.196266
</td>
<td style="text-align:right;">
0.5709286
</td>
</tr>
<tr>
<td style="text-align:left;">
tank
</td>
<td style="text-align:left;">
8-5
</td>
<td style="text-align:right;">
0
</td>
<td style="text-align:right;">
-5.159968
</td>
<td style="text-align:right;">
-14.586711
</td>
<td style="text-align:right;">
4.266775
</td>
<td style="text-align:right;">
0.4853003
</td>
</tr>
<tr>
<td style="text-align:left;">
tank
</td>
<td style="text-align:left;">
7-6
</td>
<td style="text-align:right;">
0
</td>
<td style="text-align:right;">
2.251498
</td>
<td style="text-align:right;">
-6.532572
</td>
<td style="text-align:right;">
11.035568
</td>
<td style="text-align:right;">
0.9088833
</td>
</tr>
<tr>
<td style="text-align:left;">
tank
</td>
<td style="text-align:left;">
8-6
</td>
<td style="text-align:right;">
0
</td>
<td style="text-align:right;">
1.204856
</td>
<td style="text-align:right;">
-8.642684
</td>
<td style="text-align:right;">
11.052396
</td>
<td style="text-align:right;">
0.9887213
</td>
</tr>
<tr>
<td style="text-align:left;">
tank
</td>
<td style="text-align:left;">
8-7
</td>
<td style="text-align:right;">
0
</td>
<td style="text-align:right;">
-1.046642
</td>
<td style="text-align:right;">
-10.261728
</td>
<td style="text-align:right;">
8.168444
</td>
<td style="text-align:right;">
0.9909288
</td>
</tr>
</tbody>
</table>

The average daily increase in mass of the MAT corals growing on was
40.133 mg/day, 95% CI\[37.717, 42.549\].

The average initial-mass standardized daily growth rate was 1.14 mg/day/
initial g, 95% CI\[1.071, 1.21\].

## Subtracting MAT controls from the MAT Corals

We can combine the means and confidence intervals for all the corals
thus far to get a rough comparison to the MAT corals. I’m labeling this
row “combined controls” below. There’s likely a more statistically
robust way to compare the MAT to the combination of MAT controls +
acrylic controls, but for now I’ll just present this straight forward
way.

Table 3. Comparing group means and CI. Combined controls is the sum of
the bare MAT cathodes and the acrylic control corals, which is an apt
comparison to the MAT corals.
<table>
<thead>
<tr>
<th style="text-align:left;">
substrate
</th>
<th style="text-align:left;">
type
</th>
<th style="text-align:right;">
mean
</th>
<th style="text-align:right;">
lowerCI
</th>
<th style="text-align:right;">
upperCI
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:left;">
acrylic
</td>
<td style="text-align:left;">
control
</td>
<td style="text-align:right;">
6.701651
</td>
<td style="text-align:right;">
5.963499
</td>
<td style="text-align:right;">
7.439803
</td>
</tr>
<tr>
<td style="text-align:left;">
MAT
</td>
<td style="text-align:left;">
control
</td>
<td style="text-align:right;">
34.047149
</td>
<td style="text-align:right;">
31.286521
</td>
<td style="text-align:right;">
36.807777
</td>
</tr>
<tr>
<td style="text-align:left;">
combined controls
</td>
<td style="text-align:left;">
control
</td>
<td style="text-align:right;">
40.748800
</td>
<td style="text-align:right;">
37.250020
</td>
<td style="text-align:right;">
44.247580
</td>
</tr>
<tr>
<td style="text-align:left;">
MAT
</td>
<td style="text-align:left;">
experiment
</td>
<td style="text-align:right;">
40.132686
</td>
<td style="text-align:right;">
37.716597
</td>
<td style="text-align:right;">
42.548774
</td>
</tr>
</tbody>
</table>

# Takeaways

- The average growth rate of the MAT corals is indistinguishable from
  the combination of MAT controls + acrylic controls
- The abiotic precipitate grew at a rate of 5.08x the control corals.
  This is within the range (3-20x) of the increased growth rate proposed
  by some of the extreme early case studies. Some of the field studies
  by other authors which saw a more moderate 20-50% increase in growth
  rates as determined by total linear extension, falls in line with
  increases in growth rates seen on different restoration nursery
  platforms (e.g., Kuffner *et al.* 2017; O’Donnell *et al.* 2017).
- From my preliminary abiotic growth rates derived from total alkalinity
  anomaly incubations, the 3-20x increased growth rates could be
  achieved if we increased current density to greater than we used in
  this study (say 3 or 5 $A/m^2$ compared to the 1$A/m^2$ here).
  However, this would change the precipitated mineral from calcium
  carbonate to brucite.
- From this initial evidence, MAT does not increase coral growth rates,
  likely because all increases in carbonate ion concentration are
  immediately used by the abiotic precipitation occurring at the
  cathode-seawater interface.

</div>
