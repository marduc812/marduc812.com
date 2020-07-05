---
title: Android how to use Facebook, Twitter and Google plus Intents
author: ヤング marduc
type: post
date: 2015-03-10T10:59:05+00:00
url: /2015/03/10/android-how-to-use-facebook-twitter-and-google-plus-intents/
featured_image: /wp-content/uploads/2015/03/social.jpg
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
  - 100,170,276,329,486,583,635,736,875,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
mashsb_timestamp:
  - 1587923014
dsq_thread_id:
  - 3582970249
avada_post_views_count:
  - 283
mashsb_jsonshares:
  - '{"facebook_total":0,"facebook_likes":0,"facebook_comments":0}'
yuzo_related_post_metabox:
  - 'a:3:{s:17:"yuzo_include_post";s:0:"";s:17:"yuzo_exclude_post";s:0:"";s:21:"yuzo_disabled_related";s:1:"0";}'
categories:
  - Android
  - Tuts
tags:
  - Android
  - google

---
Social networks are part of our life for sure, some times facebook or twitter or any other social network. Using them at your apps will help you to promote your app and make the user part of your team. Let&#8217;s how this can be done in Android.

<!--more-->

<h2 style="color: #3b5998;">
  Facebook
</h2>

For the Facebook intent you have to check if the user has facebook app installed or you just  have to lunch browser at the page you want. I will use Google for everything as a example.

<pre class="brush: java; title: ; notranslate" title="">try {
 Intent intent = new Intent(Intent.ACTION_VIEW, Uri.parse("fb://page/104958162837"));
                      startActivity(intent);
                  } catch(Exception e) {
 startActivity(new Intent(Intent.ACTION_VIEW, Uri.parse("https://www.facebook.com/google")));
                  }
</pre>

As you can see when we do the first try we enter a Uri for page 104958162837 that is the ID of the page of Google on Facebook.

How to find the ID of a facebook page?

All you have to do is open the page you want in our case is https://www.facebook.com/Google

and you replace **www** with **graph.** That makes our link https://graph.facebook.com/Google and you will se some text fields. The first is the ID you have to place after bf://page/&#8230;

In case the user has not installed the Facebook app by entering the link it will launch the a browser with the URL stored on case of exception.

&nbsp;

<h2 style="color: #4099ff;">
  Twitter
</h2>

For Twitter we follow exact the same tactic like for Facebook. All you have to do is to find the user&#8217;s ID.

How to find twitter ID?

Just visit this <a href="http://mytwitterid.com/" target="_blank">page</a>( you can also find other services like this)  and type your @username, in our case Google

[<img class="alignnone size-full wp-image-327" src="http://localhost/wp-content/uploads/2015/03/Screen-Shot-2015-03-10-at-12.45.10-PM.png" alt="find twitter id" width="1292" height="580" />][1]

&nbsp;

Now pace your code at the id field

<pre class="brush: java; title: ; notranslate" title="">Intent intent = null;
                  try {
                      // get the Twitter app if possible
                      YourActivity.this.getPackageManager().getPackageInfo("com.twitter.android", 0);
                      intent = new Intent(Intent.ACTION_VIEW, Uri.parse("twitter://user?user_id=20536157"));
                      intent.addFlags(Intent.FLAG_ACTIVITY_NEW_TASK);
                  } catch (Exception e) {
                      // no Twitter app, revert to browser
                      intent = new Intent(Intent.ACTION_VIEW, Uri.parse("https://twitter.com/google"));
                  }
                  YourActivity.this.startActivity(intent);
</pre>

<h2 style="color: #d34836;">
</h2>

<h2 style="color: #d34836;">
  Google+
</h2>

Google plus has the easiest was to launch a page of google+ app or browser.

<pre class="brush: java; title: ; notranslate" title="">startActivity(new Intent(Intent.ACTION_VIEW, Uri.parse("https://plus.google.com/+google")));
</pre>

When you will launch this intent you will have a pop up on your screen to select if you want to launch the app or the browser. Just in one line of code.

&nbsp;

&nbsp;

&nbsp;

 [1]: http://localhost/wp-content/uploads/2015/03/Screen-Shot-2015-03-10-at-12.45.10-PM.png