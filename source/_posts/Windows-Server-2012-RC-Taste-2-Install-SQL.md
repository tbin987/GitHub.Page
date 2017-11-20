---
title: Windows Server 2012 RC 嘗鮮 (2) 安裝SQL
tags:
  - SQL Server
  - SQL Server 2012
  - Windows Server 2012
categories: 技術分享
permalink: windows-server-2012-rc-taste-2-to-instal-sql
date: 2012-07-03 22:57:00
---

Server安裝完後，最重要的就是要安裝一些伺服器應用程式了，剛好，微軟這時同時也發布了好幾項產品，例如Visual Studio 2012 RC以及Team Foundation Server 2012 RC，所以剛裝好的Windows Server 2012 RC就可以拿來裝上TFS來玩玩囉。

在安裝TFS之前，首先要安裝的是SQL Server，雖然TFS預設會安裝上SQL Server Express，但預設並不會裝上管理工具，所以只好自己手動來安裝了。

<!-- more -->

在Server 2012安裝SQL Server其實沒甚麼兩樣，基本上大部分[下一步] 按到底就可以了：

選擇要安裝的元件，因為這裡裝的是SQL Server Express with Advanced Services，所以有管理工具以及報表服務可以選。 

<div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-LCk4MEjpves/T_MAOlSuZuI/AAAAAAAACa4/OqknEDnaVlU/s320/20120701160820.png)](http://2.bp.blogspot.com/-LCk4MEjpves/T_MAOlSuZuI/AAAAAAAACa4/OqknEDnaVlU/s1600/20120701160820.png)</div>
設定執行個體名稱以及實體路徑。 

<div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-zNkH8WQT0pA/T_MAOXXmPpI/AAAAAAAACaw/QZdzyxxe3Go/s320/20120701160851.png)](http://4.bp.blogspot.com/-zNkH8WQT0pA/T_MAOXXmPpI/AAAAAAAACaw/QZdzyxxe3Go/s1600/20120701160851.png)</div>
設定服務帳號。 

<div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-2RD1g_XcZfg/T_MAOUXXR4I/AAAAAAAACa0/CLij9NLko-Y/s320/20120701160909.png)](http://2.bp.blogspot.com/-2RD1g_XcZfg/T_MAOUXXR4I/AAAAAAAACa0/CLij9NLko-Y/s1600/20120701160909.png)</div>
設定驗證模式，預設為Windows驗證模式，這裡改用混合式驗證。 

[](http://3.bp.blogspot.com/-Za_acvFXOMw/T_MAPlbQMDI/AAAAAAAACbI/Mqgmg2DfXzE/s1600/20120701160927.png) 
<div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/--yRfGbLmE8c/T_MAP7dhzvI/AAAAAAAACbM/t9B3yfAk7DU/s320/20120701161143.png)](http://3.bp.blogspot.com/--yRfGbLmE8c/T_MAP7dhzvI/AAAAAAAACbM/t9B3yfAk7DU/s1600/20120701161143.png)</div>
設定報表服務，這裡先不做設定。 

<div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/--aSOBpAEir4/T_MAQcC66nI/AAAAAAAACbQ/lhicSEC5X70/s320/20120701161152.png)](http://1.bp.blogspot.com/--aSOBpAEir4/T_MAQcC66nI/AAAAAAAACbQ/lhicSEC5X70/s1600/20120701161152.png)</div>
錯誤報告功能，依個人喜好設定，按下[下一步]就開始安裝囉。 

<div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-OB3fRc32HLM/T_MAQ7dJzmI/AAAAAAAACbU/oZGvOa8GZGg/s320/20120701161158.png)](http://4.bp.blogspot.com/-OB3fRc32HLM/T_MAQ7dJzmI/AAAAAAAACbU/oZGvOa8GZGg/s1600/20120701161158.png)</div>
&nbsp;安裝完成。

<div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-BhwmPdKN7Qg/T_MAR86c0sI/AAAAAAAACbo/WrSr_hJ71Rw/s320/20120701164153.png)](http://2.bp.blogspot.com/-BhwmPdKN7Qg/T_MAR86c0sI/AAAAAAAACbo/WrSr_hJ71Rw/s1600/20120701164153.png)</div>
不得不說，Server 2012把開始功能表改成Metro介面後，安裝完軟體開始畫面就變成這副德行： 

<div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-0JkE8r9ort8/T_MASjGvs-I/AAAAAAAACbs/mc6YwDejAPk/s320/20120701164220.png)](http://4.bp.blogspot.com/-0JkE8r9ort8/T_MASjGvs-I/AAAAAAAACbs/mc6YwDejAPk/s1600/20120701164220.png)</div>
若不想讓項目太多的話，對想要隱藏的項目按滑鼠右鍵，選取"從[開始]畫面取消釘選"就可以把該項目隱藏啦，之後可以對開始畫面按滑鼠右鍵，點選右下角的"所有應用程式"就可以叫出來囉。

<div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-H5LSeXPYrGg/T_MF1DgRrBI/AAAAAAAACgA/M6IRRWO2x2M/s320/20120703224624.png)](http://3.bp.blogspot.com/-H5LSeXPYrGg/T_MF1DgRrBI/AAAAAAAACgA/M6IRRWO2x2M/s1600/20120703224624.png)</div>

這部分微軟真的該再修改一下，不然每次安裝完軟體都要手動一個個隱藏，以往開始功能表的資料夾歸檔的設計就被浪費了。雖然這樣是符合平板/手機的使用模式，但我們現在用的還是一般電腦甚至伺服器吧，某些操作並不是在任何裝置都可以適用的。

下一篇再來安裝Team Foundation Server 2012 RC吧。

<span id="goog_270759061"></span><span id="goog_270759062"></span>