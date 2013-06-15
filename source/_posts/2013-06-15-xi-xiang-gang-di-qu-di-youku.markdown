---
layout: post
title: "係香港地區睇youku"
date: 2013-06-15 19:02
comments: true
categories: ["chrome-extension", "tools"]
---

之前我發覺成日都有這個播唔到的地區問題


{% img left /images/blog/chinaban.png 600 600 'image' 'Location Banned' %}
今日發現係香港係可以睇YOUKU 土豆的。
解決方法係用CHROME EXTENSION

https://chrome.google.com/webstore/detail/unblock-youku/pdnfnkhpgegpcingjbfihlkjeighnddk?hl=zh-TW

這樣子就可以解決地區播放問題了！

source code:
https://github.com/whuhacker/Unblock-Youku

佢應該係把HTTP HEADER 個IP ADDRESS 換成中國的IP，這樣子就可以扮係係中國播快了！

``` javascript Modify X-Forwarded-For HTTP header https://github.com/whuhacker/Unblock-Youku/blob/master/chrome/header.js github link
function lite_header_modifier(details) {
  details.requestHeaders.push({
          name: 'X-Forwarded-For',
                 value: unblock_youku.ip_addr
          });
  return {requestHeaders: details.requestHeaders};
}
```


``` javascript Using China IP prefix https://github.com/whuhacker/Unblock-Youku/blob/master/shared/tools.js github link

function new_random_ip() {
      var ip_addr = '220.181.111.';
          ip_addr += Math.floor(Math.random() * 254 + 1); // 1 ~ 254
      return ip_addr;
}

```

