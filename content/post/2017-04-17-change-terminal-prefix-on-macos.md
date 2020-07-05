---
title: Change Terminal prefix on MacOS
author: ヤング marduc
type: post
date: 2017-04-17T14:06:15+00:00
url: /2017/04/17/change-terminal-prefix-on-macos/
featured_image: /wp-content/uploads/2017/04/Screen-Shot-2017-04-17-at-4.01.21-PM.png
yuzo_related_post_metabox:
  - 'a:3:{s:17:"yuzo_include_post";s:0:"";s:17:"yuzo_exclude_post";s:0:"";s:21:"yuzo_disabled_related";N;}'
mashsb_timestamp:
  - 1587397176
mashsb_jsonshares:
  - '{"total":0,"error":{"facebook_error":"{"error":{"message":"(#12) share field is deprecated for versions v2.9 and higher","type":"OAuthException","code":12,"fbtrace_id":"A_WBY4GYy1hVYqxmXpJXC88"}}"},"facebook_total":0}'
dsq_thread_id:
  - 5733967305
categories:
  - Tuts
tags:
  - Mac
  - tutorial

---
I know there are multiple tutorials online on how to customize the prefix on a Terminal on MacOS but I wanted to write about it so I will remember it. When you do a clean install of <!--more-->the OS, the terminal will have the following prefix.

    HOSTNAME:~ USER$
    

In my case was

    vageliss-MacBook-Pro:~ marduc$

What I wanted to do is a simple marduc$ text

### How to do it

First you need to open the Terminal and move to the [home][1] directory. The following command will take you to the home directory of your user.

    cd ~

Then you need to create a file that will define the form of the variable $PS1. If you want to see the current value of the $PS1 variable type `echo $PS1`. For me this variable was `\h:\W \u\$`.  
While you are still on the home directory type.

    vim .bash_profile

This will create a new text file on the VIM editor (you can use any text editor you prefer, doesn&#8217;t have to be VIM) and there you have to specify the form of the $PS1 variable. The way I want it to be is to display my `User$` so I typed the following.

    export PS1="\u$ "

After that you just save the file and close the terminal. When I logged in back my terminal had the following prefix.

    marduc$

### Different Prefix

If you want a different prefix, you can specify the variables you want to display.

<pre>Table of prompt customizations that are available :
\a  The ASCII bell character (007)
\A  The current time in 24-hour HH:MM format
\d  The date in "Weekday Month Day" format
\D {format} The format is passed to strftime(3) and the result is inserted into the prompt string; an empty format results in a locale-specific time representation; the braces are required
\e  The ASCII escape character (033)
\H  The hostname
\h  The hostname up to the first "."
\j  The number of jobs currently managed by the shell
\l  The basename of the shell's terminal device name
\n  A carriage return and line feed 
\r  A carriage return
\s  The name of the shell
\T  The current time in 12-hour HH:MM:SS format
\t  The current time in HH:MM:SS format
\@  The current time in 12-hour a.m./p.m. format
\u  The username of the current user
\v  The version of bash (e.g., 2.00)
\V  The release of bash; the version and patchlevel (e.g., 2.00.0)
\w  The current working directory
\W  The basename of the current working directory
\#  The command number of the current command
\!  The history number of the current command
\$  If the effective UID is 0, print a #, otherwise print a $
\nnn    Character code in octal
\\  Print a backslash
\[  Begin a sequence of non-printing characters, such as terminal control sequences
\]  End a sequence of non-printing characters</pre>

If you want to learn more about Terminal prefix customization, this guy&#8217;s [post][2] is worth a look.

[<img class="alignnone size-full wp-image-878" src="http://localhost/wp-content/uploads/2017/04/Screen-Shot-2017-04-24-at-10.14.32-PM.png" alt="" width="1364" height="592" srcset="http://localhost/wp-content/uploads/2017/04/Screen-Shot-2017-04-24-at-10.14.32-PM.png 1364w, http://localhost/wp-content/uploads/2017/04/Screen-Shot-2017-04-24-at-10.14.32-PM-300x130.png 300w, http://localhost/wp-content/uploads/2017/04/Screen-Shot-2017-04-24-at-10.14.32-PM-768x333.png 768w, http://localhost/wp-content/uploads/2017/04/Screen-Shot-2017-04-24-at-10.14.32-PM-1024x444.png 1024w" sizes="(max-width: 1364px) 100vw, 1364px" />][3]  
The way I have the prefix at the moment is normal text color for the User and a light Grey for the current directory.  
To do that you can use the following $PS1 value.

    \u:\e[37m\w$\e[39m

Pusheen cat ASCII found [here][4].

 [1]: http://www.linfo.org/home_directory.html
 [2]: http://www.linuxnix.com/linuxunix-shell-ps1-prompt-explained-in-detail/
 [3]: http://localhost/wp-content/uploads/2017/04/Screen-Shot-2017-04-24-at-10.14.32-PM.png
 [4]: http://textart4u.blogspot.cz/2014/08/pusheen-cat-ascii-art-copy-paste-codes.html