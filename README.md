# Project 7 - WordPress Pentesting

Time spent: **X** hours spent in total

> Objective: Find, analyze, recreate, and document **five vulnerabilities** affecting an old version of WordPress

## Pentesting Report

1. (Required) Vulnerability Name or ID: WordPress <= 4.2.2 - Authenticated Stored Cross-Site Scripting (XSS)
  - [ ] Summary: An attacker can use editor privaleges to inject web script using HTML code in a post.
    - Vulnerability types: XSS
    - Tested in version: 4.2
    - Fixed in version: 4.2.3
  - [ ] GIF Walkthrough: https://github.com/abrown681/cs4760/blob/master/Authenticated_Stored_Cross-Site_Scripting_(XSS).gif
  - [ ] Steps to recreate: As an author, create a post with the following html code: `"<a href="[caption code=">]</a><a title=" onmouseover=alert('test')  ">link</a>"`. Then, as an admin, hover over the link in the post. Once the admin hovers over the link, a javascript alert is executed and requires user action to disable.
  - [ ] Affected source code: 
    - [Link 1](https://klikki.fi/adv/wordpress3.html)
2. (Required) Vulnerability Name or ID: WordPress 2.5-4.6 - Authenticated Stored Cross-Site Scripting via Image Filename
  - [ ] Summary: An attacker can upload an image with a file name that contains the instructions necessary to inject malicious JavaScript code into the web broswer.
    - Vulnerability types: XSS
    - Tested in version: 4.2
    - Fixed in version: 4.6.1
  - [ ] GIF Walkthrough: https://github.com/abrown681/cs4760/blob/master/File_Names_Cross-Site_Scripting_(XSS).gif
  - [ ] Steps to recreate: As an admin, upload an image with the following filename: `cengizhansahinsumofpwn<img src=a onerror=alert(document.cookie)>.jpg` using a proxy. Then, navigate to the post as a viewer (in my case, I went to http://wpdistillery.vm/cengizhansahinsumofpwn/), which will cause the JavaScript code in the file name to be executed without the user's consent.
  - [ ] Affected source code:
    - [Link 2](https://sumofpwn.nl/advisory/2016/persistent_cross_site_scripting_vulnerability_in_wordpress_due_to_unsafe_processing_of_file_names.html)
3. (Required) Vulnerability Name or ID: WordPress <= 4.2 - Unauthenticated Stored Cross-Site Scripting (XSS)
  - [ ] Summary: Any type of user can inject JavaScript code into WordPress post comment and cause certain functionality to be disabled (including making links un-clickable) when the comment is viewed by an admin.
    - Vulnerability types: XSS
    - Tested in version: 4.2
    - Fixed in version: 4.2.1
  - [ ] GIF Walkthrough: 
  - [ ] Steps to recreate: As any type of non-admin user, go to a post and create a comment using the following text: `<a title='x onmouseover=alert(unescape(/hello%20world/.source)) style=position:absolute;left:0;top:0;width:5000px;height:5000px  AAAAAAAAAAAA...[64 kb]..AAA'></a>`
  - [ ] Affected source code:
    - [Link 3](https://klikki.fi/adv/wordpress2.html)

## Assets

List any additional assets, such as scripts or files

## Resources

- [WordPress Source Browser](https://core.trac.wordpress.org/browser/)
- [WordPress Developer Reference](https://developer.wordpress.org/reference/)

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
