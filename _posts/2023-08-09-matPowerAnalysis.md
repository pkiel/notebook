---
layout: post
title:  "Mineral Accretion Technology Power Analysis"
author: "Patrick M Kiel"
date: '2023-08-09'
categories: [research]
description: "Statistical power analysis to determine the appropriate sample size for testing the efficiacy of mineral accretion technology to enhance coral growth rates."
output:
  md_document:
    variant: gfm
    preserve_yaml: TRUE
knit: (function(inputFile, encoding) {
  rmarkdown::render(inputFile, 
  encoding = encoding, 
  output_file = paste0("2023-08-09", "-",
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
    border: 1px solid #e5e5e5;
    border-collapse: collapse;
    overflow-x: scroll;
    margin: 0 auto;
    display: inherit;
}
</style>
<!-- The content we want to show after password -->

<div id="HIDDENDIV" class="hidden" markdown="1">

<!-- Place all chunks, text, etc here as you would a normal RMarkdown document -->

# Overview

My goal with this first mineral accretion technology (MAT) experiment is
to understand 1) if the technology enhances growth rates, and 2) if
certain morphologies (branching v. massive) preferentially respond to
MAT. The results from this preliminary experiment will inform subsequent
experiments, which will first identify the optimal electrochemical
conditions and then incorporate ocean acidification and genotype
effects. Since this is a preliminary experiment to robustly assess the
efficacy of MAT, I want to have adequate statistical power to setup
success for future experiments. In other words, if MAT doesn’t work, why
bother with the more arduous experiments. Thus, the goal of this
exercise is to estimate the number of fragments per species needed to
maintain appropriate statistical power.

The idea behind the morphologies responding differently to MAT is the
distance of the primary growth axis from the steel cathode. In branching
species, such as *A. cervicornis*, the fast-growing apical tip is
farthest from the cathode, where carbonates are being converted during
electrolysis. Conversely, massive coral species with their compact
morphology places the actively growing polyps more proximate to the site
of altered water chemistry. Thus, an initial hypothesis is that massive
corals will have a greater percentage increase in growth rates than
branching corals.

I want to incorporate the two most commonly used species in Florida
coral restoration, *Acropora cervicornis* (ACER) and *Pseudodiploria
strigosa* (PSTR) <u>OR</u> *Montastrea cavernosa* (MCAV). There will be
two treatment groups (electrified/non-electrified), and an n=2 for each
treatment. All parameters (presence of platinum anode, steel cathode as
the coral base structure, wires connecting everything, peristaltic pump
in the center of the aquarium, etc.) will be equal, except that the
wires will not be connected to the power supply in the non-electrified
aquaria. To account for genet-specific growth rates, I will collect four
ramets from each genet and divide equally among the four experimental
aquaria. Thus each genet will be represented twice within treatment and
once within each aquaria.

Table 1. Count of putative genets in the Caribbean and Florida
restoration networks, aggregrated from Coral Sample Registry database.
Florida data is a subset of Caribbean data.
<table>
<thead>
<tr>
<th style="text-align:left;">
Species
</th>
<th style="text-align:right;">
Caribbean
</th>
<th style="text-align:right;">
Florida
</th>
<th style="text-align:right;">
% Florida
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:left;">
Acropora cervicornis
</td>
<td style="text-align:right;">
420
</td>
<td style="text-align:right;">
327
</td>
<td style="text-align:right;">
77.9
</td>
</tr>
<tr>
<td style="text-align:left;">
Montastraea cavernosa
</td>
<td style="text-align:right;">
264
</td>
<td style="text-align:right;">
228
</td>
<td style="text-align:right;">
86.4
</td>
</tr>
<tr>
<td style="text-align:left;">
Pseudodiploria strigosa
</td>
<td style="text-align:right;">
254
</td>
<td style="text-align:right;">
225
</td>
<td style="text-align:right;">
88.6
</td>
</tr>
<tr>
<td style="text-align:left;">
Diploria labyrinthiformis
</td>
<td style="text-align:right;">
189
</td>
<td style="text-align:right;">
187
</td>
<td style="text-align:right;">
98.9
</td>
</tr>
<tr>
<td style="text-align:left;">
Colpophyllia natans
</td>
<td style="text-align:right;">
185
</td>
<td style="text-align:right;">
171
</td>
<td style="text-align:right;">
92.4
</td>
</tr>
<tr>
<td style="text-align:left;">
Meandrina meandrites
</td>
<td style="text-align:right;">
192
</td>
<td style="text-align:right;">
171
</td>
<td style="text-align:right;">
89.1
</td>
</tr>
<tr>
<td style="text-align:left;">
Orbicella faveolata
</td>
<td style="text-align:right;">
313
</td>
<td style="text-align:right;">
170
</td>
<td style="text-align:right;">
54.3
</td>
</tr>
<tr>
<td style="text-align:left;">
Eusmilia fastigiata
</td>
<td style="text-align:right;">
165
</td>
<td style="text-align:right;">
164
</td>
<td style="text-align:right;">
99.4
</td>
</tr>
<tr>
<td style="text-align:left;">
Mycetophyllia aliciae
</td>
<td style="text-align:right;">
161
</td>
<td style="text-align:right;">
161
</td>
<td style="text-align:right;">
100.0
</td>
</tr>
<tr>
<td style="text-align:left;">
Acropora palmata
</td>
<td style="text-align:right;">
504
</td>
<td style="text-align:right;">
156
</td>
<td style="text-align:right;">
31.0
</td>
</tr>
<tr>
<td style="text-align:left;">
Dichocoenia stokesii
</td>
<td style="text-align:right;">
141
</td>
<td style="text-align:right;">
139
</td>
<td style="text-align:right;">
98.6
</td>
</tr>
<tr>
<td style="text-align:left;">
Mussa angulosa
</td>
<td style="text-align:right;">
88
</td>
<td style="text-align:right;">
88
</td>
<td style="text-align:right;">
100.0
</td>
</tr>
<tr>
<td style="text-align:left;">
Pseudodiploria clivosa
</td>
<td style="text-align:right;">
62
</td>
<td style="text-align:right;">
62
</td>
<td style="text-align:right;">
100.0
</td>
</tr>
<tr>
<td style="text-align:left;">
Mycetophyllia lamarckiana
</td>
<td style="text-align:right;">
58
</td>
<td style="text-align:right;">
58
</td>
<td style="text-align:right;">
100.0
</td>
</tr>
<tr>
<td style="text-align:left;">
Orbicella annularis
</td>
<td style="text-align:right;">
82
</td>
<td style="text-align:right;">
57
</td>
<td style="text-align:right;">
69.5
</td>
</tr>
<tr>
<td style="text-align:left;">
Agaricia lamarcki
</td>
<td style="text-align:right;">
26
</td>
<td style="text-align:right;">
26
</td>
<td style="text-align:right;">
100.0
</td>
</tr>
<tr>
<td style="text-align:left;">
Millepora complanata
</td>
<td style="text-align:right;">
16
</td>
<td style="text-align:right;">
16
</td>
<td style="text-align:right;">
100.0
</td>
</tr>
<tr>
<td style="text-align:left;">
Siderastrea siderea
</td>
<td style="text-align:right;">
17
</td>
<td style="text-align:right;">
13
</td>
<td style="text-align:right;">
76.5
</td>
</tr>
<tr>
<td style="text-align:left;">
Mycetophyllia ferox
</td>
<td style="text-align:right;">
11
</td>
<td style="text-align:right;">
11
</td>
<td style="text-align:right;">
100.0
</td>
</tr>
<tr>
<td style="text-align:left;">
Stephanocoenia intersepta
</td>
<td style="text-align:right;">
10
</td>
<td style="text-align:right;">
10
</td>
<td style="text-align:right;">
100.0
</td>
</tr>
<tr>
<td style="text-align:left;">
Porites astreoides
</td>
<td style="text-align:right;">
7
</td>
<td style="text-align:right;">
7
</td>
<td style="text-align:right;">
100.0
</td>
</tr>
<tr>
<td style="text-align:left;">
Porites porites
</td>
<td style="text-align:right;">
12
</td>
<td style="text-align:right;">
5
</td>
<td style="text-align:right;">
41.7
</td>
</tr>
<tr>
<td style="text-align:left;">
Acropora prolifera
</td>
<td style="text-align:right;">
4
</td>
<td style="text-align:right;">
4
</td>
<td style="text-align:right;">
100.0
</td>
</tr>
<tr>
<td style="text-align:left;">
Dendrogyra cylindrus
</td>
<td style="text-align:right;">
49
</td>
<td style="text-align:right;">
4
</td>
<td style="text-align:right;">
8.2
</td>
</tr>
<tr>
<td style="text-align:left;">
Solenastrea bournoni
</td>
<td style="text-align:right;">
3
</td>
<td style="text-align:right;">
3
</td>
<td style="text-align:right;">
100.0
</td>
</tr>
<tr>
<td style="text-align:left;">
Oculina diffusa
</td>
<td style="text-align:right;">
2
</td>
<td style="text-align:right;">
2
</td>
<td style="text-align:right;">
100.0
</td>
</tr>
<tr>
<td style="text-align:left;">
Orbicella franksi
</td>
<td style="text-align:right;">
43
</td>
<td style="text-align:right;">
2
</td>
<td style="text-align:right;">
4.7
</td>
</tr>
<tr>
<td style="text-align:left;">
Agaricia agaricites
</td>
<td style="text-align:right;">
1
</td>
<td style="text-align:right;">
NA
</td>
<td style="text-align:right;">
0.0
</td>
</tr>
<tr>
<td style="text-align:left;">
Favia fragum
</td>
<td style="text-align:right;">
3
</td>
<td style="text-align:right;">
NA
</td>
<td style="text-align:right;">
0.0
</td>
</tr>
<tr>
<td style="text-align:left;">
Isophyllia sinuosa
</td>
<td style="text-align:right;">
1
</td>
<td style="text-align:right;">
NA
</td>
<td style="text-align:right;">
0.0
</td>
</tr>
<tr>
<td style="text-align:left;">
Meandrina jacksoni
</td>
<td style="text-align:right;">
1
</td>
<td style="text-align:right;">
NA
</td>
<td style="text-align:right;">
0.0
</td>
</tr>
<tr>
<td style="text-align:left;">
Porites divaricata
</td>
<td style="text-align:right;">
1
</td>
<td style="text-align:right;">
NA
</td>
<td style="text-align:right;">
0.0
</td>
</tr>
<tr>
<td style="text-align:left;">
Siderastrea radians
</td>
<td style="text-align:right;">
10
</td>
<td style="text-align:right;">
NA
</td>
<td style="text-align:right;">
0.0
</td>
</tr>
</tbody>
</table>

Within the wider Caribbean region, *Acropora palmata* (504) is the
dominant species in coral restoration due to its preponderance in Puerto
Rico restoration efforts led by Sea Ventures/NOAA (322 records of the
504 putative genets). *A. palmata* is followed by *A. cervicornis*
(420), *Orbicella faveolata* (313), *M. cavernosa* (264), and *P.
strigosa* (254). When we focus solely on Florida coral restoration
efforts, *A. cervicornis* (327) is the most cultivated species as
expected followed by *M. cavernosa* (228) and *P. strigosa* (225).
<u>Thus, using <em>A. cervicornis</em> as the branching species and
<em>M. cavernosa</em> or <em>P. strigosa</em> as the massive species in
this preliminary experiment would be appropriate.</u>

# Estimating MAT Mean Effect

The following is a table of published and unpublished data I have
aggregated. While I have encountered many more references, their results
section are incomplete (missing averages and/or standard deviations of
control and treatment groups) and were unable to be cast into this
analysis.

Table 2. Summary of literature review effect sizes
<table>
<thead>
<tr>
<th style="text-align:left;">
author
</th>
<th style="text-align:left;">
doi
</th>
<th style="text-align:left;">
growth
</th>
<th style="text-align:right;">
effect size
</th>
<th style="text-align:right;">
cohens d
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:left;">
Huang
</td>
<td style="text-align:left;">
10.1080/14634988.2020.1768766
</td>
<td style="text-align:left;">
31 %
</td>
<td style="text-align:right;">
0.54000
</td>
<td style="text-align:right;">
1.3000
</td>
</tr>
<tr>
<td style="text-align:left;">
Borell
</td>
<td style="text-align:left;">
10.1007/s00338-009-0564-y
</td>
<td style="text-align:left;">
64 %
</td>
<td style="text-align:right;">
0.82450
</td>
<td style="text-align:right;">
3.0000
</td>
</tr>
<tr>
<td style="text-align:left;">
Kihara
</td>
<td style="text-align:left;">
10.3755/galaxea.15.323
</td>
<td style="text-align:left;">
8 %
</td>
<td style="text-align:right;">
0.25400
</td>
<td style="text-align:right;">
0.5250
</td>
</tr>
<tr>
<td style="text-align:left;">
Sabater & Yap
</td>
<td style="text-align:left;">
10.1016/S0022-0981(02)00051-5
</td>
<td style="text-align:left;">
-5 %
</td>
<td style="text-align:right;">
0.53000
</td>
<td style="text-align:right;">
1.2500
</td>
</tr>
<tr>
<td style="text-align:left;">
Samidon
</td>
<td style="text-align:left;">
10.3389/fmars.2022.917360
</td>
<td style="text-align:left;">
17 %
</td>
<td style="text-align:right;">
0.40325
</td>
<td style="text-align:right;">
0.8895
</td>
</tr>
<tr>
<td style="text-align:left;">
Damayanti
</td>
<td style="text-align:left;">
NA
</td>
<td style="text-align:left;">
298 %
</td>
<td style="text-align:right;">
0.93350
</td>
<td style="text-align:right;">
5.2093
</td>
</tr>
<tr>
<td style="text-align:left;">
Natasasmita
</td>
<td style="text-align:left;">
10.15406/jamb.2016.04.00086
</td>
<td style="text-align:left;">
20 %
</td>
<td style="text-align:right;">
0.82500
</td>
<td style="text-align:right;">
2.9150
</td>
</tr>
</tbody>
</table>

If we trust this data (which I don’t; hence why I’m running this
preliminary experiment instead of jumping in), then we can expect a
median percentage increase in coral growth of 20 %.

# Calculating Group Sizes

I collected growth rates from the Perry coral growth database, which
aggregates calcification data for their ReefBudget surveys. While these
data are likely not predictive of what we will observe in the laboratory
with the buoyant weight methodology, the relative differences in growth
rates among species provides a framework for us to build this
statistical power model.

Next, I estimated power-sample size curves with pooled standard
deviations (SD) varying from 0.05 - 0.25
$g \text{ } cm^{-2} \text{ } yr^{-1}$ with 0.05 increments and percent
increases in growth rates relative to control from 5-50% in 5%
increments. Effect sizes at each combination of pooled SD and percent
increase were estimated.

Our 2-factor anova will have the following form: aov(G \~ treatment \*
species). There will be 2 levels to treatment and 2 levels to species.
The significance of an interactive effect (treatment:species) suggests
that at least one of the species responded differently to the MAT
compared to the other two.

Table 3. Estimated mean growth rates per species per % increase in
growth rate conferred by MAT. % increase are arbitrary numbers ranging
from 5-50% increased growth rates
<table>
<thead>
<tr>
<th style="text-align:left;">
species
</th>
<th style="text-align:right;">
Control
</th>
<th style="text-align:right;">
5%
</th>
<th style="text-align:right;">
10%
</th>
<th style="text-align:right;">
15%
</th>
<th style="text-align:right;">
20%
</th>
<th style="text-align:right;">
25%
</th>
<th style="text-align:right;">
30%
</th>
<th style="text-align:right;">
35%
</th>
<th style="text-align:right;">
40%
</th>
<th style="text-align:right;">
45%
</th>
<th style="text-align:right;">
50%
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:left;">
ACER
</td>
<td style="text-align:right;">
7.2720
</td>
<td style="text-align:right;">
7.63560
</td>
<td style="text-align:right;">
7.99920
</td>
<td style="text-align:right;">
8.36280
</td>
<td style="text-align:right;">
8.72640
</td>
<td style="text-align:right;">
9.09000
</td>
<td style="text-align:right;">
9.45360
</td>
<td style="text-align:right;">
9.81720
</td>
<td style="text-align:right;">
10.18080
</td>
<td style="text-align:right;">
10.54440
</td>
<td style="text-align:right;">
10.9080
</td>
</tr>
<tr>
<td style="text-align:left;">
MCAV
</td>
<td style="text-align:right;">
0.6198
</td>
<td style="text-align:right;">
0.65079
</td>
<td style="text-align:right;">
0.68178
</td>
<td style="text-align:right;">
0.71277
</td>
<td style="text-align:right;">
0.74376
</td>
<td style="text-align:right;">
0.77475
</td>
<td style="text-align:right;">
0.80574
</td>
<td style="text-align:right;">
0.83673
</td>
<td style="text-align:right;">
0.86772
</td>
<td style="text-align:right;">
0.89871
</td>
<td style="text-align:right;">
0.9297
</td>
</tr>
<tr>
<td style="text-align:left;">
PSTR
</td>
<td style="text-align:right;">
0.5888
</td>
<td style="text-align:right;">
0.61824
</td>
<td style="text-align:right;">
0.64768
</td>
<td style="text-align:right;">
0.67712
</td>
<td style="text-align:right;">
0.70656
</td>
<td style="text-align:right;">
0.73600
</td>
<td style="text-align:right;">
0.76544
</td>
<td style="text-align:right;">
0.79488
</td>
<td style="text-align:right;">
0.82432
</td>
<td style="text-align:right;">
0.85376
</td>
<td style="text-align:right;">
0.8832
</td>
</tr>
</tbody>
</table>
<h5>
Figure 1. Group-size power curves for estimated % increase in growth
rates. Vertical line denotes 80% power.
</h5>

<img src="/notebook/images/matPowerAnalysis/calculating-1.png" width="90%" style="display: block; margin: auto;" />

From these power-sample size curves, we can see that we need at least 14
fragments per treatment group to have 80% power and detect a 20%
increase in MAT if the pooled SD is less than or equal to 0.25
$g \text{ } cm^{-2} \text{ } yr^{-1}$. With that same treatment size and
goal of at least 80% power, we would be able to detect a 15% increase in
growth rates if the pooled SD was less than or equal to 0.15
$g \text{ } cm^{-2} \text{ } yr^{-1}$, a 10% increase in growth rates if
the pooled SD was less than or equal to 0.10
$g \text{ } cm^{-2} \text{ } yr^{-1}$, or a 5% increase in growth rates
if the pooled SD was less than or equal to 0.05. When the observed
increase in growth rates due to MAT is greater than or equal to 25%,
there is greater than 95% power when the standard deviation is 0.25
$g \text{ } cm^{-2} \text{ } yr^{-1}$ or less.

If the observed growth rate is a modest 10% and the pooled SD is 0.25
$g \text{ } cm^{-2} \text{ } yr^{-1}$, then we would only have 30% power
with an n=14. We would need 50 fragments per group to detect a 10%
increase with the same pooled SD, which is unfeasible. However, if MAT
only increases growth rates by 10%, it would not be able to overcome the
decreases in growth rates expected by ocean acidification.

Since we have two aquariums per treatment, we can divide the required
sample size evenly and have seven fragments per species per aquarium.
When we run the final analysis, we will create two models. One model
will be a two way anova as described above. The second model will
incorporate the aquarium as a random effect, which will be compared
against the fixed effects model. Ideally, there is no statistical
advantage gained from the mixed effects model (as judged by AIC) since
the two aquaria will have equal treatment conditions and should thus
exhibit the same growth patterns. Nevertheless, incorporating this mixed
effects model will likely improve the statistical power compared to a
normal fixed-effects ANOVA if the standard deviation is greater than
what was estimated above.

# Mixed Effects Power

Calculating power and effect sizes on mixed effects models is a bit more
difficult. The best way to do it is to simulate data multiple times and
take the averages. The Superpower package makes this relatively easy.
For each of the simulations, I set the number of fragments per treatment
per aquarium at 7 fragments and identified the maximum pooled SD to
maintian 80% power. This is equivalent to the 80% power gained from
having 14 fragments with a 20% increase in MAT with a pooled SD less
than or equal to 0.25 $g \text{ } cm^{-2} \text{ } yr^{-1}$.

When there is 20% increase in growth rates, the pooled SD can increase
to 0.75. This demonstrates the added power, or the ability to have more
variation within treatment/species groups and maintain statistical
power, when employing a mixed-effects model.

<!-- # Alternative Experiment -->
<!-- Alternatively, we could focus excluseively on the treatment and ignore the species/morphology comparison. -->
<!-- ```{r} -->
<!-- power1way <- lapply(seq(0.8,0.05, -0.05), function (beta) { -->
<!--   lapply(seq(0.05,0.25,0.05), function(sd) { -->
<!--   lapply(seq(0.05,0.5, 0.05), function(multiplier) { -->
<!--       ss.1way(k=2, -->
<!--               alpha=0.05, -->
<!--               beta = beta, -->
<!--               delta=multiplier, -->
<!--               sigma=sd, -->
<!--               B=100) %>% -->
<!--         broom::tidy() %>% -->
<!--       mutate(matMultpiplier = multiplier, -->
<!--              sd = sd) -->
<!--   }) %>% -->
<!--     bind_rows() -->
<!-- }) %>%  -->
<!--   bind_rows() -->
<!-- }) %>% -->
<!--   bind_rows() %>% -->
<!--   select(matMultpiplier, power, sd, n) %>% -->
<!--   arrange(matMultpiplier) %>% -->
<!--   mutate(across(c(matMultpiplier), ~paste0(.x*100,"%"))) -->
<!-- power1way$matMultpiplier <- factor(power$matMultpiplier, -->
<!--                                levels = c('5%', '10%', '15%', -->
<!--                                           '20%', '25%', '30%', -->
<!--                                           '35%', '40%', '45%', '50%'))  -->
<!-- capFig("Group-size power curves for estimated % increase in growth rates. Horizontal line denotes 80% power.") -->
<!-- power1way %>% -->
<!--   ggplot(aes(power, n, color=as.factor(sd))) + -->
<!--   geom_point() + -->
<!--   geom_smooth(se=F) + -->
<!--   geom_vline(xintercept = 0.8) + -->
<!--   facet_wrap(~matMultpiplier, scales = "free_y") + -->
<!--   scale_x_continuous(limits = c(0,1), breaks = seq(0,1,.25), labels = scales::label_percent(), -->
<!--                     name = "Power (%)") + -->
<!--   scale_y_continuous(breaks = integer_breaks()) + -->
<!--   theme_bw() + -->
<!--   labs(color = "Standard Deviation") -->
<!-- ``` -->

# Electrical Considerations

With an n=7 per treatment per aquarium, that gives us n=7 x 2 species +
3 blanks/aquarium = 17 cathodes per aquarium. The blanks are to acount
for abiotic precipiation of abiotic electrodeposits, which are
hypothesized to be uniform (given current density and cathodes are
identical) within a treatment. At a surface area of 21 $cm^2$, that will
be a total cathode surface area of 357 $cm^2$ or 0.0357 $m^2$. Since I
would like to test current densities between 0.5-5.0 A/m2, I will need
to supply each aquarium between 14 - 140 mA, well within the range of
our capabilities. For this experiment, I will only employ one current
density to test whether MAT increases growth rate. If it indeed does, a
second preliminary expeirmnet will investigate the optimal current
density.

<div class="sketchfab-embed-wrapper">

<iframe title="MATsetup" frameborder="0" allowfullscreen mozallowfullscreen="true" webkitallowfullscreen="true" allow="autoplay; fullscreen; xr-spatial-tracking" xr-spatial-tracking execution-while-out-of-viewport execution-while-not-rendered web-share src="https://sketchfab.com/models/1a9983e7bd37458b8810e8aee72231d1/embed" width="50%" style="margin: 0 auto; height=30vh;">
</iframe>
<p style="font-size: 13px; font-weight: normal; margin: 5px; color: #4A4A4A;">
<a href="https://sketchfab.com/3d-models/matsetup-1a9983e7bd37458b8810e8aee72231d1?utm_medium=embed&utm_campaign=share-popup&utm_content=1a9983e7bd37458b8810e8aee72231d1" target="_blank" rel="nofollow" style="font-weight: bold; color: #1CAAD9;">
MATsetup </a> by
<a href="https://sketchfab.com/pkiel?utm_medium=embed&utm_campaign=share-popup&utm_content=1a9983e7bd37458b8810e8aee72231d1" target="_blank" rel="nofollow" style="font-weight: bold; color: #1CAAD9;">
pkiel </a> on
<a href="https://sketchfab.com?utm_medium=embed&utm_campaign=share-popup&utm_content=1a9983e7bd37458b8810e8aee72231d1" target="_blank" rel="nofollow" style="font-weight: bold; color: #1CAAD9;">Sketchfab</a>
</p>

</div>

</div>
