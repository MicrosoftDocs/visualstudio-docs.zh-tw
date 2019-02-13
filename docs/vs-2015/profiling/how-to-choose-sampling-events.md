---
title: 如何：選擇取樣事件 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.property.sampling
helpviewer_keywords:
- clock cycles sample event
- sample events, choosing
- profiling tools, sample events
- page faults sample event
- system calls sample event
- performance counter sample event
- performance tools, sample events
ms.assetid: ce7cb734-80ac-4930-a4ef-e24395e1cc07
caps.latest.revision: 28
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 78d5e8bbc024009ad6515bdf08c5219253b42d12
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54784508"
---
# <a name="how-to-choose-sampling-events"></a>如何：選擇取樣事件
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

根據預設，[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 程式碼剖析工具收集效能資料的間隔，是分析程序使用的處理器週期數。 一個間隔的預設週期數是 10,000,000，在 1 GH 電腦上約為 0.01 秒。 您可以變更間隔中的週期數，而且可以變更取樣事件。 下列是可用的取樣事件︰  
  
-   時脈週期 - 針對 CPU-bound 問題。  
  
-   分頁錯誤 - 針對記憶體相關問題。  
  
-   系統呼叫 - 針對 I/O 相關問題。  
  
-   效能計數器 - 低階效能問題的 CPU 計數器。  
  
> [!IMPORTANT]
>  如果您使用取樣方法收集 .NET 記憶體資料 (配置或物件存留期，或兩者)，則會忽略所有使用者指定的取樣事件，並會使用適當的記憶體配置或記憶體回收事件 (或兩者) 來收集資料。  
  
### <a name="to-select-a-sample-event"></a>選取取樣事件  
  
1.  在 [效能總管] 中，以滑鼠右鍵按一下效能工作階段，然後按一下 [屬性] 。  
  
2.  在 [屬性頁] 中，按一下 [取樣] 屬性。  
  
3.  從 [取樣事件] 下拉式清單中選取要用來對應用程式進行程式碼剖析的取樣事件。  
  
    > [!NOTE]
    >  只有當您從 [取樣事件] 下拉式清單中選取 [效能計數器] 時，才會啟用 [可用的效能計數器]。  
  
4.  如果您選取 [效能計數器]，請從 [可用的效能計數器] 樹狀檢視控制項中選取特定的 CPU 計數器。  
  
    -   [Portable Events] 節點中的計數器適用於所有類型的處理器。  
  
    -   [Platform Events] 節點中的計數器僅適用於目前電腦上的處理器，可能不適用於其他類型的處理器。  
  
5.  當您選取取樣事件時，[取樣間隔] 文字方塊中會顯示預設的取樣間隔值。 您可視需要在文字方塊中輸入您想要的值。  
  
## <a name="see-also"></a>請參閱  
 [設定效能工作階段](../profiling/configuring-performance-sessions.md)   
 [如何：選擇收集方法](../profiling/how-to-choose-collection-methods.md)   
 [CPU 和 Windows 計數器](../profiling/cpu-and-windows-counters.md)   
 [了解取樣資料值](../profiling/understanding-sampling-data-values.md)   
 [從命令列進行程式碼剖析](../profiling/using-the-profiling-tools-from-the-command-line.md)
