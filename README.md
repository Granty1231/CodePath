# Project 7 - WordPress Pentesting

Time spent: **7** hours spent in total (including setup)

> Objective: Find, analyze, recreate, and document **five vulnerabilities** affecting an old version of WordPress

## Pentesting Report

1. (Required) Authenticated Stored Cross-Site Scripting (XSS)
  - [X] Summary: Wordpress 4.2 allows for XSS through forcing a style attribute elements into a link. This vulnerability can be exploited using either a post or page element by contributors to attack administrators.
    - Vulnerability types: Cross-Site Scripting (XSS)
    - Tested in version: 4.2
    - Fixed in version: 4.2.3
  - [X] GIF Walkthrough: 
  - [X] Steps to recreate: One needs to post a link element on a page or post and add a style attribute holding a JS element. For example: <a href="[caption code=">]</a><a title=" onmouseover=alert('test')  ">link</a>. When the page is viewed, hovering over the link will generate a js alert.
  - [X] Affected source code: Vulnerability comes from poor validating of style attribute elements
    - [Link 1] https://wpvulndb.com/vulnerabilities/8111
    - [Link 2] https://klikki.fi/adv/wordpress3.html 
2. (Required) Authenticated Stored Cross-Site Scripting (XSS)
  - [X] Summary: WP 4.2 allows for the inclusion of XSS in the form of a JS alerts on pages through putting the JS in a SVG tag.
    - Vulnerability types: Cross-Site Scripting (XSS)
    - Tested in version: 4.2
    - Fixed in version: 4.2.6
  - [X] GIF Walkthrough: 
  - [X] Steps to recreate: Open a new page, post "http://www.example.com/wp-admin/customize.php?theme=<svg onload=alert(1)> (source: https://twitter.com/brutelogic/status/685105483397619713)" into the page to allow for a script to load in the SVG tag. Go to main page and the JS alert will run onloading the modified page.
  - [X] Affected source code:
    - [Link 1] (https://github.com/WordPress/WordPress/commit/7ab65139c6838910426567849c7abed723932b87)
3. (Required) Authenticated Shortcode Tags Cross-Site Scripting (XSS)
  - [X] Summary: WordPress allows for users to attach links to scripts within the shortcode tags of links on pages/posts. By including a link to a script in the caption for a link, I was able to get the site to generate a JS alert on hover over the link.
    - Vulnerability types: Cross-Site Scripting (XSS)
    - Tested in version: 4.2
    - Fixed in version: 4.2.5
  - [X] GIF Walkthrough: <img src="https://github.com/Granty1231/CodePath/blob/master/cpweek7-1.gif" width="800"> 
  - [X] Steps to recreate: 1. Go to the creation of a new page on the wordpress site. 2. Post the following script in the page body: TEST!!![caption width="1" caption='<a href="' ">]</a><a href="http://onMouseOver='alert(1)'">Click me</a>. 3. Upon saving, the page should have click me underlined which will trigger the alert upon hovering over the link. 
  - [X] Affected source code:
    - [Link 1] https://blog.checkpoint.com/2015/09/15/finding-vulnerabilities-in-core-wordpress-a-bug-hunters-trilogy-part-iii-ultimatum/
    - [Link 2] https://wpvulndb.com/vulnerabilities/8186
1. (Optional) Vulnerability Name or ID
  - [ ] Summary: 
    - Vulnerability types:
    - Tested in version:
    - Fixed in version: 
  - [ ] GIF Walkthrough: 
  - [ ] Steps to recreate: 
  - [ ] Affected source code:
    - [Link 1](https://core.trac.wordpress.org/browser/tags/version/src/source_file.php)
1. (Optional) Vulnerability Name or ID
  - [ ] Summary: 
    - Vulnerability types:
    - Tested in version:
    - Fixed in version: 
  - [ ] GIF Walkthrough: 
  - [ ] Steps to recreate: 
  - [ ] Affected source code:
    - [Link 1](https://core.trac.wordpress.org/browser/tags/version/src/source_file.php) 

## Assets

List any additional assets, such as scripts or files

## Resources

- [WordPress Source Browser](https://core.trac.wordpress.org/browser/)
- [WordPress Developer Reference](https://developer.wordpress.org/reference/)

GIFs created with [LiceCap](http://www.cockos.com/licecap/).

## Notes

One of the hardest parts was setting up the environment to begin checking exploits. Authentications on my host pc required a manual modification of my config.yml and hosts file to access wpdistillery.vm after runnign vagrant to create the instance.

## License

    Copyright [yyyy] [name of copyright owner]

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

        http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.
