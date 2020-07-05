---
title: Featured image at RSS using Mailchimp
author: ヤング marduc
type: post
date: 2015-03-15T14:32:47+00:00
url: /2015/03/15/featured-image-at-rss-using-mailchimp/
featured_image: /wp-content/uploads/2015/03/rsstomailchimp.jpg
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
  - 100,170,276,329,486,583,635,736,875,0,0,0,0,0,0,0
mashsb_timestamp:
  - 1523116037
dsq_thread_id:
  - 3597196176
avada_post_views_count:
  - 107
mashsb_jsonshares:
  - '{"facebook_total":0,"facebook_likes":0,"facebook_comments":0}'
categories:
  - Tuts
  - wordpress
tags:
  - featured image
  - mailchimp
  - rss
  - wordpress

---
I decided that it was time to change that mail Jetpack was sending and make something more beautiful and with better control. So I tried to use MailChimp, a great mail service that you can modify your mail style and you can have some extra features like detect when users open the link and more. <!--more-->

I registered an account but I couldn&#8217;t add a featured image because there was no featured image at my RSS. I searched for a lot of different things to do to add this feature but I always ended on having an empty feed page. I have no idea about php so i couldn&#8217;t that simply figure out what&#8217;s wrong.

What I did was install this great plug-in about featured images named **Featured Images in RSS w/ Size and Position** and saved my life.

Everything was working GREAT and my RSS had this great part of the featured image. You can select if you want your featured image to be thumbnail, medium and large ( I picked medium).

What you have to do then is to enter a link at your MailChimp designer and enter as link the following text **\*|RSSITEM:IMAGE|\*** and this will display your featured image at mail. This is the style that I used.

&nbsp;

[<img class="alignnone wp-image-351 size-medium" src="http://localhost/wp-content/uploads/2015/03/Screen-Shot-2015-03-15-at-3.55.52-PM-300x300.png" alt="Screen Shot 2015-03-15 at 3.55.52 PM" width="300" height="300" srcset="http://localhost/wp-content/uploads/2015/03/Screen-Shot-2015-03-15-at-3.55.52-PM-300x300.png 300w, http://localhost/wp-content/uploads/2015/03/Screen-Shot-2015-03-15-at-3.55.52-PM-150x150.png 150w, http://localhost/wp-content/uploads/2015/03/Screen-Shot-2015-03-15-at-3.55.52-PM-1024x1024.png 1024w" sizes="(max-width: 300px) 100vw, 300px" />][1]

<a href="https://wordpress.org/plugins/featured-images-for-rss-feeds/installation/" target="_blank">Plugin</a>

You can register out mailing list for more great articles.  
<!-- Begin MailChimp Signup Form -->

<div id="mc_embed_signup">
</div>

  
<!--End mc_embed_signup-->

 [1]: http://localhost/wp-content/uploads/2015/03/Screen-Shot-2015-03-15-at-3.55.52-PM.png