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
ms.openlocfilehash: 91ccf1637d6b8a1f612031c8d59deeef8e07efc7
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60077351"
---
# <a name="troubleshooting-performance-tools-issues"></a>效能工具問題疑難排解
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

當您使用程式碼剖析工具時，可能會遇到下列其中一個問題：  
  
- [程式碼剖析工具沒有收集到任何資料](#NoDataCollected)  
  
- [效能檢視和報表將函式名稱顯示為數字](#NoSymbols)  
  
## <a name="NoDataCollected"></a>程式碼剖析工具沒有收集到任何資料  
 在您分析應用程式之後，並未建立程式碼剖析資料 (.vsp) 檔案，而且您在輸出視窗或命令視窗中收到下列警告：  
  
 PRF0025：未收集任何資料。  
  
 有幾個問題會造成這個問題︰  
  
- 使用取樣或 .NET 記憶體方法分析的處理序，啟動的子處理序會成為執行應用程式工作的處理序。 例如，一些應用程式會讀取該命令列，判斷其要啟動為 Windows 應用程式或命令列應用程式。 如果要求 Windows 應用程式時，原始的處理序會啟動設定為 Windows 應用程式的新處理序，然後結束原始的處理序。 因為程式碼剖析工具不會自動收集子處理序的資料，所以不會收集到任何資料。  
  
     若要在這種情況下收集程式碼剖析資料，請將分析工具附加至子處理序，而不是使用分析工具來啟動應用程式。 如需詳細資訊，請參閱[如何：附加和中斷連結效能工具，來執行處理程序](../profiling/how-to-attach-and-detach-performance-tools-to-running-processes.md)和[附加 (VSPerfCmd)](../profiling/attach.md)  
  
## <a name="NoSymbols"></a>效能檢視和報表將函式名稱顯示為數字  
 在您分析應用程式之後，您在報表和檢視中看到數字，而不是函式名稱。  
  
 這是由程式碼剖析工具分析引擎造成的問題，因其無法找到所含的符號資訊和原始程式碼資訊對應的 .pdb 檔，例如已編譯檔案的函式名稱和行號。 根據預設，編譯器會在建置應用程式檔案時建立 .pdb 檔。 .pdb 檔案的本機目錄參考會儲存在已編譯的應用程式中。 分析引擎會在參考的目錄中尋找 .pdb 檔，然後在目前包含應用程式檔案的檔案中尋找。 如果找不到 .pdb 檔，分析引擎會使用函式位移，而不是函式名稱。  
  
 您可以下列兩種方式解決這個問題︰  
  
- 找到 .pdb 檔，並放入和應用程式檔案相同的目錄。  
  
- 在程式碼剖析資料 (.vsp) 檔案中內嵌符號資訊。 如需詳細資訊，請參閱[使用效能資料檔案儲存符號資訊](../profiling/saving-symbol-information-with-performance-data-files.md)。  
  
> [!NOTE]
>  分析引擎所需的 .pdb 檔版本要和編譯的應用程式檔案相同。 來自舊版或更新版本的應用程式檔案的 .pdb 檔不適用。
