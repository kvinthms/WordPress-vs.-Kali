# Project 7 - WordPress Pentesting

Time spent: **X** hours spent in total

> Objective: Find, analyze, recreate, and document **five vulnerabilities** affecting an old version of WordPress

## Pentesting Report

1. (Required) Unauthenticated Stored Cross-Site Scripting (XSS)
  - [ ] Summary: Allows XSS through comments that are larger thab 64kb in size. MYSQL TEXT type only allows 64kb of data so overloaded this truncates text and creates malformed HTML on the page.
    - Vulnerability types: XSS
    - Tested in version: 4.2
    - Fixed in version: 4.2.1
  - [ ] GIF Walkthrough: ![](Exploit1.gif)
  - [ ] Steps to recreate: Create a comment with an alert that also contains comment text >64kb in size.
        ```
        <a title='x onmouseover=alert(unescape(/hello%20world/.source)) style=position:absolute;left:0;top:0;width:5000px;height:5000px  AAAAAAAAAAAA...[64 kb]..AAA'></a>
        ```
  - [ ] Affected source code: N/A - MYSQL Limitation

1. (Required) Authenticated Shortcode Tags Cross-Site Scripting (XSS)
  - [ ] Summary: Allows storing XSS in clickable links by bypassing WordPress HTML tag filters. This is accomplished by abusing the seperate handling of shortcode and HTML validation. This penetration can be done by anyone with the ability to create posts which is exacerbated by the fact that 4.2 contains a core WordPress vulnerability allowing unautherized users to create posts.
    - Vulnerability types: XSS
    - Tested in version: 4.2
    - Fixed in version: 4.2.5
  - [ ] GIF Walkthrough: ![](Exploit2.gif)
  - [ ] Steps to recreate: Create a post that contains the following code:
  ```
  TEST!!![caption width="1" caption='<a href="' ">]</a><a href="http://onMouseOver='alert(1)'">Click me</a>
  ```
  - [ ] Affected source code: Code handling HTML tags and shortcode filtering
    - [Link 1](https://github.com/WordPress/WordPress/commit/f72b21af23da6b6d54208e5c1d65ececdaa109c8)

1. (Required) Vulnerability Name or ID
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
- [Exploit 1 Information](https://wpvulndb.com/vulnerabilities/7945)
- [Exploit 1 Reference](https://klikki.fi/adv/wordpress2.html)
- [Exploit 2 Information](https://wpvulndb.com/vulnerabilities/8186)
- [Exploit 2 Reference](https://blog.checkpoint.com/2015/09/15/finding-vulnerabilities-in-core-wordpress-a-bug-hunters-trilogy-part-iii-ultimatum/)

GIFs created with [LiceCap](http://www.cockos.com/licecap/).

## Notes

Describe any challenges encountered while doing the work

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
