---
title: "如何：為執行中的處理序附加和中斷連結程式碼剖析工具 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.performance.attach
helpviewer_keywords:
- performance tools, attach process
- profiling tools, detach process
- profiling tools, attach process
- performance tools, detach process
- profiler
ms.assetid: 56a99c39-e7f6-4f48-ae56-04ab8e022bf7
caps.latest.revision: "30"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: e847e1295e4514f8e1c327f207a6ae7166c892df
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-attach-and-detach-performance-tools-to-running-processes"></a>如何：為執行中的處理序附加和中斷連結程式碼剖析工具
程式碼剖析工具可以用來附加至或中斷連結執行中的處理序，以協助取樣與蒐集效能資料。 當您想要避免蒐集應用程式載入時間的資料，或是在處理序進入特定狀態後監視其效能時，就可以使用這種方法來執行處理序的程式碼剖析。  
  
> [!NOTE]
>  下列步驟適用於從 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] 整合式開發環境 (IDE) 中附加和中斷連結處理序。 如需使用命令列工具的詳細資訊，請參閱[從命令列進行程式碼剖析](../profiling/using-the-profiling-tools-from-the-command-line.md)。 如需如何對服務進行程式碼剖析的詳細資訊，請參閱[對服務進行程式碼剖析](../profiling/command-line-profiling-of-services.md)。  
  
 可以進行程式碼剖析的處理序，取決於電腦系統管理員所設定的使用者存取權限。 例如，使用者帳戶可能擁有下列任何一項的使用權限：  
  
-   進階程式碼剖析功能 (當系統管理員設定了要啟動的驅動程式和服務時)。  
  
-   只進行取樣程式碼剖析 (網域使用者)。  
  
-   拒絕任何人存取程式碼剖析。  
  
 如需詳細資訊，請參閱[分析和 Windows Vista 安全性](../profiling/profiling-and-windows-vista-security.md)，以及 [VSPerfCmd](../profiling/vsperfcmd.md) 中的 ADMIN 選項。  
  
### <a name="to-attach-to-a-running-process"></a>若要附加至執行中的處理序  
  
1.  在 [偵錯] 功能表上，指向 [分析工具]、[效能總管]，然後按一下 [附加]。    
  
     [將程式碼剖析工具附加至處理序] 對話方塊隨即出現。  
  
2.  按一下您要附加至的處理序名稱。  
  
3.  按一下 [附加] 。  
  
### <a name="to-detach-from-a-running-process"></a>若要從執行中處理序中斷連結  
  
1.  在 [偵錯] 功能表上，指向 [分析工具]、[效能總管]，然後按一下 [中斷連結]。 
  
     [將程式碼剖析工具附加至處理序] 對話方塊隨即出現。  
  
2.  按一下您要中斷連結的映像名稱。  
  
3.  按一下 [中斷連結]。  
  
## <a name="see-also"></a>請參閱  
 [控制資料收集](../profiling/controlling-data-collection.md)   
 [效能工作階段概觀](../profiling/performance-session-overview.md)   
 [如何︰啟動和結束效能資料收集](../profiling/how-to-start-and-end-performance-data-collection.md)   
 [分析和 Windows Vista 安全性](../profiling/profiling-and-windows-vista-security.md)   
 [VSPerfCmd](../profiling/vsperfcmd.md)