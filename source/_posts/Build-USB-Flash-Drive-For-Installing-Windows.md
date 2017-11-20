---
title: 建立用於安裝Windows的USB隨身碟
tags:
  - USB開機
  - Windows
categories: 技術分享
permalink: create-a-usb-flash-drive-to-instal-windows
date: 2012-11-04 22:42:00
---

在現今光碟機式微、USB隨身碟當道的情形下，使用USB隨身碟來當作安裝作業系統的媒介已經越來越普遍了，甚至連微軟自身都推出一支程式([Windows 7 USB/DVD download tool](http://www.microsoftstore.com/store/msstore/html/pbPage.Help_Win7_usbdvd_dwnTool))來將光碟轉入USB隨身碟，而利用USB隨身碟來安裝系統相對於使用光碟也有著不少的優點，在愈來愈多人詢問如何建立一支可以用來開機及安裝Windows的隨身碟的情況下，在這就將我製作的步驟寫下，讓有需求的人可以利用囉。
<!-- more -->

要建立可開機及安裝的USB隨身碟，網路上也流傳著許多不同的方法，我是使用[RMPrepUSB](http://www.rmprepusb.com/)這支程式來建立的，因為利用這支程式可以很簡單地客製化USB隨身碟，相容性也較高些，所以這方法就是目前的首選囉。

關於RMPrepUSB這支程式，官方網站有不少教學文章可以參考，我最初也是參考&nbsp;[Tutorial&nbsp;31](http://www.rmprepusb.com/tutorials/winiso)&nbsp;這篇文章來建立USB隨身碟的，但陸續又有許多強者研究出其他方法，所以現在用的已經改為 &nbsp;[Tutorial 43](http://www.rmprepusb.com/tutorials/firawiniso)&nbsp;的方式了，有興趣的可以參考下列教學：

*   [Tutorial 31 - Boot and install Windows 7 or Vista or Server 2008 (both 32 and 64 bit) from ISO files from a single bootable USB install drive](http://www.rmprepusb.com/tutorials/winiso)
*   [Tutorial 32 -&nbsp;Create a USB drive with multiple Vista/Win7/Server2008 install ISO files in 3 simple steps](http://www.rmprepusb.com/tutorials/multiisoimdiskautounattend)
*   [Tutorial 43 -&nbsp;Install Windows 8, Server 2012, Win 7, 2K8 &amp; Vista from multiple ISO files on the same Flash drive](http://www.rmprepusb.com/tutorials/firawiniso)
*   [Tutorial 30 -&nbsp;How to install XP onto a Hard Disk from an XP ISO on a bootable USB drive](http://www.rmprepusb.com/tutorials/install-xp-from-an-iso)

廢話不多說，下面就是建立USB開機隨身碟的步驟：

1\. 首先，到[RMPrepUSB](http://www.rmprepusb.com/documents/release-2-0)的官方網站下載最新版的軟體，並且安裝到系統中。

2\. 下載所需用到的 [Tut43_FiraIso.zip](http://www.rmprepusb.com/documents/rmprepusb-beta-versions/Tut43_FiraIso.zip?attredirects=0) 檔案([下載網頁](http://www.rmprepusb.com/documents/rmprepusb-beta-versions))，並將壓縮檔解壓至本機硬碟中(如：F:\BootUSB，以下稱"前置作業資料夾")
<div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-UQN0Y_Hh4_E/UJZoQQsYSpI/AAAAAAAAC8I/KCaqX0X9qNw/s1600/16.png)](http://2.bp.blogspot.com/-UQN0Y_Hh4_E/UJZoQQsYSpI/AAAAAAAAC8I/KCaqX0X9qNw/s1600/16.png)</div>

3\. 將要用來開機的Windows安裝光碟映像ISO檔準備好，並複製到[ISO]資料夾下。
[![](http://3.bp.blogspot.com/-O8sx57FgDq0/UJZpegtxcEI/AAAAAAAAC8Q/L-Di8-A5Q6M/s1600/17.png)](http://3.bp.blogspot.com/-O8sx57FgDq0/UJZpegtxcEI/AAAAAAAAC8Q/L-Di8-A5Q6M/s1600/17.png)

4\. 使用文字編輯器(如Notepad)開啟[Menu.lst]檔案，找到如下方所顯示的區段：

```
> title 1 INSTALL Windows 7 32-bit\nThis will install any edition of Windows 32-bit to your hard disk
> debug off
> set MYISO=win7.iso
> dd if=()/firadisk/au.xml of=()/AutoUnattend.xml
> dd if=()/firadisk/spaces.txt of=()/firadisk/ISONAME.CMD
> write ()/firadisk/ISONAME.CMD SET MYISO=\\iso\\%MYISO%\r\n
> map --mem (md)0x800+4 (99)
> map /ISO/%MYISO% (0xff)
> map (hd0) (hd1)
> map (hd1) (hd0)
> map --hook
> write (99) [FiraDisk]\nStartOptions=cdrom,vmem=find:/ISO/%MYISO%;\n\0
> chainloader (0xff)/BOOTMGR || chainloader (0xff)
```

{% note default %}
第一行title的地方是將來開機時所顯示的文字選項，修改成所要顯示的文字項目即可(此處對於中文的支援性不佳，為避免無法使用，故請輸入英文)；第三行"set MYISO=xxx.iso"，將"win7.iso"換成所要用來開機的ISO檔名。(此處以安裝Windwos 7/Vista為例，其他作業系統可參考RMPrepUSB官網或見後續說明)
{% endnote %}

{% note info %}
若要在USB中包含多個安裝ISO，可複製貼上上述區段，並修改黃底部分的文字即可，每個區段之間必須至少有一行空行。
{% endnote %}

{% note default %}
Menu.lst檔案的編輯，可以[搜尋grub4dos](http://lmgtfy.com/?q=grub4dos+menu.lst)或grub的說明。
{% endnote %}

5\. 做好前置作業後，將欲製作成開機磁碟的USB隨身碟插入USB連接埠，開啟RMPrepUSB軟體。
<div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-9iGsyNUKt7g/UJZlaMgeNfI/AAAAAAAAC6M/Ve2klwr26rw/s320/01.png)](http://3.bp.blogspot.com/-9iGsyNUKt7g/UJZlaMgeNfI/AAAAAAAAC6M/Ve2klwr26rw/s1600/01.png)</div>

6\. 在上方磁碟清單中選擇欲製作的那支USB隨身碟。

7\. 在[2.磁碟區標籤]輸入USB磁碟的標籤(選擇性項目，可不輸)；[3.開機選項]選擇"WinPE v2/WinPE v3/Vista/Win 7 bootable [BOOTMGR]"；[4.檔案系統和複寫]選擇"FAT32"，勾選"Boot as HDD (C: 2PTNS)"，(若ISO檔案大於4GB，檔案系統請選擇NTFS)；[5.如果勾選方塊...]點選[選擇複製資料夾]，選擇前置作業所放置檔案的資料夾(如：F:\BootUSB)

如果跳出如下的視窗，請選擇[是]繼續：
<div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-4zRLNPbN0So/UJZlaPepj1I/AAAAAAAAC6I/o6SSeX63RGE/s320/02.png)](http://4.bp.blogspot.com/-4zRLNPbN0So/UJZlaPepj1I/AAAAAAAAC6I/o6SSeX63RGE/s1600/02.png)</div>

8\. 完成後畫面將如下所示：
<div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-I7977t9si2M/UJZlaL6uPRI/AAAAAAAAC6Q/H7st7zESM84/s320/03.png)](http://3.bp.blogspot.com/-I7977t9si2M/UJZlaL6uPRI/AAAAAAAAC6Q/H7st7zESM84/s1600/03.png)</div>

9\. 接者，按下[6.準備磁碟]開始製作開機USB隨身碟。

10.首先是格式化磁碟，會跳出如下警告視窗，確認後點選[確定]繼續。
<div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-aCLROQUdWcE/UJZlanTrHmI/AAAAAAAAC6Y/5JafPmhXe0U/s320/04.png)](http://1.bp.blogspot.com/-aCLROQUdWcE/UJZlanTrHmI/AAAAAAAAC6Y/5JafPmhXe0U/s1600/04.png)</div>
<div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-F8IDcqkvu9o/UJZlbgAtBAI/AAAAAAAAC6o/x3skY3H627k/s320/05.png)](http://4.bp.blogspot.com/-F8IDcqkvu9o/UJZlbgAtBAI/AAAAAAAAC6o/x3skY3H627k/s1600/05.png)</div><div class="separator" style="clear: both; text-align: center;">
</div><div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-0IYSGvXOwAo/UJZlbP3OKcI/AAAAAAAAC6c/QcKze1ILjIE/s320/06.png)](http://1.bp.blogspot.com/-0IYSGvXOwAo/UJZlbP3OKcI/AAAAAAAAC6c/QcKze1ILjIE/s1600/06.png)</div>

11\. 當初線系統的複製視窗(如下圖)，請耐心等候複製完畢。(複製時間依檔案多寡及USB隨身碟的存取速度而異)
<div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-FaW8XIR9WLY/UJZlbizYnHI/AAAAAAAAC6k/_x1VBnLBipw/s320/07.png)](http://2.bp.blogspot.com/-FaW8XIR9WLY/UJZlbizYnHI/AAAAAAAAC6k/_x1VBnLBipw/s1600/07.png)</div>

12\. 複製完畢後，回到RMPrepUSB程式介面，點選[安裝 Grub4dos]，會跳出如下視窗，請點選[是]將grub4dos安裝在MBR。
<div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-2l0skzUoMpc/UJZldH6b7II/AAAAAAAAC7A/A6heczuJMnk/s320/09.png)](http://4.bp.blogspot.com/-2l0skzUoMpc/UJZldH6b7II/AAAAAAAAC7A/A6heczuJMnk/s1600/09.png)</div>
點選[確定]繼續安裝：
<div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-ZpZa9V6HBLQ/UJZldLciW0I/AAAAAAAAC68/M98bCNWqFUo/s320/10.png)](http://4.bp.blogspot.com/-ZpZa9V6HBLQ/UJZldLciW0I/AAAAAAAAC68/M98bCNWqFUo/s1600/10.png)</div>
按下鍵盤的[ENTER]鍵繼續：
<div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-anvIBLDp-iA/UJZldvpxyDI/AAAAAAAAC7E/Ylv5KIkAA9Q/s320/11.png)](http://2.bp.blogspot.com/-anvIBLDp-iA/UJZldvpxyDI/AAAAAAAAC7E/Ylv5KIkAA9Q/s1600/11.png)</div>
點選[確定]繼續：
<div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-_PokDhpxQLA/UJZle04f5eI/AAAAAAAAC7Y/_jtzt4Oa92Q/s1600/12.png)](http://2.bp.blogspot.com/-_PokDhpxQLA/UJZle04f5eI/AAAAAAAAC7Y/_jtzt4Oa92Q/s1600/12.png)</div>

13\. 至此，開機USB隨身碟已製作完成，使用檔案總管開啟USB磁碟後，會看到類似如下的結構：
<div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-mzis_t5HwEA/UJZliP1pLZI/AAAAAAAAC7g/6hHJZieUFPc/s320/13.png)](http://3.bp.blogspot.com/-mzis_t5HwEA/UJZliP1pLZI/AAAAAAAAC7g/6hHJZieUFPc/s1600/13.png)</div>

14\. 若要測試這支USB隨身碟是否可以正常運作，可以找台電腦，進入BIOS修改成以USB磁碟開機來測試，或是使用RMPrepUSB內含的QEMU來測試。要以QEMU來測試，點選[Test using QEMU Emulator (F11)]，當看到如下的畫面後，移動選擇光棒到開機項目按下[ENTER]進入開機安裝，若能正常進入安裝畫面，就表示製作成功。
<div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-3g8SJkjeQc4/UJZnCiZnZhI/AAAAAAAAC8A/EZUHuWNdbMQ/s320/15.png)](http://3.bp.blogspot.com/-3g8SJkjeQc4/UJZnCiZnZhI/AAAAAAAAC8A/EZUHuWNdbMQ/s1600/15.png)</div>

=======================================================================
進階用法

A. 使用USB隨身碟來安裝Windows XP

1\. 因為Windows XP的開機方式與Vista之後使用bootmgr的方式不同，所以若要製作Windows XP的開機磁碟，必須使用不同的步驟。(原始步驟請參考RMPrepUSB官網 [Tutorial 30](http://www.rmprepusb.com/tutorials/install-xp-from-an-iso))

2\. 將Windows XP的ISO檔案複製到前置作業的資料夾中(如：F:\BootUSB\WXP\XP.iso)

3\. 下載[winvblock.ima.gz](http://www.rmprepusb.com/documents/rmprepusb-beta-versions/winvblock.ima.gz?attredirects=0)檔案，並且放置在前置作業的資料夾中(如：F:\BootUSB\winvblock.ima.gz)

4\. 將下列語法加入Menu.lst當中：

```
> title Install Windows XP - STEP 1\nRemember press &lt;F6&gt; to load WinVBlock driver!!
> set MYISO=<span style="background-color: yellow;">XP.ISO</span>
> find --set-root --ignore-floppies --ignore-cd /winvblock.ima.gz
> map --mem /winvblock.ima.gz (fd0)
> map --mem /winvblock.ima.gz &nbsp;(fd1)
> # if this loads the ISO into memory slowly - then you need to run WinContig on the ISO file on your USB drive to speed it up!
> map &nbsp;/WXP/%MYISO% (0xff) || map &nbsp;--mem /WXP/%MYISO% (0xff)
> map (hd0) (hd1)
> map (hd1) (hd0)
> map --hook
> root (0xff)
> chainloader (0xff)&nbsp;> title &nbsp;&gt; Install Windows XP - STEP 2 (RAM &gt; 1GB)\nContinue to install Windows XP with RAM &gt; 1GB
> set MYISO=<span style="background-color: yellow;">XP.ISO</span>
> find --set-root --ignore-floppies --ignore-cd /winvblock.ima.gz
> # we must load the ISO into memory, so it will be slow to load here ...
> echo Loading...
> map --mem /WXP/%MYISO% (0xff) || map &nbsp;/WXP/%MYISO% (0xff)
> map (hd0) (hd1)
> map (hd1) (hd0)
> map --hook
> chainloader (hd0)+1
> pause Press ENTER and then unplug this USB drive...&nbsp;> title &nbsp;&gt; Install Windows XP - STEP 2 (RAM &lt; 1GB)\nContinue to install Windows XP with RAM &lt; 1GB
> set MYISO=<span style="background-color: yellow;">XP.ISO</span>
> map --mem /winvblock.ima.gz (fd0)
> map --mem /winvblock.ima.gz &nbsp;(fd1)
> map /WXP/%MYISO% (0xA0)
> checkrange 0x80 read 0x8280 &amp;&amp; map (hd0) (hd1)
> checkrange 0x80 read 0x8280 &amp;&amp; map (hd1) (hd0)
> map --hook
> map --rd-size=2048
> map --mem (rd)+4 (0x55)
> map --rehook
> write (0x55) #!GRUB4DOS\x00v=1\x00WXP/%MYISO%\x00\xA0\x00
> root (hd0,0)
> chainloader (hd0)+1
> pause Keep the USB drive connected until Setup completes!
```

5\. 當使用USB安裝Windows XP時，先選擇第一個項目開機，於XP安裝程式初始畫面時按下鍵盤的F6，載入"FiraDisk Driver"以正確識別USB磁碟。當第一次重開機後，再選擇第二或第三個項目繼續Windows XP的安裝。

B. 安裝Windows 8

1\. 安裝Windows 8可以使用如同安裝Windows 7的方式，但對於某些版本的Windows 8 ISO，必須輸入序號才能安裝(如Release Preview版本或Server 2012)，可利用修改自動應答檔案([FiraDisk\au.xml])來達成目的。

2\. 或是使用下列的語法：

```
> title Install Windows 8\nThis will install Windows 8 to your hard disk
> debug off
> set MYISO=WIN8.ISO
> dd if=()/firadisk/auWin8.xml of=()/AutoUnattend.xml
> dd if=()/firadisk/spaces.txt of=()/firadisk/ISONAME.CMD
> write ()/firadisk/ISONAME.CMD SET MYISO=\\iso\\%MYISO%\r\n
> map --mem (md)0x800+4 (99)
> map /ISO/%MYISO% (0xff)
> map (hd0) (hd1)
> map (hd1) (hd0)
> map --hook
> write (99) [FiraDisk]\nStartOptions=cdrom,vmem=find:/ISO/%MYISO%;\n\0
> chainloader (0xff)/BOOTMGR || chainloader (0xff)<div>
</div><div>開啟[FiraDisk\auWin8.xml]，修改下列區段，將&lt;Key&gt;換成正確的安裝序號</div><div>> &lt;UserData&gt;
> &lt;AcceptEula&gt;true&lt;/AcceptEula&gt;
> &lt;ProductKey&gt;
> &lt;Key&gt;<span style="background-color: yellow;">TK8TP-9JN6P-7X7WW-RFFTV-B7QPF</span>&lt;/Key&gt;
> &lt;/ProductKey&gt;
> &lt;/UserData&gt;</div><div>
</div>C. 使用Windows PE
```

1\. 若要使用以Windows Automated Installation Kit(WAIK)所建立的Windows PE環境開機，可以將建立出的檔案(如：BOOTMGR、[boot]、[sources]等)複製到前置作業資料夾，並於Menu.lst加入下列語法：

```
> title WinPE
> find --set-root /BOOTMGR
> chainloader /BOOTMGR
```
