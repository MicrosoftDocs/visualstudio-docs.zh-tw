---
title: DA0005：常見的 GC2 集合 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.DA0005
- vs.performance.rules.DAManyGC2Collections
- vs.performance.5
- vs.performance.rules.DA0005
ms.assetid: 8d3f267c-8a74-4cf4-91a5-0b06a76dc2bd
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5817943ebca51433e64ae3b549af76522992f018
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68158682"
---
# <a name="da0005-frequent-gc2-collections"></a>DA0005：常見的 GC2 集合
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

RuleId |DA0005 |  
|類別目錄 |.NET Framework 使用方式 |  
|程式碼剖析方法 |.NET 記憶體 |  
|訊息 |有許多物件會收集在層代 2 記憶體回收。 |  
|訊息類型 |警告 |  
  
## <a name="cause"></a>原因  
 數量高的 .NET 記憶體物件正在層代 2 記憶體回收中收回。  
  
## <a name="rule-description"></a>規則描述  
 Microsoft .NET 通用語言執行平台 (CLR) 提供一種自動的記憶體管理機制，此機制使用一種記憶體回收行程來回收應用程式不再使用之物件的記憶體。 記憶體回收行程假設許多配置的存留期都很短，因此是層代導向。 例如區域變數的存留期應該很短。 新建立的物件從第 0 代 (gen 0) 開始，然後在記憶體回收執行中留存時進展到第 1 代，如果應用程式一直使用這些物件，最後就會轉換到第 2 代。  
  
 第 0 代中的物件通常會以頻繁且非常有效率的方式回收。 第 1 代中的物件則不會以太頻繁也不會太有效率的方式回收。 最後，在第 2 代中長時間執行的物件則不會太常回收。 第 2 代回收，是執行完整的記憶體回收，也是最耗費資源的作業。  
  
 發生太高比例的第 2 代記憶體回收時，就會引發此規則。 如果有太多存留期相當短的物件在第 1 代回收之後存留下來，但接著就能在第 2 代回收中回收，則記憶體管理的成本很可能會變得過高。 如需詳細資訊，請參閱 MSDN 網站上 Rico Mariani's Performance Tidbits 的[中間存留期危機 (英文)](http://go.microsoft.com/fwlink/?LinkId=177835) 文章。  
  
## <a name="how-to-investigate-a-warning"></a>如何調查警告  
 檢閱 [.NET 記憶體資料檢視](../profiling/dotnet-memory-data-views.md)報表，以了解應用程式的記憶體配置模式。 使用[物件存留期檢視](../profiling/object-lifetime-view.md)可判斷程式的哪些資料物件會存留到第 2 代，然後從該處回收。 使用[配置檢視](../profiling/dotnet-memory-allocations-view.md)可判斷導致這些配置的執行路徑。  
  
 如需如何改善記憶體回收效能的詳細資訊，請參閱 Microsoft 網站上的[記憶體回收行程的基礎概念和效能提示 (英文)](http://go.microsoft.com/fwlink/?LinkId=148226)。 如需有關自動記憶體回收之額外負荷的詳細資訊，請參閱[大型物件堆積的面目 (英文)](http://go.microsoft.com/fwlink/?LinkId=177836)。
