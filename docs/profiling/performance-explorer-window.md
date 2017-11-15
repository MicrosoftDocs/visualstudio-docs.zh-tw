---
title: "效能總管視窗 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.performanceexplorer
- vs.performance.explorer
helpviewer_keywords: performance tools, Performance Explorer
ms.assetid: cb6a6efc-93a5-49a2-8d03-6969b5f3b6d7
caps.latest.revision: "20"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e6fc3be33c332d643e5feb48f4a3733395c2a608
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="performance-explorer-window"></a>效能總管視窗
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]整合式開發環境 (IDE) 中的 [效能總管] 視窗可讓您利用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 程式碼剖析工具來設定及啟動效能工作階段。  
  
 **Requirements**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
## <a name="performance-explorer-toolbar"></a>效能總管工具列  
 下列選項位於 [效能總管] 工具列上：  
  
-   **啟動效能精靈** - 顯示將新的效能工作階段加入 [效能總管] 視窗的 [效能精靈]。  
  
-   **新增效能工作階段** - 將空白的效能工作階段加入 [效能總管] 視窗。  
  
-   **啟動** - [啟動] 命令按鈕清單可讓您啟動立即啟用分析 ([啟動並啟用程式碼剖析]) 或暫停分析 ([啟動並暫停程式碼剖析]) 的目標應用程式。  
  
-   **方法** - 指定工作階段的程式碼剖析方法是取樣或檢測。  
  
-   **停止** - 立即結束目標應用程式和程式碼剖析工具。  
  
-   **附加/中斷連結** - 顯示 [將程式碼剖析工具附加至處理序] 對話方塊，供您選取一個執行中的處理序以附加程式碼剖析工具。  
  
## <a name="performance-explorer-window"></a>效能總管視窗  
 [效能總管] 視窗包含樹狀目錄控制項，其中顯示一或多個效能工作階段的二進位檔和報表資料檔案。  
  
-   **工作階段名稱** - 樹狀目錄控制項的根目錄，其中包含工作階段名稱。 以滑鼠右鍵按一下工作階段名稱可設定工作階段屬性，或啟動目標應用程式和程式碼剖析工具。  
  
-   **目標** - 顯示要在工作階段中進行程式碼剖析的二進位檔的名稱。 以滑鼠右鍵按一下 [目標] 來新增或移除二進位檔、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 專案或網站。 以滑鼠右鍵按一下目標名稱以設定個別二進位檔的屬性。  
  
-   **報表** - 顯示針對工作階段產生的程式碼剖析工具資料檔案的名稱。 以滑鼠右鍵按一下 [報表] 以加入現有的報表，或比較兩個程式碼剖析工具資料檔案。 以滑鼠右鍵按一下報表名稱以開啟、移除或匯出程式碼剖析工具資料檔案。  
  
## <a name="see-also"></a>另請參閱  
 [概觀](../profiling/overviews-performance-tools.md)   
 [設定效能工作階段](../profiling/configuring-performance-sessions.md)   
 [控制資料收集](../profiling/controlling-data-collection.md)