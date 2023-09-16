---
layout: post
title:  "Organizing Spec Hypoxia Data"
author: "Patrick M Kiel"
date: "2023-09-06"
categories: [methods, sws]
description: "Automated pipeline to organize microwell plate maps and the spectrophotometric readings to calculate enzyme specific activities."
output:
  md_document:
    variant: gfm
    preserve_yaml: TRUE
knit: (function(inputFile, encoding) {
  rmarkdown::render(inputFile, 
  encoding = encoding, 
  output_file = paste0("2023-09-06", "-",
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
  if (document.getElementById('password').value === 'password') {
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
<!-- The content we want to show after password -->

<div markdown="1">

<!-- Place all chunks, text, etc here as you would a normal RMarkdown document -->

# Overview

Anaerobic respiration pathways are diverse and predate the evolution of
photosynthesis. With the predicted increase in hypoxia events on coral
reefs, it is imperative that scientists understand coral metabolism in
low-oxygen environments to better predict coral survival under future
climate change scenarios. There are four conserved pathways among
eukaryotas we will be investigating within our coral hypoxia experiment.
The four enzymes which oxidize NADH in anaerobic respiration include
lactate (LDH), octopine (ODH), alanopine (ADH), and strombine (SDH)
dehydrogenase activities. You can read more about these enzymes and
their roles in coral metabolism by reading, [Murphy and Richmond (2016)
doi:10.7717/peerj.1956](https://www.doi.org/10.7717/peerj.1956) and the
references within, or consult your Cellular and Molecular Biology
textbook.

The following sections detail how we quantitatively assess the
activities of these four enzymes within corals. Briefly, we sample
polyps from a coral, homogenize in a Tris buffer solution, add aliquot
to a 96-well plate with reagents, and measure the absorbance over time
to calculate enzyme NADH reduction activity. We will also measure total
protein concentrations to standardize enzyme activity rates.

# Load plate_map

A 96-well plate helps us efficiently analyze multiple samples and
replicates of each sample. Because there are a lot of samples, however,
it is easy to mixup which well corresponds to which coral. To solve this
problem, we will use a plate map.

Table 1. Example of a 96-well plate map
<table>
<thead>
<tr>
<th style="text-align:left;">
row
</th>
<th style="text-align:left;">
X1
</th>
<th style="text-align:left;">
X2
</th>
<th style="text-align:left;">
X3
</th>
<th style="text-align:left;">
X4
</th>
<th style="text-align:left;">
X5
</th>
<th style="text-align:left;">
X6
</th>
<th style="text-align:left;">
X7
</th>
<th style="text-align:left;">
X8
</th>
<th style="text-align:left;">
X9
</th>
<th style="text-align:left;">
X10
</th>
<th style="text-align:left;">
X11
</th>
<th style="text-align:left;">
X12
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:left;">
A
</td>
<td style="text-align:left;">
Sample1
</td>
<td style="text-align:left;">
Sample1
</td>
<td style="text-align:left;">
Sample1
</td>
<td style="text-align:left;">
Sample2
</td>
<td style="text-align:left;">
Sample2
</td>
<td style="text-align:left;">
Sample2
</td>
<td style="text-align:left;">
Sample3
</td>
<td style="text-align:left;">
Sample3
</td>
<td style="text-align:left;">
Sample3
</td>
<td style="text-align:left;">
Sample4
</td>
<td style="text-align:left;">
Sample4
</td>
<td style="text-align:left;">
Sample4
</td>
</tr>
<tr>
<td style="text-align:left;">
B
</td>
<td style="text-align:left;">
Sample5
</td>
<td style="text-align:left;">
…
</td>
<td style="text-align:left;">
…
</td>
<td style="text-align:left;">
…
</td>
<td style="text-align:left;">
…
</td>
<td style="text-align:left;">
…
</td>
<td style="text-align:left;">
…
</td>
<td style="text-align:left;">
…
</td>
<td style="text-align:left;">
…
</td>
<td style="text-align:left;">
…
</td>
<td style="text-align:left;">
…
</td>
<td style="text-align:left;">
…
</td>
</tr>
<tr>
<td style="text-align:left;">
C
</td>
<td style="text-align:left;">
…
</td>
<td style="text-align:left;">
…
</td>
<td style="text-align:left;">
…
</td>
<td style="text-align:left;">
…
</td>
<td style="text-align:left;">
…
</td>
<td style="text-align:left;">
…
</td>
<td style="text-align:left;">
…
</td>
<td style="text-align:left;">
…
</td>
<td style="text-align:left;">
…
</td>
<td style="text-align:left;">
…
</td>
<td style="text-align:left;">
…
</td>
<td style="text-align:left;">
…
</td>
</tr>
<tr>
<td style="text-align:left;">
D
</td>
<td style="text-align:left;">
…
</td>
<td style="text-align:left;">
…
</td>
<td style="text-align:left;">
…
</td>
<td style="text-align:left;">
…
</td>
<td style="text-align:left;">
…
</td>
<td style="text-align:left;">
…
</td>
<td style="text-align:left;">
…
</td>
<td style="text-align:left;">
…
</td>
<td style="text-align:left;">
…
</td>
<td style="text-align:left;">
…
</td>
<td style="text-align:left;">
…
</td>
<td style="text-align:left;">
…
</td>
</tr>
<tr>
<td style="text-align:left;">
E
</td>
<td style="text-align:left;">
…
</td>
<td style="text-align:left;">
…
</td>
<td style="text-align:left;">
…
</td>
<td style="text-align:left;">
…
</td>
<td style="text-align:left;">
…
</td>
<td style="text-align:left;">
…
</td>
<td style="text-align:left;">
…
</td>
<td style="text-align:left;">
…
</td>
<td style="text-align:left;">
…
</td>
<td style="text-align:left;">
…
</td>
<td style="text-align:left;">
…
</td>
<td style="text-align:left;">
…
</td>
</tr>
<tr>
<td style="text-align:left;">
F
</td>
<td style="text-align:left;">
…
</td>
<td style="text-align:left;">
…
</td>
<td style="text-align:left;">
…
</td>
<td style="text-align:left;">
…
</td>
<td style="text-align:left;">
…
</td>
<td style="text-align:left;">
…
</td>
<td style="text-align:left;">
…
</td>
<td style="text-align:left;">
…
</td>
<td style="text-align:left;">
…
</td>
<td style="text-align:left;">
…
</td>
<td style="text-align:left;">
…
</td>
<td style="text-align:left;">
…
</td>
</tr>
<tr>
<td style="text-align:left;">
G
</td>
<td style="text-align:left;">
…
</td>
<td style="text-align:left;">
…
</td>
<td style="text-align:left;">
…
</td>
<td style="text-align:left;">
…
</td>
<td style="text-align:left;">
…
</td>
<td style="text-align:left;">
…
</td>
<td style="text-align:left;">
…
</td>
<td style="text-align:left;">
…
</td>
<td style="text-align:left;">
…
</td>
<td style="text-align:left;">
…
</td>
<td style="text-align:left;">
…
</td>
<td style="text-align:left;">
…
</td>
</tr>
<tr>
<td style="text-align:left;">
H
</td>
<td style="text-align:left;">
…
</td>
<td style="text-align:left;">
…
</td>
<td style="text-align:left;">
…
</td>
<td style="text-align:left;">
…
</td>
<td style="text-align:left;">
…
</td>
<td style="text-align:left;">
…
</td>
<td style="text-align:left;">
…
</td>
<td style="text-align:left;">
…
</td>
<td style="text-align:left;">
…
</td>
<td style="text-align:left;">
…
</td>
<td style="text-align:left;">
…
</td>
<td style="text-align:left;">
…
</td>
</tr>
</tbody>
</table>

It is important to follow the plate map carefully to keep track of
samples and to later analyze the data with a script to automatically
process the samples. [You can find a copy of the plate map
here.](https://patrickmkiel.com/notebook/images/hypoxiaEnzymeAssay/specPlateMap.xlsx)

For this format, keep in mind the following:

- The date shouldbe in the first coloumn in mm/dd/YYYY format, directly
  above the plates
- In column N, list all plate names that match the map; one plate name
  per row
- Leave at least one blank row between distinct plate maps
- You can have multiple plates for one date and you can have multiple
  dates per excel file.

## Plate Map Processing Code

``` r
# make sure the plate maps are in a folder all by themselves
map_files <- list.files("~/Grad School/TA/SWS-F23/data/templates/plateMaps/", full.names = T)

# function to process 1 or more plate map files
plate_map <- lapply(map_files, function(x) {
  read_excel(x,
                  col_names = c("row", 1:12, "plate_name")) %>%
# add the date as a column to each plate
  mutate(date = as.Date(as.numeric(row),
                        origin="1899-12-30"),
         .before = "row") %>%
    fill(date, .direction = "down")}) %>% bind_rows()

# grab the plate names
plate_names <- plate_map %>%
  select(date, plate_name) %>%
  drop_na() %>%
  # remove rows that have comments, delineated by an * in the plate name col
  filter(!str_detect(plate_name, '^\\*')) %>%
  mutate(plate_name = str_replace(plate_name,
                                     '(plate)|(PLATE)',
                                     ' '),
         # strip white space from names
         plate_name =str_replace_all(plate_name,
                                     "(\\S)\\s{2,}(?=\\S)", "\\1 "),
         # grab the plate type
         type = str_trim(str_extract(plate_name, "^.*(?=[[:digit:]])")))

plate_map <- plate_map %>%
  # remove the date row numeric
  filter(str_detect(row, "^[:alpha:]+$")) %>%
  # remove rows that correspond to an empty row on the plate
  filter(if_any(as.character(1:12),
                ~ !is.na(.))) %>%
  select(-plate_name) %>%
  #cast into long format
  pivot_longer(cols=as.character(1:12),
               names_to = "plate_map",
               values_to= "sample",
               values_drop_na = T) %>%
  mutate(plate_map = paste0(row,plate_map)) %>%
  select(-row)


#add plate num based on repeat value within a given date
plate_map <- plate_map %>%
  group_by(date, plate_map) %>%
  mutate(plate_num = row_number()) %>%
  ungroup() %>% 
  left_join(plate_names %>%
              mutate(plate_num = as.integer(str_extract(plate_name,
                                                        "(\\d)+")))) %>%
  select(-plate_num)
```

Table 2. Processed plate map
<table>
<thead>
<tr>
<th style="text-align:left;">
date
</th>
<th style="text-align:left;">
plate_map
</th>
<th style="text-align:left;">
sample
</th>
<th style="text-align:left;">
plate_name
</th>
<th style="text-align:left;">
type
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:left;">
2023-08-25
</td>
<td style="text-align:left;">
A1
</td>
<td style="text-align:left;">
A1
</td>
<td style="text-align:left;">
TAC 1
</td>
<td style="text-align:left;">
TAC
</td>
</tr>
<tr>
<td style="text-align:left;">
2023-08-25
</td>
<td style="text-align:left;">
A1
</td>
<td style="text-align:left;">
A1
</td>
<td style="text-align:left;">
PROTEIN 1
</td>
<td style="text-align:left;">
PROTEIN
</td>
</tr>
<tr>
<td style="text-align:left;">
2023-08-25
</td>
<td style="text-align:left;">
A2
</td>
<td style="text-align:left;">
A1
</td>
<td style="text-align:left;">
TAC 1
</td>
<td style="text-align:left;">
TAC
</td>
</tr>
<tr>
<td style="text-align:left;">
2023-08-25
</td>
<td style="text-align:left;">
A2
</td>
<td style="text-align:left;">
A1
</td>
<td style="text-align:left;">
PROTEIN 1
</td>
<td style="text-align:left;">
PROTEIN
</td>
</tr>
<tr>
<td style="text-align:left;">
2023-08-25
</td>
<td style="text-align:left;">
A3
</td>
<td style="text-align:left;">
A1
</td>
<td style="text-align:left;">
TAC 1
</td>
<td style="text-align:left;">
TAC
</td>
</tr>
</tbody>
</table>

# Load spectrophotometric data

The plate is then read on the plate spectrophotometer. Follow the
protocols for incubation temperature, shake settings, read wavelength,
and time. Ensure the naming scheme from the plate map is reproduced in
the spectrophotometer computer so the saved file has identical names.

Common naming schemes include, “LDH 1 T18” for LDH plate 1 measured at
the 18th minute, or “protein 2” for protein plate 2, or “TAC 1 initial”
for the initial reading of TAC plate 1.

## Spectrophotometric Data Processing Code

``` r
# make sure the spec files are in a folder all by themselves
spec_files <- list.files("~/Grad School/TA/SWS-F23/data/templates/spec/", full.names = T)

spec_dat <- lapply(spec_files, function(x) {
  read.csv(file(x,
              encoding="UCS-2LE"),
         sep = "\t", header = F,skip = 1)[,1:14] %>%
  set_names(c("date","plate_name", 1:12)) %>%
  mutate(across(3:14, ~ as.numeric(.x))) %>%
  mutate(date = as.Date(str_extract(last(date), 
                            "[[:digit:]]{1,2}\\/[[:digit:]]{1,2}\\/[[:digit:]]{4}"),
                        "%m/%d/%Y")) %>%
  #remove the unimportant rows
  filter(plate_name != 'Temperature(¡C)' | is.na(plate_name)) %>%
  #grab the correct plate name for each row
  mutate(plate_name = case_when(is.na(as.numeric(plate_name)) ~ plate_name,
                                TRUE ~ NA),
         # pull out the time point in its own col
         time = toupper(str_extract(plate_name, "(?<=[[:digit:]] ).*$")),
         # remove time point from plate name
         plate_name = str_trim(str_extract(plate_name, "^.* [[:digit:]]*(?=.*)"))) %>%
  fill(c(plate_name,time)) %>%
  #remove empty plate rows
  filter(if_any(as.character(1:12), ~ !is.na(.))) %>%
  group_by(plate_name, time) %>%
  #remove the metadata for the plate
  filter(row_number()!=1) %>%
  #append the row letter scheme
  mutate(row = case_when(row_number() == 1 ~ "A",
                         row_number() == 2 ~ "B",
                         row_number() == 3 ~ "C",
                         row_number() == 4 ~ "D",
                         row_number() == 5 ~ "E",
                         row_number() == 6 ~ "F",
                         row_number() == 7 ~ "G",
                         row_number() == 8 ~ "H",
                         TRUE ~ NA),
         .after="plate_name") %>%
  ungroup() %>%
  #build plate map from row and col
  pivot_longer(as.character(1:12),
               names_to = 'plate_map',
               values_to = 'Abs') %>%
  mutate(plate_map = paste0(row,plate_map)) %>%
  select(-row)
}) %>% bind_rows()
```

Table 3. Organized spectrophotometer data
<table>
<thead>
<tr>
<th style="text-align:left;">
date
</th>
<th style="text-align:left;">
plate_name
</th>
<th style="text-align:left;">
time
</th>
<th style="text-align:left;">
plate_map
</th>
<th style="text-align:right;">
Abs
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:left;">
2023-08-31
</td>
<td style="text-align:left;">
LDH 1
</td>
<td style="text-align:left;">
T0
</td>
<td style="text-align:left;">
A1
</td>
<td style="text-align:right;">
0.0771
</td>
</tr>
<tr>
<td style="text-align:left;">
2023-08-31
</td>
<td style="text-align:left;">
LDH 1
</td>
<td style="text-align:left;">
T0
</td>
<td style="text-align:left;">
A2
</td>
<td style="text-align:right;">
0.0736
</td>
</tr>
<tr>
<td style="text-align:left;">
2023-08-31
</td>
<td style="text-align:left;">
LDH 1
</td>
<td style="text-align:left;">
T0
</td>
<td style="text-align:left;">
A3
</td>
<td style="text-align:right;">
0.0766
</td>
</tr>
<tr>
<td style="text-align:left;">
2023-08-31
</td>
<td style="text-align:left;">
LDH 1
</td>
<td style="text-align:left;">
T0
</td>
<td style="text-align:left;">
A4
</td>
<td style="text-align:right;">
0.0767
</td>
</tr>
<tr>
<td style="text-align:left;">
2023-08-31
</td>
<td style="text-align:left;">
LDH 1
</td>
<td style="text-align:left;">
T0
</td>
<td style="text-align:left;">
A5
</td>
<td style="text-align:right;">
0.0786
</td>
</tr>
</tbody>
</table>

# Process data

Now that you have your plate map and the raw spectrophotometric data
organized, it’s time to join these data together and then analyze them.

First, join the plates together by common plate map well identifiers,
plate name, and date the plate was analyzed. Then we will group together
our triplicate measurements and take the average reading to be our
accepted absorbance, which we will use for all future calculations.

``` r
dat <- spec_dat %>%
  #ignore the case sensitivity of the plate_name
  mutate(plate_name = toupper(plate_name)) %>%
  left_join(plate_map %>% mutate(plate_name = toupper(plate_name)),
            by = c("plate_map", "plate_name", "date")) %>%
  group_by(sample, type, time) %>%
  summarise(sd = sd(Abs, na.rm=T),
            range = abs(max(Abs)-min(Abs)),
            Abs = mean(Abs, na.rm=T))
```

Now we need to convert from our absorbance to our total protein or
\[NADH\] concentration. To do that, we will need to use our standard
curves.

<h5>
Figure 1. Example standard curve for total protein concentration
</h5>

<img src="/notebook/images/hypoxiaEnzymeAssay/standardCurves-1.png" width="90%" style="display: block; margin: auto;" />

## Processing Code

See if you can finish the code. You need to calculate total protein and
NADH enzyme activity rates for the 4 anaerobic enzymes. For the activity
rates, calculate a slope of decomposition over the 30 minutes and
standardize this slope to the total protein for that coral sample. Do
not forget to subtract out the average of the standard curve 0-points
from the total protein samples prior to converting to ug/mL. On average,
you need to subtract 0.11 Abs units.

## Getting Fancy with Error Propagation

There is uncertainty in everything we measure. Often, we want to
calculate this uncertainty and report with our final results. This can
get complicated since we have multiple sources of uncertainties and need
to figure out the best way to aggregate all sources of error including,
the slope of the standard curve and the standard error of the three
measurements we took. There may be other independent sources of error,
but we’ll just focus on these two for now as an example. A commonly used
technique to solve this problem is called Monte Carlo Error Propagation.
Although it has a fancy sounding name, it’s actually quite simple and
can be accomplished in only a few lines of code.

You can read more online about Monte Carlo Error Propagation, but the
basic set of assumptions is that the standard deviation we calculated
for our data closely approximates the population standard deviation of
the measurement, which would be calculated by taking an infinite number
of measurements of the sample. The population standard deviation,
therefore, can be estimated by taking randomly selected points, within a
normal or Gaussian distribution, and propagating our errors accordingly.

First, multiply the standard deviation you calculated by 1,000 randomly
distributed normal numbers using the rnorm function. Then add these
standard deviations to the value you calculated. Do this for each term
in the value you are calculating. Finally, take the mean of these 1,000
values and use as your accepted value, and then take the standard
deviation of these 1,000 numbers as the error propagated standard error.
It sounds confusing in words, but take a look at the code below and
think about what each of the terms are doing.

Where might this be useful? Well here, you translated the errors
associated with protein absorbances of an aliquot of coral tissue and
expanded them to estimate the uncertainities around how much protein is
in the coral you sampled. In the future, perhaps you create a complex
equation that models how sea level rise will change in the future. There
are uncertainties in the present sea level you measure, plus the thermal
expansion term, the projected heating rate, the effect of gravity, and
so on… The deeper you get into science, the more measurements you take
and the more uncertainties that exist.

``` r
#define the se of the m term from the standard curve
m_err <- 2.309e-05

mcExample <- mcExample %>%
  mutate(protein.normal = ((Abs-0.11)-0.0259)/0.0006,
         protein.mc = mean((((Abs-0.11)+rnorm(1000)*sd)-0.0259)/(0.0006+rnorm(1000)*m_err)),
         protein.mc_err = sd((((Abs-0.11)+rnorm(1000)*sd)-0.0259)/(0.0006+rnorm(1000)*m_err)))
```

Table 4. Example of error propagation
<table>
<thead>
<tr>
<th style="text-align:left;">
sample
</th>
<th style="text-align:left;">
type
</th>
<th style="text-align:right;">
Abs
</th>
<th style="text-align:right;">
sd
</th>
<th style="text-align:right;">
protein.normal
</th>
<th style="text-align:right;">
protein.mc
</th>
<th style="text-align:right;">
protein.mc_err
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:left;">
D1
</td>
<td style="text-align:left;">
PROTEIN
</td>
<td style="text-align:right;">
0.3718667
</td>
<td style="text-align:right;">
0.0055429
</td>
<td style="text-align:right;">
393.2778
</td>
<td style="text-align:right;">
394.3286
</td>
<td style="text-align:right;">
17.48872
</td>
</tr>
<tr>
<td style="text-align:left;">
D10
</td>
<td style="text-align:left;">
PROTEIN
</td>
<td style="text-align:right;">
0.5114333
</td>
<td style="text-align:right;">
0.0236673
</td>
<td style="text-align:right;">
625.8889
</td>
<td style="text-align:right;">
627.0772
</td>
<td style="text-align:right;">
46.22985
</td>
</tr>
<tr>
<td style="text-align:left;">
D11
</td>
<td style="text-align:left;">
PROTEIN
</td>
<td style="text-align:right;">
0.5755000
</td>
<td style="text-align:right;">
0.0165176
</td>
<td style="text-align:right;">
732.6667
</td>
<td style="text-align:right;">
733.9122
</td>
<td style="text-align:right;">
39.19644
</td>
</tr>
<tr>
<td style="text-align:left;">
D12
</td>
<td style="text-align:left;">
PROTEIN
</td>
<td style="text-align:right;">
0.4844667
</td>
<td style="text-align:right;">
0.0077106
</td>
<td style="text-align:right;">
580.9444
</td>
<td style="text-align:right;">
582.2824
</td>
<td style="text-align:right;">
25.69766
</td>
</tr>
<tr>
<td style="text-align:left;">
D2
</td>
<td style="text-align:left;">
PROTEIN
</td>
<td style="text-align:right;">
0.4010333
</td>
<td style="text-align:right;">
0.0071009
</td>
<td style="text-align:right;">
441.8889
</td>
<td style="text-align:right;">
442.7021
</td>
<td style="text-align:right;">
21.04786
</td>
</tr>
</tbody>
</table>

You can see there is only a slight difference in the accepted value
using the standard calculation or the Monte Carlo calculation. This is
due to the 1000 random points selected within a random distrubtion of
the associated error. Since these points are random, each time you rerun
the code (unless you set a seed), you will calculate a slightly
different value. These values, however, will be well within the
associated error calculated in the last coloumn.

</div>
