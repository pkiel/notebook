---
layout: post
title:  "Cheeca DO Analysis"
author: "Patrick M Kiel"
date: '2024-05-06'
categories: [research]
description: "Reviewing the dissolved oxygen data from Cheeca Rocks, Florida Keys."
output:
  md_document:
    variant: gfm
    preserve_yaml: TRUE
knit: (function(inputFile, encoding) {
  rmarkdown::render(inputFile, 
  encoding = encoding, 
  output_file = paste0('2024-05-06', "-",
                        gsub(pattern = "\\.Rmd$",
                              "", basename(inputFile))
                        ,".md"), 
  output_dir = "../_posts") })
always_allow_html: true
---

<script>
&#10;window.onload = function() {
    //query string in the password
    const urlParams = new URLSearchParams(window.location.search);
    const pass = urlParams.get('pass')
    document.getElementById("password").value = pass;
};
&#10;function verify() {
  <!-- set the password here -->
  if (document.getElementById('password').value === 'soup') {
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
&#10;img {
margin: 0 auto;
}
&#10;table {
    width: 90%;
    border: 0px solid #fff;
    border-collapse: collapse;
    overflow-x: auto;
    margin: 0 auto;
    display: block;
}
</style>
<!-- Place all chunks, text, etc here as you would a normal RMarkdown document -->

# Overview

Here I am analyzing the available dissolved oxygen (DO) data from Cheeca
Rocks, Florida Keys. The data is available from
[NCEI](https://www.ncei.noaa.gov/access/ocean-carbon-acidification-data-system/oceans/Moorings/Cheeca.html).

<iframe src="/notebook/images/cheecaDO/cheecaMap.html" height="600px" width="100%" style="border:none;">
</iframe>

## All the Data

<h5>
Figure 2. DO Data (mg/L) throughout the monitoring period
</h5>

<img src="/notebook/images/cheecaDO/unnamed-chunk-3-1.png" width="90%" style="display: block; margin: auto;" />
The data is quite patchy indicating lapses in data collection. Furthere
there is a general trendline around 7 mg/L, but there is a period of
highs in 2018 and lows in 2020.

Let’s zoom into these years.

<h5>
Figure 3. 2018: Seems offly high
</h5>
<img src="/notebook/images/cheecaDO/unnamed-chunk-4-1.png" width="90%" style="display: block; margin: auto;" />
<h5>
Figure 4. 2020: Low then Sensor Goes Offline in November
</h5>

<img src="/notebook/images/cheecaDO/unnamed-chunk-4-2.png" width="90%" style="display: block; margin: auto;" />

Data during most of 2018 looks about ~2 mg/L too high. There seems to be
an interesting dip in late July, which could have been a mild hypoxic
event, but since the surrounding readings were high, it’s hard to say.

Data during 2020 looks artificially low throughout the year. The sudden
drop in November and then its rebounding to ~7 suggests it was
malfunctioning, brought in for servicing, calibrated, and redeployed in
December.

Since I want to capture normal variability, I’ll throw away these 2018
and 2020 datasets.

# Lets look at Diel Variability

<h5>
Figure 5. Average Diel Variability Throughout the Year. Filled circles
denote 3-month rounded daily mean DO; lines extend to 3-month rounded
daily minimum and maximum DO
</h5>

<img src="/notebook/images/cheecaDO/unnamed-chunk-5-1.png" width="90%" style="display: block; margin: auto;" />

Where do these observations come from?
<h5>
Figure 6. Diel Variability across Three Month-Binned Monitoring Period.
Filled circles denote 3-month rounded daily mean DO; lines extend to
3-month rounded daily minimum and maximum DO
</h5>

<img src="/notebook/images/cheecaDO/unnamed-chunk-6-1.png" width="90%" style="display: block; margin: auto;" />
Overall there seems to be a seasonal component with the dry, windy
season (November-April; Black and Blues) having higher DO than the wet
season (May-October; Red and Yellows). Going to create 2 diel plots for
2 seasons.

<h5>
Figure 7. Diel Variability Plots
</h5>

<img src="/notebook/images/cheecaDO/unnamed-chunk-7-1.png" width="90%" style="display: block; margin: auto;" />
The dry season panel is pretty messy and doesn’t make much sense to me.
Around midnight it shoots above 8. I’d expect the peak to be around
17-19 since peak should lag solar noon by about 30-120 minutes, and
Cheeca’s solar noon (UTC+5) is 17. The wet season panel looks like a
nice sine wave approximating the changing of photosynthesis to match
sunlight with a peak at the expected time.

What if I do the same with an outlier filter applied:

<h5>
Figure 8. Still messy
</h5>
<img src="/notebook/images/cheecaDO/unnamed-chunk-8-1.png" width="90%" style="display: block; margin: auto;" />
<h5>
Figure 9. Seasonal DO Range; Filled circles denote seasonally averaged
daily mean DO; lines extend to seasonally averaged daily minimum and
maximum DO
</h5>
<img src="/notebook/images/cheecaDO/unnamed-chunk-8-2.png" width="90%" style="display: block; margin: auto;" />Table 1.
Seasonally averaged ranges
<table class=" lightable-material" style="font-family: &quot;Source Sans Pro&quot;, helvetica, sans-serif; margin-left: auto; margin-right: auto;">
<thead>
<tr>
<th style="text-align:left;">
season
</th>
<th style="text-align:right;">
DO_min
</th>
<th style="text-align:right;">
DO_max
</th>
<th style="text-align:right;">
DO_mean
</th>
<th style="text-align:right;">
DO_range
</th>
<th style="text-align:right;">
peak_shift
</th>
<th style="text-align:right;">
trough_shift
</th>
<th style="text-align:right;">
ratio
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:left;">
dry
</td>
<td style="text-align:right;">
6.697787
</td>
<td style="text-align:right;">
7.566482
</td>
<td style="text-align:right;">
7.053075
</td>
<td style="text-align:right;">
0.8686952
</td>
<td style="text-align:right;">
0.5134069
</td>
<td style="text-align:right;">
-0.3552883
</td>
<td style="text-align:right;">
1.445043
</td>
</tr>
<tr>
<td style="text-align:left;">
wet
</td>
<td style="text-align:right;">
5.578047
</td>
<td style="text-align:right;">
6.968147
</td>
<td style="text-align:right;">
6.123676
</td>
<td style="text-align:right;">
1.3901000
</td>
<td style="text-align:right;">
0.8444707
</td>
<td style="text-align:right;">
-0.5456293
</td>
<td style="text-align:right;">
1.547700
</td>
</tr>
</tbody>
</table>

Dry Season Range: 0.87 mg/L (26.54 umol O2/kg)

Wet season Range: 1.39 mg/L (42.48 umol O2/kg)

The absolute value of the peak shift relative to the average pH

# How does all this compare to [Pezner et al. 2023?](https://doi.org/10.1038/s41558-023-01619-2)

They observed a mean daily range of 81 umol O2/kg (2.65 mg/L), with a
minimum range of 23 umol O2/kg (0.75 mg/L) and a maximum range of 258
umol O2/kg (8.43 mg/L).

So Cheeca is certainly within the range of common DO ranges on reefs,
albeit on the lower side.

# What does all this mean for FRESCA Experiments?

Not too much. The DO data is too messy for my liking. I’d prefer to do a
similar analysis by grouping together multiple reef sites in Florida,
spanning reefs with various proximities to seagrass beds, coral cover,
residence times, etc before making a final recommendation. I’d have to
go looking for continuous datasets rather than discrete samples
clustered during the day.

If I had to pick a number, 1.5 mg/L diel variability could work. It’s
not far from the Wet season range seen at Cheeca and its within the
range season on reefs aross the world from the data collected by Ariel
Pezner. This could be implemented with a -0.5 mg/L at night and + 1 mg/L
during the day. Some treatment possibilities are shown below with a
fifth-order polynomial fit to the desired variability and defined
troughs and peaks.

Table 2. 2 Posible Diel DO Implementations
<table class=" lightable-material" style="font-family: &quot;Source Sans Pro&quot;, helvetica, sans-serif; margin-left: auto; margin-right: auto;">
<thead>
<tr>
<th style="text-align:left;">
scenario
</th>
<th style="text-align:right;">
average
</th>
<th style="text-align:right;">
peak
</th>
<th style="text-align:right;">
trough
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:left;">
peak = 8
</td>
<td style="text-align:right;">
7
</td>
<td style="text-align:right;">
8
</td>
<td style="text-align:right;">
6.5
</td>
</tr>
<tr>
<td style="text-align:left;">
average = 8
</td>
<td style="text-align:right;">
8
</td>
<td style="text-align:right;">
9
</td>
<td style="text-align:right;">
7.5
</td>
</tr>
</tbody>
</table>
<h5>
Figure 10. Experimental Diel Curve
</h5>

<img src="/notebook/images/cheecaDO/unnamed-chunk-9-1.png" width="90%" style="display: block; margin: auto;" />
