---
title: '[Windows 10] can’t create new user'
author: ヤング marduc
type: post
date: 2016-04-06T15:08:47+00:00
url: /2016/04/06/windows-10-cant-create-new-user/
featured_image: /wp-content/uploads/2016/04/windows-10-add-user-100x42.jpg
factory_shortcodes_assets:
  - 'a:0:{}'
dsq_thread_id:
  - 4725141204
mashsb_timestamp:
  - 1587205097
mashsb_jsonshares:
  - '{"total":0,"error":{"facebook_error":"{"error":{"message":"(#12) share field is deprecated for versions v2.9 and higher","type":"OAuthException","code":12,"fbtrace_id":"AOSEVOqHn6nux8Is32RCfvC"}}"},"facebook_total":0}'
avada_post_views_count:
  - 215
categories:
  - Uncategorized

---
\[cs\_section style=&#8221;margin: 0px; padding: 45px 0px; &#8220;\]\[cs\_row style=&#8221;margin: 0px auto; padding: 0px; &#8221; inner\_container=&#8221;true&#8221;\]\[cs\_column style=&#8221;padding: 0px; &#8221; fade\_animation=&#8221;in&#8221; fade\_animation\_offset=&#8221;45px&#8221; fade\_duration=&#8221;750&#8243; type=&#8221;1/1&#8243;\]\[cs_text\]Windows 10 have a new UI that I personally find really useful (some people don&#8217;t), and although I have a Mac, I had to use Windows 10 for a project I&#8217;m running at the moment. I had a simple admin user<!--more-->but system didn&#8217;t allow me to open some files for security reasons and asked me to create a new user without administrator privileges.

  
I went straight into settings to create a new user. After going to Control PanelUser AccountsUser AccountsManage Accounts I clicked on Add someone else to this pc and nothing happened. No matter how many times I did a restart absolutely nothing happened.\[/cs\_text\]\[/cs\_column\]\[/cs\_row\]\[cs\_row style=&#8221;margin: 0px auto; padding: 0px; &#8221; inner\_container=&#8221;true&#8221;\]\[cs\_column style=&#8221;padding: 0px; &#8221; fade\_animation=&#8221;in&#8221; fade\_animation\_offset=&#8221;45px&#8221; fade\_duration=&#8221;750&#8243; type=&#8221;1/3&#8243;\]\[x\_image type=&#8221;none&#8221; src=&#8221;http://localhost/wp-content/uploads/2016/04/windos10-user.jpg&#8221; alt=&#8221;&#8221; link=&#8221;false&#8221; href=&#8221;#&#8221; title=&#8221;&#8221; target=&#8221;&#8221; info=&#8221;none&#8221; info\_place=&#8221;top&#8221; info\_trigger=&#8221;hover&#8221; info\_content=&#8221;&#8221;\]\[/cs\_column\]\[cs\_column style=&#8221;padding: 0px; &#8221; fade\_animation=&#8221;in&#8221; fade\_animation\_offset=&#8221;45px&#8221; fade\_duration=&#8221;750&#8243; type=&#8221;2/3&#8243;\][cs_text]On your home bar type **cmd** and right click on the Command Prompt option. Then select **Run as administrator**.

Next while your terminal is open and you have Admin rights type the following.\[/cs\_text\]\[/cs\_column\]\[/cs\_row\]\[cs\_row style=&#8221;margin: 0px auto; padding: 0px; &#8221; inner\_container=&#8221;true&#8221;\]\[cs\_column style=&#8221;padding: 0px; &#8221; fade\_animation=&#8221;in&#8221; fade\_animation\_offset=&#8221;45px&#8221; fade\_duration=&#8221;750&#8243; type=&#8221;1/1&#8243;\]\[x\_code\]net user &#8220;The Username you want&#8221; &#8220;The Password you want&#8221; /add\[/x\_code\]\[/cs\_column\]\[/cs\_row\]\[cs\_row style=&#8221;margin: 0px auto; padding: 0px; &#8221; inner\_container=&#8221;true&#8221;\]\[cs\_column style=&#8221;padding: 0px; &#8221; fade\_animation=&#8221;in&#8221; fade\_animation\_offset=&#8221;45px&#8221; fade\_duration=&#8221;750&#8243; type=&#8221;1/1&#8243;\]\[cs\_text\]For example let&#8217;s say I want to create a user named **Poki**, that has password **1234**. I will have to type:\[/cs\_text\]\[/cs\_column\]\[/cs\_row\]\[cs\_row style=&#8221;margin: 0px auto; padding: 0px; &#8221; inner\_container=&#8221;true&#8221;\]\[cs\_column style=&#8221;padding: 0px; &#8221; fade\_animation=&#8221;in&#8221; fade\_animation\_offset=&#8221;45px&#8221; fade\_duration=&#8221;750&#8243; type=&#8221;1/1&#8243;\]\[x\_code\]net user Poki 1234 /add\[/x\_code\]\[/cs\_column\]\[/cs\_row\]\[cs\_row style=&#8221;margin: 0px auto; padding: 0px; &#8221; inner\_container=&#8221;true&#8221;\]\[cs\_column style=&#8221;padding: 0px; &#8221; fade\_animation=&#8221;in&#8221; fade\_animation\_offset=&#8221;45px&#8221; fade\_duration=&#8221;750&#8243; type=&#8221;1/1&#8243;\]\[cs\_text\]This will create a user for you and when you log out, by using the credentials you entered earlier, you will be ready to log in as the new user.\[/cs\_text\]\[/cs\_column\]\[/cs\_row\]\[/cs\_section\]