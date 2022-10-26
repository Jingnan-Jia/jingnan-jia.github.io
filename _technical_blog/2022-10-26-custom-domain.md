---
title: 'Set a custom domain for your github page based website'
tags:
  - DNS
---

You may think that `yourname.github.io` is not cool enough compared with `yourname.com`. No worries, we can change the domain.

**NOte**: the following steps could also be found on [official documentation](https://docs.github.com/cn/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site?platform=windows)


1. Buy your prefered domain. I bought it from [namecheap](https://www.namecheap.com/). I strongly recommend you to also buy the SSL which can make your website more safe by starting with `https` instead of `http`. Some browsers will alear **unsafe** if your website starts with `http`.
2. After you bought your domain, you can go to the setting of you repository `username.github.io`, click `Code and automation`-> `Pages` -> `Custom domain` -> enter `www.yourname.com` -> `Save`.
3. Set DNS. Go to your domain provider website [namecheap](https://www.namecheap.com/), for example. Go to `Dashboard` -> `manage` -> `Advanced DNS`, set DNS like the following figure. The IP address in the following screenshot is the IP address of github servers. You can also copy them from [the official documentation](https://docs.github.com/cn/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site?platform=windows#:~:text=To%20create%20A%20records%2C%20point%20your%20apex%20domain%20to%20the%20IP%20addresses%20for%20GitHub%20Pages)
   ![set_dns](/images/set_dns_provider.jpg)
5. Then you need to wait for several hours to 24 hours. You can check the DNS status on `setting` of your repository. It looks like the followinig figures. If it shows `unsuccessful`, you can try again.
   
   ![dns_checking](/images/dns_checking.jpg)

6. Set SSL. 
   
   SSL can change your domain from `http` to `https`, so that browser would think your website become `Safe`. Otherwise, your website would look like:
    ![ssl_unsafe](/images/unsafe_ssl.jpg)

   So how to set SSL? <s>`At first you need to buy it from your domain provider. After that you need to install and activate it.`</s> **DO NOT BUY SSL!** Because Github itself provides very simple method to achieve it. Just go to the `setting` of your repository `username.github.io`, click `Code and automation`-> `Pages` -> Check `Enforce HTTPS`. You may need to wait for several minutes to observe its influence, and you may see the layout of the whole website broke down during these minites. Please be patient and you will see the perfect performance finally.

