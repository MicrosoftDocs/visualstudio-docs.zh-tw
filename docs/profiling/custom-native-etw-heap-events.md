---
title: 自訂原生 ETW 堆積事件 | Microsoft Docs
description: 瞭解如何使用自訂堆積來減少配置額外負荷，但仍會提供配置資訊給記憶體分析工具，以進行配置分析。
ms.custom: SEO-VS-2020
ms.date: 02/24/2017
ms.topic: conceptual
ms.assetid: 668a6603-5082-4c78-98e6-f3dc871aa55b
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- C++
ms.workload:
- cplusplus
ms.openlocfilehash: 61005bf108d0dab16ec419e942e3da97e02cdc7f
ms.sourcegitcommit: d13f7050c873b6284911d1f4acf07cfd29360183
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/22/2021
ms.locfileid: "98686320"
---
# <a name="custom-native-etw-heap-events"></a>自訂原生 ETW 堆積事件

Visual Studio 包含各種[分析與診斷工具](../profiling/profiling-feature-tour.md)，包括原生記憶體分析工具。  此分析工具會從堆積提供者攔截 [ETW 事件](/windows-hardware/drivers/devtest/event-tracing-for-windows--etw-)，並提供記憶體的配置與使用現況分析。  此工具預設只能分析透過標準 Windows 堆積所進行的配置，而不會顯示此原生堆積以外的任何配置。

在許多情況下，您可能想要使用自訂的堆積，以避免來自標準堆積的配置負荷。  比方說，您可以使用 [VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc)，將大量記憶體配置在應用程式或遊戲開頭，接著在該清單內管理自己的區塊。  在此案例中，記憶體分析工具只會查看該初始配置，而不會查看您在記憶體區塊內完成的自訂管理。  不過，使用自訂原生堆積 ETW 提供者時，您就可以讓工具了解您在標準堆積以外進行的任何配置。

例如，在如下專案中，`MemoryPool` 是自訂的堆積，因此您只會在 Windows 堆積上看到單一配置：

```cpp
class Foo
{
public:
    int x, y;
};

...

// MemoryPool is a custom managed heap, which allocates 8192 bytes
// on the standard Windows Heap named "Windows NT"
MemoryPool<Foo, 8192> mPool;

// the "allocate" method requests memory from the pool created above
// and is cast to an object of type Foo, shown above
Foo* pFoo1 = (Foo*)mPool.allocate();
Foo* pFoo2 = (Foo*)mPool.allocate();
Foo* pFoo3 = (Foo*)mPool.allocate();
```

從未追蹤自訂堆積之[記憶體使用量](../profiling/memory-usage.md) \(英文\) 工具擷取的快照，將只會顯示單一的 8192 位元組配置，而不會顯示任何由集區所做的自訂配置：

![Windows 堆積配置](media/heap-example-windows-heap.png)

藉由執行下列步驟，我們可以使用相同的工具來追蹤自訂堆積中的記憶體使用量。

## <a name="how-to-use"></a>如何使用

您可以輕鬆地在 C 和 C++ 中使用此程式庫。

1. 將自訂堆積 ETW 提供者的標頭包含在內：

   ```cpp
   #include <VSCustomNativeHeapEtwProvider.h>
   ```

1. 將 `__declspec(allocator)` 裝飾項目新增至自訂堆積管理員中的任何函式，以傳回新配置之堆積記憶體的指標。  此裝飾項目可讓工具正確識別要傳回的記憶體類型。  例如：

   ```cpp
   __declspec(allocator) void *MyMalloc(size_t size);
   ```

   > [!NOTE]
   > 此裝飾項目會告知編譯器，此函式為配置器的其中一項呼叫。  每個函式呼叫皆會將 CallSite 的位址、呼叫指令的大小和新物件的 typeId 輸出至新的 `S_HEAPALLOCSITE` 符號。  進行 CallStack 配置時，Windows 就會發出 ETW 事件與上述資訊。  記憶體分析工具會逐步引導 CallStack 尋找與 `S_HEAPALLOCSITE` 符號相符的傳回位址；符號中的 typeId 資訊則會用來顯示配置的執行階段類型。
   >
   > 簡單來說，這表示看起來像 `(B*)(A*)MyMalloc(sizeof(B))` 的呼叫在工具中會顯示為 `B` 類型，而非 `void` 或 `A`。

1. 若為 C++，請建立 `VSHeapTracker::CHeapTracker` 物件，並提供要在分析工具中顯示的堆積名稱：

   ```cpp
   auto pHeapTracker = std::make_unique<VSHeapTracker::CHeapTracker>("MyCustomHeap");
   ```

   如果您是使用 C，請改用 `OpenHeapTracker` 函式。  此函式傳回的控制代碼，可讓您在呼叫其他追蹤函式時使用：

   ```C
   VSHeapTrackerHandle hHeapTracker = OpenHeapTracker("MyHeap");
   ```

1. 使用自訂函式配置記憶體時，請呼叫 `AllocateEvent` (C++) 或 `VSHeapTrackerAllocateEvent` (C) 方法，即可傳入記憶體與其大小的指標，以追蹤配置：

   ```cpp
   pHeapTracker->AllocateEvent(memPtr, size);
   ```

   或

   ```C
   VSHeapTrackerAllocateEvent(hHeapTracker, memPtr, size);
   ```

   > [!IMPORTANT]
   > 別忘了使用先前所述的 `__declspec(allocator)` 裝飾項目，來標記您的自訂配置器函式。

1. 使用自訂函式解除配置記憶體時，請呼叫 `DeallocateEvent` (C++) 或 `VSHeapTracerDeallocateEvent` (C) 函式，即可傳入記憶體的指標，以解除配置：

   ```cpp
   pHeapTracker->DeallocateEvent(memPtr);
   ```

   或者：

   ```C
   VSHeapTrackerDeallocateEvent(hHeapTracker, memPtr);
   ```

1. 使用自訂函式解除配置記憶體時，請呼叫 `ReallocateEvent` (C++) 或 `VSHeapReallocateEvent` (C) 方法，即可傳入新記憶體、配置大小，以及舊記憶體的指標：

   ```cpp
   pHeapTracker->ReallocateEvent(memPtrNew, size, memPtrOld);
   ```

   或者：

   ```C
   VSHeapTrackerReallocateEvent(hHeapTracker, memPtrNew, size, memPtrOld);
   ```

1. 最後，若要關閉並清除 C++ 中的自訂堆積追蹤器，您可以透過手動方式、標準的範圍規則，或 `CloseHeapTracker` 函式 (C) 來使用 `CHeapTracker` 解構函式：

   ```cpp
   delete pHeapTracker;
   ```

   或者：

   ```C
   CloseHeapTracker(hHeapTracker);
   ```

## <a name="track-memory-usage"></a>追蹤記憶體使用量
這些呼叫就緒時，您即可使用 Visual Studio 中的標準 [記憶體使用量] 工具，追蹤自訂堆積的使用量。  如需如何使用這項工具的詳細資訊，請參閱[記憶體使用量](../profiling/memory-usage.md)文件。 請確定您已啟用堆積分析快照，否則不會顯示您的自訂堆積使用量。

![啟用堆積分析](media/heap-enable-heap.png)

若要檢視自訂堆積追蹤，請使用位於 [快照] 視窗右上角的 [堆積] 下拉式清單，將 [NT 堆積] 檢視變更為您已命名的堆積。

![堆積選取範圍](media/heap-example-custom-heap.png)

以上述的程式碼範例來看，當我們使用 `MemoryPool` 建立 `VSHeapTracker::CHeapTracker` 物件，並使用我們自己的 `allocate` 方法呼叫 `AllocateEvent` 方法時，您即可看到該自訂配置結果顯示 3 個執行個體，共計有 24 個位元組，且均為 `Foo` 類型。

預設的「NT 堆積」堆積看起來和之前相同，只是新增了我們的 `CHeapTracker` 物件。

![NT 堆積與追蹤程式](media/heap-example-windows-heap.png)

如同使用標準 Windows 堆積一樣，您也可以使用這項工具來比較快照，並在自訂堆積中尋找流失或損毀情況。請參閱主要的[記憶體使用量](../profiling/memory-usage.md)文件，以了解相關說明。

> [!TIP]
> Visual Studio 的 [效能分析] 工具集中也包含 [記憶體使用量] 工具，您可從 [偵錯] > [效能分析工具] 功能表選項或 **Alt**+**F2** 鍵盤組合，加以啟用。  這項功能不包含堆積追蹤，亦不會顯示此處所述的自訂堆積。  只有 [診斷工具] 視窗才包含這項功能 (您可以透過 [偵錯] > [視窗] > [顯示診斷工具] 功能表，或 **Ctrl**+**Alt**+**F2** 鍵盤組合，加以啟用)。

## <a name="see-also"></a>另請參閱
[深入瞭解程式碼剖析工具](../profiling/profiling-feature-tour.md) 
[記憶體使用量](../profiling/memory-usage.md)
