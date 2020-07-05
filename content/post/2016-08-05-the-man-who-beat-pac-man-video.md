---
title: 'The man who Beat Pac-Man [Video]'
author: ヤング marduc
type: post
date: 2016-08-05T11:27:20+00:00
url: /2016/08/05/the-man-who-beat-pac-man-video/
featured_image: /wp-content/uploads/2016/08/Screen-Shot-2016-08-05-at-14.24.01-100x50.png
factory_shortcodes_assets:
  - 'a:0:{}'
mashsb_timestamp:
  - 1586620683
avada_post_views_count:
  - 856
mashsb_shares:
  - 1
mashsb_jsonshares:
  - '{"total":1,"error":"","facebook_total":1,"twitter":0,"facebook_likes":"1","facebook_comments":"0"}'
dsq_thread_id:
  - 5042210157
categories:
  - Fun
  - interesting
tags:
  - games
  - pacman

---
[Billy Mitchell][1] was the first person ever to make a perfect score on Pac-Man with score 3.333.360 and game duration around 4 to 5 hours. Bill was awarded in the same year, as &#8220;Video Game Player of the Century&#8221; by <!--more-->Masaya Nakamura (Founder of Namco, the company behind Pac-Man).In order to achieve the perfect score he had to take advantage of some bugs in the game, like for example that one on 1:15 of the video below. The biggest bug the game actually was the last level, number 256.

[<img class="aligncenter wp-image-796" src="http://localhost/wp-content/uploads/2016/08/pacman1-260x300.png" alt="pacman1" width="300" height="347" srcset="http://localhost/wp-content/uploads/2016/08/pacman1-260x300.png 260w, http://localhost/wp-content/uploads/2016/08/pacman1-100x116.png 100w, http://localhost/wp-content/uploads/2016/08/pacman1.png 616w" sizes="(max-width: 300px) 100vw, 300px" />][2]

What happens is that the right part of the screen stops responding normally because the game runs out of memory. The counter of the fruits is an 8-bit Integer, that makes it&#8217;s range 0-255. So when reaching 256 the game, memory overflows and causes the glitch below.

<img class="aligncenter" src="http://vignette2.wikia.nocookie.net/pacman/images/7/77/Splitscreen.gif/revision/latest?cb=20100614191114" width="448" height="620" /> 

Finally because of the missing screen part, there are not enough dots to proceed to the next level. In order to proceed Mrs Pac-Mac has to eat 244 dots but there are in total 131 (122 in the left part of the screen and 9 more in the right part).

 [1]: https://en.wikipedia.org/wiki/Billy_Mitchell_(video_game_player)
 [2]: http://localhost/wp-content/uploads/2016/08/pacman1.png