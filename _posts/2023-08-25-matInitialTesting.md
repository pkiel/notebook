---
layout: post
title:  "Anode Pump Testing"
author: "Patrick M Kiel"
date: '2023-08-25'
categories: [research]
description: "Testing of the mineral accretion technology device to inform preliminary experiment."
output:
  md_document:
    variant: gfm
    preserve_yaml: TRUE
knit: (function(inputFile, encoding) {
  rmarkdown::render(inputFile, 
  encoding = encoding, 
  output_file = paste0("2023-08-25", "-",
                        gsub(pattern = "\\.Rmd$",
                              "", basename(inputFile))
                        ,".md"), 
  output_dir = "../_posts") })
always_allow_html: true
---

<!-- ```{js} -->
<!-- window.onload = function() { -->
<!--     //query string in the password -->
<!--     const urlParams = new URLSearchParams(window.location.search); -->
<!--     const pass = urlParams.get('pass') -->
<!--     document.getElementById("password").value = pass; -->
<!-- }; -->
<!-- function verify() { -->
<!-- set the password here -->
<!--   if (document.getElementById('password').value === 'password') { -->
<!--     document.getElementById('HIDDENDIV').classList.remove("hidden");  -->
<!--     document.getElementById('credentials').classList.add("hidden"); // Hide the div containing the credentials -->
<!--   } else { -->
<!--     alert('Invalid Password! You cannot view this content.'); -->
<!--     password.setSelectionRange(0, password.value.length); -->
<!--   } -->
<!--   return false; -->
<!-- } -->
<!-- ``` -->
<style type="text/css">
/*Change content Display */
<!-- .hidden { -->
<!--   display: none; -->
<!-- } -->

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
<!-- <div id="credentials"> -->
<!--   <input type="text" id="password" onkeydown="if (event.keyCode == 13) verify()" /> -->
<!--   <br/> -->
<!--   <input id="button" type="button" value="Show Content" onclick="verify()" /> -->
<!-- </div> -->
<!-- The content we want to show after password -->

<div id="HIDDENDIV" class="hidden" markdown="1">

<!-- Place all chunks, text, etc here as you would a normal RMarkdown document -->

# Overview

As part of my design to implement MAT in the laboratory, I am
encapsulating the anode in a peristaltic pump to evacuate the anodic
reactants, particularly chlorine gas. The goal of this anode pump
testing is to calculate the efficiency rates of the pump and estimate
how much chlorine gas may enter the system.

As a reminder, here is the system:

<div class="sketchfab-embed-wrapper">

<iframe title="MATsetup" frameborder="0" allowfullscreen mozallowfullscreen="true" webkitallowfullscreen="true" allow="autoplay; fullscreen; xr-spatial-tracking" xr-spatial-tracking execution-while-out-of-viewport execution-while-not-rendered web-share src="https://sketchfab.com/models/1a9983e7bd37458b8810e8aee72231d1/embed" width="60%" style="height:35vh;">
</iframe>
<p style="font-size: 13px; font-weight: normal; margin: 5px; color: #4A4A4A;">
<a href="https://sketchfab.com/3d-models/matsetup-1a9983e7bd37458b8810e8aee72231d1?utm_medium=embed&utm_campaign=share-popup&utm_content=1a9983e7bd37458b8810e8aee72231d1" target="_blank" rel="nofollow" style="font-weight: bold; color: #1CAAD9;">
MATsetup </a> by
<a href="https://sketchfab.com/pkiel?utm_medium=embed&utm_campaign=share-popup&utm_content=1a9983e7bd37458b8810e8aee72231d1" target="_blank" rel="nofollow" style="font-weight: bold; color: #1CAAD9;">
pkiel </a> on
<a href="https://sketchfab.com?utm_medium=embed&utm_campaign=share-popup&utm_content=1a9983e7bd37458b8810e8aee72231d1" target="_blank" rel="nofollow" style="font-weight: bold; color: #1CAAD9;">Sketchfab</a>
</p>

</div>

## Electrochemistry Half Reactions

![Water reduction reactions producing hydrogen gas bubbles on the steel
cathode](/test.png)

1.  @ the steel cathode, oxygen/water reduction

- $O_{2(g)} + 2H_20_{(aq)} + 4e^- \rightarrow 4OH^-_{(aq)}$
- $2H_2O_{(aq)} + 2e^- \rightarrow H_{2(g)} + 2(OH)^- _{(aq)}$
- $OH^-_{(aq)} + HCO_3^{2-} \iff CO_3^{2-} + H_2O_{(aq)}$

2.  @ the platinum anode, oxidation of chloride

- $2Cl^-_{(aq)} \rightarrow Cl_{2(g)} + 2e^-$

For steel, the potential needs to be \< -0.356V/SSC (potential relative
to silver-silver chloride electrode) to be below the corrosion domain.
From -0.406 to -1.006V/SSC, the cathode is in the oxygen reduction
domain; above 1.006V/SSC, the steel is in the water reduction domain. On
a steel cathode, potentials more cathodic than −1.044 V/SCC, the pH
value at the steel–seawater interface will exceed 9.0, which may favor
the formation of brucite Mg(OH)2, which requires a minimum value of 9.3.

Further, at these higher potentials, the rate of chloride oxidation
increases. Thus, there is a two-fold advantage of operating at lower
cathodic potentials between -0.4 and -1.0V/SSC to minimize chloride
evolution and maintain within the oxygen reduction domain to precipiate
calcium carbonate and not brucite.

# Dye Testing

The end-goal of this test is to generate a table that looks like the
following:

Table 1. Idealized results for conceptual purposes only, not actual data
<table>
<thead>
<tr>
<th style="text-align:left;">
sample
</th>
<th style="text-align:right;">
total volume
</th>
<th style="text-align:right;">
dye volume
</th>
<th style="text-align:right;">
% evacuated
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:left;">
aquarium init
</td>
<td style="text-align:right;">
75000
</td>
<td style="text-align:right;">
0.0
</td>
<td style="text-align:right;">
NA
</td>
</tr>
<tr>
<td style="text-align:left;">
effluent
</td>
<td style="text-align:right;">
2500
</td>
<td style="text-align:right;">
29.9
</td>
<td style="text-align:right;">
99.7
</td>
</tr>
<tr>
<td style="text-align:left;">
tank final
</td>
<td style="text-align:right;">
72530
</td>
<td style="text-align:right;">
0.1
</td>
<td style="text-align:right;">
0.3
</td>
</tr>
</tbody>
</table>

This table shows that the initial volume of the aquarium is 75L and has
no dye. 30mL of dye were added to the aquarium while the pump was
running at 305mL/min for 8 minutes and 12 seconds, which decanted 2.5L
into a separate container. Within that 2.5L, 29.9mL of the dye was
collected and removed from the aquarium. The aquarium now has 72.53L of
solution, which contains only 0.1mL of the dye that was not collected by
the pump. Thus this idealized situation has a pump collection rat eof
99.7%

## First Test

The first test I ran on a brushed motor DC pump that was pumping at a
rate of 30mL/min. This matched the 30mL/min rate of dye I planned to
inject into the system.

<iframe width="560" height="315" src="https://www.youtube.com/embed/BzIQTHvdd6Q" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen>
</iframe>

Immediately, I noticed problems that prevented further analysis. The dye
was much denser than seawater so the majority of the dye was falling to
the bottom of the tank. The chlorine gas will be buoyant bubbles that
should follow the flow of water it is in, and so the dye is not a good
proxy to test the effiency of the pump. Further, the pump rate was far
too low to be of any use.

## Second Test

I used one of the new ERL2 peristaltic pumps which was getting a maximum
rate of 305 $\pm$ 3 mL/min (mean $\pm$ 1SD of 5 tests). I then took the
stock dye solution and measured its density to be approximately 1.16
$g \text{ } cm^-3$. I created 100mL of diluted dye stock to reach a
density of 1.03 $g \text{ } cm^-3$, by diluting with RO water to match
the density of the seawater in the aquarium. This density-mathced,
diluted dye become the new dye standard from which I measured pump
capture efficiency. I ran the following test twice, named round 1 and
round 2.

<iframe width="560" height="315" src="https://www.youtube.com/embed/gZEQghycPDY" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen>
</iframe>

First, I created a calibration curve, to linearly model the Beer-Lambert
Law, with the formula $A=\epsilon lC$, where A is absorbance, $\epsilon$
is the molar absorption coefficient, l is the path length of the cuvette
(1 cm), and C is concentration of the sample/standard. Concentration was
expressed as volume of dye per volume solution.

Since the molar absorption coefficient and path length is constant, the
terms $\epsilon * l$ can be combined into the constant m, to produce the
simplified equation A=mC. Standard concentrations bracketting the
expected concentration of the samples were prepared and plotted against
their measured absorbances to calculate the slope m.

This is done simply in R using the lm function to generate a linear
model and the geom_smooth funciton of ggplot with the method=“lm” to
plot the data.

For the standards, I expected the best case scenario to be 29mL dye/2500
mL solution = 1.2% and 1mL dye/72530 mL to be 0.001%, likely below the
detectable limit. At the worst case, no dye would be collected and the
concentration of the aquarium after the pump removed exclusively 2.5L of
seawater would be 30mL dye/72530mL solution = 0.04%. So I created
standard solutions in triplicate from 0.03 - 3.3 % to cover all
scenarios.

``` r
calibration <- calibration %>%
  mutate(concentration = dye/(dye+RO))

calibration_lm <- lm(abs~concentration, data = calibration)

calibration %>%
  gplot(aes(concentration,abs)) +
  geom_point() +
  geom_smooth(se=F,method="lm")
```

<h5>
Figure 1. Dye standard curve absorbance at 480nm
</h5>
<img src="/notebook/images/matInitialTesting/calibration-1.png" width="90%" style="display: block; margin: auto;" />
<h5>
Figure 2. Precision increases as concentration increaes
</h5>

<img src="/notebook/images/matInitialTesting/calibration-2.png" width="90%" style="display: block; margin: auto;" />
There was high degrees of precision, with a mean coefficient of
variation (CV) of 0.0504%. Nevertheless, precision decreased as
concentration decreased, evidenced by the increase of coefficient of
variation at low concentrations.

The linear function to determine concentration from absorbance fit the
Beer-Lambert assumptions, including an intercept of approximately 0 and
a high coefficient of determination ($R^2$) of 0.994.

Table 2. Round 1: Average absorbance from triplicate readings
<table>
<thead>
<tr>
<th style="text-align:left;">
sample_id
</th>
<th style="text-align:right;">
abs
</th>
<th style="text-align:right;">
sol volume
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:left;">
dye
</td>
<td style="text-align:right;">
2.9670000
</td>
<td style="text-align:right;">
3
</td>
</tr>
<tr>
<td style="text-align:left;">
tankInit
</td>
<td style="text-align:right;">
0.0020000
</td>
<td style="text-align:right;">
72000
</td>
</tr>
<tr>
<td style="text-align:left;">
tankDyeImmediate
</td>
<td style="text-align:right;">
0.0043333
</td>
<td style="text-align:right;">
72030
</td>
</tr>
<tr>
<td style="text-align:left;">
effluent
</td>
<td style="text-align:right;">
0.0893333
</td>
<td style="text-align:right;">
1800
</td>
</tr>
<tr>
<td style="text-align:left;">
tank30min
</td>
<td style="text-align:right;">
0.0123333
</td>
<td style="text-align:right;">
70230
</td>
</tr>
</tbody>
</table>
Table 3. Round 1: Subtracted tank_init, calculate C and dye.vol
<table>
<thead>
<tr>
<th style="text-align:left;">
sample_id
</th>
<th style="text-align:right;">
abs
</th>
<th style="text-align:right;">
sol volume
</th>
<th style="text-align:right;">
concentration
</th>
<th style="text-align:right;">
dye.vol
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:left;">
dye
</td>
<td style="text-align:right;">
2.9670000
</td>
<td style="text-align:right;">
3
</td>
<td style="text-align:right;">
24.2647999
</td>
<td style="text-align:right;">
72.7944
</td>
</tr>
<tr>
<td style="text-align:left;">
tankInit
</td>
<td style="text-align:right;">
0.0000000
</td>
<td style="text-align:right;">
72000
</td>
<td style="text-align:right;">
0.0000000
</td>
<td style="text-align:right;">
0.0000
</td>
</tr>
<tr>
<td style="text-align:left;">
tankDyeImmediate
</td>
<td style="text-align:right;">
0.0023333
</td>
<td style="text-align:right;">
72030
</td>
<td style="text-align:right;">
0.0190825
</td>
<td style="text-align:right;">
1374.5146
</td>
</tr>
<tr>
<td style="text-align:left;">
effluent
</td>
<td style="text-align:right;">
0.0873333
</td>
<td style="text-align:right;">
1800
</td>
<td style="text-align:right;">
0.7142318
</td>
<td style="text-align:right;">
1285.6173
</td>
</tr>
<tr>
<td style="text-align:left;">
tank30min
</td>
<td style="text-align:right;">
0.0103333
</td>
<td style="text-align:right;">
70230
</td>
<td style="text-align:right;">
0.0845083
</td>
<td style="text-align:right;">
5935.0212
</td>
</tr>
</tbody>
</table>

These numbers don’t make sense. While concentration is highest in
effluent as expected, it’s dye vol is estimated at 1.286L, which is well
above the 30mL I injected. I’m wondering if this is a problem of units?
I’m using dye/solution concentration %, but Beer-Lambert is meant for
molar concentrations. I’m looking into this some more.

</div>
