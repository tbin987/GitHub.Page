---
title: Windows Server 2012 RC 嘗鮮 (1) 安裝篇
tags:
  - Windows Server 2012
categories: 技術分享
permalink: windows-server-2012-rc-taste-1-instalation-articles
date: 2012-06-03 14:52:00
---

隨著Windows 8 Release Preview的發佈，Server版本也悄悄現身啦
<div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-tQ5x5TwusAg/T8r45qC9QMI/AAAAAAAACJo/1oq6Am67y0I/s320/20120603134242.png)](http://1.bp.blogspot.com/-tQ5x5TwusAg/T8r45qC9QMI/AAAAAAAACJo/1oq6Am67y0I/s1600/20120603134242.png)</div>[http://technet.microsoft.com/zh-tw/windowsserver/hh534429.aspx](http://technet.microsoft.com/zh-tw/windowsserver/hh534429.aspx)

<!-- more -->

同時發佈的還有期待已久的Visual Studio 2012 RC
<div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-5OemYKu4bws/T8r7SfXCHpI/AAAAAAAACJ8/JbfPkYCv3s0/s320/20120603135304.png)](http://3.bp.blogspot.com/-5OemYKu4bws/T8r7SfXCHpI/AAAAAAAACJ8/JbfPkYCv3s0/s1600/20120603135304.png)</div>[http://www.microsoft.com/visualstudio/11/zh-tw](http://www.microsoft.com/visualstudio/11/zh-tw)

Windows 8 已經有太多人玩了，再加上之前小玩過Developer Preview及Customer Preview，對於Windows 8沒什麼新鮮感，所以這次就來玩玩Server的版本囉。

首先就是從Technet Evaluation Center下載ISO檔案囉： 
<div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-LYQFLScIw9g/T8r80HYgc2I/AAAAAAAACKE/Ks9wLcYbMZM/s320/20120603134933.png)](http://3.bp.blogspot.com/-LYQFLScIw9g/T8r80HYgc2I/AAAAAAAACKE/Ks9wLcYbMZM/s1600/20120603134933.png)</div>
這次釋出的語言版本有12種，有支援正體中文喔！
資料填一填就開始下載了，下載的正體中文 ISO檔名為： 
8400.0.WINMAIN_WIN8RC.120518-1423_X64FRE_SERVER_ZH-TW-HRC_SSS_X64FRE_ZH-TW_DV5.ISO 

下載完當然就要開VM來安裝了，當然，Server 2012還太新，VMWare不認得是正常的，設定選擇Windows Server 2008 R2 x64就可以了
<div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-yh64XRJGkY0/T8r-K5USm1I/AAAAAAAACKM/xcqRlZ02BpM/s200/20120603140345.png)](http://3.bp.blogspot.com/-yh64XRJGkY0/T8r-K5USm1I/AAAAAAAACKM/xcqRlZ02BpM/s1600/20120603140345.png)</div>
<div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-RycTolO0XNs/T8r-K79n9pI/AAAAAAAACKQ/fkbQzgXIIyw/s200/20120603140528.png)](http://4.bp.blogspot.com/-RycTolO0XNs/T8r-K79n9pI/AAAAAAAACKQ/fkbQzgXIIyw/s1600/20120603140528.png)</div>
開始安裝囉
<div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-DYIDRS7Een0/T8r0zq1yFOI/AAAAAAAAB9I/J0VvoRxDaI4/s320/20120603120714.png)](http://2.bp.blogspot.com/-DYIDRS7Een0/T8r0zq1yFOI/AAAAAAAAB9I/J0VvoRxDaI4/s1600/20120603120714.png)</div>
<div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-1MYRYCpK2vs/T8r01B3aGoI/AAAAAAAAB9U/ISzUFSrK02g/s320/20120603120729.png)](http://3.bp.blogspot.com/-1MYRYCpK2vs/T8r01B3aGoI/AAAAAAAAB9U/ISzUFSrK02g/s1600/20120603120729.png)</div>
一開始的設定就跟安裝Windows&nbsp; 7或是Server 2008 R2一樣，選擇地區及語言選項後才會開始安裝

<div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-NgESov2BQTw/T8r02XsELkI/AAAAAAAAB9k/57GZFcW6f2Q/s320/20120603120803.png)](http://2.bp.blogspot.com/-NgESov2BQTw/T8r02XsELkI/AAAAAAAAB9k/57GZFcW6f2Q/s1600/20120603120803.png)</div>

<div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-ail1z9eEnSU/T8r03ghAGiI/AAAAAAAAB90/_tHRoommO3U/s320/20120603120838.png)](http://4.bp.blogspot.com/-ail1z9eEnSU/T8r03ghAGiI/AAAAAAAAB90/_tHRoommO3U/s1600/20120603120838.png)</div>
<div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-Ryqe1aW3GMA/T8r06BYHxiI/AAAAAAAAB-I/ymZf322eB2g/s320/20120603120904.png)](http://2.bp.blogspot.com/-Ryqe1aW3GMA/T8r06BYHxiI/AAAAAAAAB-I/ymZf322eB2g/s1600/20120603120904.png)</div>
Server 2012一樣提供有一般GUI版本以及Server Core 的選項可以選擇，不過在目前RC版只有Datacenter一種版本可以選擇

<div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-WFBtx_FivT8/T8r07i8SXlI/AAAAAAAAB-M/1zQKfQftkcg/s320/20120603120927.png)](http://4.bp.blogspot.com/-WFBtx_FivT8/T8r07i8SXlI/AAAAAAAAB-M/1zQKfQftkcg/s1600/20120603120927.png)</div>
<div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-oFfEHACOj2s/T8r08MqSYJI/AAAAAAAAB-U/iAuUgqWgaRI/s320/20120603120951.png)](http://4.bp.blogspot.com/-oFfEHACOj2s/T8r08MqSYJI/AAAAAAAAB-U/iAuUgqWgaRI/s1600/20120603120951.png)</div>
<div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-Jij4iRPj5-U/T8r0823PXBI/AAAAAAAAB-c/1lqsS2UI_48/s320/20120603121012.png)](http://4.bp.blogspot.com/-Jij4iRPj5-U/T8r0823PXBI/AAAAAAAAB-c/1lqsS2UI_48/s1600/20120603121012.png)</div>
因為是全新的VM，當然只能選自訂選項囉 

<div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-c79ppLAh8T4/T8r0-LMLnhI/AAAAAAAAB-s/FpmPMOgMNdg/s320/20120603121025.png)](http://4.bp.blogspot.com/-c79ppLAh8T4/T8r0-LMLnhI/AAAAAAAAB-s/FpmPMOgMNdg/s1600/20120603121025.png)</div>
<div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-A5IJCtKc0lg/T8r0-_9jraI/AAAAAAAAB-4/FjBHksTh_wk/s320/20120603121054.png)](http://4.bp.blogspot.com/-A5IJCtKc0lg/T8r0-_9jraI/AAAAAAAAB-4/FjBHksTh_wk/s1600/20120603121054.png)</div>
開始安裝 

<div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-4b5CfMerfwI/T8r0_zqJNVI/AAAAAAAAB_A/7Z1btJnm2eY/s320/20120603121107.png)](http://3.bp.blogspot.com/-4b5CfMerfwI/T8r0_zqJNVI/AAAAAAAAB_A/7Z1btJnm2eY/s1600/20120603121107.png)</div>
<div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-f78oNkc_kYE/T8r1B9EmcJI/AAAAAAAAB_M/7kPlncPjLG0/s320/20120603121913.png)](http://3.bp.blogspot.com/-f78oNkc_kYE/T8r1B9EmcJI/AAAAAAAAB_M/7kPlncPjLG0/s1600/20120603121913.png)</div>
<div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-kk35SJmAEj8/T8r1CXdir5I/AAAAAAAAB_U/g_D6uDr-gSE/s320/20120603121923.png)](http://4.bp.blogspot.com/-kk35SJmAEj8/T8r1CXdir5I/AAAAAAAAB_U/g_D6uDr-gSE/s1600/20120603121923.png)</div>
安裝還頗迅速的，這次VM的設定為C2D 1.86G單核心，2G RAM，從開始複製一直到第一次重新開機，只花了8分鐘左右 

<div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-INCfsYEt7Yo/T8r1DWnDQcI/AAAAAAAAB_o/5BiMoCdfV54/s320/20120603122014.png)](http://2.bp.blogspot.com/-INCfsYEt7Yo/T8r1DWnDQcI/AAAAAAAAB_o/5BiMoCdfV54/s1600/20120603122014.png)</div>
第一次進入系統，修先要設定的是管理員密碼，從這開始，畫面就開始為Metro風格的UI了 

<div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-CPv-0lHm5Cg/T8r1IqzbjEI/AAAAAAAACAM/mcZ3Sq6XNok/s320/20120603122418.png)](http://1.bp.blogspot.com/-CPv-0lHm5Cg/T8r1IqzbjEI/AAAAAAAACAM/mcZ3Sq6XNok/s1600/20120603122418.png)</div>
密碼欄位如同手機系統一樣，有個可以暫時顯示密碼的功能 

<div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-4J7DGja7EEY/T8r1J45wYUI/AAAAAAAACAY/ngqcmHwxGsI/s320/20120603122457.png)](http://3.bp.blogspot.com/-4J7DGja7EEY/T8r1J45wYUI/AAAAAAAACAY/ngqcmHwxGsI/s1600/20120603122457.png)</div>
<div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-5NBArsGnt5w/T8r1KWnGMEI/AAAAAAAACAg/UvUsjBEBHuY/s320/20120603122537.png)](http://2.bp.blogspot.com/-5NBArsGnt5w/T8r1KWnGMEI/AAAAAAAACAg/UvUsjBEBHuY/s1600/20120603122537.png)</div>
設定完成，開始進入系統。Server系統免不了一開始要按下[Ctrl]+[Alt]+[Del]，只是這畫面乍看之下還以為是手機或平板的畫面，微軟真的是鐵了心要把所有系統 的介面都統一，至於結果如何就再觀察囉

<div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-WUYnCcbpj8o/T8r1LLSyNWI/AAAAAAAACAo/G0hDpd_O-eU/s320/20120603122806.png)](http://2.bp.blogspot.com/-WUYnCcbpj8o/T8r1LLSyNWI/AAAAAAAACAo/G0hDpd_O-eU/s1600/20120603122806.png)</div>
<div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-W21VWafivok/T8r1L-cm4JI/AAAAAAAACA0/d8_sCaU0lzo/s320/20120603122832.png)](http://2.bp.blogspot.com/-W21VWafivok/T8r1L-cm4JI/AAAAAAAACA0/d8_sCaU0lzo/s1600/20120603122832.png)</div>
<div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-04eCi9Ct44E/T8r1NCLzIsI/AAAAAAAACA4/LXbPWNLqVmc/s320/20120603122900.png)](http://3.bp.blogspot.com/-04eCi9Ct44E/T8r1NCLzIsI/AAAAAAAACA4/LXbPWNLqVmc/s1600/20120603122900.png)</div>
<div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-b4weQILTpZ4/T8r1NoACF5I/AAAAAAAACBA/NcQG4akmg-0/s320/20120603122932.png)](http://2.bp.blogspot.com/-b4weQILTpZ4/T8r1NoACF5I/AAAAAAAACBA/NcQG4akmg-0/s1600/20120603122932.png)</div>
<div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-cuinnAhUvCw/T8r1ORVe82I/AAAAAAAACBI/Sk8tU7bEVMU/s320/20120603122943.png)](http://1.bp.blogspot.com/-cuinnAhUvCw/T8r1ORVe82I/AAAAAAAACBI/Sk8tU7bEVMU/s1600/20120603122943.png)</div>
經過一段時間的載入設定後，終於進入桌面啦，這裡就還蠻像Windows 7 / Server 2008 R2的傳統桌面，唯一比較不同的就是[開始]按鈕不見啦

<div class="separator" style="clear: both; text-align: center;"></div><div class="separator" style="clear: both; text-align: center;"></div><div class="separator" style="clear: both; text-align: center;"></div><div class="separator" style="clear: both; text-align: center;"></div><div class="separator" style="clear: both; text-align: center;"></div><div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-jrlXyuX3Naw/T8r1P9l2jXI/AAAAAAAACBY/_5DuHQBGKCg/s320/20120603123023.png)](http://1.bp.blogspot.com/-jrlXyuX3Naw/T8r1P9l2jXI/AAAAAAAACBY/_5DuHQBGKCg/s1600/20120603123023.png)</div><div class="separator" style="clear: both; text-align: center;"></div><div class="separator" style="clear: both; text-align: center;"></div>
目前釋出的RC版本號為6.2.8400

<div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-pDzZmdVTDpY/T8r16vuCcGI/AAAAAAAACHU/FNFZjK0aTl0/s320/20120603124913.png)](http://1.bp.blogspot.com/-pDzZmdVTDpY/T8r16vuCcGI/AAAAAAAACHU/FNFZjK0aTl0/s1600/20120603124913.png)</div>
Windows Server 2012的安裝就到這裡，後續操作就待下篇繼續。