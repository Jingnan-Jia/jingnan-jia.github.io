---
title: How to get the fiel creation or docification time with seconds?
tags:
  - Python
---

I want to get the fiel creation or docification time **with seconds!!!**

In windows, it seems impossible to see the exect time in Windows explorer, because it only shows the date and hour and minutes, missing the seconds!

Luckily, we have Python!

```
modified = os.path.getmtime(file)
print("Date modified: "+time.ctime(modified))
print("Date modified:",datetime.datetime.fromtimestamp(modified))

# out: 
# Date modified: Tue Apr 21 11:50:46 2015
# Date modified: 2015-04-21 11:50:46


```