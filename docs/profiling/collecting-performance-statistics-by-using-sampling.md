---
title: "使用取樣收集效能統計資料 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "程式碼剖析工具，取樣"
  - "取樣分析方法"
ms.assetid: 8e36361b-bb3d-40c6-b286-0e68c0ecb915
caps.latest.revision: 21
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 21
---
# 使用取樣收集效能統計資料
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

根據預設，[!INCLUDE[vsPreShort](../code-quality/includes/vspreshort_md.md)] 程式碼剖析工具取樣方法會以每 10,000,000 次處理器週期為單位 \(約為 1 GHz 電腦上每百分之一秒\) 收集程式碼剖析資訊。  取樣方法對於尋找處理器使用率問題來說很有用，建議於開始調查大部分效能問題時使用。  
  
 **需求**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
> [!NOTE]
>  Windows 8 和 Windows Server 2012 中的增強安全性功能，需要在 Visual Studio 分析工具收集這些平台資料的方式上進行重大變更。  Windows 市集應用程式也需要新的收集技術。  請參閱 [剖析 Windows 8 和 Windows Server 2012 應用程式](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)。  
  
 您可以使用下列其中一個程序來指定取樣方法：  
  
-   在 \[程式碼剖析精靈\] 的第一個頁面上，按一下 \[**CPU 取樣 \(建議使用\)**\]。  
  
-   在 \[**效能總管**\] 工具列的 \[**方法**\] 清單中，按一下 \[**取樣**\]。  
  
-   在效能工作階段的 \[屬性\] 對話方塊中，按一下 \[**一般**\] 頁面上的 \[**取樣**\]。  
  
## 一般工作  
 您可以在效能工作階段的 *Performance Session* \[**屬性頁**\] 對話方塊中指定其他選項。  若要開啟此對話方塊：  
  
-   在 \[**效能總管**\] 中，以滑鼠右鍵按一下效能工作階段名稱，然後按一下 \[**屬性**\]。  
  
 下表中的工作說明當您使用取樣方法進行程式碼剖析時，可以在 \[*Performance Session* **屬性頁**\] 對話方塊中指定的選項。  
  
|工作|相關內容|  
|--------|----------|  
|在 \[**一般**\] 頁面上，加入 .NET 記憶體配置及存留期資料收集，並為產生的程式碼剖析資料 \(.vsp\) 檔案指定命名的詳細資料。|-   [收集 .NET 記憶體配置和存留期資料](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)<br />-   [如何：設定程式碼剖析資料檔案名稱選項](../profiling/how-to-set-performance-data-file-name-options.md)|  
|在 \[**取樣**\] 頁面上，變更取樣率，將取樣事件從處理器時脈週期變更為另一個處理器效能計數器，或是兩者都變更。|-   [如何：選擇取樣事件](../Topic/How%20to:%20Choose%20Sampling%20Events.md)|  
|如果您的程式碼方案中有多個 .exe 專案，請在 \[**啟動**\] 頁面上指定要啟動的應用程式及其啟動順序。|-   [收集階層互動資料](../profiling/collecting-tier-interaction-data.md)|  
|在 \[**階層互動**\] 頁面上，將 ADO.NET 呼叫資訊加入至執行程式碼剖析期間收集的資料。|-   [收集階層互動資料](../profiling/collecting-tier-interaction-data.md)|  
|在 \[**Windows 事件**\] 頁面上，指定一個或多個要透過取樣資料收集的 Windows 事件追蹤 \(ETW\) 事件。|-   [如何：收集 Windows 事件追蹤 \(ETW\) 資料](../Topic/How%20to:%20Collect%20Event%20Tracing%20for%20Windows%20\(ETW\)%20Data.md)|  
|在 \[**Windows 計數器**\] 頁面上，指定一個或多個要加入至程式碼剖析資料中做為標記的作業系統效能計數器。|-   [如何：收集 Windows 計數器資料](../profiling/how-to-collect-windows-counter-data.md)|  
|如果您的應用程式模組使用多個版本，請在 \[**進階**\] 頁面上，指定要進行程式碼剖析的 .NET Framework 執行階段版本。  根據預設，會對第一個載入的版本進行程式碼剖析。|-   [如何：在並存案例中指定要分析的 .NET Framework 執行階段](../Topic/How%20to:%20Specify%20the%20.NET%20Framework%20Runtime.md)|