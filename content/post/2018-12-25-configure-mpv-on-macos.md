---
title: Configure mpv on MacOS
author: ヤング marduc
type: post
date: 2018-12-25T22:51:20+00:00
url: /2018/12/25/configure-mpv-on-macos/
featured_image: /wp-content/uploads/2018/12/mpv_cov-741x293.jpg
yuzo_related_post_metabox:
  - 'a:3:{s:17:"yuzo_include_post";s:0:"";s:17:"yuzo_exclude_post";s:0:"";s:21:"yuzo_disabled_related";N;}'
mashsb_timestamp:
  - 1587994899
mashsb_jsonshares:
  - '{"total":0,"error":{"facebook_error":"{"error":{"message":"(#12) share field is deprecated for versions v2.9 and higher","type":"OAuthException","code":12,"fbtrace_id":"Aoick-hW5xB9raFYs_O0_ea"}}"},"facebook_total":0}'
categories:
  - Tuts
tags:
  - Mac
  - tutorial

---
<div class="wp-block-jetpack-markdown">
  <p>
    My main device is a MacBook and the player I usually used was VLC. VLC is easy to use and it has been here for all these years, but it was time for a change. Recently I switched to <code>mpv</code>, that is flexible, customizable and open source.
  </p>
</div>

<!--more-->

<div class="wp-block-jetpack-markdown">
  <h4>
    Install mpv
  </h4>
  
  <p>
    You can download it from their website, there you can find prebuild binaries for Windows, MacOS, Linux, Android and some BSD platforms. After downloading the installation pretty easy, just extract the content of the compressed file and move the executable to your <code>Application</code> folder.
  </p>
</div>

<hr class="wp-block-separator" />

<div class="wp-block-jetpack-markdown">
  <h3>
    Configuration
  </h3>
  
  <p>
    For that, a folder is required for mpv, in order to store its configuration. The easiest option is to clone <code>Argon's Github</code> repository, that uses the <code>autosub-mpv</code> plugin by vayan and loads a really well configured mpv.
  </p>
</div>

<pre class="brush: bash; title: ; notranslate" title="">git clone https://github.com/Argon-/mpv-config.git ~/.config/mpv
</pre>

<div class="wp-block-jetpack-markdown">
  <h4>
    Auto subtitle download
  </h4>
  
  <p>
    In order to do it, <code>subliminal</code> is required. Subliminal is a library for automatically finding subtitles. Installation is really easy since it is part of brew.
  </p>
</div>

<pre class="brush: bash; title: ; notranslate" title="">brew install subliminal
</pre>

<div class="wp-block-jetpack-markdown">
  <p>
    To enable auto subtitle download, change the <code>input.conf</code> file and replace or specify a new key. In my case I replaced <code>b</code>, that by default it increases the video playback speed.
  </p>
</div>

<pre class="brush: plain; title: ; notranslate" title="">b      script_binding auto_load_subs ;find subtitles
</pre>

<div class="wp-block-jetpack-markdown">
  <p>
    While the video plays, by clicking <code>b</code>, mpv will find subtitles for the video file.
  </p>
  
  <h4>
    Additional Configuration
  </h4>
  
  <p>
    On mpv.conf I commented the following lines.
  </p>
  
  <ul>
    <li>
      On line 12 commented the <code>#no-border</code> option, mainly because for me it&#8217;s easier to manage the window.
    </li>
    <li>
      Commented line 21 (<code>#input-media-keys=no</code>) to allow OSX media keys.
    </li>
    <li>
      On line 108, change the subtitle language order by using the ISO 639-1 Code.
    </li>
  </ul>
  
  <h4>
    Shortcut keys
  </h4>
  
  <table>
    <tr>
      <th>
        Key
      </th>
      
      <th>
        Action
      </th>
    </tr>
    
    <tr>
      <td>
        →
      </td>
      
      <td>
        Front 5 sec
      </td>
    </tr>
    
    <tr>
      <td>
        ←
      </td>
      
      <td>
        Back 5 sec
      </td>
    </tr>
    
    <tr>
      <td>
        shift + →
      </td>
      
      <td>
        Front 1 sec
      </td>
    </tr>
    
    <tr>
      <td>
        shift + ←
      </td>
      
      <td>
        Back 1 sec
      </td>
    </tr>
    
    <tr>
      <td>
        shift + ↑
      </td>
      
      <td>
        Front 120 sec
      </td>
    </tr>
    
    <tr>
      <td>
        shift + ↓
      </td>
      
      <td>
        Back 120 sec
      </td>
    </tr>
    
    <tr>
      <td>
        n
      </td>
      
      <td>
        Sub delay +0.1s
      </td>
    </tr>
    
    <tr>
      <td>
        N
      </td>
      
      <td>
        Sub delay -0.1s
      </td>
    </tr>
    
    <tr>
      <td>
        ESC
      </td>
      
      <td>
        Cycle fullscreen
      </td>
    </tr>
    
    <tr>
      <td>
        SPACE
      </td>
      
      <td>
        Cycle pause
      </td>
    </tr>
    
    <tr>
      <td>
        TAB
      </td>
      
      <td>
        Cycle mute
      </td>
    </tr>
    
    <tr>
      <td>
        ENTER
      </td>
      
      <td>
        Show progress
      </td>
    </tr>
  </table>
</div>

<hr class="wp-block-separator" />

<div class="wp-block-jetpack-markdown">
  <h5>
    References
  </h5>
  
  <ul>
    <li>
      <a href="https://mpv.io/installation/">mpv.io download</a>
    </li>
    <li>
      <a href="https://subliminal.readthedocs.io/en/latest/">Subliminal</a>
    </li>
    <li>
      <a href="https://github.com/Argon-/mpv-config/">Argon-mpv-config Github</a>
    </li>
    <li>
      <a href="https://github.com/vayan/autosub-mpv/blob/master/autosub.lua">autosub-mpv Github</a>
    </li>
  </ul>
</div>