---
layout: post
title:  "Anode Pump Testing"
author: "Patrick M Kiel"
date: '2023-07-28'
categories: [research]
description: "Testing of the anode pump with a UV-Vis spectrophotometer to improve the lab-based mineral accretion technology setup."
output:
  md_document:
    variant: gfm
    preserve_yaml: TRUE
knit: (function(inputFile, encoding) {
  rmarkdown::render(inputFile, 
  encoding = encoding, 
  output_file = paste0("2023-07-28", "-",
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

To create the calibratin curve, build a linear model with the formula
A=mC, where A is absorbance, C is concentration, and m is the molar
absorptivity. The goal with the calibration data is to estimate the
slope (m) from the known concentrations, which will be used for
subsequent tests.

For concentration, you can do volumetric concentration,
$C = V_{dye}/V_{sol}$. For instance a mixture of 1mL dye to 30mL RO
water would be, $C = 1/(30+1) = 1/31 = 0.0323$.

Within geom_smooth function of ggplot, you can set the method of lm to
fit the curve. It does the same thing, but only graphically. A good
curve goes through the origin, such that the b of the linear slope is
practically 0. That’s why we leave it out of the calculations above.
Further, the line should go through all the points, indicating a linear
relationship between concentration and absorbance.

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

<img src="/notebook/images/anodePump/calibration-1.png" width="90%" style="display: block; margin: auto;" />

<table>
<caption>
This needs to be fixed. Estimating captured dye Vol
</caption>
<thead>
<tr>
<th style="text-align:left;">
sample_id
</th>
<th style="text-align:right;">
volume
</th>
<th style="text-align:right;">
abs
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
3
</td>
<td style="text-align:right;">
2.9670000
</td>
<td style="text-align:right;">
1.0000000
</td>
<td style="text-align:right;">
-1174.5829
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
0.0893333
</td>
<td style="text-align:right;">
0.7305883
</td>
<td style="text-align:right;">
648.8878
</td>
</tr>
<tr>
<td style="text-align:left;">
tank30min
</td>
<td style="text-align:right;">
70180
</td>
<td style="text-align:right;">
0.0123333
</td>
<td style="text-align:right;">
0.1008648
</td>
<td style="text-align:right;">
5901.1088
</td>
</tr>
<tr>
<td style="text-align:left;">
tankDyeImmediate
</td>
<td style="text-align:right;">
71995
</td>
<td style="text-align:right;">
0.0043333
</td>
<td style="text-align:right;">
0.0354390
</td>
<td style="text-align:right;">
1373.8467
</td>
</tr>
<tr>
<td style="text-align:left;">
tankInit
</td>
<td style="text-align:right;">
71995
</td>
<td style="text-align:right;">
0.0020000
</td>
<td style="text-align:right;">
0.0163565
</td>
<td style="text-align:right;">
0.0000
</td>
</tr>
<tr>
<td style="text-align:left;">
remaining
</td>
<td style="text-align:right;">
NA
</td>
<td style="text-align:right;">
NA
</td>
<td style="text-align:right;">
NA
</td>
<td style="text-align:right;">
6549.9966
</td>
</tr>
</tbody>
</table>

</div>
