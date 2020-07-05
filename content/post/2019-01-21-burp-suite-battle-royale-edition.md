---
title: Burp Suite – Battle Royale Edition
author: ヤング marduc
type: post
date: 2019-01-21T22:15:43+00:00
url: /2019/01/21/burp-suite-battle-royale-edition/
featured_image: /wp-content/uploads/2019/01/burp-suite-battle-royale-741x293.jpg
yuzo_related_post_metabox:
  - 'a:3:{s:17:"yuzo_include_post";s:0:"";s:17:"yuzo_exclude_post";s:0:"";s:21:"yuzo_disabled_related";N;}'
mashsb_timestamp:
  - 1587468792
mashsb_jsonshares:
  - '{"facebook_total":3,"facebook_likes":3,"facebook_comments":0}'
mashsb_shares:
  - 3
categories:
  - Security
  - Tuts
tags:
  - Security
  - tutorial

---
Everyone who doesn&#8217;t live under a rock, knows and probably used Burp Suite, by PortSwigger. Recently a Beta 2.0 version was released with multiple new features and a new dashboard to control all the processing running, from one tab. In this post I will write about some features of Burp, that I found useful and I use almost daily to make my life easier.  


<!--more-->

<div class="wp-block-jetpack-markdown">
  <h3>
    Scope
  </h3>
  
  <p>
    Having the right scope is the first thing to start with. By saying scope, you know that in tests, scope can vary from a simple page to a complete domain (the best case in my opinion).
  </p>
  
  <p>
    Let&#8217;s say for example that the website in scope is <code>sub.example.com</code>. To specify which domain is in scope, go to <code>Target</code> tab and then <code>Scope</code>. There is an option <code>use advanced scope control</code>, and by enabling that you can customise the scope that you want want to have on your website, either it&#8217;s one domain or a subdomain. Click <code>Paste URL</code> and Burp, will fill the fields for you. You will see something like that:
  </p>
</div><figure class="wp-block-image">

<img src="http://localhost/wp-content/uploads/2019/01/scope1-1.jpg" alt="" class="wp-image-1039" srcset="http://localhost/wp-content/uploads/2019/01/scope1-1.jpg 800w, http://localhost/wp-content/uploads/2019/01/scope1-1-300x158.jpg 300w, http://localhost/wp-content/uploads/2019/01/scope1-1-768x403.jpg 768w" sizes="(max-width: 800px) 100vw, 800px" /> <figcaption>In case you want all domains of example.com to be in scope,  
replace sub with an asterisk, so it will be `^*\.example\.com$`</figcaption></figure> 

<div class="wp-block-jetpack-markdown">
  <p>
    In case you don&#8217;t care about the Port or the File path, you can leave them empty and Burp will handle it as a wildcard. You can limit Burp, to show only items in scope, by going to <code>Proxy</code> -> <code>HTTP history</code> -> Click on <code>Filter</code> field and enable <code>Show only in scope items</code>. The same way can be done for <code>Site map</code>.
  </p>
  
  <h3>
    Enumeration
  </h3>
  
  <p>
    The main way I enumerated content is by using gobuster, useful for directory and DNS enumeration. Recently, I found out that Burp, for multiple versions now, gives the option to find content of the website using its <code>Discover Content</code> functionality. This feature can be used by going to <code>Target</code> -> <code>Sitemap</code> -> Right click on the domain in scope -> <code>Engagement tools</code> and <code>Discover content</code>.
  </p>
  
  <p>
    There, you can specify what kind of enumeration you want to do, if it is files only, directories or both, what type of file extensions Burp should look for, depth, number of threads and more. The advantage that I can find in this way of enumerating instead of using another tool, is that you can have better project structure inside Site Map with every request and its response.
  </p>
</div>

<div class="wp-block-jetpack-markdown">
  <h3>
    Intruder
  </h3>
  
  <p>
    Intruder is used for brute forcing but mainly for brute forcing of parameters, that for enumeration. Something that we don&#8217;t see that often these days (luckily) is Basic Authorization. The way Basic authorization works is by sending user&#8217;s credentials in the following form username:password Base64 encoded. In case we know someones username (let&#8217;s say admin) and we want to brute force the password, a simple payload marker (§) won&#8217;t be enough.
  </p>
  
  <p>
    The way Burp can process the payload before sending that is really straight forward. In Intruder go to <code>Payloads</code> tab and scroll down to <code>Payload Processing</code>. Add a new rule, select <code>Add prefix</code> and write as prefix <code>admin:</code> that we know that is the username. Then, add new rule and select <code>encoding</code> and <code>Base64-encode</code>. This will Base64 encode the payload before sending it. Finally, because Base64 uses equal signs (=) to match the four bytes block size, on <code>Payload encoding</code> field, remove the equal sign from the list of characters. This will prevent Burp from sending YWRtaW46YWRtaW4<code>%3d</code> instead of YWRtaW46YWRtaW4<code>=</code>.
  </p>
</div><figure class="wp-block-image">

<img src="http://localhost/wp-content/uploads/2019/01/intruder.jpg" alt="" class="wp-image-1040" srcset="http://localhost/wp-content/uploads/2019/01/intruder.jpg 1000w, http://localhost/wp-content/uploads/2019/01/intruder-300x130.jpg 300w, http://localhost/wp-content/uploads/2019/01/intruder-768x332.jpg 768w" sizes="(max-width: 1000px) 100vw, 1000px" /> <figcaption>Multiple options are offered for payload processing including  
`Match & Replace`, `Hashing`, `Encoding` and `RegEx matching`.</figcaption></figure> 

<div class="wp-block-jetpack-markdown">
  <p>
    One small tweak that can save you some time, is to change the behaviour of a new Intruder window. By clicking <code>Intruder</code> -> <code>New tab behaviour</code> -> <code>Copy configuration from last tab</code>. Additionally, in case you believe something went wrong with Intruder, you can right click on the items that you are interested about and select <code>Request items again</code>.
  </p>
</div>

<div class="wp-block-jetpack-markdown">
  <h3>
    Proof of Concepts
  </h3>
  
  <h5>
    CSRF
  </h5>
  
  <p>
    Burp has a really helpful functionality, that just by doing a right click on the request that you would like to create a PoC, select <code>Engagemenet tools</code> and <code>Generate CSRF PoC</code>.
  </p>
</div><figure class="wp-block-image">

<img src="http://localhost/wp-content/uploads/2019/01/csrf-burp.jpg" alt="" class="wp-image-1044" srcset="http://localhost/wp-content/uploads/2019/01/csrf-burp.jpg 800w, http://localhost/wp-content/uploads/2019/01/csrf-burp-300x100.jpg 300w, http://localhost/wp-content/uploads/2019/01/csrf-burp-768x255.jpg 768w" sizes="(max-width: 800px) 100vw, 800px" /> <figcaption>By selecting Options you can customise the PoC. Something that I like to do is specify to send the request on page load, so no interaction is required. </figcaption></figure> 

<div class="wp-block-jetpack-markdown">
  <h5>
    Clickjacking
  </h5>
  
  <p>
    Burp gives the ability to create a proof of concept by using <code>Burp Clickbandit</code>. Clickbandit is available under the Burp menu and generates javascript code, that by pasting on browser&#8217;s console it will run the website inside an iframe. Then by clicking on the part of the page that you want the button to be set for the Proof of Concept, it will generate an HTML page with your proof of concept.
  </p>
</div><figure class="wp-block-image">

<img src="http://localhost/wp-content/uploads/2019/01/burp-clickbandit.jpg" alt="" class="wp-image-1045" srcset="http://localhost/wp-content/uploads/2019/01/burp-clickbandit.jpg 1000w, http://localhost/wp-content/uploads/2019/01/burp-clickbandit-300x78.jpg 300w, http://localhost/wp-content/uploads/2019/01/burp-clickbandit-768x200.jpg 768w" sizes="(max-width: 1000px) 100vw, 1000px" /> <figcaption>Sample view of Burp Clickbandit.</figcaption></figure> 

<div class="wp-block-jetpack-markdown">
  <h3>
    Shortcuts
  </h3>
  
  <p>
    Using shortcuts makes life so much easier. 90% of the time your hands are on a keyboard and it is easier to click 2 buttons that scrolling with the mouse. This is a list of shortcuts that will save you some time.
  </p>
  
  <table>
    <tr>
      <th style="text-align:center">
        Combination
      </th>
      
      <th>
        Action
      </th>
      
      <th>
        + Shift
      </th>
    </tr>
    
    <tr>
      <td style="text-align:center">
        CTRL + R
      </td>
      
      <td>
        Send request to <code>R</code>epeater
      </td>
      
      <td>
        Go to <code>R</code>epeater
      </td>
    </tr>
    
    <tr>
      <td style="text-align:center">
        CTRL + I
      </td>
      
      <td>
        Send request to <code>I</code>ntruder
      </td>
      
      <td>
        Go to <code>I</code>ntruder
      </td>
    </tr>
    
    <tr>
      <td style="text-align:center">
        CTRL + T
      </td>
      
      <td>
        Turn Proxy On/Off
      </td>
      
      <td>
        Go to <code>T</code>arget
      </td>
    </tr>
    
    <tr>
      <td style="text-align:center">
        CTRL + U
      </td>
      
      <td>
        <code>U</code>RL encode
      </td>
      
      <td>
        <code>U</code>RL decode
      </td>
    </tr>
    
    <tr>
      <td style="text-align:center">
        CTRL + H
      </td>
      
      <td>
        <code>H</code>TML encode
      </td>
      
      <td>
        <code>H</code>TML decode
      </td>
    </tr>
    
    <tr>
      <td style="text-align:center">
        CTRL + B
      </td>
      
      <td>
        <code>B</code>ase64 encode
      </td>
      
      <td>
        <code>B</code>ase64 decode
      </td>
    </tr>
    
    <tr>
      <td style="text-align:center">
        CTRL + Space
      </td>
      
      <td>
        Issue repeater request
      </td>
      
      <td>
        &#8211;
      </td>
    </tr>
  </table>
</div><figure class="wp-block-image">

<img src="http://localhost/wp-content/uploads/2019/01/burp-hotkeys.jpg" alt="" class="wp-image-1046" srcset="http://localhost/wp-content/uploads/2019/01/burp-hotkeys.jpg 800w, http://localhost/wp-content/uploads/2019/01/burp-hotkeys-300x98.jpg 300w, http://localhost/wp-content/uploads/2019/01/burp-hotkeys-768x250.jpg 768w" sizes="(max-width: 800px) 100vw, 800px" /> <figcaption>You can customise shortcuts by going to  
`User Options` -> `Misc` -> `Hotkeys` -> `Edit hotkeys`.</figcaption></figure> 

<div class="wp-block-jetpack-markdown">
  <h3>
    Burp Extensions
  </h3>
  
  <p>
    Bellow is a list of the extensions I believe is work to give it a try.
  </p>
  
  <table>
    <tr>
      <th>
        Name
      </th>
      
      <th>
        Use
      </th>
      
      <th>
        Type
      </th>
    </tr>
    
    <tr>
      <td>
        Active Scan++
      </td>
      
      <td>
        Improves Passive and Active Scanner
      </td>
      
      <td>
        Free
      </td>
    </tr>
    
    <tr>
      <td>
        WSDLer
      </td>
      
      <td>
        WSDL to SOAP requests
      </td>
      
      <td>
        Free
      </td>
    </tr>
    
    <tr>
      <td>
        Freddy
      </td>
      
      <td>
        Exploit deserialization attacks
      </td>
      
      <td>
        Pro
      </td>
    </tr>
    
    <tr>
      <td>
        SQLipy
      </td>
      
      <td>
        SQLmap on Burp
      </td>
      
      <td>
        Free
      </td>
    </tr>
    
    <tr>
      <td>
        TokenJar
      </td>
      
      <td>
        Manage CSRF tokens and Session IDs
      </td>
      
      <td>
        Free
      </td>
    </tr>
    
    <tr>
      <td>
        J2EEScan
      </td>
      
      <td>
        Tests J2EE applications
      </td>
      
      <td>
        Pro
      </td>
    </tr>
    
    <tr>
      <td>
        Retire.js
      </td>
      
      <td>
        Detects vulnerable Javascript libraries
      </td>
      
      <td>
        Pro
      </td>
    </tr>
    
    <tr>
      <td>
        Logger++
      </td>
      
      <td>
        Improves filtering process
      </td>
      
      <td>
        Free
      </td>
    </tr>
    
    <tr>
      <td>
        Brida
      </td>
      
      <td>
        Bridge between Frida and Burp
      </td>
      
      <td>
        Free
      </td>
    </tr>
    
    <tr>
      <td>
        Request Minimizer
      </td>
      
      <td>
        Minimizes long session cookies etc
      </td>
      
      <td>
        Free
      </td>
    </tr>
    
    <tr>
      <td>
        Sleepy Puppy
      </td>
      
      <td>
        Detect delayed XSS vulnerabilities
      </td>
      
      <td>
        Free
      </td>
    </tr>
    
    <tr>
      <td>
        NoPE Proxy
      </td>
      
      <td>
        Extension for Non HTTP Requests
      </td>
      
      <td>
        Free
      </td>
    </tr>
    
    <tr>
      <td>
        Reflected parameters
      </td>
      
      <td>
        Checks for parameters that get reflected on the response
      </td>
      
      <td>
        Pro
      </td>
    </tr>
    
    <tr>
      <td>
        .NET beautifier
      </td>
      
      <td>
        Make easily readable .NET by hiding ViewStates etc.
      </td>
      
      <td>
        Free
      </td>
    </tr>
    
    <tr>
      <td>
        JSON beautifier
      </td>
      
      <td>
        Readable JSON strings
      </td>
      
      <td>
        Free
      </td>
    </tr>
  </table>
  
  <p>
    Keep in mind that multiple of those extensions require <code>Jython</code>, that can be installed directly from Burp Suite.
  </p>
</div>

<div class="wp-block-jetpack-markdown">
  <h3>
    References
  </h3>
  
  <ul>
    <li>
      <a href="https://github.com/Netflix-Skunkworks/sleepy-puppy/tree/master/burp-extension">Sleepy Puppy</a>
    </li>
    <li>
      <a href="https://github.com/summitt/Burp-Non-HTTP-Extension">NoPE Proxy</a>
    </li>
  </ul>
</div>

Note: The title is just for fun of course, there is no Battle Royale on Burp Suite. I think so at least.