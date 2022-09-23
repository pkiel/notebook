---
layout: post
title:  "TGA Analysis of Coral Skeletons"
author: "Patrick M Kiel"
date: '2022-09-15'
categories: [research]
description: "Review of thermogravimetric analysis techniques for quanitative comparisons of coral skeletal properties."
output:
  md_document:
    variant: gfm
    preserve_yaml: TRUE
knit: (function(inputFile, encoding) {
  rmarkdown::render(inputFile, 
  encoding = encoding, 
  output_file = paste0('2022-09-15', "-",
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
  if (document.getElementById('password').value === 'tga') {
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
    max-width: 90%;
    margin: 0 auto;
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

Thermogravimetric analysis (TGA) is a quantitative materials technique
that linearly heats a sample and simultaneously measures its mass as the
sample degrades. By looking at the percent decomposition over discrete
regions, we can characterize the coral sample’s fractional constituents.
The heating occurs in an inert environment (N<sub>2</sub> gas) to avoid
sample oxidation.

For analysis, we can use the first derivative of the TGA curve (called
the DTG curve) to identify the start, peak, and end temperatures for
each respective region. Then, we can integrate between the start and end
temperatures to calculate the percent degradation. For example, an
aragonite coral skeleton may have two peaks: decomposition of the
intracrystaline organics at approximately and the decomposition of
CaCO<sub>3</sub> to CaO and CO<sub>2</sub> at approximately 600-800°C
(Fig 1.).

<h5>
Figure 1. Example TGA and DTG Curve
</h5>

<img src="/notebook/images/tgaAnalysis/example-TGA-1.png" width="90%" style="display: block; margin: auto;" />

In this document, I review the current coral TGA literature, describe
the samples I have tested thus far and the proposed analysis
methodology, and begin to analyze my initial results.

# Literature Review

There are a handful of publications which have used TGA to analyze coral
skeletons grown or collected under acidified environments. The most
interesting ones in my opinion are Coronado *et al.* 2019, Moynihan *et
al.* 2021, and Prada *et al.* 2021 for their use of the method and the
findings they present. A complete list of references I draw upon is
included below.

### Coronado *et al.* 2019

This paper sought to disentangle the biological effects on calcification
to make corals a more reliable paleoclimate proxy (i.e. better their
understand vital effects). They cultured *Stylophora pistillata* under
pH 8.2, 7.6, and 7.3 and found differences in the aragonite precipitated
by the corals under these treatments due to the increased amount of
intracrystalline organic matrix and water content as measured by TGA.

They heated at a rate of 10°C/min to 1000°C, but limited their analysis
to discrete regions from ambient to 520°C, focusing mainly on the
decomposition of water from ambient to 275°C and bulk organic matrix, OH
groups, and possible ACC from 275-520°C (Table 1). There was no clear
pattern for water, but for the 275-520°C group there was a lineal
increase across treatments(Fig. 2).

<table class=" lightable-classic" style="font-family: &quot;Arial Narrow&quot;, &quot;Source Sans Pro&quot;, sans-serif; margin-left: auto; margin-right: auto;">
<caption>
Table 1: Coronado et al. 2019 analysis Regions
</caption>
<thead>
<tr>
<th style="text-align:center;font-weight: bold;">
Temperature
</th>
<th style="text-align:center;font-weight: bold;">
Name
</th>
<th style="text-align:center;font-weight: bold;">
Reasoning
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:center;">
20-150
</td>
<td style="text-align:center;">
Nonstructural water
</td>
<td style="text-align:center;">
evaporation of nonstructural water molecules
</td>
</tr>
<tr>
<td style="text-align:center;">
150-210
</td>
<td style="text-align:center;">
Structural Water
</td>
<td style="text-align:center;">
</td>
</tr>
<tr>
<td style="text-align:center;">
210-275
</td>
<td style="text-align:center;">
</td>
<td style="text-align:center;">
</td>
</tr>
<tr>
<td style="text-align:center;">
275-300
</td>
<td style="text-align:center;">
</td>
<td style="text-align:center;">
</td>
</tr>
<tr>
<td style="text-align:center;">
300-330
</td>
<td style="text-align:center;">
ACC
</td>
<td style="text-align:center;">
crystallization of ACC, which occurs \~ 316
</td>
</tr>
<tr>
<td style="text-align:center;">
330-411
</td>
<td style="text-align:center;">
</td>
<td style="text-align:center;">
</td>
</tr>
<tr>
<td style="text-align:center;">
411-440
</td>
<td style="text-align:center;">
</td>
<td style="text-align:center;">
transformation of aragonite to calcite, which occurs \~418
</td>
</tr>
<tr>
<td style="text-align:center;">
440-520
</td>
<td style="text-align:center;">
</td>
<td style="text-align:center;">
</td>
</tr>
<tr>
<td style="text-align:center;">
20-275
</td>
<td style="text-align:center;">
H2O
</td>
<td style="text-align:center;">
Integrates over all nonstructural water
</td>
</tr>
<tr>
<td style="text-align:center;">
275-520
</td>
<td style="text-align:center;">
OM-OH-ACC
</td>
<td style="text-align:center;">
captures all organic matrix, structural water, and ACC crystallization
</td>
</tr>
</tbody>
</table>
<h5>
Figure 2. TGA Results from Coronado et al. 2019
</h5>

![](/notebook/images/tgaAnalysis/Coronado2019Results.png)<!-- -->

### Moynihan *et al.* 2021

This paper looked at *Porites* coral cores collected from Thailand,
Singapore, and Taiwan and correlated micro-mechanical properties with
environmental conditions. They found that corals from low salinity and
high sedimentation environments (large freshwater influx) had higher
organic content and increased embrittlement.

Their analysis looked at TGA from 20-500°C, which was achieved by
heating to a 200C isotherm for 5 minutes followed by a 10°C/min ramp to
400°C and then followed by a 20°C/min ramp to 500°C. They used the DTG
curve to identify the temperature of maximum weight loss change (Tmax)
and then defined three regions to determine percent change: 175 to
225°C, Tmax-50 - Tmax+50°C, and Tmax+50 to 500°C. They measured
micro-mechanical properties with an nanoindentation test.

<h5>
Figure 3. Regression of micro-mechanical properties and TGA, Moynihan et
al. 2019
</h5>

![](/notebook/images/tgaAnalysis/Moynihan2021.png)<!-- -->

### Prada *et al.* 2021

This paper looked at four populations of naturally occurring reefs in
Papa New Guinea, two located by a CO<sub>2</sub> seep and two nearby
control sites. They measured 32 samples in total (10 for each control
and seep site at Dobu and 6 for each site at Upa Upasina). Their
analysis looked at TGA from 20-600°C at 10°C/min incremeents with a
120°C istotherm for 5 minutes to stabalize the removal of adsorbed
water. They then focussed their analysis on the region from 125-250°C
(structured water molecules) and 250-470°C (organix matrix).

They only found significant differences between sites in intraskeletal
strucutred water and intraskeletal OM at Upa Upasina, suggesting that
differences may not be solely environmentally controlled and their may
be physiological control of these parameters which are different between
different populations. Though further evidence to support this claim is
not presented here.

<h5>
Figure 4. TGA Results from Prada et al. 2021
</h5>

![](/notebook/images/tgaAnalysis/Prada2021.png)<!-- -->

## Takeaways

Each of these papers analyzed TGA data slightly differently. However,
there is general agreement in the organic matrix limits (250-470°C) and
the structural water limits (150-225°C). There is potentially other
regions of interest too including the crystallization of ACC (300-330°C,
\~316°C) and the monotropic transformation of aragonite to calcite
(411-440°C, \~418°C). See section below where I propose the analysis I
will undertake.

## References

1.  Coronado, I., Fine, M., Bosellini, F. R. & Stolarski, J. Impact of
    ocean acidification on crystallographic vital effect of the coral
    skeleton. Nat. Commun. 10, 1–9 (2019).
2.  Cuif, J. P., Dauphin, Y. Y., Doucet, J., Salome, M. & Susini, J.
    XANES mapping of organic sulfate in three scleractinian coral
    skeletons. Geochim. Cosmochim. Acta 67, 75–83 (2003).
3.  Cuif, J. P. et al. Fine-scale growth patterns in coral skeletons:
    Biochemical control over crystallization of aragonite fibres and
    assessment of early diagenesis. Geol. Soc. Spec. Publ. 303, 87–96
    (2008).
4.  Cuif, J. P., Dauphin, Y., Berthet, P. & Jegoudez, J. Associated
    water and organic compounds in coral skeletons: Quantitative
    thermogravimetry coupled to infrared absorption spectrometry.
    Geochemistry, Geophys. Geosystems 5, 1–9 (2004).
5.  Dauphin, Y., Cuif, J. P. & Massard, P. Persistent organic components
    in heated coral aragonitic skeletons-Implications for
    palaeoenvironmental reconstructions. Chem. Geol. 231, 26–37 (2006).
6.  Falini, G. et al. Control of aragonite deposition in colonial corals
    by intra-skeletal macromolecules. J. Struct. Biol. 183, 226–238
    (2013).
7.  Goffredo, S. et al. Biomineralization control related to population
    density under ocean acidification. Nat. Clim. Chang. 4, 593–597
    (2014).
8.  Moynihan, M. A. et al. Environmental impact on the mechanical
    properties of Porites spp. corals. Coral Reefs 40, 701–717 (2021).
9.  Pasquini, L. et al. Isotropic microscale mechanical properties of
    coral skeletons. J. R. Soc. Interface 12, 1–9 (2015).
10. Prada, F. et al. Coral micro- and macro-morphological skeletal
    properties in response to life-long acclimatization at CO2 vents in
    Papua New Guinea. Sci. Rep. 11, 1–10 (2021).
11. Reggi, M. et al. Biomineralization in mediterranean corals: The role
    of the intraskeletal organic matrix. Cryst. Growth Des. 14,
    4310–4320 (2014).
12. Schmidt, M. P., Ilott, A. J., Phillips, B. L. & Reeder, R. J.
    Structural changes upon dehydration of amorphous calcium carbonate.
    Cryst. Growth Des. 14, 938–951 (2014).
13. Stolarski, J. & Mazur, M. Nanostructure of biogenic versus abiogenic
    calcium carbonate crystals. Acta Palaeontol. Pol. 50, 847–865
    (2005).

# Samples

The corals for this first batch of analysis come from Allyson Demerlis’s
recent project where she investigated gene expression during a rapid
bleaching experiment of 3 *Acropora cervicornis* genotypes. Some of the
corals underwent a thermal stress-hardening treatment where the corals
were exposed to a daily variable temperature which is believed to
increase a coral’s bleaching resilience. The corals exposed to the high
temperatures (36°C) had high amounts of mortality and I took these
skeletons to analyze.

<h5>
Figure 5. Calcification data from Allyson Demerlis’s project
</h5>

<img src="/notebook/images/tgaAnalysis/allysonStressHardening-1.png" width="90%" style="display: block; margin: auto;" />

There was a significant effect of the coral genotype (F=23.27,
p=7.78e-6), but no observed effect of stress hardening treatment on
calcification rates (F=0.91, p=0.352). Following post-hoc testing, the
significant genotype effect was driven by genotype MB-B which had much
higher rates than BC-8B and SI-C which had similar calcification rates.

Thus, we are conducting these tests with a special focus on genotype
MB-B to see if its faster calcification rate results in any observable
differences in skeletal properties.

# Proposed Analysis

With the reviewed literature above, I synthesized the analysis I plan to
conduct with the goals of 1) automating the analysis; 2) characterizing
the structural water, organic matrix, ACC, aragonite to calcite, and
calcium carbonate regions; and 3) analyzing if there are any propertie
conserved among genotypes.

## Programatic Analysis

The first way I will analyze will be to find inflection points of the
DTG curve to identify the start, peak, and stop of the organc matrix
region between 240 and 450°C and the calcium carbonate region between
450 and 850°C. I first calculate the second derivative of the TGA curve
and identify all points of inflection (f’’ goes from positive to
negative). In theory there should only be three points of inflection
denoting the start, peak, and stop of the DTG curve. However, due to
noise within the data, there is often instances where there is five or
more points of inflection. To counteract that, I also run a cumulative
minimum function to find the minimum of the DTG curve which corresponds
to the peak. I then find the 3 values within the returned point of
inflection which center around the peak.

Here is an example. My inflection function returns the values
12,10,7,6,9,10,12. And the cummin function returns the value 6. I center
this around the inflection point and extract 7,6, and 9.

This removes the observed noise and when graphed below, you can see that
the extract points correspond with the inflection points you can
visualize.

The other ways I will analyze the data will be over discrete intervals
including,

1.  Non structural water (40-150)
2.  Structural water (125-250)
3.  Total water (40-250)
4.  Organic matrix (250-470)
5.  Crystallization of ACC (300-330)
6.  Aragonite to Calcite Transformation (411-440)
7.  Organic Matrix + ACC + OH Groups (275-520)
8.  CaCO3 (600-800)

# Initial Results

\[\[1\]\]
<img src="/notebook/images/tgaAnalysis/TGA-Analysis-1.png" width="90%" style="display: block; margin: auto;" />
\[\[2\]\]
<img src="/notebook/images/tgaAnalysis/TGA-Analysis-2.png" width="90%" style="display: block; margin: auto;" />
\[\[3\]\]
<img src="/notebook/images/tgaAnalysis/TGA-Analysis-3.png" width="90%" style="display: block; margin: auto;" />
\[\[4\]\]
<img src="/notebook/images/tgaAnalysis/TGA-Analysis-4.png" width="90%" style="display: block; margin: auto;" />
\[\[5\]\]
<img src="/notebook/images/tgaAnalysis/TGA-Analysis-5.png" width="90%" style="display: block; margin: auto;" />
\[\[6\]\]
<img src="/notebook/images/tgaAnalysis/TGA-Analysis-6.png" width="90%" style="display: block; margin: auto;" />
\[\[7\]\]
<img src="/notebook/images/tgaAnalysis/TGA-Analysis-7.png" width="90%" style="display: block; margin: auto;" />
\[\[8\]\]
<img src="/notebook/images/tgaAnalysis/TGA-Analysis-8.png" width="90%" style="display: block; margin: auto;" />
\[\[9\]\]
<img src="/notebook/images/tgaAnalysis/TGA-Analysis-9.png" width="90%" style="display: block; margin: auto;" />
\[\[10\]\]
<img src="/notebook/images/tgaAnalysis/TGA-Analysis-10.png" width="90%" style="display: block; margin: auto;" />
<table>
<caption>
Table 2: Batch 1 Results
</caption>
<thead>
<tr>
<th style="text-align:center;">
sample
</th>
<th style="text-align:center;">
region
</th>
<th style="text-align:center;">
start
</th>
<th style="text-align:center;">
peak
</th>
<th style="text-align:center;">
stop
</th>
<th style="text-align:center;">
loss
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:center;">
147
</td>
<td style="text-align:center;">
caco3
</td>
<td style="text-align:center;">
481.04
</td>
<td style="text-align:center;">
721.23
</td>
<td style="text-align:center;">
806.28
</td>
<td style="text-align:center;">
39.953
</td>
</tr>
<tr>
<td style="text-align:center;">
148
</td>
<td style="text-align:center;">
caco3
</td>
<td style="text-align:center;">
480.22
</td>
<td style="text-align:center;">
728.76
</td>
<td style="text-align:center;">
822.17
</td>
<td style="text-align:center;">
40.729
</td>
</tr>
<tr>
<td style="text-align:center;">
149
</td>
<td style="text-align:center;">
caco3
</td>
<td style="text-align:center;">
489.67
</td>
<td style="text-align:center;">
736.54
</td>
<td style="text-align:center;">
783.31
</td>
<td style="text-align:center;">
41.623
</td>
</tr>
<tr>
<td style="text-align:center;">
15
</td>
<td style="text-align:center;">
caco3
</td>
<td style="text-align:center;">
483.64
</td>
<td style="text-align:center;">
727.17
</td>
<td style="text-align:center;">
828.90
</td>
<td style="text-align:center;">
42.146
</td>
</tr>
<tr>
<td style="text-align:center;">
23
</td>
<td style="text-align:center;">
caco3
</td>
<td style="text-align:center;">
474.82
</td>
<td style="text-align:center;">
736.70
</td>
<td style="text-align:center;">
813.37
</td>
<td style="text-align:center;">
39.913
</td>
</tr>
<tr>
<td style="text-align:center;">
35
</td>
<td style="text-align:center;">
caco3
</td>
<td style="text-align:center;">
492.03
</td>
<td style="text-align:center;">
738.92
</td>
<td style="text-align:center;">
787.37
</td>
<td style="text-align:center;">
41.630
</td>
</tr>
<tr>
<td style="text-align:center;">
40
</td>
<td style="text-align:center;">
caco3
</td>
<td style="text-align:center;">
494.61
</td>
<td style="text-align:center;">
738.14
</td>
<td style="text-align:center;">
783.18
</td>
<td style="text-align:center;">
41.561
</td>
</tr>
<tr>
<td style="text-align:center;">
58
</td>
<td style="text-align:center;">
caco3
</td>
<td style="text-align:center;">
482.51
</td>
<td style="text-align:center;">
736.05
</td>
<td style="text-align:center;">
781.15
</td>
<td style="text-align:center;">
41.728
</td>
</tr>
<tr>
<td style="text-align:center;">
67
</td>
<td style="text-align:center;">
caco3
</td>
<td style="text-align:center;">
488.29
</td>
<td style="text-align:center;">
718.48
</td>
<td style="text-align:center;">
768.58
</td>
<td style="text-align:center;">
41.672
</td>
</tr>
<tr>
<td style="text-align:center;">
88
</td>
<td style="text-align:center;">
caco3
</td>
<td style="text-align:center;">
485.81
</td>
<td style="text-align:center;">
729.35
</td>
<td style="text-align:center;">
776.11
</td>
<td style="text-align:center;">
41.586
</td>
</tr>
<tr>
<td style="text-align:center;">
147
</td>
<td style="text-align:center;">
organics
</td>
<td style="text-align:center;">
245.99
</td>
<td style="text-align:center;">
300.97
</td>
<td style="text-align:center;">
364.31
</td>
<td style="text-align:center;">
1.891
</td>
</tr>
<tr>
<td style="text-align:center;">
148
</td>
<td style="text-align:center;">
organics
</td>
<td style="text-align:center;">
245.19
</td>
<td style="text-align:center;">
301.84
</td>
<td style="text-align:center;">
378.50
</td>
<td style="text-align:center;">
1.965
</td>
</tr>
<tr>
<td style="text-align:center;">
149
</td>
<td style="text-align:center;">
organics
</td>
<td style="text-align:center;">
247.95
</td>
<td style="text-align:center;">
299.61
</td>
<td style="text-align:center;">
376.28
</td>
<td style="text-align:center;">
1.865
</td>
</tr>
<tr>
<td style="text-align:center;">
15
</td>
<td style="text-align:center;">
organics
</td>
<td style="text-align:center;">
253.59
</td>
<td style="text-align:center;">
303.58
</td>
<td style="text-align:center;">
381.91
</td>
<td style="text-align:center;">
1.780
</td>
</tr>
<tr>
<td style="text-align:center;">
23
</td>
<td style="text-align:center;">
organics
</td>
<td style="text-align:center;">
253.12
</td>
<td style="text-align:center;">
298.10
</td>
<td style="text-align:center;">
369.77
</td>
<td style="text-align:center;">
1.786
</td>
</tr>
<tr>
<td style="text-align:center;">
35
</td>
<td style="text-align:center;">
organics
</td>
<td style="text-align:center;">
255.31
</td>
<td style="text-align:center;">
300.30
</td>
<td style="text-align:center;">
378.63
</td>
<td style="text-align:center;">
1.789
</td>
</tr>
<tr>
<td style="text-align:center;">
40
</td>
<td style="text-align:center;">
organics
</td>
<td style="text-align:center;">
254.55
</td>
<td style="text-align:center;">
296.21
</td>
<td style="text-align:center;">
387.88
</td>
<td style="text-align:center;">
1.860
</td>
</tr>
<tr>
<td style="text-align:center;">
58
</td>
<td style="text-align:center;">
organics
</td>
<td style="text-align:center;">
252.46
</td>
<td style="text-align:center;">
302.45
</td>
<td style="text-align:center;">
379.12
</td>
<td style="text-align:center;">
1.827
</td>
</tr>
<tr>
<td style="text-align:center;">
67
</td>
<td style="text-align:center;">
organics
</td>
<td style="text-align:center;">
249.91
</td>
<td style="text-align:center;">
299.89
</td>
<td style="text-align:center;">
368.22
</td>
<td style="text-align:center;">
1.826
</td>
</tr>
<tr>
<td style="text-align:center;">
88
</td>
<td style="text-align:center;">
organics
</td>
<td style="text-align:center;">
264.10
</td>
<td style="text-align:center;">
299.09
</td>
<td style="text-align:center;">
365.75
</td>
<td style="text-align:center;">
1.638
</td>
</tr>
</tbody>
</table>

# Stats

<h5>
Figure 6. Genotype Specific Percent Loss
</h5>

<img src="/notebook/images/tgaAnalysis/genotypeStats-1.png" width="90%" style="display: block; margin: auto;" />
The organics figure looks like MB-B has a slight difference, but looking
at the y axis its median is only 7% less than the median of the other
two genotypes and currently not showing significant genotype differences
(F=3.372, p=0.094). However, we still have a handful of more samples to
run. FTIR analysis may help classify the specific differences rather
than bulk concentration of organics quantified here.

</div>
