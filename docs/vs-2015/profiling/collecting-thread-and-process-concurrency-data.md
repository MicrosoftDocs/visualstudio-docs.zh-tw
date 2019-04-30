---
title: 收集執行緒和處理序並行資料 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- concurrency profiling method
- Profiling Tools, concurrency method
ms.assetid: fa03d381-a9ee-408c-876d-05111e29225b
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cf8a9de5f2a7e520a745fab81197016d6e1bd15d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62568156"
---
# <a name="collecting-thread-and-process-concurrency-data"></a>收集執行緒和處理序並行資料
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 分析工具的並行分析方法可讓您收集資源爭用資料，包括每個會造成分析應用程式中的函式等候存取資源之同步處理事件的相關資訊。  
  
 **需求**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)]、[!INCLUDE[vsPreLong](../includes/vsprelong-md.md)]、[!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
  您可以使用下列其中一種程序來指定並行分析方法：  
  
- 在分析精靈的第一個頁面上，按一下 [並行]。  
  
- 在效能工作階段 [屬性] 對話方塊中的 [一般] 頁面上，按一下 [並行]。  
  
- 在 [效能總管] 工具列的 [方法] 清單中，按一下 [並行]。  
  
## <a name="common-tasks"></a>一般工作  
 您可以在效能工作階段的 [效能工作階段]  對話方塊中指定其他選項。 若要開啟此對話方塊：  
  
- 在 **效能總管**中，以滑鼠右鍵按一下效能工作階段名稱，然後按一下 [屬性] 。  
  
  下表中的工作說明當您使用並行方法進行分析時，可以在 [效能工作階段屬性頁] 對話方塊中指定的選項。  
  
|工作|相關內容|  
|----------|---------------------|  
|在 [一般] 頁面上，指定產生的分析資料 (.vsp) 檔案的命名詳細資料。|-   [如何：設定效能資料檔案名稱選項](../profiling/how-to-set-performance-data-file-name-options.md)|  
|在 [啟動] 頁面上，如果您的程式碼方案中有多個 .exe 專案，請指定要啟動的應用程式。|-   [如何：指定要啟動的二進位檔](../profiling/how-to-specify-the-binary-to-start.md)|  
|在 [階層互動]  頁面上，將 ADO.NET 呼叫資料加入程式碼剖析執行。|-   [收集階層互動資料](../profiling/collecting-tier-interaction-data.md)|  
|在 [Windows 計數器]  頁面上，指定將加入程式碼剖析資料為標記的一或多個作業系統效能計數器。|-   [如何：收集 Windows 計數器資料](../profiling/how-to-collect-windows-counter-data.md)|  
|在 [進階] 頁面上，如果您的應用程式模組使用多個版本，請指定要分析的 .NET Framework 執行階段版本。 預設會分析載入的第一個版本。|-   [如何：指定 .NET Framework 執行階段](../profiling/how-to-specify-the-dotnet-framework-runtime.md)|
