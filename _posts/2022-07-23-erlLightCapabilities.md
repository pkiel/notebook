---
layout: post
title:  "Incorporating Seasonality into ERL"
author: "Patrick M Kiel"
date: '2022-07-23'
categories: [research]
description: "NOAA AOML Coral Program uses Radion XR30 Pro in its Experimental Reef Laboratory. Here we discuss our capabilities to incorporate seasonal changes of light duration and spectra into our aquariums."
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

<style type="text/css">
img {
  margin: 0 auto;
}
</style>

# Overview

The
<a href="https://www.aoml.noaa.gov/experimental-reef-lab/" target="_blank">Experimental
Reef Lab at the University of Miami</a> uses
<a href="https://ecotechmarine.com/radion" target="_blank">Ecotech
Marine’s Radion XR30 Pro</a> lights to illuminate our corals. Here I
will outline our capabilities to mimic natural light regimes in our
aquaria including seasonal variation and moonlight.

# Light Performance

The standard setup we have places the light 50cm above the bottom of the
aquarium. This results in the following light curve based on full
spectrum set to 100% and the point intensity varying from 0-100%. As
Morgan has shown, we can lower the light closer to the water to reach
PAR levels exceeding 800.

<img src="/notebook/images/ERLLights/unnamed-chunk-2-1..png" width="80%" />
- Note - All values were converted to our lab standard by dividing
Apogee readings by 1.2 to be equal to values we see from Seabird EcoPAR.

![Mobius Day Light Settings](/notebook/images/ERLLights/mobiusDay.png)

I collected light spectra for each setting in the Mobius app. I also
captured a spectrum with the light off to create an ambient spectrum
that I will subtract from all other spectrums. Below is an example of
the subtraction.

<img src="/notebook/images/ERLLights/spectra diff example-1..png" width="80%" /><img src="/notebook/images/ERLLights/spectra diff example-2..png" width="80%" />

## Light Spectra

<img src="/notebook/images/ERLLights/day spectra-1..png" width="80%" />

<img src="/notebook/images/ERLLights/day spectra-2..png" width="80%" />

<img src="/notebook/images/ERLLights/day spectra-3..png" width="80%" />

<img src="/notebook/images/ERLLights/day spectra-4..png" width="80%" />

<img src="/notebook/images/ERLLights/day spectra-5..png" width="80%" />

<img src="/notebook/images/ERLLights/day spectra-6..png" width="80%" />

<img src="/notebook/images/ERLLights/day spectra-7..png" width="80%" />

<img src="/notebook/images/ERLLights/day spectra-8..png" width="80%" />

<img src="/notebook/images/ERLLights/day spectra-9..png" width="80%" />

## Moonlight

Through the Mobius app, we can adjust 4 parameters to mimic moonlight:
intensity, color channel balance (Moonlight/Moonlight Blue), set times,
and lunar cycle. At maximum intensity, the light is only outputting 2
PAR. Below are 3 spectra of the lights set at 100% Moonlight, 100%
Moonlight Blue, and 50% for each Moonlight and Moonlight Blue.

<img src="/notebook/images/ERLLights/moon-1..png" width="80%" />

<img src="/notebook/images/ERLLights/moon-2..png" width="80%" />

<img src="/notebook/images/ERLLights/moon-3..png" width="80%" />

We can also enable lunar cycle which creates a 28 day cycle with each
day resulting in a scaled brightness. For instance, if the full moon is
day 0 and point brightness is set to 100%, then on day 0 the brightness
will be 100%. On day 7 (last quarter) the brightness would be 50%. On
day 14 (new moon), the light will not come on at all. This cycles
through and scales to whatever one sets as the full moon settings. If
lunar cycle is disabled, then the full settings will be applied each
day.

![Mobius Moon Light Settings](/notebook/images/ERLLights/mobiusMoon.png)

## Seasonal

To mimic seasonal changes in the light regime, Mobius has a tool called
<a href="/notebook/images/ERLLights/InsolationExplainer.pdf" target="blank">Insolation</a>
which permits dynamic daily adjustments of the light schedule. One
imports a table that specifies the sunrise, sunset, sun intensity,
moonrise, moonset, and moon intensity. This tool allows users to upload
a csv of setpoints for an entire year.

This table will work together with the setpoints one sets to create a
unique light curve for each day. You set the shape of the curve which is
proportionally changed by the specific times set in the Insolation
table.

Insolation is a beta feature and needs further testing. I’ve started a
line of communication with the EcoTech Marine team to get this tool
working for us, and I will keep you updated on that progress. If this
tool works as advertised, it will permit experimentation on light
seasonality.

## Day Curves

Finally, we can change how the light changes throughout the day.
Currently we have been using 4 set points to create a rhombus shaped
curve with a 3 hour linear ramp of sunrise and sunset and a linear hold
at maximum PAR for 6 hours. In the user template window, there is a tool
to help create setpoints to mimic a sine or parabolic curve. This
effectively creates a handful of linear setpoints giving a best fit to
the aforementioned curves.

# Data to Inform Settings

Since most of the corals we analyze in the lab come from coral nurseries
or reefs around Miami, I will use this data to inform the set points we
choose.

## Light Set Points

Light data comes from NOAA’s Global Monitoring Laboratory set at the
coordinates for the Key Biscayne UM Nursery (25.676,-80.110).

<img src="/notebook/images/ERLLights/solar time from NOAA-1..png" width="80%" />

<img src="/notebook/images/ERLLights/solar time from NOAA-2..png" width="80%" />

<img src="/notebook/images/ERLLights/solar time from NOAA-3..png" width="80%" />
<img src="/notebook/images/ERLLights/solar time from NOAA-4..png" width="80%" />

From this data, we can extract daily setpoints to upload to the
Insolation table. We are unable to control solar noon with the current
Insolation tool. However, this has a narrow range and is arguably less
important than other setpoints.

## Nursery PAR Data

<img src="/notebook/images/ERLLights/nursery PAR-1..png" width="80%" /><img src="/notebook/images/ERLLights/nursery PAR-2..png" width="80%" />

PAR data collected by Morgan Chakraborty and Nathan Formel

It most approximates a sine wave with a peak at solar noon.

## Natural Spectrums

We have not yet collected natural light spectrums. Here is some
published spectra:

![Light spectrum from Slagel et al. 2021,
<doi:10.1002/zoo.21589>](/notebook/images/ERLLights/slagelSpectrum.jpg)

# Relevant Publications

1.  <a href="https://doi.org/10.1002/zoo.21589" target="_blank">Slagel
    et al.</a> Compared growth of *Acropora cervicornis* at FLAQ grown
    under LED v natural sunlight. LED corals had greater G than natural
    light corals, but TLE did not differ. However, photosynthetic
    efficiency was greater in natural light corals.

2.  <a href="https://doi.org/10.1371/journal.pone.0092781" target="_blank">Wijgerde
    et al.</a> Observed greater survivorship under blue light, no real
    observable differences in symbiont health/density. No replication of
    treatments across multiple papers by the same authors.
    Intro/discussion well cited for further investigations

3.  Martinez-Rugerio et al. *ICRS Talk* Experimentally demonstrated
    dissepiments are formed by a moon cue. Observed no differences in G
    between simulated moon and no moon treatment groups, but observed
    reduced extension and greater skeletal bulk density. There’s a
    DeCarlo and Cohen paper in Coral Reefs which looked at dissepiments
    under ct scan in field corals and observed a lunar cue too.
