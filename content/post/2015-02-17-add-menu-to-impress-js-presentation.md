---
title: Add Menu to Impress.js presentation
author: ヤング marduc
type: post
date: 2015-02-17T19:32:54+00:00
url: /2015/02/17/add-menu-to-impress-js-presentation/
featured_image: /wp-content/uploads/2015/02/impress.js.jpg
background_selector_orientation:
  - full_width_layout
body_color_rgba:
  - 1
body_source:
  - no-image
body_parallax:
  - 'false'
page_color_rgba:
  - 1
page_source:
  - no-image
page_parallax:
  - 'false'
header_color_rgba:
  - 1
header_source:
  - no-image
header_parallax:
  - 'false'
banner_color_rgba:
  - 1
banner_source:
  - no-image
banner_parallax:
  - 'false'
footer_color_rgba:
  - 1
footer_source:
  - no-image
footer_parallax:
  - 'false'
enable_noti_bar:
  - -1
mashsb_shares:
  - 100,170,276,329,486,583,635,736,875,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
mashsb_timestamp:
  - 1583402542
dsq_thread_id:
  - 3524355913
avada_post_views_count:
  - 215
mashsb_jsonshares:
  - '{"facebook_total":0,"facebook_likes":0,"facebook_comments":0}'
categories:
  - Tuts
tags:
  - css
  - impress.js
  - menu

---
I recently made a small presentation, using Impress.js which is a great tool.You can make presentations using HTML and Javascript. You can customise the result with your own CSS and you can take some great ideas from a list  of <a href="https://github.com/bartaz/impress.js/wiki/Examples-and-demos" target="_blank">impress.js presentations</a>.

<!--more-->

When I completed my presentation, I wanted to make a menu, so I could add some links or some more infos about the presentation.  So I created a menu with a custom style.

<pre class="brush: xml; title: ; notranslate" title="">&lt;ul class="menu_button"&gt;
	&lt;li&gt;&lt;a href="link"&gt;&lt;img src="home.png"&gt;&lt;/a&gt;&lt;/li&gt;
  	&lt;li&gt;&lt;a href="link"&gt;&lt;img src="ergasia.png"&gt;&lt;/a&gt;&lt;/li&gt;
  	&lt;li&gt;&lt;a href="link"&gt;&lt;img src="git.png"&gt;&lt;/a&gt;&lt;/li&gt;
&lt;/ul&gt;
</pre>

But when you click an icon, nothing happens. The way you can make it work is just by adding the following line at your css for the class of the menu. In my case it&#8217;s menu_button.

<pre class="brush: css; title: ; notranslate" title="">pointer-events: auto;
</pre>

This will make your menu clickable and you will make it work perfectly!

If you want more infos you can take a look at my <a href="http://localhost/thesis" target="_blank">presentation</a> or at the <a href="https://github.com/marduc812/Thesis_pres" target="_blank">source</a>.(it&#8217;s at Greek)  
asd