---
title: 效能工具問題疑難排解 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: troubleshooting
ms.assetid: 0b61cdf7-75b7-4abd-aff2-7bd997717626
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 575f17c641eb057dc01fb3302098bd9f8b47f9c5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839068"
---
# <a name="troubleshooting-performance-tools-issues"></a>效能工具問題疑難排解
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

當您使用程式碼剖析工具時，可能會遇到下列其中一個問題：  
  
- [分析工具不會收集任何資料](#NoDataCollected)  
  
- [效能視圖和報表顯示函數名稱的數位](#NoSymbols)  
  
## <a name="no-data-is-collected-by-the-profiling-tools"></a><a name="NoDataCollected"></a> 分析工具不會收集任何資料  
 在您分析應用程式之後，並未建立程式碼剖析資料 (.vsp) 檔案，而且您在輸出視窗或命令視窗中收到下列警告：  
  
 PRF0025: 未收集任何資料。  
  
 有幾個問題會造成這個問題︰  
  
- 使用取樣或 .NET 記憶體方法分析的處理序，啟動的子處理序會成為執行應用程式工作的處理序。 例如，一些應用程式會讀取該命令列，判斷其要啟動為 Windows 應用程式或命令列應用程式。 如果要求 Windows 應用程式時，原始的處理序會啟動設定為 Windows 應用程式的新處理序，然後結束原始的處理序。 因為程式碼剖析工具不會自動收集子處理序的資料，所以不會收集到任何資料。  
  
     若要在這種情況下收集程式碼剖析資料，請將分析工具附加至子處理序，而不是使用分析工具來啟動應用程式。 如需詳細資訊，請參閱 [如何：將效能工具附加和卸離以執行進程](../profiling/how-to-attach-and-detach-performance-tools-to-running-processes.md) 並 [附加 (>vsperfcmd) ](../profiling/attach.md)  
  
## <a name="performance-views-and-reports-display-numbers-for-function-names"></a><a name="NoSymbols"></a> 效能視圖和報表顯示函數名稱的數位  
 在您分析應用程式之後，您在報表和檢視中看到數字，而不是函式名稱。  
  
 這是由程式碼剖析工具分析引擎造成的問題，因其無法找到所含的符號資訊和原始程式碼資訊對應的 .pdb 檔，例如已編譯檔案的函式名稱和行號。 根據預設，編譯器會在建置應用程式檔案時建立 .pdb 檔。 .pdb 檔案的本機目錄參考會儲存在已編譯的應用程式中。 分析引擎會在參考的目錄中尋找 .pdb 檔，然後在目前包含應用程式檔案的檔案中尋找。 如果找不到 .pdb 檔，分析引擎會使用函式位移，而不是函式名稱。  
  
 您可以下列兩種方式解決這個問題︰  
  
- 找到 .pdb 檔，並放入和應用程式檔案相同的目錄。  
  
- 在程式碼剖析資料 (.vsp) 檔案中內嵌符號資訊。 如需詳細資訊，請參閱[使用效能資料檔案儲存符號資訊](../profiling/saving-symbol-information-with-performance-data-files.md)。  
  
> [!NOTE]
> 分析引擎所需的 .pdb 檔版本要和編譯的應用程式檔案相同。 來自舊版或更新版本的應用程式檔案的 .pdb 檔不適用。
