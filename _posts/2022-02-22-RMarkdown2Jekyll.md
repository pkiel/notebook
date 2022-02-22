---
layout: post
title:  "Publishing RMarkdown Reports with Jekyll"
author: "Patrick Kiel"
date: "2022-02-22"
categories: [methods]
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

Two major goals of this Open Notebook are to have my analyses publicly
available for peer review and to share my reports with collaborators. I
primarily use R and find RMarkdown an effective way to create
reproducible code. However, sharing HTML files or PDF files back and
forth over email is cumbersome, and prevents the use of dynamic applets.
Toward this end, I have developed a reusable RMarkdown template that
generates a Github Flavored markdown file which is converted to a Jekyll
static page on my Open Notebook website.

I can some create some code and it is viewable by others to see what I
am doing.

``` r
mtcars %>%
  group_by(cyl) %>%
  summarise(count = n(),
            averageMPG = mean(mpg, na.rm = T),
            sdMPG = sd(mpg, na.rm = T)) %>%
  kbl() %>%
  kable_material()
```

<table class=" lightable-material" style="font-family: &quot;Source Sans Pro&quot;, helvetica, sans-serif; margin-left: auto; margin-right: auto;">
<thead>
<tr>
<th style="text-align:right;">
cyl
</th>
<th style="text-align:right;">
count
</th>
<th style="text-align:right;">
averageMPG
</th>
<th style="text-align:right;">
sdMPG
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:right;">
4
</td>
<td style="text-align:right;">
11
</td>
<td style="text-align:right;">
26.66364
</td>
<td style="text-align:right;">
4.509828
</td>
</tr>
<tr>
<td style="text-align:right;">
6
</td>
<td style="text-align:right;">
7
</td>
<td style="text-align:right;">
19.74286
</td>
<td style="text-align:right;">
1.453567
</td>
</tr>
<tr>
<td style="text-align:right;">
8
</td>
<td style="text-align:right;">
14
</td>
<td style="text-align:right;">
15.10000
</td>
<td style="text-align:right;">
2.560048
</td>
</tr>
</tbody>
</table>

I can also code some output and you can see the code and figure.

``` r
mtcars %>%
  ggplot(aes(factor(cyl), mpg)) +
  geom_boxplot() +
  theme_classic()
```

![](/notebook/images/boxplotExample-1.png)<!-- -->

Finally, I can just output a figure without underlying code.
![](/notebook/images/lmExample-1.png)<!-- -->
