---
layout: post
title:  "Incorporating Seasonality into ERL"
author: "Patrick M Kiel"
date: '2022-07-25'
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
Marine’s Radion XR30 Pro</a> lights to illuminate our experimental
aquariums. Here I will outline our capabilities to mimic natural light
regimes in our aquaria including seasonal variation and moonlight.

We can incorporate seasonal changes of light exposure with daily changes
in exposure duration and intensity. Further, we can add simulated
moonlight into our system, fully equipped with changing moonrise and
moonset times and lunar phases.

# Light Performance

The standard setup we have places the light 50cm above the bottom of the
aquarium. This results in the following light curve based on full
spectrum set to 100% and the point intensity varying from 0-100%. As
Morgan has shown, we can lower the light closer to the water to reach
PAR levels exceeding 800 $\\mu mol \\space m^{-2} \\space s^{-1}$ .

![Mobius Day Light Settings set to 100%
intensity](/notebook/images/ERLLights/mobiusDay.png)

<img src="/notebook/images/ERLLights/unnamed-chunk-2-1..png" width="80%" />
- Note - All values were converted to our lab standard by dividing
Apogee readings by 1.2 to be equal to values we see from Seabird EcoPAR.

## Light Spectra

I collected a light spectrum for each setting in the Mobius app. I also
captured a spectrum with the light off to create an ambient spectrum
that I will subtract from all other spectra. Below is an example of the
subtraction.

<img src="/notebook/images/ERLLights/spectra diff example-1..png" width="80%" /><img src="/notebook/images/ERLLights/spectra diff example-2..png" width="80%" />

### Spectra

<img src="/notebook/images/ERLLights/day spectra-1..png" width="80%" />

<img src="/notebook/images/ERLLights/day spectra-2..png" width="80%" />

<img src="/notebook/images/ERLLights/day spectra-3..png" width="80%" />

<img src="/notebook/images/ERLLights/day spectra-4..png" width="80%" />

<img src="/notebook/images/ERLLights/day spectra-5..png" width="80%" />

<img src="/notebook/images/ERLLights/day spectra-6..png" width="80%" />

<img src="/notebook/images/ERLLights/day spectra-7..png" width="80%" />

<img src="/notebook/images/ERLLights/day spectra-8..png" width="80%" />

<img src="/notebook/images/ERLLights/day spectra-9..png" width="80%" />

We can leverage these spectra to create the simulated sunlight we
desire.

## Moonlight

Through the Mobius app, we can adjust 4 parameters to mimic moonlight:
intensity, color channel balance (Moonlight/Moonlight Blue), set times,
and lunar cycle. **At maximum intensity, the light is only outputting 2
PAR.** Below are 3 spectra of the lights set at 100% Moonlight, 100%
Moonlight Blue, and 50% for each Moonlight and Moonlight Blue.

![Mobius Moon Light Settings](/notebook/images/ERLLights/mobiusMoon.png)

<img src="/notebook/images/ERLLights/moon-1..png" width="80%" />

<img src="/notebook/images/ERLLights/moon-2..png" width="80%" />

<img src="/notebook/images/ERLLights/moon-3..png" width="80%" />

**We can also enable lunar cycle which creates a 28 day cycle with each
day resulting in a scaled brightness.** For instance, if the full moon
is day 0 and point brightness is set to 100%, then on day 0 the
brightness will be 100%. On day 7 (last quarter) the brightness would be
50%. On day 14 (new moon), the light will not come on at all. This
cycles through and scales to whatever one sets as the full moon
settings. If lunar cycle is disabled, then the full settings will be
applied each day.

## Seasonal

**To mimic seasonal changes in the light regime, Mobius has a tool
called
<a href="/notebook/images/ERLLights/InsolationExplainer.pdf" target="blank">Insolation</a>
which permits dynamic daily adjustments of the light schedule.** One
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
at maximum PAR for 6 hours. **In the user template window, there is a
tool to help create setpoints to mimic a sine or parabolic curve which
more closely follows natural lighting regimes.**

# Data to Inform Settings

Since most of the organisms we analyze in the lab come from reefs around
Miami, I will use this data to inform the set points we choose.

## Sun Rise and Set Times

Sunrise and sunset data comes from NOAA’s Global Monitoring Laboratory
set at the coordinates for the Key Biscayne UM Nursery (25.676,-80.110).

<img src="/notebook/images/ERLLights/solar time from NOAA-1..png" width="80%" />

<img src="/notebook/images/ERLLights/solar time from NOAA-2..png" width="80%" />

<img src="/notebook/images/ERLLights/solar time from NOAA-3..png" width="80%" />
<img src="/notebook/images/ERLLights/solar time from NOAA-4..png" width="80%" />

From this data, we can extract daily setpoints to upload to the
Insolation table. We are unable to control solar noon with the current
Insolation tool. However, this has a narrow range and is arguably less
critical than other setpoints.

## Moon Rise and Set Times

Moonrise and Moonset are defined as times when the moon passes through
the horizon
<a href="https://en.wikipedia.org/wiki/Moonrise_and_moonset#Time" target="_blank">which
changes with the phases.</a> Data was collected from the
<a href="https://aa.usno.navy.mil/data/api" target="_blank">US Naval
Observatory’s Astronomical Applications Department API</a>.

Since the light provided by the moon is better modeled as a percentage
of brightness supplied by the full moon (rise at sunset and set at
sunrise), the precise timing of the moonrise and moonset does not
matter. Rather, changing the brightness on a schedule that tracks the
lunar phases is prudent with 0% occuring at a New Moon and 100% at a
full moon. I just think this data is cool.

<img src="/notebook/images/ERLLights/moon time-1..png" width="80%" /><img src="/notebook/images/ERLLights/moon time-2..png" width="80%" />

## Solar Intensity

To investigate seasonal trends in light, I plan to use the PAR data
extracted from
<a href="https://oceancolor.gsfc.nasa.gov/l3/" target="_blank">NASA’s
MODIS Level-3 Data.</a> This data is supplied as mean daily exposure (
$mol \\space m^{-2} \\space day^{-1}$ ) and has a 4km resolution. I plan
to calculate a daily average value for the last 10 years and construct a
seasonal light exposure plot. Assuming that the attenuation of light in
a water column is constant throughout the year, then we can extract
seasonal light exposure curves to aid in our construction of modeled
light exposure for our experiments. The exact brightness, however, will
be informed by PAR data collected *in situ*.

I have not yet conducted this analysis.

## Nursery PAR Data

<img src="/notebook/images/ERLLights/nursery PAR-1..png" width="80%" /><img src="/notebook/images/ERLLights/nursery PAR-2..png" width="80%" />

PAR data collected by Morgan Chakraborty and Nathan Formel

It most approximates a sine wave with a peak at solar noon.

## NCEI Data

I found this dataset on NCEI for one of the C-MAN stations located at
Molasses Reef (25.012, -80.376). Need to look more into this PAR data
and compare to the MODIS derived data from above, but it provides a long
term seasonal trend with a maximum PAR in late June approximately equal
to the summer solstice.

<img src="/notebook/images/ERLLights/Molasses Data-1..png" width="80%" /><img src="/notebook/images/ERLLights/Molasses Data-2..png" width="80%" />

Don’t really trust the subsurface (1m) dataset. My guess is that it’s
right below the buoy and thus it is partly shaded by said buoy, and the
odd pattern may align with prevailing winds as that may move the buoy
around. Not sure if it’s a moored buoy. Shot in the dark though :)

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
