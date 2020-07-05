---
title: Use Twitter Intent to tweet
author: ヤング marduc
type: post
date: 2015-03-13T10:58:35+00:00
url: /2015/03/13/use-twitter-intent-to-tweet/
featured_image: /wp-content/uploads/2015/03/tweet.jpg
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
  - 100,170,276,329,486,583,635,736,875,0,0,0,0,0,0,0,0,0,0,0,0
mashsb_timestamp:
  - 1531356079
dsq_thread_id:
  - 3591788021
avada_post_views_count:
  - 178
mashsb_jsonshares:
  - '{"facebook_total":0,"facebook_likes":0,"facebook_comments":0}'
categories:
  - Android
  - Tuts
tags:
  - Android

---
Previously I posted a small tutorial how to launch social networks using their intents. Now I&#8217;m going to show you how to post some text from your app to your twitter app. This intent <!--more-->won&#8217;t post instantly the text you typed, but it will create a tweet with it and the user just has to press the tweet button. This can be used for the promotion of your app. You have some text like &#8220;I&#8217;m playing Gold Miner, the world&#8217;s best game. You can download it for free at &#8230;&#8221; (you will still have the 140 characters limit).

I&#8217;m going to test this feature using some EditText.

[<img class="alignnone size-full wp-image-344" src="http://localhost/wp-content/uploads/2015/03/tweet.jpg" alt="tweet" width="400" height="300" />][1]

&nbsp;

<pre class="brush: java; title: ; notranslate" title="">tweet = tweetET.getText().toString();
                Intent tweetIntent = new Intent(Intent.ACTION_SEND);
                tweetIntent.putExtra(Intent.EXTRA_TEXT, tweet);
                tweetIntent.setType("text/plain");

                PackageManager packManager = getPackageManager();
                List&lt;ResolveInfo&gt; resolvedInfoList = packManager.queryIntentActivities(tweetIntent,  PackageManager.MATCH_DEFAULT_ONLY);

                boolean resolved = false;
                for(ResolveInfo resolveInfo: resolvedInfoList){
                    if(resolveInfo.activityInfo.packageName.startsWith("com.twitter.android")){
                        tweetIntent.setClassName(
                                resolveInfo.activityInfo.packageName,
                                resolveInfo.activityInfo.name );
                        resolved = true;
                        break;
                    }
                }
                if(resolved){
                    startActivity(tweetIntent);
                }else{
                    Toast.makeText(MainActivity.this, "Please install twitter app", Toast.LENGTH_LONG).show();
                }
</pre>

You can display the number of characters entered so far using the addTextChangedListener

<pre class="brush: java; title: ; notranslate" title="">tweetET.addTextChangedListener(new TextWatcher() {
            @Override
            public void beforeTextChanged(CharSequence s, int start, int count, int after) {

            }

            @Override
            public void onTextChanged(CharSequence s, int start, int before, int count) {
                tweetSize.setText(s.length()+"/140");
            }

            @Override
            public void afterTextChanged(Editable s) {

            }
        });
</pre>

This won&#8217;t stop user from entering more than 140 characters. If want to stop him you can use XML and add android:maxLength=&#8221;140&#8243; at your editText.

<pre class="brush: xml; title: ; notranslate" title="">&lt;EditText
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:id="@+id/editText"
        android:maxLength="140"
        android:layout_alignParentTop="true"
        android:layout_alignParentLeft="true"
        android:layout_alignParentStart="true"
        android:layout_toLeftOf="@+id/button"
        android:layout_toStartOf="@+id/button" /&gt;
</pre>

 [1]: http://localhost/wp-content/uploads/2015/03/tweet.jpg