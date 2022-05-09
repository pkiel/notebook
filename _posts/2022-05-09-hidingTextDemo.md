---
layout: post
title:  "Password Protected Posts"
author: "Patrick M Kiel"
date: '2022-05-09'
categories: [methods]
description: "Follow this guide to build password protected posts for GitHub Pages hosted Jekyll blogs using this simple Javascript code."
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

# Overview

I mainly use this blog to share data analysis with my collaborators.
Since we are working with unpublished datasets that are still being
analyzed, I do not want this data to be visible to everyone who visits
my notebook.

For this reason, I have adapted the following code to work with my
Jekyll pages and RMarkdown workflow. To understand this workflow better,
[please visit this
post.](https://patrickmkiel.com/notebook/methods/RMarkdown2Jekyll/)

First, create a new Javascript chunk and create the password
verification script.

``` js
function verify() {
  if (document.getElementById('password').value === 'password') {
    document.getElementById('HIDDENDIV').classList.remove("hidden"); 
    document.getElementById('credentials').classList.add("hidden"); // Hide the div containing the credentials
  } else {
    alert('Invalid Password! You cannot view this content.');
    password.setSelectionRange(0, password.value.length);
  }
  return false;
}
```

Then, create a css chunk and create the hidden class.

``` css
/*Change content Display */
.hidden {
  display: none;
}
```

Next up, create the “credentials” div which will hold the password box
and the input. I also have an alert box pop up if the password is wrong.
You can get as fancy as you want here with css.

``` html
<!-- The password box -->
<div id="credentials">
  <input type="text" id="password" onkeydown="if (event.keyCode == 13) verify()" />
  <br/>
  <input id="button" type="button" value="Show Content" onclick="verify()" />
</div>
```

Finally create a new div which will hold all of your hidden content
which will display once the password is correct. It is important to
include the markdown=“1” argument so that Jekyll knows all code within
this html div tag needs to be executed. Otherwise verbatim code will be
displayed.

``` html
<div id="HIDDENDIV" class="hidden" markdown="1">

  # Place all r chunks, text, etc. in between these div tags

</div>
```

And that’s it! It certainly is not secure. One can go onto your GitHub
account and look at the raw code and the underlying data if you have it
hosted. But for most cases, this hidden content trick with simple
Javascript is quite effective.

# Example

<script type="text/javascript">
function verify() {
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

![](/notebook/images/tesing-1.png)<!-- -->

</div>
