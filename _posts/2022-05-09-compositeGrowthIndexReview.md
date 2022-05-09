---
layout: post
title: "*Acropora cervicornis* Composite Growth Index"
author: "Patrick Kiel"
date: '2022-05-09'
categories: [methods]
description: "Growth of the staghorn coral is measured in many different ways. Here I propose a composite indexing methodology to align disparate measurements to deduce genotype-specific influences on growth."
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
caption {
      color: black;
      font-weight: bold;
      font-size: 1.2em;
}

.tocify-extend-page {
  height: 0 !important;
}
</style>
<script type="text/javascript">
function verify() {
  if (document.getElementById('password').value === 'acropora') {
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

<iframe src="/notebook/images/compositeGrowth/genotypeTraitOverview.html" height="100vh" width="100%" style="border:none;">
</iframe>

</div>
