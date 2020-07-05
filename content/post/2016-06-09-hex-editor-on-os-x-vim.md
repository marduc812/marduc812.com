---
title: 'Hex Editor on OS X [vim]'
author: ヤング marduc
type: post
date: 2016-06-09T20:17:14+00:00
url: /2016/06/09/hex-editor-on-os-x-vim/
featured_image: /wp-content/uploads/2016/06/vim-hex-editor-os-x-100x54.jpg
factory_shortcodes_assets:
  - 'a:0:{}'
dsq_thread_id:
  - 4897844126
mashsb_timestamp:
  - 1582570580
mashsb_jsonshares:
  - '{"total":0,"error":{"facebook_error":"{"error":{"message":"(#12) share field is deprecated for versions v2.9 and higher","type":"OAuthException","code":12,"fbtrace_id":"A1xUDcIWkHlhsKkV6_XQuBA"}}"},"facebook_total":0}'
avada_post_views_count:
  - 361
yuzo_related_post_metabox:
  - 'a:3:{s:17:"yuzo_include_post";s:0:"";s:17:"yuzo_exclude_post";s:0:"";s:21:"yuzo_disabled_related";N;}'
categories:
  - Tuts
tags:
  - Mac
  - tutorial

---
Today I was playing with Spotify and while I was browsing the Cache folders, I found out that the content of these folders is in hex format. The only thing I could see<!--more--> was numbers, so I needed a hex editor in order to view the files.

You don&#8217;t need to download anything the only think you have to do is just open the file by using the vim text editor from your terminal. In order to open a file with vim you type.

<pre class="brush: bash; title: ; notranslate" title="">vim {path of the file you want or just drop the file here}</pre>

&nbsp;

<img class="alignnone size-full wp-image-723" src="http://localhost/wp-content/uploads/2016/06/vim-hex-editor-os-x-2.png" alt="vim hex editor os x (2)" width="1000" height="539" srcset="http://localhost/wp-content/uploads/2016/06/vim-hex-editor-os-x-2.png 1000w, http://localhost/wp-content/uploads/2016/06/vim-hex-editor-os-x-2-300x162.png 300w, http://localhost/wp-content/uploads/2016/06/vim-hex-editor-os-x-2-768x414.png 768w, http://localhost/wp-content/uploads/2016/06/vim-hex-editor-os-x-2-100x54.png 100w, http://localhost/wp-content/uploads/2016/06/vim-hex-editor-os-x-2-862x465.png 862w" sizes="(max-width: 1000px) 100vw, 1000px" /> 

When you see something like the image above type the following:

<pre class="brush: bash; title: ; notranslate" title="">:% ! xxd</pre>

This will turn you editor into a hex editor like shown in the picture below. [<img class="alignnone size-full wp-image-724" src="http://localhost/wp-content/uploads/2016/06/vim-hex-editor-os-x-3.png" alt="vim hex editor os x (3)" width="1000" height="539" srcset="http://localhost/wp-content/uploads/2016/06/vim-hex-editor-os-x-3.png 1000w, http://localhost/wp-content/uploads/2016/06/vim-hex-editor-os-x-3-300x162.png 300w, http://localhost/wp-content/uploads/2016/06/vim-hex-editor-os-x-3-768x414.png 768w, http://localhost/wp-content/uploads/2016/06/vim-hex-editor-os-x-3-100x54.png 100w, http://localhost/wp-content/uploads/2016/06/vim-hex-editor-os-x-3-862x465.png 862w" sizes="(max-width: 1000px) 100vw, 1000px" />][1]

If you want to turn it back to normal editor use the same command like before just type -r in the end.

<pre class="brush: bash; title: ; notranslate" title="">:% ! xxd -r</pre>

[<img class="alignnone size-full wp-image-725" src="http://localhost/wp-content/uploads/2016/06/vim-hex-editor-os-x-4.png" alt="vim hex editor os x (4)" width="1000" height="539" srcset="http://localhost/wp-content/uploads/2016/06/vim-hex-editor-os-x-4.png 1000w, http://localhost/wp-content/uploads/2016/06/vim-hex-editor-os-x-4-300x162.png 300w, http://localhost/wp-content/uploads/2016/06/vim-hex-editor-os-x-4-768x414.png 768w, http://localhost/wp-content/uploads/2016/06/vim-hex-editor-os-x-4-100x54.png 100w, http://localhost/wp-content/uploads/2016/06/vim-hex-editor-os-x-4-862x465.png 862w" sizes="(max-width: 1000px) 100vw, 1000px" />][2]

This will bring your text editor to it&#8217;s normal form. If you still need a better hex editor to do a more complex work you can use [Hex Fiend][3] that is free and [open source][4] or [Synalyze it][5] that offers a free and a premium version.

 [1]: http://localhost/wp-content/uploads/2016/06/vim-hex-editor-os-x-3.png
 [2]: http://localhost/wp-content/uploads/2016/06/vim-hex-editor-os-x-4.png
 [3]: http://ridiculousfish.com/hexfiend/
 [4]: https://github.com/ridiculousfish/HexFiend
 [5]: https://www.synalysis.net/