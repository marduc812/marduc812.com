---
title: Find subdomains using Project Sonar by Rapid7
author: ヤング marduc
type: post
date: 2018-12-19T23:56:12+00:00
url: /2018/12/19/find-subdomains-using-project-sonar-by-rapid7/
featured_image: /wp-content/uploads/2018/12/project-sonar.png
yuzo_related_post_metabox:
  - 'a:3:{s:17:"yuzo_include_post";s:0:"";s:17:"yuzo_exclude_post";s:0:"";s:21:"yuzo_disabled_related";N;}'
mashsb_timestamp:
  - 1587963491
mashsb_jsonshares:
  - '{"total":0,"error":{"facebook_error":"{"error":{"message":"(#12) share field is deprecated for versions v2.9 and higher","type":"OAuthException","code":12,"fbtrace_id":"A_-A_3G2ICLx5CA8Jazv2sp"}}"},"facebook_total":0}'
categories:
  - Security
  - Tuts
tags:
  - Security
  - tutorial

---
<div class="wp-block-jetpack-markdown">
  <p>
    Recently a friend of mine told me about Project Sonar by Rapid7. The purpose of this project is to enumerate as many as possible services online.
  </p>
</div>

<!--more-->

<div class="wp-block-jetpack-markdown">
  <p>
    The enumeration happens by scanning all the IPs and determining what services are running on those. This is done from multiple subnets, so they will be able to collect as much information as possible. On Patrik Hudak&#8217;s website, there is an in depth explanation of how the project works, like on the Rapid7 website.
  </p>
</div>

<hr class="wp-block-separator" />

<div class="wp-block-jetpack-markdown">
  <h2>
    Querying domains
  </h2>
  
  <h3>
    How to get the data
  </h3>
  
  <p>
    I downloaded the Forward DNS records, and specifically the <code>2018-11-23-1542931676-fdns_any.json.gz</code>, that like it&#8217;s visible it is a compressed file and has size <code>25.6 GB</code>.
  </p>
  
  <h5>
    Forward DNS JSON scheme
  </h5>
  
  <p>
    Below is the structure of the JSON file.
  </p>
  
  <pre><code>{
  "$id": "https://opendata.rapid7.com/sonar.fdns_v2/",
  "type": "object",
  "definitions": {},
  "$schema": "http://json-schema.org/draft-07/schema#",
  "additionalProperties": false,
  "properties": {
    "timestamp": {
      "$id": "/properties/timestamp",
      "type": "string",
      "description": "The time when this response was received in seconds since the epoch"
    },
    "name": {
      "$id": "/properties/name",
      "type": "string",
      "description": "The record name"
    },
    "type": {
      "$id": "/properties/type",
      "type": "string",
      "description": "The record type"
    },
    "value": {
      "$id": "/properties/value",
      "type": "string",
      "description": "The response received for a record of the given name and type"
    }
  }
}
</code></pre>
  
  <h3>
    Parse results from the file
  </h3>
  
  <p>
    First <code>jq</code> needs to be installed to help with JSON processing. jq can be installed by typing <code>sudo apt install jq</code> on Kali or <code>brew install jq</code> on MacOS. To get the content subdomains of your choice, you can use the following command.
  </p>
</div>

<pre class="brush: bash; title: ; notranslate" title="">zcat fdns.json.gz
| grep -F '.example.com"'
| jq -crM 'if (.name | test("\\.example\\.com$")) then .name else empty end'
| sort
| uniq
| tee -a example.com.list
</pre>

<div class="wp-block-jetpack-markdown">
  <p>
    This command worked for both my Kali and MacOS, but in case you have an issue you can run it with <code>zcat file.gz</code> directly. When you parse your subdomains, using tee, it copies stdin to stdout and also to any file specified.
  </p>
</div>

<hr class="wp-block-separator" />

<div class="wp-block-jetpack-markdown">
  <h5>
    Update
  </h5>
  
  <p>
    I did a small bash script so I don&#8217;t have to write the command all the time. If you are here, I guess you know how to run a .sh script, so the only thing is that you add the domain you want to test as argument.
  </p>
  
  <p>
    <code>$ sonar_search.sh google.com</code>
  </p>
</div>

<div class="wp-block-jetpack-markdown">
  <h3>
    References
  </h3>
  
  <h5>
    DNS Records
  </h5>
  
  <ul>
    <li>
      <a href="https://opendata.rapid7.com/about/">Project Sonar</a>
    </li>
    <li>
      <a href="https://opendata.rapid7.com/">Download Links</a>
    </li>
    <li>
      <a href="https://blog.rapid7.com/2013/09/26/internet-wide-probing-rapid7-sonar/">Scanning All The Things Info</a>
    </li>
  </ul>
  
  <h5>
    Tools
  </h5>
  
  <ul>
    <li>
      <a href="">zcat</a>
    </li>
    <li>
      <a href="https://stedolan.github.io/jq/">jq</a>
    </li>
  </ul>
  
  <h5>
    External
  </h5>
  
  <ul>
    <li>
      <a href="https://0xpatrik.com/project-sonar-guide/">0xpatrik.com</a>
    </li>
    <li>
      <a href="https://opendata.rapid7.com/static/img/bg-sonar.jpg">Cover Picture</a>
    </li>
  </ul>
</div>