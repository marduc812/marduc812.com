---
title: Aquatone – npm executable not found
author: ヤング marduc
type: post
date: 2018-10-10T17:41:52+00:00
url: /2018/10/10/aquatone-npm-executable-not-found/
featured_image: /wp-content/uploads/2018/10/Screenshot-2018-12-20-at-01.01.56.png
yuzo_related_post_metabox:
  - 'a:3:{s:17:"yuzo_include_post";s:0:"";s:17:"yuzo_exclude_post";s:0:"";s:21:"yuzo_disabled_related";N;}'
mashsb_timestamp:
  - 1587024332
mashsb_jsonshares:
  - '{"total":0,"error":{"facebook_error":"{"error":{"message":"(#12) share field is deprecated for versions v2.9 and higher","type":"OAuthException","code":12,"fbtrace_id":"A3gnJUG9N_8YRKopxSUgCLe"}}"},"facebook_total":0}'
categories:
  - Security
  - Tuts
tags:
  - Security
  - tutorial

---
Aquatone is a great tool, developed by user @michenriksen, used for subdomain takeovers. The reason that I specifically like this tool is because it helps you enumerate subdomains easily, giving you IPs with Open Ports and their matching subdomain.

<!--more-->

### How it works

Aquatone is divided in 4 different scripts, `discover`, `gather`, `scan` and `takeover`.

  * `discover` &#8211; Collects the subdomains of the domain specified
  * `scan` &#8211; Enumerate Open Ports of hosts identified previously
  * `gather` &#8211; Enumerate Web Servicies found on those hosts and take screenshots
  * `takeover` &#8211; Based on standard error messages it will report if a domain is vulnerable or not.

### npm executable not found

#### Error

This error pops up when some is on the gather script. The message is pretty clear to be honest, that npm executable is not present.

#### Solution

Clone `npm` from their official Github https://github.com/npm/cli (_Note is was recently moved from https://github.com/npm/npm_) and install it using `Make`.

<pre><pre class="brush: plain; title: ; notranslate" title="">
git clone https://github.com/npm/cli.git
cd cli
make install
</pre>


<h5>
  Verify installation
</h5>


<pre><pre class="brush: plain; title: ; notranslate" title="">
npm -v
</pre>


<h3>
  More info
</h3>


<ul>
  <li>
    <a href="https://michenriksen.com/">@michenriksen</a>
  </li>
  
  
  <li>
    <a href="https://github.com/michenriksen/aquatone">Aquatone Github</a>
  </li>
  
</ul>