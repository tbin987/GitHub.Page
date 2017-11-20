---
title: 建置DCMTK
tags:
  - DCMTK
  - DICOM
categories: 程式設計
permalink: build-dcmtk
date: 2012-09-02 20:45:00
---

DCMTK 3.6.0發布囉：
[http://dicom.offis.de/dcmtk](http://dicom.offis.de/dcmtk)

上一次建置DCMTK時，還是3.5.3版加上VC2005，現在3.6.0版已經發布，且VC也已經發行到2012年版了。鑒於上一次建置已經有一段時間了，再加上當時僅建置DCMTK函式庫本身，並沒將外部函式庫一併建置，所以這次建置就順便來做個紀錄吧。

<!-- more -->

1\. 首先，當然就是要從DCMTK的官網下載函式庫的原始碼來囉，這次選擇的是3.6.0版本：
ftp://dicom.offis.de/pub/dicom/offis/software/dcmtk/dcmtk360/dcmtk-3.6.0.zip

2\. 因為還要加入外部函式庫，所以相關的檔案也要下載下來：
ZLIB:
ftp://dicom.offis.de/pub/dicom/offis/software/dcmtk/dcmtk360/support/zlib-1.2.5.tar.gz
LIBTIFF:
ftp://dicom.offis.de/pub/dicom/offis/software/dcmtk/dcmtk360/support/tiff-3.9.4.tar.gz
LIBPNG:
ftp://dicom.offis.de/pub/dicom/offis/software/dcmtk/dcmtk360/support/libpng-1.4.3.tar.gz
LIBXML2:
ftp://dicom.offis.de/pub/dicom/offis/software/dcmtk/dcmtk360/support/libxml2-2.7.7.tar.gz
LIBICONV:
ftp://dicom.offis.de/pub/dicom/offis/software/dcmtk/dcmtk360/support/libiconv-1.13.1.tar.gz
OpenSSL:
ftp://dicom.offis.de/pub/dicom/offis/software/dcmtk/dcmtk360/support/openssl-1.0.0c.tar.gz

3\. 因為上面這幾個函式庫還需要自己另外建置，但可能是我用的建置環境比較新，一直建置不成功，所以就直接下載官網上已經預先編譯好的函式庫來使用囉：
ftp://dicom.offis.de/pub/dicom/offis/software/dcmtk/dcmtk360/support/dcmtk-3.6.0-win32-i386-support_MT.zip
或
ftp://dicom.offis.de/pub/dicom/offis/software/dcmtk/dcmtk360/support/dcmtk-3.6.0-win32-i386-support_MD.zip

這裡有兩種版本：多執行緒靜態連結(/MT)以及多執行緒動態連結(/MD)，視程式要使用函式庫的方法選擇適當的檔案囉。(DCMTK 3.6.0預設是建置為/MT)

4\. 因為在Windows下建置DCMTK需要使用到CMake，所以要到CMake官網下載來使用：
http://www.cmake.org/files/v2.8/cmake-2.8.9-win32-x86.exe (安裝程式)
或
http://www.cmake.org/files/v2.8/cmake-2.8.9-win32-x86.zip (免安裝)

5\. 接下來就要開始建置了，首先將DCMTK原始碼解壓縮到建置資料夾：
例如：E:\Project\Code\DCMTK\

6\. 再來將預先編譯好的函式庫解壓縮到建置資料夾，並將會使用到的各外部支援函式庫資料夾內的bin、include、lib都移動到同一位置，如下圖：
<div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-kwIl4Wu8toM/UEMt0AS275I/AAAAAAAACuE/MR07AgzpRNk/s320/01.png)](http://4.bp.blogspot.com/-kwIl4Wu8toM/UEMt0AS275I/AAAAAAAACuE/MR07AgzpRNk/s1600/01.png)</div>
<div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-udH-BaN-vtE/UEMt24WVwII/AAAAAAAACuM/1WrWy6sSA1E/s320/02.png)](http://2.bp.blogspot.com/-udH-BaN-vtE/UEMt24WVwII/AAAAAAAACuM/1WrWy6sSA1E/s1600/02.png)</div>

7\. 因為DCMTK預設的連結方式為多執行緒靜態連結(/MT, /MTd)，而這裡要建置的程式將使用動態連結(/MD, /MDd)，故需要先對dcmtk文件做修改。

8\. 使用文字編輯器開啟dcmtk-3.6.0\CMakeList.txt，將所有的/MT修改成/MD，/MTd修改成/MDd。

9\. 開啟CMake，於”Where is the source code”選擇dcmtk-3.6.0.zip解壓縮後的位置；於”Where to build the binaries”選擇建置用專案的存放位置。

<div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-CnkhfC1mTMs/UEMvONAhxwI/AAAAAAAACuU/PfCgcHtJOMU/s320/03.png)](http://3.bp.blogspot.com/-CnkhfC1mTMs/UEMvONAhxwI/AAAAAAAACuU/PfCgcHtJOMU/s1600/03.png)</div>

[](http://3.bp.blogspot.com/-iCAl9ercn5A/UEMviABcYGI/AAAAAAAACuc/jDlWnuUC2bM/s1600/04.png)

10\. 點選[Configure]進行設定
首先選擇要使用的建置專案環境，若使用DCMTK官網的外部支援函式庫預先建置檔案，必須選擇Visual Studio 2010(即Visual Studio 10)
<div class="separator" style="clear: both; text-align: center;"></div><div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-iCAl9ercn5A/UEMviABcYGI/AAAAAAAACuc/jDlWnuUC2bM/s320/04.png)](http://3.bp.blogspot.com/-iCAl9ercn5A/UEMviABcYGI/AAAAAAAACuc/jDlWnuUC2bM/s1600/04.png)</div>
按下[Finish]，CMake即開始初始設定。

注意：DCMTK官網上放的預先編譯函式庫是以Visual Studio 2010 (VC10)建置的，若拿來用與Visual Studio 2012 (VC11)編譯，會產生"映像有安全例外處理常式(/SAFESEH)"的錯誤，故須自行以VC11重新編譯外部函式庫才行。而因為以VC11編譯這些函式庫的步驟過於複雜，且目前仍有部分函式庫無法編譯成功，故目前還是先使用官方的預先編譯函式庫。使用Visual Studio  2012仍然可以編譯VC10的程式，只要電腦中有安裝Visual Studio 2010，並且在專案屬性的[一般]\[平台工具組]選擇"Visual  Studio 2010 (v100)"即可。
<div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-ymJyEsuimsk/UENSmGCS_nI/AAAAAAAACw0/-Sa_pp4BUGI/s320/18.png)](http://1.bp.blogspot.com/-ymJyEsuimsk/UENSmGCS_nI/AAAAAAAACw0/-Sa_pp4BUGI/s1600/18.png)</div>

11\. 經過一段時間後，會出現：
<div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-N2qj1qWsRLY/UEMvjzFcXlI/AAAAAAAACuk/hPp4wq0rw8s/s320/05.png)](http://4.bp.blogspot.com/-N2qj1qWsRLY/UEMvjzFcXlI/AAAAAAAACuk/hPp4wq0rw8s/s1600/05.png)</div>
首先於”CMAKE_INSTALL_PREFIX”設定建置完的函式庫存放路徑；若要使用外部支援函式庫，必須將”DCMTK_WITH_XXX”勾選，並且於下方的”WITH_XXXINC”設定函式庫檔案所在路徑。 

設定完成如下畫面：
<div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-abXmyjS-PRI/UEMxBgbVxcI/AAAAAAAACus/jmX0S-JM53I/s320/06.png)](http://1.bp.blogspot.com/-abXmyjS-PRI/UEMxBgbVxcI/AAAAAAAACus/jmX0S-JM53I/s1600/06.png)</div>
12\. 再按下[Configure]，若設定都正確紅色區塊將消失：

<div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-WFcL_xfGEdc/UEMxDFbDhbI/AAAAAAAACu0/BvXhmOHCvis/s320/07.png)](http://3.bp.blogspot.com/-WFcL_xfGEdc/UEMxDFbDhbI/AAAAAAAACu0/BvXhmOHCvis/s1600/07.png)</div>
13\. 按下[Generate]產生建置用的專案檔。
<div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-PUOZkLyYA7g/UEMxhtQU2eI/AAAAAAAACu8/D-jiDrBcZlk/s320/08.png)](http://3.bp.blogspot.com/-PUOZkLyYA7g/UEMxhtQU2eI/AAAAAAAACu8/D-jiDrBcZlk/s1600/08.png)</div>
至此，前置作業完成，接下來要開始於Visual Studio建置DCMTK了。

14\. 關閉CMake，到”Where to build the binaries”路徑以Visual Studio開啟DCMTK.sln方案檔。
<div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-BaTTZ8ZEg_s/UEMyLR20NrI/AAAAAAAACvE/QsTQmeVHQO0/s320/09.png)](http://3.bp.blogspot.com/-BaTTZ8ZEg_s/UEMyLR20NrI/AAAAAAAACvE/QsTQmeVHQO0/s1600/09.png)</div>
<div class="separator" style="clear: both; text-align: center;">[](http://3.bp.blogspot.com/-BaTTZ8ZEg_s/UEMyLR20NrI/AAAAAAAACvE/QsTQmeVHQO0/s1600/09.png)</div>15\. 開始建置前，需要先設定建置環境。<span style="font-family: &quot;新細明體&quot;,&quot;serif&quot;; font-size: 12.0pt; mso-ansi-language: EN-US; mso-ascii-font-family: Calibri; mso-ascii-theme-font: minor-latin; mso-bidi-font-family: &quot;Times New Roman&quot;; mso-bidi-font-size: 11.0pt; mso-bidi-language: AR-SA; mso-bidi-theme-font: minor-bidi; mso-fareast-language: ZH-TW; mso-fareast-theme-font: minor-fareast; mso-hansi-font-family: Calibri; mso-hansi-theme-font: minor-latin;">於方案總管選取所有專案，右鍵選擇</span><span lang="EN-US" style="font-family: &quot;Calibri&quot;,&quot;sans-serif&quot;; font-size: 12.0pt; mso-ansi-language: EN-US; mso-ascii-theme-font: minor-latin; mso-bidi-font-family: &quot;Times New Roman&quot;; mso-bidi-font-size: 11.0pt; mso-bidi-language: AR-SA; mso-bidi-theme-font: minor-bidi; mso-fareast-font-family: 新細明體; mso-fareast-language: ZH-TW; mso-fareast-theme-font: minor-fareast; mso-hansi-theme-font: minor-latin;">[</span><span style="font-family: &quot;新細明體&quot;,&quot;serif&quot;; font-size: 12.0pt; mso-ansi-language: EN-US; mso-ascii-font-family: Calibri; mso-ascii-theme-font: minor-latin; mso-bidi-font-family: &quot;Times New Roman&quot;; mso-bidi-font-size: 11.0pt; mso-bidi-language: AR-SA; mso-bidi-theme-font: minor-bidi; mso-fareast-language: ZH-TW; mso-fareast-theme-font: minor-fareast; mso-hansi-font-family: Calibri; mso-hansi-theme-font: minor-latin;">屬性</span><span lang="EN-US" style="font-family: &quot;Calibri&quot;,&quot;sans-serif&quot;; font-size: 12.0pt; mso-ansi-language: EN-US; mso-ascii-theme-font: minor-latin; mso-bidi-font-family: &quot;Times New Roman&quot;; mso-bidi-font-size: 11.0pt; mso-bidi-language: AR-SA; mso-bidi-theme-font: minor-bidi; mso-fareast-font-family: 新細明體; mso-fareast-language: ZH-TW; mso-fareast-theme-font: minor-fareast; mso-hansi-theme-font: minor-latin;">]</span>

<div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-aNu1_YRlPyQ/UEMyMxuSoUI/AAAAAAAACvM/92rDgZv7PqU/s320/10.png)](http://4.bp.blogspot.com/-aNu1_YRlPyQ/UEMyMxuSoUI/AAAAAAAACvM/92rDgZv7PqU/s1600/10.png)</div>
&nbsp;16\. 選擇[所有組態]，點選[VC++目錄]：

<div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-BrHKrd97yCU/UEMyP9_ZuxI/AAAAAAAACvU/haWipnNeJAg/s320/11.png)](http://4.bp.blogspot.com/-BrHKrd97yCU/UEMyP9_ZuxI/AAAAAAAACvU/haWipnNeJAg/s1600/11.png)</div>
17\. 於[可執行檔目錄]點選編輯，加入由dcmtk-3.6.0-win32-i386-support_MD.zip解壓縮後的”bin”路徑： 
<div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-P6JUFRs2c9I/UEMyRA9Fw7I/AAAAAAAACvc/HVYQ-W4CI8A/s320/12.png)](http://3.bp.blogspot.com/-P6JUFRs2c9I/UEMyRA9Fw7I/AAAAAAAACvc/HVYQ-W4CI8A/s1600/12.png)</div>
18\. 於[Include目錄]點選編輯，加入由dcmtk-3.6.0-win32-i386-support_MD.zip解壓縮後的”include”路徑： 
<div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-bRP7_dN6YH0/UEMyT4BDrGI/AAAAAAAACvk/TNzsIzzlYw0/s320/13.png)](http://1.bp.blogspot.com/-bRP7_dN6YH0/UEMyT4BDrGI/AAAAAAAACvk/TNzsIzzlYw0/s1600/13.png)</div>
19\. 於[程式庫目錄]點選編輯，加入由dcmtk-3.6.0-win32-i386-support_MD.zip解壓縮後的”lib”路徑： 
<div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-Gt5jrwCUvhQ/UEMyV_p54aI/AAAAAAAACvs/SC3ziOl7C9c/s320/14.png)](http://2.bp.blogspot.com/-Gt5jrwCUvhQ/UEMyV_p54aI/AAAAAAAACvs/SC3ziOl7C9c/s1600/14.png)</div>
回屬性頁後點選[套用]，確認設定儲存後關閉屬性頁。接著就要開始正式建置DCMTK了。

20\. 選擇並建置”ALL_BUILD”專案：
<div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-X9rr398U_cI/UEMyXDMznnI/AAAAAAAACv0/EKqKciqej7c/s1600/15.png)](http://1.bp.blogspot.com/-X9rr398U_cI/UEMyXDMznnI/AAAAAAAACv0/EKqKciqej7c/s1600/15.png)</div>
21\. 經過一段時間的建置後，若設定都正確，就會顯示78個專案建置完成的訊息：
<div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-m53fzBOTeN4/UEMycLdIqHI/AAAAAAAACv8/0-B6gYJ6rsg/s320/16.png)](http://2.bp.blogspot.com/-m53fzBOTeN4/UEMycLdIqHI/AAAAAAAACv8/0-B6gYJ6rsg/s1600/16.png)</div>
22\. "ALL_BUILD"專案建置完成後，再對"INSTALL"專案建置。

23\. 最後，在建置輸出資料夾中就可以找到函式庫檔案以及範例執行檔。
<div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-SnFhPMFTeU0/UENIXVYXZNI/AAAAAAAACwc/rtnSE2QScmo/s320/17.png)](http://3.bp.blogspot.com/-SnFhPMFTeU0/UENIXVYXZNI/AAAAAAAACwc/rtnSE2QScmo/s1600/17.png)</div><div class="separator" style="clear: both; text-align: center;">[
](http://1.bp.blogspot.com/-s6khL92rRmU/UEM7yW14RNI/AAAAAAAACwM/SHNz7DhwsD4/s1600/17.png)</div>24\. 接下來，就可以利用建置完成的函式庫來寫DICOM程式了。