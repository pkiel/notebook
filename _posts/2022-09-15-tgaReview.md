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
sample degrades. By looking at the percent of decomposition over
discrete regions, we can characterize the coral sample’s fractional
constituents. The heating occurs in an inert environment (N<sub>2</sub>
gas) to avoid sample oxidation.

\[1\] "
<h5>
Figure 1. Example TGA and DTG Curve
</h5>

" ![](/notebook/images/example-TGA-1.png)<!-- -->

In this document, I review the current coral TGA literature, describe
the samples I have tested thus far and the proposed analysis
methodology, and begin to analyze my inital results.

# Literature Review

# Samples

# Proposed Analysis

# Initial Results

</div>
