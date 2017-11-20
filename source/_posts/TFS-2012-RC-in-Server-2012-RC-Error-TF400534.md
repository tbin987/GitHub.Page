---
title: TFS 2012 RC in Server 2012 RC - Error TF400534
tags:
  - Team Foundation Server
  - Windows Server 2012
categories: 技術分享
permalink: tfs-2012-rc-in-server-2012-rc-eror-tf40534
date: 2012-07-07 19:28:00
---

在Windows Server 2012 RC上安裝Team Foundation Server 2012 RC時，在一開始安裝就出現錯誤：

Error : TF400534: 封裝(tfs_objectmodel_x64_lang) 快取失敗，狀態為: 0x80092009。
Error : TF400166: 封裝快取失敗。 如需詳細資訊，請查閱個別封裝的快取錯誤。

<!-- more -->
<div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-9TH0B_VnON0/T_MAbcVMckI/AAAAAAAACb8/qdqCFC2i_OU/s320/20120701175107.png)](http://1.bp.blogspot.com/-9TH0B_VnON0/T_MAbcVMckI/AAAAAAAACb8/qdqCFC2i_OU/s1600/20120701175107.png)</div>
不管重新安裝多少次還是出現一樣的錯誤，重抓ISO安裝檔回來試也一樣。後來開啟Windows Uodate，找到兩個更新：KB2718791、KB2718704，看了一下說明，禍首應該就是KB2718704，安裝封裝的憑證問題。

<div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-i3CeiEvbYJs/T_MAhsISJrI/AAAAAAAACcQ/jJiHIGHM0U4/s320/20120701190155.png)](http://3.bp.blogspot.com/-i3CeiEvbYJs/T_MAhsISJrI/AAAAAAAACcQ/jJiHIGHM0U4/s1600/20120701190155.png)</div>
裝了這兩個更新後，再執行TFS的安裝程式就正常了。