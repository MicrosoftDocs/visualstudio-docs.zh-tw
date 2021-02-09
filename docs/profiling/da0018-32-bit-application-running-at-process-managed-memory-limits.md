---
title: DA0018-32-以進程 managed 記憶體限制執行的位應用程式 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.performance.18
- vs.performance.DA0018
- vs.performance.rules.DA0018
ms.assetid: 98eb2d96-f92f-42f9-915c-e5ac2330ffbf
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: f5730e96a47e7e931606269341d5f1cca302a0e5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99886388"
---
# <a name="da0018-32-bit-application-running-at-process-managed-memory-limits"></a>DA0018：以處理序 Managed 記憶體限制執行的 32 位元應用程式

|Item|值|
|-|-|
|規則 ID|DA0018|
|類別|分析工具使用方式|
|程式碼剖析方法|取樣|
|訊息|Managed 記憶體配置接近 32 位元處理序的預設限制。 您的應用程式可能是記憶體繫結。|
|規則型別|警告|

 當您使用取樣、.NET 記憶體或資源爭用方法進行分析時，必須至少收集 10 個樣本才能觸發此規則。

## <a name="cause"></a>原因
 分析執行期間收集的系統資料指出，.NET Framework 記憶體堆積已接近 Managed 堆積在 32 位元處理序中可以到達的大小上限。 此大小上限是預設值。 此值是根據可為私用位元組配置的處理序位址空間總量。 報告的值是當分析的處理序作用中時，堆積的最大觀察值。 請考慮使用 .NET 記憶體分析方法再次進行分析，並最佳化應用程式使用的 Managed 資源。

 當 Managed 堆積的大小接近預設限制時，可能需要更頻繁地叫用自動記憶體回收處理序。 這會增加記憶體管理的負擔。

 在 32 位元電腦上執行的 32 位元應用程式才會引發此規則。

## <a name="rule-description"></a>規則描述
 Microsoft .NET 通用語言執行平台 (CLR) 提供一種自動的記憶體管理機制，此機制使用一種記憶體回收行程回收應用程式不再使用之物件的記憶體。 記憶體回收行程假設許多配置的存留期都很短，因此是層代導向。 例如區域變數的存留期應該很短。 新建立的物件從第 0 代 (gen 0) 開始，然後在記憶體回收執行中留存時進展到第 1 代，如果應用程式一直使用這些物件，最後就會轉換到第 2 代。

 大於 85 KB 的 Managed 物件會配置在大型物件堆積上，比起小型物件，比較不會受到頻繁的記憶體回收和壓縮。 大型物件會分開管理，因為一般認為大型物件通常比較持久，而且因為將持久而大型的物件與經常配置的較小型物件混合可能會產生最分散的堆積。

 當 Managed 堆積的總大小接近預設限制時，記憶體管理的負擔通常會變大而開始影響應用程式的回應性和延展性。

## <a name="how-to-investigate-a-warning"></a>如何調查警告
 按兩下 [錯誤清單] 視窗中的訊息，流覽至 [ [標記](../profiling/marks-view.md) ] view。 尋找 **.NET CLR Memory\\# Bytes in all Heaps** 和 **# Total committed bytes** 欄。 判斷是否有特定的程式執行階段，當中的 Managed 記憶體配置比其他階段更繁重。 將 **# Bytes in all Heaps** 欄的值與 **.NET CLR Memory\\# of Gen 0 Collections**、**.NET CLR Memory\\# of Gen 1 Collections** 和 **.NET CLR Memory\\# of Gen 2 Collections** 欄中報告的記憶體回收速度比較，判斷 Managed 記憶體配置的模式是否會影響記憶體回收的速率。

 在 .NET Framework 應用程式中，通用語言執行平台限制 Managed 堆積的大小上限要稍微小於處理序位址空間之私用區域部分大小上限的一半。 對於在 32 位元電腦上執行的 32 位元處理序，2GB 代表處理序位址空間之私用部分的上限。 當 Managed 堆積的總大小開始接近預設限制時，可能會增加管理記憶體的負擔，且會降低應用程式效能。

 如果 Managed 記憶體負擔過重是問題，請考量下列其中一個選項︰

- 最佳化 Managed 記憶體資源的應用程式使用方式

   -或-

- 採取步驟解除 32 位元處理序之虛擬記憶體大小上限的架構限制

  若要最佳化 Managed 記憶體資源的應用程式使用方式，請在 .NET 記憶體配置分析執行中收集 Managed 記憶體配置資料。 請參閱 [.Net 記憶體資料檢視](../profiling/dotnet-memory-data-views.md) 報表，以瞭解應用程式的記憶體配置模式。

  您可以使用 [ [物件存留期] 視圖](../profiling/object-lifetime-view.md) ，判斷程式的哪些資料物件會在產生中存活，然後從該處回收。

  使用[配置檢視](../profiling/dotnet-memory-allocations-view.md)可判斷導致這些配置的執行路徑。

  如需如何改善記憶體回收效能的詳細資訊，請參閱 MSDN 網站上的 .NET Framework 技術文件：[記憶體回收行程的基礎概念和效能提示 (英文)](/previous-versions/dotnet/articles/ms973837(v=msdn.10))。

  若要對處理序位址空間之私用部分大小解除虛擬記憶體的架構限制，請嘗試在 64 位元電腦上執行這個 32 位元處理序。  在 64 位元電腦上的 32 位元處理序可以取得高達 4 GB 的私用虛擬記憶體。

  在 64 位元電腦上執行的 64 位元處理序可以取得高達 8 TB 的虛擬記憶體。 請考慮重新編譯應用程式，以原生的 64 位元應用程式執行。 此規則僅供參考，可能不需要更正措施。
