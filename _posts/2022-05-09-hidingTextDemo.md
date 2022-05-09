---
layout: post
title:  "Testing Javascript Passwords"
author: "Patrick M Kiel"
date: '2022-05-09'
categories: [methods]
description: "Here I am testing Javascript enabled passwords of content on my blog"
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
function verify() {
  if (document.getElementById('password').value === 'password') {
    document.getElementById('HIDDENDIV').classList.remove("hidden"); 
    document.getElementById('credentials').classList.add("hidden"); // Hide the div containing the credentials
  } else {
    alert('Invalid Password!');
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
<!-- <div id="credentials"> -->
<!--   <input type="text" id="password" onkeydown="if (event.keyCode == 13) verify()" /> -->
<!--   <br/> -->
<!--   <input id="button" type="button" value="Show Content" onclick="verify()" /> -->
<!-- </div> -->
<!-- The content we want to show after password -->
<!-- <div id="HIDDENDIV" class="hidden"> -->

![](/notebook/images/tesing-1.png)<!-- -->

<!-- </div> -->
