---
title: 支援陳述式，適用於 Visual Basic 6.0 |Microsoft 文件
ms.date: 08/28/2017
ms.technology: devlang-vb
ms.topic: conceptual
dev_langs:
- VB
helpviewer_keywords:
- VB6 support
- Visual Basic 6.0 support
ms.assetid: ffc5ba4d-44d7-4ef7-a3f6-38a8738bf127
author: paulyuk
ms.author: paulyuk
ms.workload:
- paulyuk
ms.openlocfilehash: cc55dec5960717e3807602bc76031f7502ec90c9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="support-statement-for-visual-basic-60-on-windows"></a>支援適用於 Visual Basic 6.0 在 Windows 上的陳述式


## <a name="executive-summary"></a>執行摘要

Visual Basic 小組致力於下列支援 Windows 作業系統上的 Visual Basic 6.0 應用程式的"它只適用於 「 相容性： 

- Windows 10
- Windows 8.1
- Windows 7
- Windows Server 2016
- Windows Server 2012 包括 R2
- Windows Server 2008 R2 的包括

Visual Basic 小組的目標是 Visual Basic 6.0 應用程式會繼續支援 Windows 版本上執行。 這份文件中有詳細說明，Visual Basic 6.0 核心執行階段會支援完整的存留期間受支援的 Windows 版本中，也就是五年的主要支援後面接著五年的延伸支援 (http://support.microsoft.com/gp/lifepolicy)。 支援列會受到嚴重衰退和現有的應用程式的重大安全性問題。

## <a name="technical-summary"></a>技術摘要

Visual Basic 6.0 這些索引鍵的交付項目所組成：
- Visual 基本 6.0 IDE （整合式的開發環境）。
- Visual Basic 6.0 的執行階段： 的基底文件庫和用來執行 VB 6.0 應用程式的執行引擎。
- Visual Basic 6.0 的執行階段擴充檔案： 選取 ActiveX 控制項 OCX 檔案、 程式庫，以及傳送 IDE 媒體以及的線上版本的工具。

## <a name="the-visual-basic-60-ide"></a>Visual 基本 6.0 IDE

Visual Basic 6.0 IDE 已不再支援從 2008 年 4 月 8 日開始。 此外，在 Windows 和 Visual Basic 小組已完成測試 Windows Vista、 Windows 7、 Windows Server 2008、 Windows 8 和 Windows 8.1，了解，以及減輕 （適當的話） 上的 Visual Basic 6.0 IDE 32 位元版本的 Windows （請參閱上的相容性問題[64 位元 Windows](#62-bit-windows)下面章節，以進一步了解 64 位元系統)。 這項公告 ide 不會變更的支援原則。

## <a name="the-visual-basic-60-runtime"></a>Visual Basic 6.0 的執行階段

Visual Basic 6.0 的執行階段會定義為原本的 Visual Basic 6.0 轉散發清單中包含的已編譯二進位檔。 這些檔案被標示為 「 可散布原始的 Visual Basic 6.0 授權中。 這些檔案的範例包括 Visual Basic 6.0 的執行階段程式庫 (`msvbvm60.dll`)，控制項 (也就是`msflxgrd.ocx`) 以及執行階段的其他主要功能區域 (也就是 MDAC) 的支援檔案。

執行階段分成三個群組：

- 支援的執行階段檔案-傳送的作業系統

   大部分的應用程式案例中，所用的索引鍵 Visual Basic 6.0 執行階段檔案都隨附於並支援的 Windows 版本的存留期間支援。 此存留期為 5 年的主要支援和五年的延伸支援從指定的版本的 Windows 隨附的時間。 這些檔案已經過測試，在我們測試支援的 Windows 版本上執行的 Visual Basic 6.0 應用程式的相容性。 

   > [!NOTE]
   > 所有支援的 Windows 版本包含幾乎完全相同的檔案清單，並包含這些檔案的應用程式的可轉散發套件需求應該幾乎完全相同。 其中一個主要差異在於`TriEdit.dll`已從 Windows Vista 和更新版本中移除。

- 支援執行階段檔案--擴充檔案將應用程式

   此延伸的清單包含的索引鍵的控制項、 程式庫，以及可從 IDE 媒體或從 Microsoft.com 安裝到開發人員電腦的工具。 一般而言，VB6 IDE 這些控制項預設安裝到開發人員電腦。 開發人員仍必須轉散發這些檔案與應用程式。 支援的檔案版本上可用的線上 Microsoft Download Center (http://go.microsoft.com/fwlink/?LinkID=142927)。

- 不支援執行階段檔案

   某些檔案是具有或不在主流支援，或從未包含執行階段可轉散發套件的一部分 (例如，它們已包含在`\Tools`支援傳統 VB4/VB5 應用程式，在 IDE 媒體上的資料夾或協力廠商控制項，所以)。 這些檔案不支援在視窗中：相反地，它們是受限於所隨附的媒體適用於任何支援合約。 這表示無任何擔保周圍支援與服務。 在某些情況下，才支援這些程式庫的更新版本。 以下提供回溯相容性或支援版本移轉的詳細資訊。

如需每個支援群組中包含的檔案的特定詳細資料請參閱[執行階段定義](#runtime-definition)下一節。

## <a name="the-visual-basic-60-support-lifetime"></a>Visual Basic 6.0 支援存留期

支援和/或傳送上支援的 Windows 版本的 Visual Basic 6.0 runtime 二進位檔不會變更的支援原則的 Visual Basic 6.0 IDE 或 Visual Studio 6.0 IDE 整體。 這些產品移出 2008 年 4 月 8 日的延伸支援。

Microsoft 產品支援生命週期的詳細資訊，請參閱http://support.microsoft.com/gp/lifepolicy。 這個支援生命週期的一部分，Microsoft 將持續在支援的 Windows 版本上支援 Visual Basic 6.0 的執行階段，這些作業系統的支援存留期間。 這表示，例如 Visual Basic 6.0 的執行階段會支援 Windows Server 2003 上，2008 年 6 月主流支援和 2013 年 6 月的延伸支援日之前。
如支援週期，或若要了解其他支援選項的更多詳細資料，請造訪我們的支援網頁在http://www.microsoft.com/support。

## <a name="64-bit-windows"></a>64 位元 Windows

Visual Basic 6.0 的執行階段檔案都是 32 位元。 這些檔案會隨附在 64 位元 Windows 作業系統下表中所參考。 在 WOW 模擬環境中只支援 32 位元 VB6 應用程式和元件。 32 位元元件也必須裝載在 32 位元應用程式處理序。

Visual Basic 6.0 IDE 永遠不會提供在原生 64 位元版本中，也不具有 32 位元 IDE 就已經支援 64 位元 Windows 上。 VB6 開發在 Windows 64 位元或 32 位元以外的任何原生架構上並不會不支援。

## <a name="windows-7"></a>Windows 7

這個支援聲明的初始版本，因為 Windows 7 作業系統已經釋放。 這份文件已更新以釐清 VB6 在 Windows 7 上的 Microsoft 的支援。

VB6 執行階段將出貨，而且將支援在 Windows 7 作業系統的存留期。 Visual Basic 6.0 的執行階段檔案繼續為 32 位元，而且所有元件都必須都裝載在 32 位元應用程式處理序。

## <a name="windows-81"></a>Windows 8.1

這個支援聲明的初始版本，Windows 8.1 作業系統已釋放。 這份文件已更新以釐清 VB6 Windows 8.1 上的 Microsoft 的支援。

VB6 執行階段將出貨，而且將支援在 Windows 8.1 作業系統的存留期。 Visual Basic 6.0 的執行階段檔案繼續為 32 位元，而且所有元件都必須都裝載在 32 位元應用程式處理序。 開發人員可以將支援劇本的 Windows 8.1 視為正在相同，因為其適用於 Windows 7。

## <a name="windows-10"></a>Windows 10

這個支援聲明的初始版本，因為 Windows 10 作業系統已經釋放。 這份文件已更新以釐清 VB6 Windows 10 上的 Microsoft 的支援。

VB6 執行階段將出貨，而且將在 Windows 10 中支援的 os 的存留期間。 Visual Basic 6.0 的執行階段檔案繼續為 32 位元，而且所有元件都必須都裝載在 32 位元應用程式處理序。 開發人員可以將支援劇本 for Windows 10 視為正在相同，因為其適用於 Windows 8.1。

## <a name="windows-server-2008"></a>Windows Server 2008

這個支援聲明的初始版本，因為 Windows Server 2008 作業系統已經釋放。 這份文件已更新以釐清 VB6 Windows Server 2008 上的 Microsoft 的支援。

VB6 執行階段將出貨，而且將支援在 Windows Server 2008 作業系統的存留期。 Visual Basic 6.0 的執行階段檔案繼續為 32 位元，而且所有元件都必須都裝載在 32 位元應用程式處理序。

## <a name="windows-server-2008-r2"></a>Windows Server 2008 R2

這個支援聲明的初始版本，因為已發行 Windows Server 2008 R2 作業系統。 這份文件已更新以釐清 VB6 Windows Server 2008 R2 上的 Microsoft 的支援。

VB6 執行階段將出貨，而且將在 Windows Server 2008 R2 中支援的 os 的存留期間。 Visual Basic 6.0 的執行階段檔案繼續為 32 位元，而且所有元件都必須都裝載在 32 位元應用程式處理序。 開發人員可以將支援劇本適用於 Windows Server 2008 R2 視為正在相同，因為其適用於 Windows Server 2008。

## <a name="windows-server-2012"></a>Windows Server 2012

這個支援聲明的初始版本，因為 Windows Server 2012 作業系統已經釋放。 這份文件已更新以釐清 VB6 Windows Server 2012 上的 Microsoft 的支援。

VB6 執行階段將出貨，而且將在 Windows Server 2012 支援的 os 的存留期間。 Visual Basic 6.0 的執行階段檔案繼續為 32 位元，而且所有元件都必須都裝載在 32 位元應用程式處理序。 開發人員可以視為支援本文的 Windows Server 2012 的相同，因為其適用於 Windows Server 2008 R2。

## <a name="windows-server-2012-r2"></a>Windows Server 2012 R2

這個支援聲明的初始版本，因為已發行 Windows Server 2012 R2 作業系統。 這份文件已更新以釐清 VB6 Windows Server 2012 R2 上的 Microsoft 的支援。

VB6 執行階段將出貨，而且將在 Windows Server 2012 R2 中支援的 os 的存留期間。 Visual Basic 6.0 的執行階段檔案繼續為 32 位元，而且所有元件都必須都裝載在 32 位元應用程式處理序。 開發人員可以視為支援本文的 Windows Server 2012 r2 的相同，因為其適用於 Windows Server 2012。

## <a name="windows-server-2016"></a>Windows Server 2016

這個支援聲明的初始版本，因為 Windows Server 2016 作業系統已經釋放。 這份文件已更新以釐清 VB6 Windows Server 2016 的 Microsoft 的支援。

VB6 執行階段將出貨，而且將 Windows Server 2016 中支援的 os 的存留期間。 Visual Basic 6.0 的執行階段檔案繼續為 32 位元，而且所有元件都必須都裝載在 32 位元應用程式處理序。 開發人員可以將支援劇本適用於 Windows Server 2016 視為正在相同，因為其適用於 Windows Server 2012 R2。

## <a name="supported-windows-operating-system-versions"></a>支援的 Windows 作業系統版本

本節提供有關提供某種程度的 VB6 支援之作業系統的其他資訊。 

|Windows 作業系統|VB6 支援的執行階段</br>在 Windows 中傳送的檔案必須支援嗎？|VB6 支援 Rutime</br>擴充檔</br>將您的應用程式有支援？| VB6 IDE 提供支援？|
|---|---|---|---|
|Windows 10 中，所有的 32 位元版本|[是] *|[是] *|否|
|Windows 10 中，所有的 64 位元版本 (僅 WOW)|[是] * </br> 只有在 wow 模式下執行的 32 位元應用程式|是* </br> 只有在 wow 模式下執行的 32 位元應用程式|否|
|Windows 8.1，所有的 32 位元版本|[是] *|[是] *|否|
| Windows 8.1，所有的 64 位元版本 (僅 WOW)|[是] * </br> 只有在 wow 模式下執行的 32 位元應用程式|是* </br> 只有在 wow 模式下執行的 32 位元應用程式|否|
|Windows 7 中，所有的 32 位元版本|[是] *|[是] *|否|
|Windows 7 中，所有的 64 位元版本 (僅 WOW)|[是] * </br> 只有在 wow 模式下執行的 32 位元應用程式|[是] * </br> 只有在 wow 模式下執行的 32 位元應用程式|否|
|Windows Server 2016 中，所有的 64 位元版本 (僅 WOW)|是* </br> 只有在 wow 模式下執行的 32 位元應用程式|是* </br> 只有在 wow 模式下執行的 32 位元應用程式|否|
|Windows Server 2012 R2，所有的 64 位元版本 (僅 WOW)<br>Windows Server 2012，所有的 64 位元版本 (僅 WOW)|是* </br> 只有在 wow 模式下執行的 32 位元應用程式|是* </br> 只有在 wow 模式下執行的 32 位元應用程式|否|
|Windows Server 2008 R2，所有的 x64 版本 (僅 WOW)</br>所有 x64 Windows Server 2008 版本 (僅 WOW)|[是] * </br> 只有在 wow 模式下執行的 32 位元應用程式|[是] * </br> 只有在 wow 模式下執行的 32 位元應用程式|否|
|Windows Server 2008，所有的 32 位元版本|[是] *|[是] *|否|


> [!NOTE]
> &#42;Windows 支援生命週期會受限於 VB6 執行階段支援。  例如，如果目標作業系統處於延長支援，VB6 不能有比延長支援更高版本的支援層級。  [Windows 支援生命週期說明書](https://support.microsoft.com/en-us/help/13853/windows-lifecycle-fact-sheet)包含先前和目前的 Windows 版本相關的其他 lifecycle 資訊。

## <a name="visual-basic-60-runtime-usage-inside-vba-and-office"></a>Visual Basic 6.0 VBA 和 Office 內的執行階段使用

Visual Basic 應用程式，或 VBA 是常用的應用程式的自動化和其他應用程式，最常在 Microsoft Office 應用程式內的巨集的不同技術。 VBA 隨附於 Office，並因此 VBA 的支援由 Office 的支援原則。 不過，有很多情況下，VBA 用來呼叫，或裝載 Visual Basic 6.0 runtime 二進位檔和控制項的位置。 在這些情況下，Visual Basic 6.0 支援執行階段檔案的作業系統，支援 VBA 環境內使用時，也支援擴充的檔案清單。

VB6 VBA 內都必須支援的執行階段情況下，下列必須為真：

- 仍然支援 VB runtime 的主機作業系統版本。
- 仍然支援主機版本的 Office vba。
- 仍然支援問題的執行階段檔案。

## <a name="visual-basic-script-vbscript"></a>Visual Basic Script (VBScript)

VBScript 無關 Visual Basic 6.0 及這個支援聲明。 不過，VBScript 目前會做為 Windows 7、 Windows 8.1、 Windows 10、 Windows Server 2008 R2、 Windows Server 2012 R2 和 Windows Server 2016 所包括的包括一部分的出貨，而且由作業系統的支援生命週期。

## <a name="third-party-components"></a>第三方元件

Microsoft 不能提供協力廠商元件，例如 OCX/ActiveX 控制項的支援。 如需詳細資訊，這些元件的支援連絡控制項廠商原始建議的客戶。

## <a name="reporting-issues-with-vb-60-applications-running-on-windows"></a>與在 Windows 上執行的 VB 6.0 應用程式報告問題

計劃使用 Visual Basic 6.0 使用其中一個列出的 Windows 作業系統的開發人員應該安裝該作業系統，並開始使用原始的應用程式接受度測試應用程式相容性測試。

如果您發現問題出在其中一個列出的 Windows 作業系統上執行的 Visual Basic 6.0 應用程式，請依照一般支援管道報告這個問題。

## <a name="supported-and-shipping-in-windows"></a>支援和傳送中的 Windows

| | | | |
|---|---|---|---|
|atl.dll|         msadcor.dll|     msorcl32.dll|   ole2.dll|
|asycfilt.dll|    msadcs.dll|      msvbvm60.dll|   ole32.dll|
|comcat.dll|      msadds.dll|      msvcirt.dll|    oleaut32.dll|
|compobj.dll|     msaddsr.dll|     msvcrt.dll|     oleaut32.dll|
|dbnmpntw.dll|    msader15.dll|    msvcrt40.dll|   oledb32.dll|
|dcomcnfg.exe|    msado15.dll|     mtxdm.dll|      oledb32r.dll|
|dllhost.exe|     msador15.dll|    mtxoci.dll|     oledlg.dll|
|ds16gt.dll|      msadrh15.dll|    odbc16gt.dll|   olepro32.dll|
|ds32gt.dll|      mscpxl32.dll|    odbc32.dll|     olethk32.dll|
|expsrv.dll|      msdadc.dll|      odbc32gt.dll|   regsvr32.exe|
|hh.exe|          msdaenum.dll|    Odbcad32.exe|   rpcns4.dll|
|hhctrl.ocx|      msdaer.dll|      odbccp32.cpl|   rpcrt4.dll|
|imagehlp.dll|    msdaora.dll|     odbccp32.dll|   scrrun.dll|
|iprop.dll|       msdaosp.dll|     odbccr32.dll|   secur32.dll|
|itircl.dll|      msdaprst.dll|    odbccu32.dll|   simpdata.tlb|
|itss.dll|        msdaps.dll|      odbcint.dll|    sqloledb.dll|
|mfc40.dll|       msdasc.dll|      odbcji32.dll|   sqlsrv32.dll|
|mfc42.dll|       msdasql.dll|     odbcjt32.dll|   stdole2.tlb|
|mfc42enu.dll|    msdasqlr.dll|    odbctrac.dll|   stdole32.tlb|
|msadce.dll|      msdatsrc.tlb|    oddbse32.dll|   storage.dll|
|msadcer.dll|     msdatt.dll|      odexl32.dll|    vbajet32.dll|
|msadcf.dll|      msdfmap.dll|     odfox32.dll|    vfpodbc.dll|
|msadcfr.dll|     msdfmap.ini|     odpdx32.dll|                |
|msadco.dll|      msjtes40.dll|    odtext32.dll|               |

## <a name="supported-runtime-files-to-distribute-with-your-application"></a>將您的應用程式支援的執行階段檔案

| | | | |
|---|---|---|---|
|comct232.ocx |msbind.dll   |msdbrptr.dll  |msstdfmt.dll| 
|comct332.ocx |mscdrun.dll  |msflxgrd.ocx  |msstkprp.dll| 
|comctl32.ocx |mschrt20.ocx |mshflxgd.ocx  |mswcrun.dll|  
|comdlg32.ocx |mscomct2.ocx |mshtmpgr.dll  |mswinsck.ocx| 
|dbadapt.dll  |mscomctl.ocx |msinet.ocx    |picclp32.ocx| 
|dbgrid32.ocx |mscomm32.ocx |msmapi32.ocx  |richtx32.ocx| 
|dblist32.ocx |msdatgrd.ocx |msmask32.ocx  |sysinfo.ocx|  
|mci32.ocx    |msdatlst.ocx |msrdc20.ocx   |tabctl32.ocx| 
|msadodc.ocx  |msdatrep.ocx |msrdo20.dll

## <a name="unsupported-but-supported-and-compatible-updates-or-upgrades-are-available"></a>不支援，但支援和相容的更新或升級可用

| | | | |
|---|---|---|---|
|dao350.dll|   msexch35.dll| msjter35.dll| msrepl35.dll|
|mdac_typ.exe| msexcl35.dll| msjtor35.dll| mstext35.dll|
|mschart.ocx|  msjet35.dll|  msltus35.dll| msxbse35.dll|
|msdaerr.dll|  msjint35.dll| mspdox35.dll| odbctl32.dll|
|msdatl2.dll|  msjt4jlt.dll| msrd2x35.dll| oledb32x.dll|

## <a name="unsupported-runtime-files"></a>不支援執行階段檔案

| | | | |
|---|---|---|---|
|anibtn32.ocx| spin32.ocx|   rpcltscm.dll|  rdocurs.dll|
|graph32.ocx|  gauge32.ocx|  rpcmqcl.dll|   vbar332.dll|
|keysta32.ocx| gswdll32.dll| rpcmqsvr.dll|  visdata.exe|
|autmgr32.exe| ciscnfg.exe|  rpcss.exe|     vsdbflex.srg|
|autprx32.dll| olecnv32.dll| dbmsshrn.dll|  threed32.ocx|
|racmgr32.exe| rpcltc1.dll|  dbmssocn.dll|  MSWLess.ocx|
|racreg32.dll| rpcltc5.dll|  windbver.exe|  tlbinf32.dll|
|grid32.ocx|   rpcltccm.dll| msderun.dll|   triedit.dll|
|msoutl32.ocx| rpclts5.dll|  odkob32.dll|

## <a name="localization-support-binaries"></a>當地語系化支援二進位檔

下列的二進位檔所需的支援當地語系化版本的 Windows 作業系統上執行的 Visual Basic 6.0 應用程式。 它們支援，但不是會隨附於 Windows。 這些檔案都必須隨附於您的應用程式安裝程式。

### <a name="supported-runtime-files-to-distribute-with-your-application"></a>將您的應用程式支援的執行階段檔案

|JPN|KOR|CHT|CHS|
|---|---|---|---|
|mfc42jpn.dll|  mfc42kor.dll|  mfc42cht.dll|  mfc42chs.dll|
|scrrnjp.dll|   scrrnko.dll|   scrrncht.dll|  scrrnchs.dll|
|vb6jp.dll|     vb6ko.dll|     vb6cht.dll|    vb6chs.dll|
|cmct2jp.dll|   cmct2ko.dll|   cmct2cht.dll|  cmct2chs.dll|
|cmct3jp.dll|   cmct3ko.dll|   cmct3cht.dll|  mscc2chs.dll|
|mscc2jp.dll|   mscc2ko.dll|   mscc2cht.dll|  cmct3chs.dll|
|cmctljp.dll|   cmctlko.dll|   cmctlcht.dll|  cmctlchs.dll|
|cmdlgjp.dll|   cmdlgko.dll|   mscmccht.dll|  mscmcchs.dll|
|mscmcjp.dll|   mscmcko.dll|   cmdlgcht.dll|  cmdlgchs.dll|
|dbgrdjp.dll|   dbgrdko.dll|   dbgrdcht.dll|  dbgrdchs.dll|
|dblstjp.dll|   dblstko.dll|   dblstcht.dll|  dblstchs.dll|
|mcijp.dll|     mciko.dll|     mcicht.dll|    mcichs.dll|
|msadnjp.dll|   msadnko.dll|   msadncht.dll|  msadnchs.dll|
|adodcjp.dll|   adodcko.dll|   adodccht.dll|  adodcchs.dll|
|mschtjp.dll|   mschtko.dll|   mschtcht.dll|  mschtchs.dll|
|msch2jp.dll|   msch2ko.dll|   msch2cht.dll|  msch2chs.dll|
|mscomjp.dll|   mscomko.dll|   mscomcht.dll|  mscomchs.dll|
|datgdjp.dll|   datgdko.dll|   datgdcht.dll|  datgdchs.dll|
|datlsjp.dll|   datlsko.dll|   datlscht.dll|  datlschs.dll|
|datrpjp.dll|   datrpko.dll|   datrpcht.dll|  datrpchs.dll|
|dbrprjp.dll|   dbrprko.dll|   dbrprcht.dll|  dbrprchs.dll|
|flxgdjp.dll|   flxgdko.dll|   flxgdcht.dll|  flxgdchs.dll|
|mshfgjpn.dll|  mshfgkor.dll|  mshfgcht.dll|  mshfgchs.dll|
|htmprjp.dll|   htmprko.dll|   htmprcht.dll|  htmprchs.dll|
|inetjp.dll|    inetko.dll|    inetcht.dll|   inetchs.dll|
|msmpijp.dll|   msmpiko.dll|   msmpicht.dll|  msmpichs.dll|
|msmskjp.dll|   msmskko.dll|   msmskcht.dll|  msmskchs.dll|
|rdc20jp.dll|   rdc20ko.dll|   rdc20cht.dll|  rdc20chs.dll|
|rdo20jp.dll|   rdo20ko.dll|   rdo20cht.dll|  rdo20chs.dll|
|stdftjp.dll|   stdftko.dll|   stdftcht.dll|  stdftchs.dll|
|mswcrjp.dll|   mswcrko.dll|   mswcrcht.dll|  mswcrchs.dll|
|winskjp.dll|   winskko.dll|   winskcht.dll|  winskchs.dll|
|pcclpjp.dll|   pcclpko.dll|   pcclpcht.dll|  pcclpchs.dll|
|rchtxjp.dll|   rchtxko.dll|   rchtxcht.dll|  rchtxchs.dll|
|sysinjp.dll|   sysinko.dll|   sysincht.dll|  sysinchs.dll|
|tabctjp.dll|   tabctko.dll|   tabctcht.dll|  tabctchs.dll|

|ITA|FRA|ESP|DEU|
|---|---|---|---|
|mfc42ita.dll|  mfc42fra.dll|  mfc42esp.dll|  mfc42deu.dll|
|scrrnit.dll|   scrrnfr.dll|   scrrnes.dll|   scrrnde.dll|
|vb6it.dll|     vb6fr.dll|     vb6es.dll|     vb6de.dll|
|cmct2it.dll|   cmct2fr.dll|   cmct2es.dll|   cmct2de.dll|
|mscc2it.dll|   mscc2fr.dll|   mscc2es.dll|   mscc2de.dll|
|cmct3it.dll|   cmct3fr.dll|   cmct3es.dll|   cmct3de.dll|
|cmctlit.dll|   cmctlfr.dll|   cmctles.dll|   cmctlde.dll|
|mscmcit.dll|   mscmcfr.dll|   mscmces.dll|   mscmcde.dll|
|cmdlgit.dll|   cmdlgfr.dll|   cmdlges.dll|   cmdlgde.dll|
|dbgrdit.dll|   dbgrdfr.dll|   dbgrdes.dll|   dbgrdde.dll|
|dblstit.dll|   dblstfr.dll|   dblstes.dll|   dblstde.dll|
|mciit.dll|     mcifr.dll|     mcies.dll|     mcide.dll|
|msadnit.dll|   msadnfr.dll|   msadnes.dll|   msadnde.dll|
|adodcit.dll|   adodcfr.dll|   adodces.dll|   adodcde.dll|
|mschtit.dll|   mschtfr.dll|   mschtes.dll|   mschtde.dll|
|msch2it.dll|   msch2fr.dll|   msch2es.dll|   msch2de.dll|
|mscomit.dll|   mscomfr.dll|   mscomes.dll|   mscomde.dll|
|atgdit.dll|    datgdfr.dll|   datgdes.dll|   datgdde.dll|
|datlsit.dll|   datlsfr.dll|   datlses.dll|   datlsde.dll|
|datrpit.dll|   datrpfr.dll|   datrpes.dll|   datrpde.dll|
|dbrprit.dll|   dbrprfr.dll|   dbrpres.dll|   dbrprde.dll|
|flxgdit.dll|   flxgdfr.dll|   flxgdes.dll|   flxgdde.dll|
|mshfgit.dll|   mshfgfr.dll|   mshfges.dll|   mshfgde.dll|
|htmprit.dll|   htmprfr.dll|   htmpres.dll|   htmprde.dll|
|inetit.dll|    inetfr.dll|    inetes.dll|    inetde.dll|
|msmpiit.dll|   msmpifr.dll|   msmpies.dll|   msmpide.dll|
|msmskit.dll|   msmskfr.dll|   msmskes.dll|   msmskde.dll|
|rdc20it.dll|   rdc20fr.dll|   rdc20es.dll|   rdc20de.dll|
|rdo20it.dll|   rdo20fr.dll|   rdo20es.dll|   rdo20de.dll|
|stdftit.dll|   stdftfr.dll|   stdftes.dll|   stdftde.dll|
|mswcrit.dll|   mswcrfr.dll|   mswcres.dll|   mswcrde.dll|
|winskit.dll|   winskfr.dll|   winskes.dll|   winskde.dll|
|pcclpit.dll|   pcclpfr.dll|   pcclpes.dll|   pcclpde.dll|
|rchtxit.dll|   rchtxfr.dll|   rchtxes.dll|   rchtxde.dll|
|sysinit.dll|   sysinfr.dll|   sysines.dll|   sysinde.dll|
|tabctit.dll|   tabctfr.dll|   tabctes.dll|   tabctde.dll|

