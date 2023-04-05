---
layout: post
title:  "Morphometrics from 3D Scans"
author: "Patrick M Kiel"
date: '2023-04-04'
categories: [research]
description: "Geometric complexity is the heart of coral reefs from ecosystem to organismal scales. Here, I provide an outline to apply morphometrics to 3D scans of coral fragments and relate the morphology to growth rates and ocen acidification sensitivity."
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

Fractal dimensions (FD) can describe the complexity of shapes at various
scales. While coral colonies and coral reefs are not strictly fractals,
colonial organisms and reef assemblages share some key characteristics
to fractals, including morphological irregularities, self-similarity and
high degrees of space filling. FD can align with other traditional
measurements such as surface area to volume ratio, rugosity, etc; but FD
offers increased information as seen in the below theoretical example of
a coral reef (Fig. 1; Torres-Pulliza *et al* 2020). This figure
illustrates 3 reefs with identical rugosiites but decreasing fractal
dimensions (FD), a \< b \< c.

![Theoretical fractal
dimension](https://media.springernature.com/lw685/springer-static/image/art%3A10.1038%2Fs41559-020-1281-8/MediaObjects/41559_2020_1281_Fig1_HTML.png)
Many processes (ecological, growth, resistance to stressors, biophysical
pathways with seawater) may scale (linearly, non-linearly/unimodal) with
increased morphological complexity. Therefore, using FD to
quantitatively describe morphological complexity can be informative.
However, its important to note that FD is only a singular metric of
morphological complexity and should be placed in appropriate context.
Since FD only describes space filling at different scales, dissimilar
shapes may share a FD despite rather obvious differences in branching or
size. Nevertheless, FD can play an important role in describing coral
morphology, especially when comparing ecosystems/coral colonies of
approximately the same scale.

Reichert *et al.* (2017) developed an easy to use tool to calculate FD
of a 3D coral colony using the Bouligand-Minkowski method. First, I am
reanalyzing the 3D scanned files from Reichert *et al.* (2017) to ensure
I am using their code correctly. I am using their obj scan files and the
analysis toolbox they released as part of the supplementary material.
The toolbox takes in an obj scan file and produces a txt file with 3
columns: dilation radius, log(dilation radius), and log(influence
volume). Dilation radius is produced for 1 \<= R \<= 20.

![Examles of corals in the
analysis](https://besjournals.onlinelibrary.wiley.com/cms/asset/98018c3c-a06e-4a41-ad6a-3e5cd3b1473e/mee312829-fig-0002-m.png)

Reichert *et al.* (2017) assessed the influence of dilation radii on the
ability to discern inter-and-intraspecific differences among 3d scans
(i.e. does a fractal D tell us if a coral fragment is identical to its
clonemate/conspecific). They tested all integers 3 $\le$ R $\le$ 20, and
found that when R = 8, fractal dimensions had the best ability to
discriminate inter-and-intraspecific differences. Thus, they calculate
and report all fractal dimensions based on a dilation radius of 8.

Given that the toolbox produces dilation radius from 1 \<= R \<= 20, you
should be able to subset this data frame to just the integers 3 \<= R
\<= 20 or all real numbers 3 \<= R \<= 20 to calculate and derive the
same values reported in Reichert *et al.* (2017). So I’m going to do
just that.

# Formulas

Reichert *et al.* (2017) use the Bouligand–Minkowski method to estimate
a colony’s fractal dimension as, “it is one of the most accurate methods
for computing fractal dimensions and it is highly sensitive to detecting
small changes in models (Tricot, 1995). Due to its use of Euclidean
distances, the approach is invariant to rotation. Thus, prior
normalization steps are not necessary (Tricot, 1995).”

They define D as,

$$
D = 3 - \lim_{R \to 0} \frac{log(V(R))}{log(R)}  
$$ where R is the dilation radius and V(R) is the influence volume.

Here, you can visualize the measuring principles of the
Bouligand-Minkowski method with increasing dilation radii from
a–\>c. Spheres are located at the vertex of the 3d mesh. Larger radii
progressively fill the volume enclosed by the mesh, resulting in a
larger influence volume. The limit integrates across these spatial
scales (radii a-c) to synthesize a singular characteristic of the mesh’s
complexity.

\` ![Bouligand-Minkowski
Concept](https://besjournals.onlinelibrary.wiley.com/cms/asset/6797afd6-8813-48eb-9457-874fed88814e/mee312829-fig-0001-m.png)

As this is a power law, you can estimate the limit by taking the slope
of the log-log plot that fits the curve log(R) x log(V(R)). Thus, D can
be estimated as 3-m, where m is the slope of the log-log plot.

You can progressively slide the curve from the beginning (R=2) to a
maximum radii, and then calculate the slope over each defined region.
For example, if you wanted to evaluate dilation radii from 2-15, you
would first take the slope of the curve from (0,2), then (0,3), and so
on until (0,15). You would calculate the FD at each R in the series and
evaluate its discriminatory power.The code is as follows,

``` r
  #calculate linear model over the region
  m = lm(log.infl.vol ~ log.dil.rad,
          #filter data to integers only between 3 & 20
          #R is the desired dilation radius
          data = dat %>% filter(dil.rad<= & R))

  #extract the slope
  m$coefficients[[2]]
```

# Example Data

Using the 3D scans from Reichert *et al.* (2017), I independently
calculated the Fractal Dimension using their toolbox. Below is a table
of the data where I exclusively looked at time point 0 data.

<table class="table" style="margin-left: auto; margin-right: auto;">
<caption>
Table 1: Comparison of Fractal Dimensions. I can replicate their FD.
</caption>
<thead>
<tr>
<th style="text-align:left;">
ID
</th>
<th style="text-align:left;">
Species
</th>
<th style="text-align:left;">
Genus
</th>
<th style="text-align:left;">
Colony
</th>
<th style="text-align:right;">
ReichD
</th>
<th style="text-align:right;">
D8
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:left;">
Ahu_1\_01
</td>
<td style="text-align:left;">
Ahu
</td>
<td style="text-align:left;">
Acropora
</td>
<td style="text-align:left;">
Ahu 1
</td>
<td style="text-align:right;">
1.947933
</td>
<td style="text-align:right;">
1.94793
</td>
</tr>
<tr>
<td style="text-align:left;">
Ahu_1\_02
</td>
<td style="text-align:left;">
Ahu
</td>
<td style="text-align:left;">
Acropora
</td>
<td style="text-align:left;">
Ahu 1
</td>
<td style="text-align:right;">
1.958113
</td>
<td style="text-align:right;">
1.95811
</td>
</tr>
<tr>
<td style="text-align:left;">
Ahu_1\_03
</td>
<td style="text-align:left;">
Ahu
</td>
<td style="text-align:left;">
Acropora
</td>
<td style="text-align:left;">
Ahu 1
</td>
<td style="text-align:right;">
1.956783
</td>
<td style="text-align:right;">
1.95678
</td>
</tr>
<tr>
<td style="text-align:left;">
Ahu_1\_04
</td>
<td style="text-align:left;">
Ahu
</td>
<td style="text-align:left;">
Acropora
</td>
<td style="text-align:left;">
Ahu 1
</td>
<td style="text-align:right;">
1.960783
</td>
<td style="text-align:right;">
1.96078
</td>
</tr>
<tr>
<td style="text-align:left;">
Ahu_1\_06
</td>
<td style="text-align:left;">
Ahu
</td>
<td style="text-align:left;">
Acropora
</td>
<td style="text-align:left;">
Ahu 1
</td>
<td style="text-align:right;">
1.950659
</td>
<td style="text-align:right;">
1.95066
</td>
</tr>
<tr>
<td style="text-align:left;">
Ahu_1\_07
</td>
<td style="text-align:left;">
Ahu
</td>
<td style="text-align:left;">
Acropora
</td>
<td style="text-align:left;">
Ahu 1
</td>
<td style="text-align:right;">
1.954873
</td>
<td style="text-align:right;">
1.95487
</td>
</tr>
<tr>
<td style="text-align:left;">
Ahu_1\_08
</td>
<td style="text-align:left;">
Ahu
</td>
<td style="text-align:left;">
Acropora
</td>
<td style="text-align:left;">
Ahu 1
</td>
<td style="text-align:right;">
1.953186
</td>
<td style="text-align:right;">
1.95319
</td>
</tr>
<tr>
<td style="text-align:left;">
Ahu_2\_01
</td>
<td style="text-align:left;">
Ahu
</td>
<td style="text-align:left;">
Acropora
</td>
<td style="text-align:left;">
Ahu 2
</td>
<td style="text-align:right;">
1.956169
</td>
<td style="text-align:right;">
1.95617
</td>
</tr>
<tr>
<td style="text-align:left;">
Ahu_2\_02
</td>
<td style="text-align:left;">
Ahu
</td>
<td style="text-align:left;">
Acropora
</td>
<td style="text-align:left;">
Ahu 2
</td>
<td style="text-align:right;">
1.962931
</td>
<td style="text-align:right;">
1.96293
</td>
</tr>
<tr>
<td style="text-align:left;">
Ahu_2\_03
</td>
<td style="text-align:left;">
Ahu
</td>
<td style="text-align:left;">
Acropora
</td>
<td style="text-align:left;">
Ahu 2
</td>
<td style="text-align:right;">
1.950780
</td>
<td style="text-align:right;">
1.95078
</td>
</tr>
<tr>
<td style="text-align:left;">
Ahu_2\_04
</td>
<td style="text-align:left;">
Ahu
</td>
<td style="text-align:left;">
Acropora
</td>
<td style="text-align:left;">
Ahu 2
</td>
<td style="text-align:right;">
1.948467
</td>
<td style="text-align:right;">
1.94847
</td>
</tr>
<tr>
<td style="text-align:left;">
Ahu_2\_05
</td>
<td style="text-align:left;">
Ahu
</td>
<td style="text-align:left;">
Acropora
</td>
<td style="text-align:left;">
Ahu 2
</td>
<td style="text-align:right;">
1.957679
</td>
<td style="text-align:right;">
1.95768
</td>
</tr>
<tr>
<td style="text-align:left;">
Ahu_2\_06
</td>
<td style="text-align:left;">
Ahu
</td>
<td style="text-align:left;">
Acropora
</td>
<td style="text-align:left;">
Ahu 2
</td>
<td style="text-align:right;">
1.968450
</td>
<td style="text-align:right;">
1.96845
</td>
</tr>
<tr>
<td style="text-align:left;">
Ahu_2\_07
</td>
<td style="text-align:left;">
Ahu
</td>
<td style="text-align:left;">
Acropora
</td>
<td style="text-align:left;">
Ahu 2
</td>
<td style="text-align:right;">
1.942573
</td>
<td style="text-align:right;">
1.94257
</td>
</tr>
<tr>
<td style="text-align:left;">
Ahu_2\_08
</td>
<td style="text-align:left;">
Ahu
</td>
<td style="text-align:left;">
Acropora
</td>
<td style="text-align:left;">
Ahu 2
</td>
<td style="text-align:right;">
1.944379
</td>
<td style="text-align:right;">
1.94438
</td>
</tr>
<tr>
<td style="text-align:left;">
Ahu_3\_01
</td>
<td style="text-align:left;">
Ahu
</td>
<td style="text-align:left;">
Acropora
</td>
<td style="text-align:left;">
Ahu 3
</td>
<td style="text-align:right;">
1.975106
</td>
<td style="text-align:right;">
1.97511
</td>
</tr>
<tr>
<td style="text-align:left;">
Ahu_3\_02
</td>
<td style="text-align:left;">
Ahu
</td>
<td style="text-align:left;">
Acropora
</td>
<td style="text-align:left;">
Ahu 3
</td>
<td style="text-align:right;">
1.972426
</td>
<td style="text-align:right;">
1.97243
</td>
</tr>
<tr>
<td style="text-align:left;">
Ahu_3\_03
</td>
<td style="text-align:left;">
Ahu
</td>
<td style="text-align:left;">
Acropora
</td>
<td style="text-align:left;">
Ahu 3
</td>
<td style="text-align:right;">
1.972287
</td>
<td style="text-align:right;">
1.97229
</td>
</tr>
<tr>
<td style="text-align:left;">
Ahu_3\_04
</td>
<td style="text-align:left;">
Ahu
</td>
<td style="text-align:left;">
Acropora
</td>
<td style="text-align:left;">
Ahu 3
</td>
<td style="text-align:right;">
1.966668
</td>
<td style="text-align:right;">
1.96667
</td>
</tr>
<tr>
<td style="text-align:left;">
Ahu_3\_05
</td>
<td style="text-align:left;">
Ahu
</td>
<td style="text-align:left;">
Acropora
</td>
<td style="text-align:left;">
Ahu 3
</td>
<td style="text-align:right;">
1.959671
</td>
<td style="text-align:right;">
1.95967
</td>
</tr>
<tr>
<td style="text-align:left;">
Ahu_3\_06
</td>
<td style="text-align:left;">
Ahu
</td>
<td style="text-align:left;">
Acropora
</td>
<td style="text-align:left;">
Ahu 3
</td>
<td style="text-align:right;">
1.978112
</td>
<td style="text-align:right;">
1.97811
</td>
</tr>
<tr>
<td style="text-align:left;">
Ahu_3\_07
</td>
<td style="text-align:left;">
Ahu
</td>
<td style="text-align:left;">
Acropora
</td>
<td style="text-align:left;">
Ahu 3
</td>
<td style="text-align:right;">
1.952993
</td>
<td style="text-align:right;">
1.95299
</td>
</tr>
<tr>
<td style="text-align:left;">
Ami_1\_01
</td>
<td style="text-align:left;">
Ami
</td>
<td style="text-align:left;">
Acropora
</td>
<td style="text-align:left;">
Ami 1
</td>
<td style="text-align:right;">
1.952524
</td>
<td style="text-align:right;">
1.95252
</td>
</tr>
<tr>
<td style="text-align:left;">
Ami_1\_02
</td>
<td style="text-align:left;">
Ami
</td>
<td style="text-align:left;">
Acropora
</td>
<td style="text-align:left;">
Ami 1
</td>
<td style="text-align:right;">
1.965593
</td>
<td style="text-align:right;">
1.96559
</td>
</tr>
<tr>
<td style="text-align:left;">
Ami_1\_03
</td>
<td style="text-align:left;">
Ami
</td>
<td style="text-align:left;">
Acropora
</td>
<td style="text-align:left;">
Ami 1
</td>
<td style="text-align:right;">
1.953116
</td>
<td style="text-align:right;">
1.95312
</td>
</tr>
<tr>
<td style="text-align:left;">
Ami_1\_05
</td>
<td style="text-align:left;">
Ami
</td>
<td style="text-align:left;">
Acropora
</td>
<td style="text-align:left;">
Ami 1
</td>
<td style="text-align:right;">
1.961815
</td>
<td style="text-align:right;">
1.96182
</td>
</tr>
<tr>
<td style="text-align:left;">
Ami_1\_06
</td>
<td style="text-align:left;">
Ami
</td>
<td style="text-align:left;">
Acropora
</td>
<td style="text-align:left;">
Ami 1
</td>
<td style="text-align:right;">
1.964092
</td>
<td style="text-align:right;">
1.96409
</td>
</tr>
<tr>
<td style="text-align:left;">
Ami_1\_07
</td>
<td style="text-align:left;">
Ami
</td>
<td style="text-align:left;">
Acropora
</td>
<td style="text-align:left;">
Ami 1
</td>
<td style="text-align:right;">
1.948878
</td>
<td style="text-align:right;">
1.94888
</td>
</tr>
<tr>
<td style="text-align:left;">
Ami_1\_08
</td>
<td style="text-align:left;">
Ami
</td>
<td style="text-align:left;">
Acropora
</td>
<td style="text-align:left;">
Ami 1
</td>
<td style="text-align:right;">
1.948296
</td>
<td style="text-align:right;">
1.94830
</td>
</tr>
<tr>
<td style="text-align:left;">
Ami_1\_09
</td>
<td style="text-align:left;">
Ami
</td>
<td style="text-align:left;">
Acropora
</td>
<td style="text-align:left;">
Ami 1
</td>
<td style="text-align:right;">
1.959278
</td>
<td style="text-align:right;">
1.95928
</td>
</tr>
<tr>
<td style="text-align:left;">
Ami_2\_01
</td>
<td style="text-align:left;">
Ami
</td>
<td style="text-align:left;">
Acropora
</td>
<td style="text-align:left;">
Ami 2
</td>
<td style="text-align:right;">
1.977577
</td>
<td style="text-align:right;">
1.97758
</td>
</tr>
<tr>
<td style="text-align:left;">
Ami_2\_02
</td>
<td style="text-align:left;">
Ami
</td>
<td style="text-align:left;">
Acropora
</td>
<td style="text-align:left;">
Ami 2
</td>
<td style="text-align:right;">
1.977062
</td>
<td style="text-align:right;">
1.97706
</td>
</tr>
<tr>
<td style="text-align:left;">
Ami_2\_03
</td>
<td style="text-align:left;">
Ami
</td>
<td style="text-align:left;">
Acropora
</td>
<td style="text-align:left;">
Ami 2
</td>
<td style="text-align:right;">
1.977408
</td>
<td style="text-align:right;">
1.97741
</td>
</tr>
<tr>
<td style="text-align:left;">
Ami_2\_04
</td>
<td style="text-align:left;">
Ami
</td>
<td style="text-align:left;">
Acropora
</td>
<td style="text-align:left;">
Ami 2
</td>
<td style="text-align:right;">
1.969991
</td>
<td style="text-align:right;">
1.96999
</td>
</tr>
<tr>
<td style="text-align:left;">
Ami_2\_05
</td>
<td style="text-align:left;">
Ami
</td>
<td style="text-align:left;">
Acropora
</td>
<td style="text-align:left;">
Ami 2
</td>
<td style="text-align:right;">
1.968271
</td>
<td style="text-align:right;">
1.96827
</td>
</tr>
<tr>
<td style="text-align:left;">
Ami_2\_06
</td>
<td style="text-align:left;">
Ami
</td>
<td style="text-align:left;">
Acropora
</td>
<td style="text-align:left;">
Ami 2
</td>
<td style="text-align:right;">
1.975237
</td>
<td style="text-align:right;">
1.97524
</td>
</tr>
<tr>
<td style="text-align:left;">
Ami_3\_01
</td>
<td style="text-align:left;">
Ami
</td>
<td style="text-align:left;">
Acropora
</td>
<td style="text-align:left;">
Ami 3
</td>
<td style="text-align:right;">
1.955278
</td>
<td style="text-align:right;">
1.95528
</td>
</tr>
<tr>
<td style="text-align:left;">
Ami_3\_02
</td>
<td style="text-align:left;">
Ami
</td>
<td style="text-align:left;">
Acropora
</td>
<td style="text-align:left;">
Ami 3
</td>
<td style="text-align:right;">
1.955035
</td>
<td style="text-align:right;">
1.95504
</td>
</tr>
<tr>
<td style="text-align:left;">
Ami_3\_03
</td>
<td style="text-align:left;">
Ami
</td>
<td style="text-align:left;">
Acropora
</td>
<td style="text-align:left;">
Ami 3
</td>
<td style="text-align:right;">
1.958062
</td>
<td style="text-align:right;">
1.95806
</td>
</tr>
<tr>
<td style="text-align:left;">
Ami_3\_04
</td>
<td style="text-align:left;">
Ami
</td>
<td style="text-align:left;">
Acropora
</td>
<td style="text-align:left;">
Ami 3
</td>
<td style="text-align:right;">
1.935490
</td>
<td style="text-align:right;">
1.93549
</td>
</tr>
<tr>
<td style="text-align:left;">
Ami_3\_05
</td>
<td style="text-align:left;">
Ami
</td>
<td style="text-align:left;">
Acropora
</td>
<td style="text-align:left;">
Ami 3
</td>
<td style="text-align:right;">
1.944109
</td>
<td style="text-align:right;">
1.94411
</td>
</tr>
<tr>
<td style="text-align:left;">
Ami_3\_06
</td>
<td style="text-align:left;">
Ami
</td>
<td style="text-align:left;">
Acropora
</td>
<td style="text-align:left;">
Ami 3
</td>
<td style="text-align:right;">
1.945086
</td>
<td style="text-align:right;">
1.94509
</td>
</tr>
<tr>
<td style="text-align:left;">
Ami_3\_07
</td>
<td style="text-align:left;">
Ami
</td>
<td style="text-align:left;">
Acropora
</td>
<td style="text-align:left;">
Ami 3
</td>
<td style="text-align:right;">
1.936752
</td>
<td style="text-align:right;">
1.93675
</td>
</tr>
<tr>
<td style="text-align:left;">
Ami_3\_08
</td>
<td style="text-align:left;">
Ami
</td>
<td style="text-align:left;">
Acropora
</td>
<td style="text-align:left;">
Ami 3
</td>
<td style="text-align:right;">
1.946074
</td>
<td style="text-align:right;">
1.94607
</td>
</tr>
<tr>
<td style="text-align:left;">
Pcy_1\_01
</td>
<td style="text-align:left;">
Pcy
</td>
<td style="text-align:left;">
Porites
</td>
<td style="text-align:left;">
Pcy 1
</td>
<td style="text-align:right;">
1.944737
</td>
<td style="text-align:right;">
1.94474
</td>
</tr>
<tr>
<td style="text-align:left;">
Pcy_1\_02
</td>
<td style="text-align:left;">
Pcy
</td>
<td style="text-align:left;">
Porites
</td>
<td style="text-align:left;">
Pcy 1
</td>
<td style="text-align:right;">
1.935159
</td>
<td style="text-align:right;">
1.93516
</td>
</tr>
<tr>
<td style="text-align:left;">
Pcy_1\_03
</td>
<td style="text-align:left;">
Pcy
</td>
<td style="text-align:left;">
Porites
</td>
<td style="text-align:left;">
Pcy 1
</td>
<td style="text-align:right;">
1.936948
</td>
<td style="text-align:right;">
1.93695
</td>
</tr>
<tr>
<td style="text-align:left;">
Pcy_1\_04
</td>
<td style="text-align:left;">
Pcy
</td>
<td style="text-align:left;">
Porites
</td>
<td style="text-align:left;">
Pcy 1
</td>
<td style="text-align:right;">
1.935638
</td>
<td style="text-align:right;">
1.93564
</td>
</tr>
<tr>
<td style="text-align:left;">
Pcy_1\_05
</td>
<td style="text-align:left;">
Pcy
</td>
<td style="text-align:left;">
Porites
</td>
<td style="text-align:left;">
Pcy 1
</td>
<td style="text-align:right;">
1.936519
</td>
<td style="text-align:right;">
1.93652
</td>
</tr>
<tr>
<td style="text-align:left;">
Pcy_1\_06
</td>
<td style="text-align:left;">
Pcy
</td>
<td style="text-align:left;">
Porites
</td>
<td style="text-align:left;">
Pcy 1
</td>
<td style="text-align:right;">
1.934990
</td>
<td style="text-align:right;">
1.93499
</td>
</tr>
<tr>
<td style="text-align:left;">
Pcy_2\_01
</td>
<td style="text-align:left;">
Pcy
</td>
<td style="text-align:left;">
Porites
</td>
<td style="text-align:left;">
Pcy 2
</td>
<td style="text-align:right;">
1.937472
</td>
<td style="text-align:right;">
1.93747
</td>
</tr>
<tr>
<td style="text-align:left;">
Pcy_2\_02
</td>
<td style="text-align:left;">
Pcy
</td>
<td style="text-align:left;">
Porites
</td>
<td style="text-align:left;">
Pcy 2
</td>
<td style="text-align:right;">
1.926380
</td>
<td style="text-align:right;">
1.92638
</td>
</tr>
<tr>
<td style="text-align:left;">
Pcy_2\_03
</td>
<td style="text-align:left;">
Pcy
</td>
<td style="text-align:left;">
Porites
</td>
<td style="text-align:left;">
Pcy 2
</td>
<td style="text-align:right;">
1.924577
</td>
<td style="text-align:right;">
1.92458
</td>
</tr>
<tr>
<td style="text-align:left;">
Pcy_2\_04
</td>
<td style="text-align:left;">
Pcy
</td>
<td style="text-align:left;">
Porites
</td>
<td style="text-align:left;">
Pcy 2
</td>
<td style="text-align:right;">
1.930265
</td>
<td style="text-align:right;">
1.93027
</td>
</tr>
<tr>
<td style="text-align:left;">
Pcy_2\_05
</td>
<td style="text-align:left;">
Pcy
</td>
<td style="text-align:left;">
Porites
</td>
<td style="text-align:left;">
Pcy 2
</td>
<td style="text-align:right;">
1.945649
</td>
<td style="text-align:right;">
1.94565
</td>
</tr>
<tr>
<td style="text-align:left;">
Pcy_2\_06
</td>
<td style="text-align:left;">
Pcy
</td>
<td style="text-align:left;">
Porites
</td>
<td style="text-align:left;">
Pcy 2
</td>
<td style="text-align:right;">
1.932566
</td>
<td style="text-align:right;">
1.93257
</td>
</tr>
<tr>
<td style="text-align:left;">
Pcy_2\_07
</td>
<td style="text-align:left;">
Pcy
</td>
<td style="text-align:left;">
Porites
</td>
<td style="text-align:left;">
Pcy 2
</td>
<td style="text-align:right;">
1.919607
</td>
<td style="text-align:right;">
1.91961
</td>
</tr>
<tr>
<td style="text-align:left;">
Pcy_3\_01
</td>
<td style="text-align:left;">
Pcy
</td>
<td style="text-align:left;">
Porites
</td>
<td style="text-align:left;">
Pcy 3
</td>
<td style="text-align:right;">
1.930831
</td>
<td style="text-align:right;">
1.93083
</td>
</tr>
<tr>
<td style="text-align:left;">
Pcy_3\_02
</td>
<td style="text-align:left;">
Pcy
</td>
<td style="text-align:left;">
Porites
</td>
<td style="text-align:left;">
Pcy 3
</td>
<td style="text-align:right;">
1.949956
</td>
<td style="text-align:right;">
1.94996
</td>
</tr>
<tr>
<td style="text-align:left;">
Pcy_3\_03
</td>
<td style="text-align:left;">
Pcy
</td>
<td style="text-align:left;">
Porites
</td>
<td style="text-align:left;">
Pcy 3
</td>
<td style="text-align:right;">
1.925206
</td>
<td style="text-align:right;">
1.92521
</td>
</tr>
<tr>
<td style="text-align:left;">
Pcy_3\_04
</td>
<td style="text-align:left;">
Pcy
</td>
<td style="text-align:left;">
Porites
</td>
<td style="text-align:left;">
Pcy 3
</td>
<td style="text-align:right;">
1.936933
</td>
<td style="text-align:right;">
1.93693
</td>
</tr>
<tr>
<td style="text-align:left;">
Pcy_3\_05
</td>
<td style="text-align:left;">
Pcy
</td>
<td style="text-align:left;">
Porites
</td>
<td style="text-align:left;">
Pcy 3
</td>
<td style="text-align:right;">
1.938964
</td>
<td style="text-align:right;">
1.93896
</td>
</tr>
<tr>
<td style="text-align:left;">
Pcy_3\_06
</td>
<td style="text-align:left;">
Pcy
</td>
<td style="text-align:left;">
Porites
</td>
<td style="text-align:left;">
Pcy 3
</td>
<td style="text-align:right;">
1.937276
</td>
<td style="text-align:right;">
1.93728
</td>
</tr>
<tr>
<td style="text-align:left;">
Pcy_3\_07
</td>
<td style="text-align:left;">
Pcy
</td>
<td style="text-align:left;">
Porites
</td>
<td style="text-align:left;">
Pcy 3
</td>
<td style="text-align:right;">
1.943986
</td>
<td style="text-align:right;">
1.94399
</td>
</tr>
<tr>
<td style="text-align:left;">
Pda_1\_01
</td>
<td style="text-align:left;">
Pda
</td>
<td style="text-align:left;">
Pocillopora
</td>
<td style="text-align:left;">
Pda 1
</td>
<td style="text-align:right;">
1.950075
</td>
<td style="text-align:right;">
1.95007
</td>
</tr>
<tr>
<td style="text-align:left;">
Pda_1\_02
</td>
<td style="text-align:left;">
Pda
</td>
<td style="text-align:left;">
Pocillopora
</td>
<td style="text-align:left;">
Pda 1
</td>
<td style="text-align:right;">
1.956012
</td>
<td style="text-align:right;">
1.95601
</td>
</tr>
<tr>
<td style="text-align:left;">
Pda_1\_03
</td>
<td style="text-align:left;">
Pda
</td>
<td style="text-align:left;">
Pocillopora
</td>
<td style="text-align:left;">
Pda 1
</td>
<td style="text-align:right;">
1.946938
</td>
<td style="text-align:right;">
1.94694
</td>
</tr>
<tr>
<td style="text-align:left;">
Pda_1\_04
</td>
<td style="text-align:left;">
Pda
</td>
<td style="text-align:left;">
Pocillopora
</td>
<td style="text-align:left;">
Pda 1
</td>
<td style="text-align:right;">
1.943154
</td>
<td style="text-align:right;">
1.94315
</td>
</tr>
<tr>
<td style="text-align:left;">
Pda_1\_05
</td>
<td style="text-align:left;">
Pda
</td>
<td style="text-align:left;">
Pocillopora
</td>
<td style="text-align:left;">
Pda 1
</td>
<td style="text-align:right;">
1.947336
</td>
<td style="text-align:right;">
1.94734
</td>
</tr>
<tr>
<td style="text-align:left;">
Pda_1\_06
</td>
<td style="text-align:left;">
Pda
</td>
<td style="text-align:left;">
Pocillopora
</td>
<td style="text-align:left;">
Pda 1
</td>
<td style="text-align:right;">
1.952487
</td>
<td style="text-align:right;">
1.95249
</td>
</tr>
<tr>
<td style="text-align:left;">
Pda_2\_01
</td>
<td style="text-align:left;">
Pda
</td>
<td style="text-align:left;">
Pocillopora
</td>
<td style="text-align:left;">
Pda 2
</td>
<td style="text-align:right;">
1.937791
</td>
<td style="text-align:right;">
1.93779
</td>
</tr>
<tr>
<td style="text-align:left;">
Pda_2\_03
</td>
<td style="text-align:left;">
Pda
</td>
<td style="text-align:left;">
Pocillopora
</td>
<td style="text-align:left;">
Pda 2
</td>
<td style="text-align:right;">
1.960746
</td>
<td style="text-align:right;">
1.96075
</td>
</tr>
<tr>
<td style="text-align:left;">
Pda_2\_04
</td>
<td style="text-align:left;">
Pda
</td>
<td style="text-align:left;">
Pocillopora
</td>
<td style="text-align:left;">
Pda 2
</td>
<td style="text-align:right;">
1.936594
</td>
<td style="text-align:right;">
1.93659
</td>
</tr>
<tr>
<td style="text-align:left;">
Pda_2\_05
</td>
<td style="text-align:left;">
Pda
</td>
<td style="text-align:left;">
Pocillopora
</td>
<td style="text-align:left;">
Pda 2
</td>
<td style="text-align:right;">
1.950042
</td>
<td style="text-align:right;">
1.95004
</td>
</tr>
<tr>
<td style="text-align:left;">
Pda_2\_06
</td>
<td style="text-align:left;">
Pda
</td>
<td style="text-align:left;">
Pocillopora
</td>
<td style="text-align:left;">
Pda 2
</td>
<td style="text-align:right;">
1.952868
</td>
<td style="text-align:right;">
1.95287
</td>
</tr>
<tr>
<td style="text-align:left;">
Pda_2\_07
</td>
<td style="text-align:left;">
Pda
</td>
<td style="text-align:left;">
Pocillopora
</td>
<td style="text-align:left;">
Pda 2
</td>
<td style="text-align:right;">
1.952384
</td>
<td style="text-align:right;">
1.95238
</td>
</tr>
<tr>
<td style="text-align:left;">
Pda_3\_01
</td>
<td style="text-align:left;">
Pda
</td>
<td style="text-align:left;">
Pocillopora
</td>
<td style="text-align:left;">
Pda 3
</td>
<td style="text-align:right;">
1.945583
</td>
<td style="text-align:right;">
1.94558
</td>
</tr>
<tr>
<td style="text-align:left;">
Pda_3\_02
</td>
<td style="text-align:left;">
Pda
</td>
<td style="text-align:left;">
Pocillopora
</td>
<td style="text-align:left;">
Pda 3
</td>
<td style="text-align:right;">
1.936259
</td>
<td style="text-align:right;">
1.93626
</td>
</tr>
<tr>
<td style="text-align:left;">
Pda_3\_03
</td>
<td style="text-align:left;">
Pda
</td>
<td style="text-align:left;">
Pocillopora
</td>
<td style="text-align:left;">
Pda 3
</td>
<td style="text-align:right;">
1.950971
</td>
<td style="text-align:right;">
1.95097
</td>
</tr>
<tr>
<td style="text-align:left;">
Pda_3\_05
</td>
<td style="text-align:left;">
Pda
</td>
<td style="text-align:left;">
Pocillopora
</td>
<td style="text-align:left;">
Pda 3
</td>
<td style="text-align:right;">
1.944535
</td>
<td style="text-align:right;">
1.94454
</td>
</tr>
<tr>
<td style="text-align:left;">
Pda_3\_07
</td>
<td style="text-align:left;">
Pda
</td>
<td style="text-align:left;">
Pocillopora
</td>
<td style="text-align:left;">
Pda 3
</td>
<td style="text-align:right;">
1.943428
</td>
<td style="text-align:right;">
1.94343
</td>
</tr>
<tr>
<td style="text-align:left;">
Plu_1\_02
</td>
<td style="text-align:left;">
Plu
</td>
<td style="text-align:left;">
Porites
</td>
<td style="text-align:left;">
Plu 1
</td>
<td style="text-align:right;">
1.915073
</td>
<td style="text-align:right;">
1.91507
</td>
</tr>
<tr>
<td style="text-align:left;">
Plu_1\_03
</td>
<td style="text-align:left;">
Plu
</td>
<td style="text-align:left;">
Porites
</td>
<td style="text-align:left;">
Plu 1
</td>
<td style="text-align:right;">
1.914772
</td>
<td style="text-align:right;">
1.91477
</td>
</tr>
<tr>
<td style="text-align:left;">
Plu_1\_04
</td>
<td style="text-align:left;">
Plu
</td>
<td style="text-align:left;">
Porites
</td>
<td style="text-align:left;">
Plu 1
</td>
<td style="text-align:right;">
1.913889
</td>
<td style="text-align:right;">
1.91389
</td>
</tr>
<tr>
<td style="text-align:left;">
Plu_1\_05
</td>
<td style="text-align:left;">
Plu
</td>
<td style="text-align:left;">
Porites
</td>
<td style="text-align:left;">
Plu 1
</td>
<td style="text-align:right;">
1.926412
</td>
<td style="text-align:right;">
1.92641
</td>
</tr>
<tr>
<td style="text-align:left;">
Plu_1\_06
</td>
<td style="text-align:left;">
Plu
</td>
<td style="text-align:left;">
Porites
</td>
<td style="text-align:left;">
Plu 1
</td>
<td style="text-align:right;">
1.921944
</td>
<td style="text-align:right;">
1.92194
</td>
</tr>
<tr>
<td style="text-align:left;">
Plu_1\_07
</td>
<td style="text-align:left;">
Plu
</td>
<td style="text-align:left;">
Porites
</td>
<td style="text-align:left;">
Plu 1
</td>
<td style="text-align:right;">
1.927036
</td>
<td style="text-align:right;">
1.92704
</td>
</tr>
<tr>
<td style="text-align:left;">
Plu_2\_01
</td>
<td style="text-align:left;">
Plu
</td>
<td style="text-align:left;">
Porites
</td>
<td style="text-align:left;">
Plu 2
</td>
<td style="text-align:right;">
1.924559
</td>
<td style="text-align:right;">
1.92456
</td>
</tr>
<tr>
<td style="text-align:left;">
Plu_2\_02
</td>
<td style="text-align:left;">
Plu
</td>
<td style="text-align:left;">
Porites
</td>
<td style="text-align:left;">
Plu 2
</td>
<td style="text-align:right;">
1.932550
</td>
<td style="text-align:right;">
1.93255
</td>
</tr>
<tr>
<td style="text-align:left;">
Plu_2\_03
</td>
<td style="text-align:left;">
Plu
</td>
<td style="text-align:left;">
Porites
</td>
<td style="text-align:left;">
Plu 2
</td>
<td style="text-align:right;">
1.919497
</td>
<td style="text-align:right;">
1.91950
</td>
</tr>
<tr>
<td style="text-align:left;">
Plu_2\_04
</td>
<td style="text-align:left;">
Plu
</td>
<td style="text-align:left;">
Porites
</td>
<td style="text-align:left;">
Plu 2
</td>
<td style="text-align:right;">
1.933703
</td>
<td style="text-align:right;">
1.93370
</td>
</tr>
<tr>
<td style="text-align:left;">
Plu_2\_05
</td>
<td style="text-align:left;">
Plu
</td>
<td style="text-align:left;">
Porites
</td>
<td style="text-align:left;">
Plu 2
</td>
<td style="text-align:right;">
1.932976
</td>
<td style="text-align:right;">
1.93298
</td>
</tr>
<tr>
<td style="text-align:left;">
Plu_2\_06
</td>
<td style="text-align:left;">
Plu
</td>
<td style="text-align:left;">
Porites
</td>
<td style="text-align:left;">
Plu 2
</td>
<td style="text-align:right;">
1.928865
</td>
<td style="text-align:right;">
1.92886
</td>
</tr>
<tr>
<td style="text-align:left;">
Plu_3\_01
</td>
<td style="text-align:left;">
Plu
</td>
<td style="text-align:left;">
Porites
</td>
<td style="text-align:left;">
Plu 3
</td>
<td style="text-align:right;">
1.925979
</td>
<td style="text-align:right;">
1.92598
</td>
</tr>
<tr>
<td style="text-align:left;">
Plu_3\_02
</td>
<td style="text-align:left;">
Plu
</td>
<td style="text-align:left;">
Porites
</td>
<td style="text-align:left;">
Plu 3
</td>
<td style="text-align:right;">
1.930310
</td>
<td style="text-align:right;">
1.93031
</td>
</tr>
<tr>
<td style="text-align:left;">
Plu_3\_03
</td>
<td style="text-align:left;">
Plu
</td>
<td style="text-align:left;">
Porites
</td>
<td style="text-align:left;">
Plu 3
</td>
<td style="text-align:right;">
1.935038
</td>
<td style="text-align:right;">
1.93504
</td>
</tr>
<tr>
<td style="text-align:left;">
Plu_3\_04
</td>
<td style="text-align:left;">
Plu
</td>
<td style="text-align:left;">
Porites
</td>
<td style="text-align:left;">
Plu 3
</td>
<td style="text-align:right;">
1.923040
</td>
<td style="text-align:right;">
1.92304
</td>
</tr>
<tr>
<td style="text-align:left;">
Plu_3\_05
</td>
<td style="text-align:left;">
Plu
</td>
<td style="text-align:left;">
Porites
</td>
<td style="text-align:left;">
Plu 3
</td>
<td style="text-align:right;">
1.935577
</td>
<td style="text-align:right;">
1.93558
</td>
</tr>
<tr>
<td style="text-align:left;">
Plu_3\_06
</td>
<td style="text-align:left;">
Plu
</td>
<td style="text-align:left;">
Porites
</td>
<td style="text-align:left;">
Plu 3
</td>
<td style="text-align:right;">
1.919738
</td>
<td style="text-align:right;">
1.91974
</td>
</tr>
<tr>
<td style="text-align:left;">
Pve_1\_01
</td>
<td style="text-align:left;">
Pve
</td>
<td style="text-align:left;">
Pocillopora
</td>
<td style="text-align:left;">
Pve 1
</td>
<td style="text-align:right;">
1.966073
</td>
<td style="text-align:right;">
1.96607
</td>
</tr>
<tr>
<td style="text-align:left;">
Pve_1\_02
</td>
<td style="text-align:left;">
Pve
</td>
<td style="text-align:left;">
Pocillopora
</td>
<td style="text-align:left;">
Pve 1
</td>
<td style="text-align:right;">
1.964679
</td>
<td style="text-align:right;">
1.96468
</td>
</tr>
<tr>
<td style="text-align:left;">
Pve_1\_03
</td>
<td style="text-align:left;">
Pve
</td>
<td style="text-align:left;">
Pocillopora
</td>
<td style="text-align:left;">
Pve 1
</td>
<td style="text-align:right;">
1.964669
</td>
<td style="text-align:right;">
1.96467
</td>
</tr>
<tr>
<td style="text-align:left;">
Pve_1\_04
</td>
<td style="text-align:left;">
Pve
</td>
<td style="text-align:left;">
Pocillopora
</td>
<td style="text-align:left;">
Pve 1
</td>
<td style="text-align:right;">
1.960303
</td>
<td style="text-align:right;">
1.96030
</td>
</tr>
<tr>
<td style="text-align:left;">
Pve_1\_05
</td>
<td style="text-align:left;">
Pve
</td>
<td style="text-align:left;">
Pocillopora
</td>
<td style="text-align:left;">
Pve 1
</td>
<td style="text-align:right;">
1.957218
</td>
<td style="text-align:right;">
1.95722
</td>
</tr>
<tr>
<td style="text-align:left;">
Pve_1\_06
</td>
<td style="text-align:left;">
Pve
</td>
<td style="text-align:left;">
Pocillopora
</td>
<td style="text-align:left;">
Pve 1
</td>
<td style="text-align:right;">
1.955084
</td>
<td style="text-align:right;">
1.95508
</td>
</tr>
<tr>
<td style="text-align:left;">
Pve_1\_07
</td>
<td style="text-align:left;">
Pve
</td>
<td style="text-align:left;">
Pocillopora
</td>
<td style="text-align:left;">
Pve 1
</td>
<td style="text-align:right;">
1.955287
</td>
<td style="text-align:right;">
1.95529
</td>
</tr>
<tr>
<td style="text-align:left;">
Pve_1\_08
</td>
<td style="text-align:left;">
Pve
</td>
<td style="text-align:left;">
Pocillopora
</td>
<td style="text-align:left;">
Pve 1
</td>
<td style="text-align:right;">
1.963527
</td>
<td style="text-align:right;">
1.96353
</td>
</tr>
<tr>
<td style="text-align:left;">
Pve_2\_01
</td>
<td style="text-align:left;">
Pve
</td>
<td style="text-align:left;">
Pocillopora
</td>
<td style="text-align:left;">
Pve 2
</td>
<td style="text-align:right;">
1.959375
</td>
<td style="text-align:right;">
1.95938
</td>
</tr>
<tr>
<td style="text-align:left;">
Pve_2\_02
</td>
<td style="text-align:left;">
Pve
</td>
<td style="text-align:left;">
Pocillopora
</td>
<td style="text-align:left;">
Pve 2
</td>
<td style="text-align:right;">
1.950475
</td>
<td style="text-align:right;">
1.95047
</td>
</tr>
<tr>
<td style="text-align:left;">
Pve_2\_03
</td>
<td style="text-align:left;">
Pve
</td>
<td style="text-align:left;">
Pocillopora
</td>
<td style="text-align:left;">
Pve 2
</td>
<td style="text-align:right;">
1.958198
</td>
<td style="text-align:right;">
1.95820
</td>
</tr>
<tr>
<td style="text-align:left;">
Pve_2\_04
</td>
<td style="text-align:left;">
Pve
</td>
<td style="text-align:left;">
Pocillopora
</td>
<td style="text-align:left;">
Pve 2
</td>
<td style="text-align:right;">
1.972118
</td>
<td style="text-align:right;">
1.97212
</td>
</tr>
<tr>
<td style="text-align:left;">
Pve_2\_05
</td>
<td style="text-align:left;">
Pve
</td>
<td style="text-align:left;">
Pocillopora
</td>
<td style="text-align:left;">
Pve 2
</td>
<td style="text-align:right;">
1.957665
</td>
<td style="text-align:right;">
1.95767
</td>
</tr>
<tr>
<td style="text-align:left;">
Pve_2\_06
</td>
<td style="text-align:left;">
Pve
</td>
<td style="text-align:left;">
Pocillopora
</td>
<td style="text-align:left;">
Pve 2
</td>
<td style="text-align:right;">
1.944179
</td>
<td style="text-align:right;">
1.94418
</td>
</tr>
<tr>
<td style="text-align:left;">
Pve_3\_01
</td>
<td style="text-align:left;">
Pve
</td>
<td style="text-align:left;">
Pocillopora
</td>
<td style="text-align:left;">
Pve 3
</td>
<td style="text-align:right;">
1.959757
</td>
<td style="text-align:right;">
1.95976
</td>
</tr>
<tr>
<td style="text-align:left;">
Pve_3\_02
</td>
<td style="text-align:left;">
Pve
</td>
<td style="text-align:left;">
Pocillopora
</td>
<td style="text-align:left;">
Pve 3
</td>
<td style="text-align:right;">
1.952404
</td>
<td style="text-align:right;">
1.95240
</td>
</tr>
<tr>
<td style="text-align:left;">
Pve_3\_03
</td>
<td style="text-align:left;">
Pve
</td>
<td style="text-align:left;">
Pocillopora
</td>
<td style="text-align:left;">
Pve 3
</td>
<td style="text-align:right;">
1.960369
</td>
<td style="text-align:right;">
1.96037
</td>
</tr>
<tr>
<td style="text-align:left;">
Pve_3\_04
</td>
<td style="text-align:left;">
Pve
</td>
<td style="text-align:left;">
Pocillopora
</td>
<td style="text-align:left;">
Pve 3
</td>
<td style="text-align:right;">
1.954793
</td>
<td style="text-align:right;">
1.95479
</td>
</tr>
<tr>
<td style="text-align:left;">
Pve_3\_05
</td>
<td style="text-align:left;">
Pve
</td>
<td style="text-align:left;">
Pocillopora
</td>
<td style="text-align:left;">
Pve 3
</td>
<td style="text-align:right;">
1.949538
</td>
<td style="text-align:right;">
1.94954
</td>
</tr>
<tr>
<td style="text-align:left;">
Pve_3\_06
</td>
<td style="text-align:left;">
Pve
</td>
<td style="text-align:left;">
Pocillopora
</td>
<td style="text-align:left;">
Pve 3
</td>
<td style="text-align:right;">
1.967342
</td>
<td style="text-align:right;">
1.96734
</td>
</tr>
</tbody>
</table>

As you can see, I am calculating their data the same way. So all
calculations are working. Let’s proceed with discriminatory analyses.

## Radii Analysis

I calculated a FD for radii 2-20 to conduct a discriminatory test
similar to the Reichert *et al.* (2017) analysis. They found that r=8
had the highest discriminatory power.

## Interspecific Detection

<h5>
Figure 4. Interspecific discriminaotry power of FD at different radii
</h5>
<img src="/notebook/images/3dmorphometrics/interspecificDiscriminatoryAnalysis-1.png" width="90%" style="display: block; margin: auto;" />
<table class="table" style="margin-left: auto; margin-right: auto;">
<caption>
Table 2: Interspecific radii discriminaotry power. N represents the
number of significantly different pairwise comparisons, and is ordered
by the most signifcant values.
</caption>
<thead>
<tr>
<th style="text-align:right;">
radii
</th>
<th style="text-align:right;">
n
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:right;">
7
</td>
<td style="text-align:right;">
12
</td>
</tr>
<tr>
<td style="text-align:right;">
8
</td>
<td style="text-align:right;">
12
</td>
</tr>
<tr>
<td style="text-align:right;">
19
</td>
<td style="text-align:right;">
11
</td>
</tr>
<tr>
<td style="text-align:right;">
20
</td>
<td style="text-align:right;">
11
</td>
</tr>
<tr>
<td style="text-align:right;">
3
</td>
<td style="text-align:right;">
10
</td>
</tr>
<tr>
<td style="text-align:right;">
6
</td>
<td style="text-align:right;">
10
</td>
</tr>
<tr>
<td style="text-align:right;">
9
</td>
<td style="text-align:right;">
10
</td>
</tr>
<tr>
<td style="text-align:right;">
18
</td>
<td style="text-align:right;">
10
</td>
</tr>
<tr>
<td style="text-align:right;">
4
</td>
<td style="text-align:right;">
9
</td>
</tr>
<tr>
<td style="text-align:right;">
5
</td>
<td style="text-align:right;">
9
</td>
</tr>
<tr>
<td style="text-align:right;">
10
</td>
<td style="text-align:right;">
9
</td>
</tr>
<tr>
<td style="text-align:right;">
11
</td>
<td style="text-align:right;">
9
</td>
</tr>
<tr>
<td style="text-align:right;">
12
</td>
<td style="text-align:right;">
9
</td>
</tr>
<tr>
<td style="text-align:right;">
13
</td>
<td style="text-align:right;">
9
</td>
</tr>
<tr>
<td style="text-align:right;">
14
</td>
<td style="text-align:right;">
9
</td>
</tr>
<tr>
<td style="text-align:right;">
15
</td>
<td style="text-align:right;">
9
</td>
</tr>
<tr>
<td style="text-align:right;">
16
</td>
<td style="text-align:right;">
9
</td>
</tr>
<tr>
<td style="text-align:right;">
17
</td>
<td style="text-align:right;">
9
</td>
</tr>
<tr>
<td style="text-align:right;">
2
</td>
<td style="text-align:right;">
7
</td>
</tr>
</tbody>
</table>
<table class="table" style="margin-left: auto; margin-right: auto;">
<caption>
Table 3: Avg significance of radii interspecific discriminaotry power.
Radius is the dilation radius, and p.avg is the average signficant
pairwise difference between the 12 groups.
</caption>
<thead>
<tr>
<th style="text-align:right;">
radii
</th>
<th style="text-align:right;">
p.avg
</th>
<th style="text-align:right;">
n
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:right;">
8
</td>
<td style="text-align:right;">
0.0025290
</td>
<td style="text-align:right;">
12
</td>
</tr>
<tr>
<td style="text-align:right;">
7
</td>
<td style="text-align:right;">
0.0063254
</td>
<td style="text-align:right;">
12
</td>
</tr>
<tr>
<td style="text-align:right;">
20
</td>
<td style="text-align:right;">
0.0035425
</td>
<td style="text-align:right;">
11
</td>
</tr>
<tr>
<td style="text-align:right;">
19
</td>
<td style="text-align:right;">
0.0055155
</td>
<td style="text-align:right;">
11
</td>
</tr>
</tbody>
</table>

Dilation radii of 7 and 8 produce the highest interspecific
discriminatory power. Using these radii, we can differentiate between
all species except: Ahu-Ami, Ahu-Pve, Ami-Pve, Ahu-Pda, Pda-Pve. When
looking at the average pairwise significance from radii 7 and 8, 8
performs better than 7. 19 and 20 follow close behind, with these radii
not being able to discriminate between Ahu and Pda, but there average
pairwise significance is still better than a radii of 8. So we cannot
differentiate the Acroporas and the *Pocillopora verrucosa* with radii
of 7 and 8, and we add *Pocillopora damicornis* to that list when we
change the radii to 19 or 20. **Therefore, we are really only able to
differentiate between the Porites and the branching corals. **

## Intraspecific Detection

Running these tests on only a subset of radii where the n from Table 2
is greater than or equal to 10 (the 8 best performing radii).
<h5>
Figure 5. Intraspecific discriminaotry power of FD at different radii
</h5>
<img src="/notebook/images/3dmorphometrics/intraspecificDiscriminatoryAnalysis-1.png" width="90%" style="display: block; margin: auto;" />
<table class="table" style="margin-left: auto; margin-right: auto;">
<caption>
Table 4: Intraspecific radii discriminaotry power. N represents the
number of significantly different pairwise comparisons, and is ordered
by the most signifcant values.
</caption>
<thead>
<tr>
<th style="text-align:right;">
radii
</th>
<th style="text-align:right;">
n
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:right;">
19
</td>
<td style="text-align:right;">
11
</td>
</tr>
<tr>
<td style="text-align:right;">
20
</td>
<td style="text-align:right;">
11
</td>
</tr>
<tr>
<td style="text-align:right;">
18
</td>
<td style="text-align:right;">
9
</td>
</tr>
<tr>
<td style="text-align:right;">
9
</td>
<td style="text-align:right;">
6
</td>
</tr>
<tr>
<td style="text-align:right;">
8
</td>
<td style="text-align:right;">
5
</td>
</tr>
<tr>
<td style="text-align:right;">
7
</td>
<td style="text-align:right;">
4
</td>
</tr>
<tr>
<td style="text-align:right;">
6
</td>
<td style="text-align:right;">
3
</td>
</tr>
</tbody>
</table>
<table class="table" style="margin-left: auto; margin-right: auto;">
<caption>
Table 5: Avg significance of radii intraspecific discriminaotry power.
Radius is the dilation radius, and p.avg is the average signficant
pairwise difference between the significantly diffrent groups.
</caption>
<thead>
<tr>
<th style="text-align:right;">
radii
</th>
<th style="text-align:right;">
p.avg
</th>
<th style="text-align:right;">
n
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:right;">
20
</td>
<td style="text-align:right;">
0.0142110
</td>
<td style="text-align:right;">
11
</td>
</tr>
<tr>
<td style="text-align:right;">
19
</td>
<td style="text-align:right;">
0.0145423
</td>
<td style="text-align:right;">
11
</td>
</tr>
<tr>
<td style="text-align:right;">
18
</td>
<td style="text-align:right;">
0.0067559
</td>
<td style="text-align:right;">
9
</td>
</tr>
<tr>
<td style="text-align:right;">
9
</td>
<td style="text-align:right;">
0.0113366
</td>
<td style="text-align:right;">
6
</td>
</tr>
<tr>
<td style="text-align:right;">
8
</td>
<td style="text-align:right;">
0.0096806
</td>
<td style="text-align:right;">
5
</td>
</tr>
<tr>
<td style="text-align:right;">
7
</td>
<td style="text-align:right;">
0.0127828
</td>
<td style="text-align:right;">
4
</td>
</tr>
<tr>
<td style="text-align:right;">
6
</td>
<td style="text-align:right;">
0.0190583
</td>
<td style="text-align:right;">
3
</td>
</tr>
</tbody>
</table>

For intraspecific differences, dilation radii 19 & 20 produced optimal
results, followed closely behind by 18 (Table 3). This is different from
interspecific variation; 7 and 8 performed much worse here (\< half of
detected pair-wise differences compared to 19,20). 18, 19 and 20 could
detect intraspecific differences in all 6 species, while 7 and 8 could
only detect intraspecific differences in 2 species (Acroporas).
Differences in all 3 Ami colonies could be detected with a radii of 8,
9, 18, 19 or 20, suggesting consistently different morphologies for each
of the colonies of this species. Ahu (6 radii), Pcy (2 r) and Pda (2 r)
could detect 2 pairwise differences, indicating a single colony was
significantly different than the other two.

These results are interesting. While fractal dimensions cannot
distinguish between Acroporas and other branching species, it can
consistently distinguish intraspecific variation among these species,
especially *Acropora humilis*. This might suggest that these species
have plastic morphologies that vary among the population, but that this
variation can be parsed apart by colony-specific morphology. Further,
Reichert *et al.* (2017) report the fractal dimension analyses were
superior in quantifying intraspecific changes of colonies over time
compared to traditional morphological characteristics, indicating that
these analyses are sensitive to small scale changes. Are these colonies
collected from distinct environments, which uniquely shaped the colony
morphology? Are genetics at play? From these data alone, it’s impossible
to tell. But we can begin to explore these questions using my data
below.

The take away from these analyses are: 1. morphological complexity can
be described with fractal dimensions 2. FD can generally discern between
inter- and intra-specific, but its not perfect 3. Dilation radii must be
selected according to resolution of analyses

# Analyzing Our Scans

<h5>
Figure 6. Genotype-specific discriminaotry power of FD at different
radii
</h5>
<img src="/notebook/images/3dmorphometrics/genetSpecificAnalysis-1.png" width="90%" style="display: block; margin: auto;" />
<table class="table" style="margin-left: auto; margin-right: auto;">
<caption>
Table 6: Genotype radii discriminaotry power. Radius is the dilation
radius, and the remaining columns indicate the level and number of
significantly different pair-wise comparisons among the genotypes
</caption>
<thead>
<tr>
<th style="text-align:right;">
radius
</th>
<th style="text-align:right;">
\*\*\*\*
</th>
<th style="text-align:right;">
\*\*\*
</th>
<th style="text-align:right;">
\*\*
</th>
<th style="text-align:right;">

- </th>
  <th style="text-align:right;">
  ns
  </th>
  </tr>
  </thead>
  <tbody>
  <tr>
  <td style="text-align:right;">
  6
  </td>
  <td style="text-align:right;">
  3
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
  NA
  </td>
  </tr>
  <tr>
  <td style="text-align:right;">
  7
  </td>
  <td style="text-align:right;">
  3
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
  NA
  </td>
  </tr>
  <tr>
  <td style="text-align:right;">
  8
  </td>
  <td style="text-align:right;">
  3
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
  NA
  </td>
  </tr>
  <tr>
  <td style="text-align:right;">
  9
  </td>
  <td style="text-align:right;">
  3
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
  NA
  </td>
  </tr>
  <tr>
  <td style="text-align:right;">
  10
  </td>
  <td style="text-align:right;">
  3
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
  NA
  </td>
  </tr>
  <tr>
  <td style="text-align:right;">
  11
  </td>
  <td style="text-align:right;">
  3
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
  NA
  </td>
  </tr>
  <tr>
  <td style="text-align:right;">
  12
  </td>
  <td style="text-align:right;">
  3
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
  NA
  </td>
  </tr>
  <tr>
  <td style="text-align:right;">
  13
  </td>
  <td style="text-align:right;">
  3
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
  NA
  </td>
  </tr>
  <tr>
  <td style="text-align:right;">
  14
  </td>
  <td style="text-align:right;">
  3
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
  NA
  </td>
  </tr>
  <tr>
  <td style="text-align:right;">
  15
  </td>
  <td style="text-align:right;">
  3
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
  NA
  </td>
  </tr>
  <tr>
  <td style="text-align:right;">
  16
  </td>
  <td style="text-align:right;">
  3
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
  NA
  </td>
  </tr>
  <tr>
  <td style="text-align:right;">
  17
  </td>
  <td style="text-align:right;">
  3
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
  NA
  </td>
  </tr>
  <tr>
  <td style="text-align:right;">
  5
  </td>
  <td style="text-align:right;">
  2
  </td>
  <td style="text-align:right;">
  1
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
  </tr>
  <tr>
  <td style="text-align:right;">
  18
  </td>
  <td style="text-align:right;">
  2
  </td>
  <td style="text-align:right;">
  1
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
  </tr>
  <tr>
  <td style="text-align:right;">
  19
  </td>
  <td style="text-align:right;">
  2
  </td>
  <td style="text-align:right;">
  1
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
  </tr>
  <tr>
  <td style="text-align:right;">
  4
  </td>
  <td style="text-align:right;">
  2
  </td>
  <td style="text-align:right;">
  NA
  </td>
  <td style="text-align:right;">
  1
  </td>
  <td style="text-align:right;">
  NA
  </td>
  <td style="text-align:right;">
  NA
  </td>
  </tr>
  <tr>
  <td style="text-align:right;">
  20
  </td>
  <td style="text-align:right;">
  2
  </td>
  <td style="text-align:right;">
  NA
  </td>
  <td style="text-align:right;">
  1
  </td>
  <td style="text-align:right;">
  NA
  </td>
  <td style="text-align:right;">
  NA
  </td>
  </tr>
  <tr>
  <td style="text-align:right;">
  3
  </td>
  <td style="text-align:right;">
  1
  </td>
  <td style="text-align:right;">
  NA
  </td>
  <td style="text-align:right;">
  1
  </td>
  <td style="text-align:right;">
  1
  </td>
  <td style="text-align:right;">
  NA
  </td>
  </tr>
  <tr>
  <td style="text-align:right;">
  2
  </td>
  <td style="text-align:right;">
  NA
  </td>
  <td style="text-align:right;">
  1
  </td>
  <td style="text-align:right;">
  NA
  </td>
  <td style="text-align:right;">
  NA
  </td>
  <td style="text-align:right;">
  2
  </td>
  </tr>
  </tbody>
  </table>

<table class="table" style="margin-left: auto; margin-right: auto;">
<caption>
Table 7: Avg significance of genotype radii discriminaotry power. Radius
is the dilation radius, and p.avg is the average signficant pairwise
difference between the three groups.
</caption>
<thead>
<tr>
<th style="text-align:right;">
radii
</th>
<th style="text-align:right;">
p.avg
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:right;">
11
</td>
<td style="text-align:right;">
2.00e-07
</td>
</tr>
<tr>
<td style="text-align:right;">
10
</td>
<td style="text-align:right;">
2.00e-07
</td>
</tr>
<tr>
<td style="text-align:right;">
12
</td>
<td style="text-align:right;">
2.00e-07
</td>
</tr>
<tr>
<td style="text-align:right;">
9
</td>
<td style="text-align:right;">
3.00e-07
</td>
</tr>
<tr>
<td style="text-align:right;">
13
</td>
<td style="text-align:right;">
3.00e-07
</td>
</tr>
<tr>
<td style="text-align:right;">
8
</td>
<td style="text-align:right;">
5.00e-07
</td>
</tr>
<tr>
<td style="text-align:right;">
14
</td>
<td style="text-align:right;">
6.00e-07
</td>
</tr>
<tr>
<td style="text-align:right;">
7
</td>
<td style="text-align:right;">
1.40e-06
</td>
</tr>
<tr>
<td style="text-align:right;">
15
</td>
<td style="text-align:right;">
1.40e-06
</td>
</tr>
<tr>
<td style="text-align:right;">
16
</td>
<td style="text-align:right;">
4.00e-06
</td>
</tr>
<tr>
<td style="text-align:right;">
6
</td>
<td style="text-align:right;">
7.10e-06
</td>
</tr>
<tr>
<td style="text-align:right;">
17
</td>
<td style="text-align:right;">
1.33e-05
</td>
</tr>
</tbody>
</table>

Dilation radii 6-17 perform the best and have identical significance
levels. If we take a look at the average pairwise significance between
the 3 groups, using a radius of 11 produces the best results. However,
choosing any radius 6-17 will produce a very significant average p value
\<0.00001, which adds confidence that there is a difference in the
fractal dimensions of these 3 genotypes.

This is interesting because these fragments were picked to be, 1. around
the same size \~7cm, 2. from unique colony in nursery (a tree had \>60
colonies all of one genotype) 3. minimal branching, 1 apical tip

So even though we selected to have visually identical fragments,
genotype specific morphology is evident. Let’s investigate other
classical morphometrics to see if these genotypes were different. For
all analyses below, I am using FD11 as the measurement of FD.

<h5>
Figure 7. Traditional morphometric comparisons of fragment height,
surface area, volume, and surface area:volume ratio
</h5>

<img src="/notebook/images/3dmorphometrics/classicMorphometrics-1.png" width="90%" style="display: block; margin: auto;" />\#
A tibble: 12 x 13 metric data anova results term group1 group2 null.\~1
estim\~2 conf.\~3 <chr> <list> <list> <list> <chr> <chr> <chr> <dbl>
<dbl> <dbl> 1 SA <tibble> <aov> <tibble> genoty\~ AC-2 MB-C 0 -4.42
-8.98 2 SA <tibble> <aov> <tibble> genoty\~ AC-2 SI-A 0 8.48 4.10 3 SA
<tibble> <aov> <tibble> genoty\~ MB-C SI-A 0 12.9 8.47 4 V <tibble>
<aov> <tibble> genoty\~ AC-2 MB-C 0 -0.693 -1.58 5 V <tibble> <aov>
<tibble> genoty\~ AC-2 SI-A 0 1.34 0.479 6 V <tibble> <aov> <tibble>
genoty\~ MB-C SI-A 0 2.03 1.16 7 SA_V <tibble> <aov> <tibble> genoty\~
AC-2 MB-C 0 0.121 -0.380 8 SA_V <tibble> <aov> <tibble> genoty\~ AC-2
SI-A 0 -0.358 -0.840 9 SA_V <tibble> <aov> <tibble> genoty\~ MB-C SI-A 0
-0.479 -0.966 10 H <tibble> <aov> <tibble> genoty\~ AC-2 MB-C 0 -0.263
-0.638 11 H <tibble> <aov> <tibble> genoty\~ AC-2 SI-A 0 -0.118 -0.479
12 H <tibble> <aov> <tibble> genoty\~ MB-C SI-A 0 0.145 -0.220 \# … with
3 more variables: conf.high <dbl>, p.adj <dbl>, p.adj.signif <chr>, \#
and abbreviated variable names 1: null.value, 2: estimate, 3: conf.low

The three genotypes did not have significantly different surface area to
volume ratio or heights. However, there were significant pairwise
differences between surface area and volumes between SI-A and the other
genotypes. Standardizing all growth rates to surface area is therefore
critical for this data.

<h5>
Figure 8. Linear regression of traditional morphometrics to FD
</h5>

<img src="/notebook/images/3dmorphometrics/FD-corrs-1.png" width="90%" style="display: block; margin: auto;" />

There’s a pretty strong relationship between surface area and volume
with FD, with FD explaining about 61% and 44% of the variance in SA and
V, respectively. There is no relationship between height and surface
area to volume ratio with fractal dimension.

<h5>
Figure 9. Avg Daily Growth by (A) Treatment and (B) Genotype
</h5>

<img src="/notebook/images/3dmorphometrics/growthStats-1.png" width="90%" style="display: block; margin: auto;" />

Growth rates are lower than anticipated. This is a combination of
actually depressed growth from what I was expecting and the high
resolution of our 3D scanner where estimated SA is much higher than
usually measured. To try and make comparable, I looked at some other
published work on the ’ol AcDC and found some SA derived from stitched
together images on imajeJ in a Muller et al paper. Their average SA was
\~ 7$cm^2$, which is in comparison to our avg SA \~ 39. If we simply
divide the two and scale the growth rates accordingly, we get an avg
LCO2 growth rate of 0.73 mg/cm^-2/day. However, numerous papers from
NOAA AOML Coral Program lab have used the same 3D scanner setup to
derive growth rates that were higher than what I observed. I do not know
the exact SA from these studies, but they were significantly shorter
than the experiment I ran which may explain the depressed growth rates
(Enochs *et al* 2018 for instance). Nevertheless, the patterns are
interesting and what I will be focussing on.

<h5>
Figure 10. Regression of absolute growth (mg) to (A) surface area and
(B) fractal dimension, separated by treatment group
</h5>
<img src="/notebook/images/3dmorphometrics/gMorphCorrs-1.png" width="90%" style="display: block; margin: auto;" />
<h5>
Figure 11. Regression of daily growth rate (mg/cm^2/day) to (A) surface
area and (B) fractal dimension, separated by treatment group
</h5>

<img src="/notebook/images/3dmorphometrics/gMorphCorrs-2.png" width="90%" style="display: block; margin: auto;" />

Absolute growth scales with both surface area and fractal dimension.
Surface area and FD explain more variance in the HCO2 (69% v 60%) than
the LCO2 (43% v 44%) groups. Overall, surface area explains more
variance in absolute growth than FD, but it is roughly negligible.

When standardizing absolute growth to surface area, an interesting
pattern emerges. Here, the amount of variance in growth rates explained
by FD is nearly twice that of surface area. Further, for the LCO2
groups, none of the variance in growth rates is explained by either of
the morphometrics, which is in contrast to the HCO2 groups where surface
area and FD explain 25% and 47% of the variance, respectively.

We cannot separate SA and FD from each other completely. Since FD
describes how surface area fills space at different scales, it makes
sense that as FD increases, SA will increase as well. Not in a perfect
1:1 relationship, but a general trend. This data, therefore,
demonstrates that resistance to OA (maintained growth rates) is driven
more by fractal dimensions (measurement of surface complexity) than by
total surface area. Further, since SA standardized growth rates still
increased as surface area increased, it is likely that growth rates do
not scale linearly with SA.

# What does this all mean?

Let’s dive into that second plot more and the hypotheses that this data
may support.
<img src="/notebook/images/3dmorphometrics/plotItAgain-1.png" width="90%" style="display: block; margin: auto;" />
This data supports the hypothesis that surface complexity confers
resistance to OA but does not confer increased growth rates under
ambient conditions. This hypothesis aligns closesly with the hypothesis
outlined in Chan *et al.* (2016). Briefly, surface complexity slows
water flow around the colony, thickening the diffusive boundary layer
(DBL) and increasing water residence time in the thin layer directly
surrounding the coral. Therefore, the coral’s metabolism has a greater
influence on the properties of this seawater: during the day this water
will have a higher pH than bulk seawater (photosynthesis) and at night
this water will have a lower pH than bulk seawater (respiration). Coral
metabolism and water residence time is well investigated at the
ecosystem scale where these same properties are at play, but how these
properties play out at the organismal scale remains largely unexplored.
Together, these relative highs and lows create a variable pH environment
that could stress harden a coral where it has adapted and/or acclimated
and can, therefore, better withstand OA. Alternatively, this diel
variability could work in concert with day to night calcification ratios
to enhance daytime calcification to counteract the mean decrease in pH,
effectively ameliorating OA (Enochs *et al.* 2018; Chan & Higgins 2017).

Chan *et al.* (2016) supported this hypothesis by measuring pH changes
in the DBL under different morphologies at different flow rates. They
saw that under low flow velocities and complex morphologies (they did
not quantify complexity, just had 2 different species w/ obvious surface
complexity differences), pH upregulation in the DBL was quite high and
had the potential to ameliorate the effects of OA in the DBL (DBL pH
under OA = DBL pH under ambient due to elevations). These data closely
approximated their modeled pH increases based on photosynthesis and
calcification rates. How these DBL pH increases manifest to growth
rates/OA resistance remains to be seen. Comeau *et al* (2019) measured
pH in DBL (microprobes), pH in calcifying fluids (boron systematics),
and growth rates under different light and flow regimes. For the
*Acropora* congeneric, they did not detect any elevations in DBL pH
during the day, but did detect large decreases during the night.
However, for *Plesiastrea veripora*, they detected a large increase in
DBL pH which increased under OA treatments in low flow identical to the
findings in Chan *et al.* (2016). These same corals did not, however,
have elevated pH in the calcifying fluid or maintain growth rates under
OA. It is important to note that Comeau *et al* (2019) did not have
variable pH treatments and did not measure pH DBL under darkness.

Unfortunately, I was unable to measure the DBL pH with microsensors, and
I did not measure the metabolism of the corals. But, this is the first
dataset I am aware of that has experimental evidence of surface
complexity driving OA resistance. How the potential pH variability
caused by the surface complexity affects calcifying fluid pH as
determined by boron systematics remains to be seen. We should have that
data soon. Comeau *et al.* (2022) used boron systematics to probe the
calcifying fluid pH of corals collected from volcanic CO2 seeps in Papua
New Guinea. These seeps had low, but highly variable pH. The corals from
this environment maintained constant calcifying pH, relative to nearby
controls, despite the low mean pH. The growth rates of these corals are
not known.

# Next steps

I think there is an interesting story here of genotype-specific surface
complexity correlating with OA resistance. First, I’d like to explore
some more metrics of surface complexity from these 3D scans. I’m excited
to finish up the boron chemistry work to see how that plays into this
story. Finally, I’d like to import a characteristic 3D model of each
genotype into a computational model to see if surface complexity
measures due indeed create a thicker DBL. From this model, I can measure
water residence times, expected pH increases, etc.

# References

1.  Chan NCS, Wangpraseurt D, Kühl M, Connolly SR (2016) Flow and coral
    morphology control coral surface pH: Implications for the effects of
    ocean acidification. *Frontiers in Marine Science* 3:1-11.

2.  Chan WY, Eggins SM (2017) Calcification responses to diurnal
    variation in seawater carbonate chemistry by the coral Acropora
    formosa. *Coral Reefs* 36:763–772.

3.  Comeau S, Cornwall CE, Pupier CA, DeCarlo TM, Alessi C, Trehern R,
    McCulloch M (2019) Flow-driven micro-scale pH variability affects
    the physiology of corals and coralline algae under ocean
    acidification. *Scientific Reports* 9:1–12.

4.  Comeau S, Cornwall CE, Shlesinger T, Hoogenboom MO, Mana R,
    McCulloch MT, Rodolfo-Metalpa R (2022) pH variability at volcanic
    CO2 seeps regulates coral calcifying fluid chemistry. *Global Change
    Biology* 28(8):2751–2763.

5.  Enochs IC, Manzello DP, Jones P, Aguilar C, Cohen K, Valentino L,
    Schopmeyer S, Kolodzeij G, Jankulak M, Lirman D (2018) The influence
    of diel carbonate chemistry fluctuations on the calcification rate
    of Acropora cervicornis under present day and future acidification
    conditions. *Journal of Experimental Marine Biology and Ecology*
    506:135–143.

6.  Reichert J, Backes AR, Schubert P, Wilke T (2017) The power of 3D
    fractal dimensions for comparative shape and structural complexity
    analyses of irregularly shaped organisms. *Methods in Ecology and
    Evolution* 8(12):1650–1658.

7.  Torres-Pulliza D, Dornelas MA, Pizarro O, Bewley M, Blowes SA,
    Boutros N, Brambilla V, Chase TJ, Frank G, Friedman A, *et
    al.* (2020) A geometric basis for surface habitat complexity and
    biodiversity. *Nature Ecology & Evolution* 4:1495-1501.

</div>
