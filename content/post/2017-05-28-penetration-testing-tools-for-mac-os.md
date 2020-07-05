---
title: Penetration Testing Tools for Mac OS
author: ヤング marduc
type: post
date: 2017-05-28T14:40:42+00:00
url: /2017/05/28/penetration-testing-tools-for-mac-os/
featured_image: /wp-content/uploads/2017/05/penetration-testing-tools-mac-os.jpg
yuzo_related_post_metabox:
  - 'a:3:{s:17:"yuzo_include_post";s:0:"";s:17:"yuzo_exclude_post";s:0:"";s:21:"yuzo_disabled_related";N;}'
mashsb_timestamp:
  - 1587998094
mashsb_shares:
  - 6
mashsb_jsonshares:
  - '{"total":5,"error":"","twitter":4,"facebook_total":2,"facebook_likes":2,"facebook_comments":0}'
dsq_thread_id:
  - 5857973917
categories:
  - Tuts
tags:
  - Mac
  - Security

---
I was playing with <a href="https://www.metasploit.com/" target="_blank" rel="noopener noreferrer">Metasploit Framework</a> and I was using the `msfvenom` payload. For that purpose I was using `Kali Linux` as a Virtual Machine, mainly because all the tools are pre-installed there. Running a <!--more-->Virtual Machine is not as easy as running the tools in a host Operating System. The available RAM of course is much less than the actual host and some times configuring things can be complex.

### Nmap (Free)

Nmap is the best port scanning tool you can use and also open source. Used widely, mainly because of the incredible power and flexibility it offers. On Mac OS Nmap comes with `ZenMap`, in the installation pack. For those who don&#8217;t like the terminal Zenmap is the perfect tool. I prefer using Nmap but in some cases, like for example when you have multiple hosts to scan, Zenmap makes reading them much easier.

Installation of Nmap is really simple and it does not require any typing at all. You can just download a `.dmg` file from the official website and do a normal installation like in every other application.

Links: <a href="https://nmap.org/book/inst-macosx.html" target="_blank" rel="noopener noreferrer">Nmap</a> &#8211; <a href="https://github.com/nmap/nmap" target="_blank" rel="noopener noreferrer">Github</a>

### Nikto (Free)

Nikto comes pre-installed on Kali Linux and some times it can help you find some hidden Gems on the web server you are testing. Nikto is a Web Server scanner that will inform you in case there is an outdated software version, if it finds some insecure or default files / directories and about some possible server misconfigurations.

In order to install Nikto you need to install Homebrew. To install Homebrew you need to type a single command on your terminal.

<pre id="selectable">ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
</pre>

After installation if you didn&#8217;t agree with the Terms of Service of X-Code you will probably need to follow the instuctions. The instructions are pretty clear and simple to follow. Next you have to install Nikto. Go back to your terminal and type the following.

<pre class="language-bash" data-lang="bash">brew install nikto</pre>

After finishing the installation you will be able to scan every web server using the command `nikto -h {URL}`.

Links: <a href="https://brew.sh/" target="_blank" rel="noopener noreferrer">Homebrew</a> &#8211; [Github][1] &#8211; <a href="https://cirt.net/Nikto2" target="_blank" rel="noopener noreferrer">Nikto</a>

### Wireshark (Free)

The Wireshark is the most known Network Traffic Sniffer, that is open-source like all the tools so far. The Wireshark distribution also comes with TShark, which is aline-oriented sniffer (similar to Sun&#8217;s snoop, or tcpdump) that uses thesame dissection, capture-file reading and writing, and packet filteringcode as Wireshark, and with editcap, which is a program to read capturefiles and write the packets from that capture file, possibly in adifferent capture file format, and with some packets possibly removed from the capture.

Installation is pretty simple, since it come as a `.dmg` file and the installation is like on every other application on Mac OS. After installation a new icon will appear on the launchpad&#8217;s application list. From there just by clicking it you can start sniffing the network traffic, after specifying the interface you would like to intercept.

Links: <a href="https://www.wireshark.org/download.html" target="_blank" rel="noopener noreferrer">Wireshark</a> &#8211; <a href="https://github.com/wireshark/wireshark" target="_blank" rel="noopener noreferrer">Github</a>

### Sqlmap (Free)

The Sqlmap is a powerful tool for finding `SQL injections`. It is completely automated and just by specifying a parameter the tool will try to exploit the injectable parameter sometimes even without you having to specify the type of database. It supports multi databases including SQL and non-SQL databases. Installation is pretty simple by using `brew`.

<pre class="language-bash" data-lang="bash">brew install sqlmap</pre>

When the installation is complete you can just type `sqlmap` on terminal to launch the tool.

Links: <a href="http://sqlmap.org/" target="_blank" rel="noopener noreferrer">sqlmap</a> &#8211; <a href="https://github.com/sqlmapproject/sqlmap" target="_blank" rel="noopener noreferrer">Github</a>

### Zed Attack Proxy (Free)

The `OWASP` Zed Attack Proxy (ZAP) is one of the world’s most popular free security tools and is actively maintained by hundreds of international volunteers[*][2]. It can help you automatically find security vulnerabilities in your web applications while you are developing and testing your applications. Its also a great tool for experienced pentesters to use for manual security testing.

The easiest way to install ZAP is by using brew. Start by installing `caskroom`.

<pre class="language-bash" data-lang="bash">brew install caskroom/cask/brew-cask</pre>

After the installation is complete the system is ready to install ZAP.

<pre class="language-bash" data-lang="bash">brew cask install owasp-zap</pre>

After the installation is complete a new ZAP icon will appear on the launchpad.

Links: <a href="https://www.owasp.org/index.php/OWASP_Zed_Attack_Proxy_Project" target="_blank" rel="noopener noreferrer">OWASP ZAP</a> &#8211; [Github][3]

### Burp Suite (Free / Paid)

My personally favourite proxy tool is Burp Suite. It offers pretty much the same options as ZAP, with better and much easier to use design. This is only for the Community version. The paid version offers automated fuzzing, with good results, it offers Intruder, a function to repeat requests for fuzzing, with custom wordlist, support for regular expressions and much more. Intruder is also available for the Community version, but it has a throttling that can be a bit slow. Installing Burp is really easy, you just need to visit their website and they offer an option for Mac OS, and you just download an install the .dmg file.

Links: <a href="https://portswigger.net/burp/communitydownload" target="_blank" rel="noopener">Burp Suite</a>

### Aircrack-ng

Unluckily the tool for every Wi-Fi pentration testing is partially available on OS X. You can do a really simple installation of the Aircrack-ng with macports, but `Airodump-ng` and `Aireplay-ng` are linux only and will not work under OS X native, so for reinjecting and sniffing you will have to use other means.

<pre class="language-bash" data-lang="bash">sudo port install aircrack-ng</pre>

After finishing the installation you can use it by typing aircrack-ng and the options you prefer.

<pre class="language-bash" data-lang="bash">Aircrack-ng 1.2 rc4 - (C) 2006-2015 Thomas d'Otreppe
  http://www.aircrack-ng.org

  usage: aircrack-ng [options] &lt;.cap / .ivs file(s)&gt;

  Common options:

      -a &lt;amode&gt; : force attack mode (1/WEP, 2/WPA-PSK)
      -e &lt;essid&gt; : target selection: network identifier
      -b &lt;bssid&gt; : target selection: access point's MAC
      -p &lt;nbcpu&gt; : # of CPU to use  (default: all CPUs)
      -q         : enable quiet mode (no status output)
      -C &lt;macs&gt;  : merge the given APs to a virtual one
      -l &lt;file&gt;  : write key to file

  Static WEP cracking options:

      -c         : search alpha-numeric characters only
      -t         : search binary coded decimal chr only
      -h         : search the numeric key for Fritz!BOX
      -d &lt;mask&gt;  : use masking of the key (A1:XX:CF:YY)
      -m &lt;maddr&gt; : MAC address to filter usable packets
      -n &lt;nbits&gt; : WEP key length :  64/128/152/256/512
      -i &lt;index&gt; : WEP key index (1 to 4), default: any
      -f &lt;fudge&gt; : bruteforce fudge factor,  default: 2
      -k &lt;korek&gt; : disable one attack method  (1 to 17)
      -x or -x0  : disable bruteforce for last keybytes
      -x1        : last keybyte bruteforcing  (default)
      -x2        : enable last  2 keybytes bruteforcing
      -X         : disable  bruteforce   multithreading
      -y         : experimental  single bruteforce mode
      -K         : use only old KoreK attacks (pre-PTW)
      -s         : show the key in ASCII while cracking
      -M &lt;num&gt;   : specify maximum number of IVs to use
      -D         : WEP decloak, skips broken keystreams
      -P &lt;num&gt;   : PTW debug:  1: disable Klein, 2: PTW
      -1         : run only 1 try to crack key with PTW

  WEP and WPA-PSK cracking options:

      -w &lt;words&gt; : path to wordlist(s) filename(s)

  WPA-PSK options:

      -E &lt;file&gt;  : create EWSA Project file v3
      -J &lt;file&gt;  : create Hashcat Capture file
      -S         : WPA cracking speed test
      -r &lt;DB&gt;    : path to airolib-ng database
                   (Cannot be used with -w)

  Other options:

      -u         : Displays # of CPUs & MMX/SSE support
      --help     : Displays this usage screen</pre>

Links: <a href="https://www.aircrack-ng.org/doku.php?id=install_aircrack#installing_on_mac_osx" target="_blank" rel="noopener noreferrer">Aircrack-ng</a> &#8211; <a href="https://github.com/aircrack-ng/aircrack-ng" target="_blank" rel="noopener noreferrer">Github</a>

### TestSSL (Free)

TestSSL is the best tool to test the SSL configuration of the server you are testing. What I like the most about TestSSL is the clean UI it offers and the simplicity in use. You get different results depending on the device you want to have as a reference and writes in really clean form the possible vulnerabilities of the current configuration.

To install `TestSLL` you firstly have to download the `git` repository from Github. Current stable version is 2.8.

<pre><code id="selectable">git clone https://github.com/drwetter/testssl.sh.git
</code></pre>

Then go to the folder of TestSSL.

<pre><code id="selectable">cd testssl.sh/
</code></pre>

If you want to run TestSSL on a server you can just execute the `.sh` file followed by the URL of the website.

<pre><code id="selectable">./testssl.sh google.com
</code></pre>

Links: <a href="https://testssl.sh/" target="_blank" rel="noopener noreferrer">TestSSL</a> &#8211; <a href="https://github.com/drwetter/testssl.sh/tree/2.8" target="_blank" rel="noopener noreferrer">Github</a>

### Wappalyzer (Free)

This browser extension is available for both Firefox and Chrome, giving users the ability to really easily identify technologies used on a Web Application. This simple plugin displays versions of web server servers, libraries, programming languages and more. What makes this plugin so helpful is it&#8217;s accuracy, how easy is it to use and of course it is open source. I find out about this plugin a few months back and I am using it extensively, so it is worth a shot.

Links: <a href="https://addons.mozilla.org/en-US/firefox/addon/wappalyzer/" target="_blank" rel="noopener">Firefox</a> &#8211; <a href="https://chrome.google.com/webstore/detail/wappalyzer/gppongmhjkpfnbhagpmjfkannfbllamg" target="_blank" rel="noopener">Chrome</a> &#8211; <a href="https://github.com/AliasIO/Wappalyzer" target="_blank" rel="noopener">Github</a>

### Gobuster (Free)

Great tool for enumerating directories, files and DNS subdomains. What I like about Gobuster is the flexibility if offers with extensions, authentication and mainly support for multithreading. I was mainly using dirb for enumerating files and directories, but what was the biggest concern for me was the fact that dirb does not support multiple threads, and this makes the process really slower. Using brew is it easy to install Gobuster.

<pre id="selectable">brew install gobuster
</pre>

Links: <a href="https://github.com/OJ/gobuster" target="_blank" rel="noopener">Github</a>

&nbsp;

 [1]: https://github.com/sullo/nikto
 [2]: https://github.com/zaproxy/zaproxy#justification
 [3]: https://github.com/zaproxy/zaproxy