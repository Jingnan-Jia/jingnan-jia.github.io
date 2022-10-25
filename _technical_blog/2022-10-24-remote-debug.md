---
title: 'Remote debugging'
date: 2022-10-24
tags:
  - PyCharm
  - VS Code
  - remote debugging
---

PyCharm and VS Code provide remote debugging features. Let's see how to implement it, respectively. 

Before continue, you need to know some knowledge on [ssh](https://jingnan-jia.github.io/technical_blog/2022-10-24-ssh/) from my previous blog.




# No gateway/proxy between local machine and remote machine

## PyCharm
Placeholder


## VS Code
Before remote development, we need to config the SSH for VS Code.
1. Install `remote development` extension.
2. In `remote explore`, click `SSH targets`
3. Click `config`, add the following code to SSH configeration file `XXX\.ssh\config` 
    ```bash
    Host remote1
      HostName remote-host-name
      User username
      IdentityFile XXX\.ssh\id_rsa
    ```
4. The `IdentityFile` path should be the private key path which was generated following [this blog](_technical_blog/2022-10-24-ssh.md) (If you have already generate the key in VS Code terminal, then you can remote this line)
5. The first connection may require password, after that you can connect remote machine without password.
  
The above content can also be found as the first chapter of [this blog](https://zhuanlan.zhihu.com/p/385073692).But the second part of this blog is too complex. Do not use it.

After we successfully connect to remote machine, we can open the remote directory/file using VS Code and run the code directly using the remote Python interpreter (`ctrl+shift+p` -> `Python: interpreter` to select your prefer interpreter).



# Gateway/proxy between local machine and remote machine

## PyCharm


## VS Code
The same process with the aforementioned No gateway method, the only thing we need to pay attention is to build password-less SSH connection via gateway following [this blog](https://pubappslu.atlassian.net/wiki/spaces/HPCWIKI/pages/37748788/Login+to+ALICE+or+SHARK+from+Linux#Making-logins-even-more-convenient-with-ssh-keys)
```bash
Host remote2
  HostName remote-host-name
  User username
  ProxyJump username@gateway-host-name:22
```