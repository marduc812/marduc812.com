---
title: How difficult is it to hide files from Forensic Software?
author: ヤング marduc
type: post
date: 2016-11-21T14:08:12+00:00
url: /2016/11/21/how-difficult-is-it-to-hide-files-from-forensic-softwares/
featured_image: /wp-content/uploads/2016/11/cover.jpg
factory_shortcodes_assets:
  - 'a:0:{}'
yuzo_related_post_metabox:
  - 'a:3:{s:17:"yuzo_include_post";s:0:"";s:17:"yuzo_exclude_post";s:0:"";s:21:"yuzo_disabled_related";N;}'
mashsb_timestamp:
  - 1587423668
avada_post_views_count:
  - 370
mashsb_shares:
  - 1
mashsb_jsonshares:
  - '{"total":1,"error":"","twitter":0,"facebook_total":1,"facebook_likes":1,"facebook_comments":0}'
dsq_thread_id:
  - 5321178936
categories:
  - interesting
tags:
  - anti-forensics

---
Recently i did a small research on Digital Forensics and especially on Anti-forensics. For those who don&#8217;t know what Anti-forensics are, can be explained by the definition given by Liu and Brown in &#8220;Bleeding-Edge Anti-Forensics.&#8221; (2006).

<!--more-->

> Attempts to negatively affect the existence, amount, and/or quality of evidence from a crime scene, or make the examination of evidence difficult or impossible to conduct.

There multiple ways someone would modify the result of a forensic analysis, just by:

  * Modifying the data
  * Deleting the data
  * Hiding the data
  * Preventing the analysis by attacking the software

My idea to try anti-forensics came by learning more about SSDs and how they work. Especially about a micro-controller that picks the block on the hard disk that the data should get stored. This technique is called Wear Leveling and in order to extend hard disks life, it writes on different blocks every time. By deleting the file start generate random data of different sizes it will cover the files deleted pretty soon.

### Development

I wrote 4 scripts using Python, that each one of theme would do something different about anti-forensics. In order to test the effectiveness of the scripts I planted 50 files that I wanted to hide from the forensic software. I using different methods for deletion, using file shredding techniques and simple deletion, just by sending it to the Recycler.  Although I had no previous experience in Python, just by having a basing understanding of how Windows OS works I was able to modify the results of the forensic softwares (EnCase and Autopsy).

#### Delit.py

This was the script that was responsible for the safe deletion of the files. The features of this script was to modify the Access / Modified time of the file, so it will appear like it was never open. Implement safe deletion methods like DOD 5220.22 M, AFSSI 5020 ,Gutmann ,Schneier and a custom one that will rename the file and modify the data of a file 10 times before deleting it.

#### ow.py

This script is responsible for the creation of files in order to create junk data on the SSD. It creates files on 1GB, then deletes them and when this process is over it creates small random files until it covers 100% of the hard disk. That way the micro-controller is forced to write on previously deleted files.

#### cl.py

By running this script it will delete the data from all famous browsers (Chrome, Edge, Firefox), also create junk files for Clipboard and then delete them, delete Recycler datas, Temporary files and Windows Event Logs.

#### makebomb.py

By creating ZipBombs, is possible to delay the analysis of the forensic software, but not that much since modern forensic software can identify threads like this. What this script does is create a 1GB test file, just filled with &#8220;1&#8221;. When this file get&#8217;s zipped, it gets really small (around 500kB). The script will create 30 copies of this file and convert them in one zip. The zips size is now 100kB but the unzipped size of the zip is 30GB. Then the zip does the sae process 2 more times creating an incredible amount of data in a small zip file.

## Results

The results from the 50 files where kind of big surprise for me, since autopsy was able to find more deleted files that EnCase, although EnCase is widely accepted in every court. The list below shows the % of the files that each software WASN&#8217;T able to find. The files were:

20 Image Files (jpeg, bmp, gif)  
10 Audio Files (mp3)  
5 Video Files (mpeg, mp4, mkv)  
5 Executables (exe)  
10 Random Files ( dmg, zip, msi)

[<img class="alignnone wp-image-834 size-large" src="http://localhost/wp-content/uploads/2016/11/Screen-Shot-2016-11-21-at-16.06.40-1024x502.png" alt="forensic findings" width="1024" height="502" srcset="http://localhost/wp-content/uploads/2016/11/Screen-Shot-2016-11-21-at-16.06.40-1024x502.png 1024w, http://localhost/wp-content/uploads/2016/11/Screen-Shot-2016-11-21-at-16.06.40-300x147.png 300w, http://localhost/wp-content/uploads/2016/11/Screen-Shot-2016-11-21-at-16.06.40-768x377.png 768w, http://localhost/wp-content/uploads/2016/11/Screen-Shot-2016-11-21-at-16.06.40.png 1076w" sizes="(max-width: 1024px) 100vw, 1024px" />][1]

[<img class="alignnone size-full wp-image-843" src="http://localhost/wp-content/uploads/2016/11/datas.jpg" alt="datas" width="1836" height="1554" srcset="http://localhost/wp-content/uploads/2016/11/datas.jpg 1836w, http://localhost/wp-content/uploads/2016/11/datas-300x254.jpg 300w, http://localhost/wp-content/uploads/2016/11/datas-768x650.jpg 768w, http://localhost/wp-content/uploads/2016/11/datas-1024x867.jpg 1024w" sizes="(max-width: 1836px) 100vw, 1836px" />][2]

<span style="color: #99cc00;"><strong>Worked</strong></span> means that the script was able to hide the data from the Forensic Software  
<span style="color: #3366ff;"><strong>NR</strong></span> means that the Forensic Software was able to retrieve some parts of the file and not the complete file.  
<span style="color: #ff0000;"><strong>FL</strong></span> means that the Forensic Software retrieved the complete file.

After all it&#8217;s simple to modify the data from a computer just by having a basic understanding of how things work. Also is pretty simple to hide in case you are in trouble with law and you have some time. For best results you could probably melt your hard disk.

 [1]: http://localhost/wp-content/uploads/2016/11/Screen-Shot-2016-11-21-at-16.06.40.png
 [2]: http://localhost/wp-content/uploads/2016/11/datas.jpg