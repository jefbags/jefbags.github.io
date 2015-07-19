---
layout: post
category: AR
title: 2nd Test Post
tagline: by Jeff Baglioni
tags: 
  - android
  - c++
  - DD-WRT
published: true
---

This is the 2nd test post.


![test3]({{ site.baseurl }}/images/jekyll-logo.png)



| `Tables`      | `Are`         | `Cool`  |
| ------------- |:-------------:| -----:|
| col 3 isssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssss      | right-aligned | $1600 |
| col 2 is      | centered      |   $12 |
| zebra stripes | are neat      |    $1 |




Markdown | Less | Pretty
--- | --- | ---
*Still* | `renders` | **nicely**
1 | 2 | 3

s

use Text::MultiMarkdown 'markdown';

my $text = <<EOL;
css: table.css

|             |          Grouping           ||
First Header  | Second Header | Third Header |
 ------------ | :-----------: | -----------: |
Content       |          *Long Cell*        ||
Content       |   **Cell**    |         Cell |

New section   |     More      |         Data |
And more      |            And more          |
[Prototype table]
EOL

my $html = markdown( $text, {document_format => 'Complete'} );

