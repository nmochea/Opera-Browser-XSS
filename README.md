## Opera Browser Reflected (XSS)

I’m glad you’re here. Please have fun reading and don’t forget to connect with my social media [Facebook](https://facebook.com/neilmark.ochea.54) and [Twitter](https://twitter.com/phclownx).


This post is about an Reflected XSS that I found on Opera Browser Application which could have been used to get cookies and read file logs.



While using opera browser apk I noticed something strange the address bar in opera browser replaced by the reader mode and the web title added without any filter, I know that I can trigger the xss in reader mode but i dont know where so this my conclusion visit the website with xss payload and click the reader mode then xss will trigger.


I was on the website I looked in reader mode but it did not show up hmm wtf so i looked another website, again, again but still not showing up the reader mode, I would have given up but an idea entered my mind what if I compose my own payload and that is what I will read in reader mode maybe the xss payload trigger, so what site i can compose my payload and then i remember about google calendar you can write title and description its perfect for what I’m looking for.


## Step to Reproduce
* Open opera browser and go to
```
https://calendar.google.com/calendar/u/0/r?pli=1 
```
* Create a new task with following payload

**Title**
```html
“><img src=x onerror=alert(1);
```
**Description**
```html
<head>
</head> 
<body>
</body>
```
* Then save the task then click the task and send it to your gmail.
* Goto inbox open the message and copy the message id from url address.
* Insert the message id to this link
```
https://mail.google.com/mail/u/0/?source=sync&tf=1&view=pt&th=[ID]&search=all&msg=[ID]
```
* Paste the link to the new tab and go, from the right top header click the reader mode then the xss will trigger.

[![Proof of Concepts](https://share.gifyoutube.com/RO4NwK.gif)](https://www.youtube.com/watch?v=vBAzBQ2-n0E)


## Hall of Fame
I'm added to Opera Security Hall of Fame in 2020
[List of Hall of Fame](https://security.opera.com/hall-of-fame/)

## Vulnerability Disclosure
| Date | Contact |
| ----------- | ----------- |
| September 23, 2020 | I emailed Opera Security Team regarding this vulnerability issue. |
| September 25, 2020 | I provided additional details and some screenshot as proof of concepts. |
| September 29, 2020 | The Opera Browser released an updated, the security team emailed me that the vulnerability has been fixed and ask me to reproduce again to confirmed the fixed. |
