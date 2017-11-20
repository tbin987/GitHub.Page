---
title: SQL 資料庫評估
tags:
  - Access
  - LocalDB
  - SQL CE
  - SQL Server
  - SQLite
  - 資料庫
categories: 技術分享
permalink: sql-database-evaluation
date: 2012-05-07 00:05:00
---

在用了許久的ADO with Access之後，有感於這種資料庫的限制及困擾，一直以來都在尋找替代方案。因了原本接手開發的軟體在資料庫這塊一直都是雜亂且散佈於各模組內，雖然有想用其他的資料庫取而代之，但是更改底層資料庫不是件簡單的事，就只好一直沿用了。

而今，即將開發一全新系統，想當然爾對於要採用的資料庫的評估就是件很重要的事了。因為即將要開發的系統是運作在32位元Windows底下，所以就針對幾項常見的資料庫，做了個簡單的評估：

*   Access
*   SQL Server
*   SQL Server Express
*   SQL Server Compact Edition (SQL CE)
*   SQL Server LocalDB
*   SQLite
<!-- more -->

<span style="font-size: large;">Access</span>

Access一直以來都是開發人員在開發簡單的單機程式所會採用的資料庫之一，因為有著一個還算好用的UI介面，加上早期微軟對其的支援，而且大多數在不需要安裝額外軟體的情況下都可以存取，使得Access資料庫的使用率都不算低，簡單歸納優缺點如下：

*   優點

*   缺點

<span style="font-size: large;">SQL Server</span>

<span style="font-size: large;"><span style="font-size: small;">SQL Server是近年來微軟主推的資料庫系統，已慢慢整合進微軟大多數的開發工具內，也是現今許多伺服器主機所使用的資料庫系統。</span></span>

*   優點

*   缺點<span style="font-size: large;"><span style="font-size: small;">&nbsp;SQL Server是一套很完善的資料庫系統，但也因為支援的功能多，運作所需的資源相對的也很多，若是僅拿來作為本機獨立運作所需的資料庫系統就顯得大材小用了。</span></span>

<span style="font-size: large;">SQL Server Express</span>

<span style="font-size: large;"><span style="font-size: small;">SQL Server Express是微軟提供的較精簡的資料庫系統，基本上大多SQL Server提供的功能在Express版本上都有支援，只是附屬的功能較為簡化，但大多常用的都完整支援了。</span></span>

*   優點

*   缺點<span style="font-size: large;"><span style="font-size: small;">
</span></span>
<span style="font-size: large;"><span style="font-size: small;">SQL Server Express拿來做為一個需要資料庫的系統是很足夠的，不僅支援大多數SQL Server的功能，而且還是免費使用，當系統發展擴大後還可升級為完整的SQL Server版本。但對於僅用來儲存資料的本機軟體而言，Express還是過於龐大了。</span></span>

<span style="font-size: large;">SQL Server LocalDB<span style="font-size: small;">&nbsp;</span></span>

<span style="font-size: large;"><span style="font-size: small;">SQL Server LocalDB是微軟提供的更為精簡的資料庫系統，主要目的是提供給開發人員一個簡易的資料庫系統，不用去處理SQL Server Express以上版本所需的DBA資料庫管理等事項，可以僅專注在開發與資料上，相對的許多功能都被拿掉或精簡了，但大多數基本的SQL是都有支援的。</span></span>

*   優點

*   缺點<span style="font-size: large;"><span style="font-size: small;">
</span></span>
<span style="font-size: large;"><span style="font-size: small;">SQL Server LocalDB拿來做為一個僅需要資料庫作為儲存的系統是很足夠且適合的，支援了基本的SQL Server功能，也是免費使用，當系統發展擴大後可升級為SQL Server Express版本。 </span></span>

<span style="font-size: large;">SQL Server Compact Edition<span style="font-size: small;">&nbsp;</span></span>

<span style="font-size: large;"><span style="font-size: small;">SQL Server Compact Edition (SQL CE)是微軟提供作為行動裝置及嵌入式系統所用的精簡資料庫系統，具備基本的RDBMS支援，可將資料庫系統包含於開發的軟體中。</span></span>

*   優點

*   缺點

<span style="font-size: large;">SQLite<span style="font-size: small;">&nbsp;</span></span>

<span style="font-size: large;"><span style="font-size: small;">SQLite是一個開放原始碼的嵌入式精簡資料庫系統，具備SQL-92支援，可將資料庫系統包含於開發的軟體中，目前也獲得許多軟體及系統採用。</span></span>

*   優點

*   缺點

<span style="font-size: large;">小結</span>

這幾項資料庫系統評估下來，各有優缺點，要使用哪一套端看最後使用的環境需求而定。例如若要開發一個簡單的程式，但需要資料庫來做為程式內部資料的臨時性儲存，或是需要較低資源需求的，那SQLite是一個非常好的選擇；若要開發一個稍微大一點的單機程式，但需要大一些且未來可擴充的資料庫，則可以選擇SQL Server LocalDB；若要開發一套系統程式，單機或是網路架構，需要資料庫系統作為後援資料，那就非SQL Server莫屬，中小型可用Express版本，大型則可選擇Standard乃至Exterprise版本。

<span style="font-size: large;">參考資料</span>

[Comparison of SQL Server Compact, SQL Server Express 2012 and LocalDB](http://erikej.blogspot.com/2011/01/comparison-of-sql-server-compact-4-and.html)

[Differences Between SQL Server Compact and SQL Server](http://msdn.microsoft.com/en-us/library/bb896140.aspx)
[Features Supported by the Editions of SQL Server 2012](http://msdn.microsoft.com/en-us/library/cc645993%28v=SQL.110%29.aspx)
[SQL Server 學習筆記](http://sharedderrick.blogspot.com/)

<span style="font-size: large;">連結</span>
[SQL Server Express 2012 下載](http://www.microsoft.com/downloads/zh-tw/details.aspx?FamilyID=c3a54822-f858-494a-9d74-b811e29179e7)
[SQL Server Compact 4.0 下載](http://www.microsoft.com/downloads/zh-tw/details.aspx?familyid=033cfb76-5382-44fb-bc7e-b3c8174832e2)
[SQLite](http://www.sqlite.org/)