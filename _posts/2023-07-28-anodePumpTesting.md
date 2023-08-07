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
<!--   <!-- set the password here -->

–\>
<!--   if (document.getElementById('password').value === 'password') { -->
<!--     document.getElementById('HIDDENDIV').classList.remove("hidden");  -->
<!--     document.getElementById('credentials').classList.add("hidden"); // Hide the div containing the credentials -->
<!--   } else { -->
<!--     alert('Invalid Password! You cannot view this content.'); -->
<!--     password.setSelectionRange(0, password.value.length); -->
<!--   } --> <!--   return false; --> <!-- } --> <!-- ``` -->

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
slope (m), which will be used for subsequent tests.

For concentration, you can do volumetric concentration,
$C = V_{dye}/V_{sol}$. For instance a mixture of 1mL dye to 30mL RO
water would be, $C = 1/(30+1) = 1/31 = 0.0323$.

Within geom_smooth function of ggplot, you can set the method of lm to
fit the curve. It does the same thing, but only graphically.

``` r
calibration <- calibration %>%
  mutate(concentration = dye/(dye+RO))

calibration_lm <- lm(abs~concentration, data = calibration)

calibration %>%
  gplot(aes(concentration,abs)) +
  geom_point() +
  geom_smooth(se=F,method="lm")
```

Call: lm(formula = abs \~ concentration, data = calibration)

Residuals: Min 1Q Median 3Q Max -0.0026521 -0.0016951 -0.0008566
0.0012619 0.0066087

Coefficients: Estimate Std. Error t value Pr(\>\|t\|)  
(Intercept) 0.0081306 0.0009194 8.843 7.34e-07 *** concentration
8.1782272 0.0519395 157.457 \< 2e-16 *** — Signif. codes: 0 ‘***’ 0.001
’**’ 0.01 ’*’ 0.05 ‘.’ 0.1 ’ ’ 1

Residual standard error: 0.002474 on 13 degrees of freedom Multiple
R-squared: 0.9995, Adjusted R-squared: 0.9994 F-statistic: 2.479e+04 on
1 and 13 DF, p-value: \< 2.2e-16

<h5>
Figure 1. Dye standard curve absorbance at 480nm
</h5>

<img src="/notebook/images/anodePump/calibration-1.png" width="90%" style="display: block; margin: auto;" />

          sample_id round RO  dye   abs concentration volume   dye.vol

1 dye rd1 0 3000 2.969 1.000000000 3 3.0000 2 dye rd1 0 3000 2.966
1.000000000 3 3.0000 3 dye rd1 0 3000 2.966 1.000000000 3 3.0000 4
tankInit rd1 NA NA 0.001 0.008178227 71995 588.7915 5 tankInit rd1 NA NA
0.003 0.024534681 71995 1766.3744 6 tankInit rd1 NA NA 0.002 0.016356454
71995 1177.5829 7 tankDyeImmediate rd1 NA NA 0.004 0.032712909 71995
2355.1659 8 tankDyeImmediate rd1 NA NA 0.005 0.040891136 71995 2943.9573
9 tankDyeImmediate rd1 NA NA 0.004 0.032712909 71995 2355.1659 10
effluent rd1 NA NA 0.090 0.736040444 2500 1840.1011 11 effluent rd1 NA
NA 0.090 0.736040444 2500 1840.1011 12 effluent rd1 NA NA 0.088
0.719683989 2500 1799.2100 13 tank30min rd1 NA NA 0.013 0.106316953
70180 7461.3238 14 tank30min rd1 NA NA 0.014 0.114495180 70180 8035.2717
15 tank30min rd1 NA NA 0.010 0.081782272 70180 5739.4798 \# A tibble: 6
x 5 sample_id volume abs concentration dye.vol <chr> <int> <dbl> <dbl>
<dbl> 1 dye 3 2.97 1 -1175. 2 effluent 2500 0.0893 0.731 649. 3
tank30min 70180 0.0123 0.101 5901. 4 tankDyeImmediate 71995 0.00433
0.0354 1374. 5 tankInit 71995 0.002 0.0164 0 6 remaining NA NA NA 6550.

</div>
