---
title: Use Cloudflare to accelerate your website hosted on GitHub
tags:
  - Github
  - Website
  - Tutorial
---

Some of my friends in mainland of China complained that they could not visit my website fluently. I need to do something to solve it!

Actually, I have tried to use Gitee or Coding (Chinese GitHub) to backup my current website and use soome technique to forward the visits to Gitee/Coding or GitHub according to the visitors' location. However, Gitee and Coding is not free and they are not stable. The worse thing is that I have to push my code to Gitee/Coding and GitHub for each update of my website.

So I decided to accelerate my website using Cloudflare. It is free and stable.

Now lets see the steps.

1. Register your account at https://dash.cloudflare.com/
2. Select the 'free plan' to accelerate your website.
3. Enter your website domain (e.g. domain-name.com) without any 'https' or 'www'.
4. "continue", then you will see the screenshot below:
![](/images/cloudflare.png)
5. Go to your domain's provider website (mine is 'namespace'), add the nameservers proveded by 'cloudflare' to it.
![](/images/nameserver.png)

6. I found that aftet the above 5 steps, our website cannot be visited at all. ERRO is "too many redirects ...". Let me research the reason.
7. The reason is that my github setting checked the 'SSL' which means taht all http://user-domain.com wil be redirected to https://user-domain.com. But Cloudflare only receive http domans. So I unchecked the 'SSL' in github. But the website is still not available. 'too many redirects' still exists.
8. No worries. Go to Cloudflare, finish its 4-step beginers' guide to make your website safer and faster. Sorry I forgot to take a screenshot duirng I did that. After that, you can invite your Chinese friends to visit your website to see if it works.

References:

1. https://www.sdwebseo.com/cloudflare/
2. https://community.cloudflare.com/t/community-tip-fixing-err-too-many-redirects/42335
3. https://www.sdwebseo.com/cloudflare/
4. https://developers.cloudflare.com/ssl/troubleshooting/too-many-redirects/#:~:text=Redirect%20loops%20will%20occur%20if,all%20HTTP%20requests%20to%20HTTPS.&text=To%20solve%20this%20issue%2C%20either,configured%20at%20your%20origin%20server).