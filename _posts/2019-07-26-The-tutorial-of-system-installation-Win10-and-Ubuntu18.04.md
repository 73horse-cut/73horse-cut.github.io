---
title:  "📕 The tutorial of system installation Win10 and Ubuntu18.04"
date:   2019-07-26 12:28:50 +0800
categories: "Advising"
tags: ["windows", "Ubuntu"]
---
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;There r so many errors while I following the way to install the Ubuntu on CSDN,and it made me so sad.So I decide to write something for others~

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;记得刚开始下决心那天匆匆忙忙找桂生在实验室搞了16.04的镜像，满怀信心地分了盘，重启疯狂按F2，选择U盘启动…… 一切操作是多么行云流水而又赏心悦目。说实话，其实第一次就安装成功了，只不过ubuntu安在了机械盘第一次开机慢，等了好久没有出现桌面…😭 我直接给关机卸掉了😭<br>

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;查找原因的时候看到一个老哥写经验帖搞了15遍装机，这么一想我13遍就搞明白了，他竟然搞了15遍🤭


# 其实坑确实有，列一下遇到的：
## 根目录/分配空间不足，装CUDA、Torch之后10G空间直接给沾满了？？<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;✋网上说的根目录装系统给10G，巴拉巴拉剩下的空间全给/home
[比如这个...](https://www.cnblogs.com/Duane/p/6776302.html)<br>

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;👍分盘的时候如果没有单独分配/usr会导致根目录文件很大，要么给根目录大空间，要么把/usr分出来也给够空间。

## 引导启动要分清，EFI/UEFI搞人心态！<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;✋网上步骤全是分盘的时候将/boot作为挂载，就是开机的时候ubuntu来引导win，这里问题不大，我也是这么下来的，然后网上步骤又很一致地告诉大家开机会直接进入win，只要安装  **EsayBCD** 这东西就可解决了，这里坑了我10遍不止…UEFI启动的电脑根本不起作用好吗？？你好歹推荐我个EasyUEFI啊…<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;👍开机按F2的时候注意下面一个图，UEFI启动的电脑一定要选择UEFI:USB FLASH DRIVE PMAP这一项555555555 还有卸载的时候也要把启动项里面的UBUNTU18给删掉~<br>

<figure>
  <img src="{{ site.baseurl }}/assets/images/190727image/1.jpg">
</figure>
## Ubuntu空间分配👌
- **/boot** - 400 MB ； 实际需求大约 100 ~ 200MB，就分400M,可以选择在固态里单独分这个boot，据说引导快？？反正我系统在机械也快不到哪去。
- **/**  &nbsp;&nbsp;- 35GB↑ ； 15-20 GB 对于大多数用户来说是一个比较合适的取值，python用的多就得大点喽~
- **/home** - 60G； 通常用于存放用户数据，下载的文件和媒体文件.
- **swap** - 自己电脑内存的两倍； 我是24G，交换空间用处暂时不明，我空间大任性。


## 参考文档
- [EFI](https://blog.csdn.net/qq_24624539/article/details/81775635)
- [UEFI](https://www.cnblogs.com/Duane/p/6776302.html)
