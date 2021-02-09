---
title: 使用 CRT 程式庫尋找記憶體流失 |Microsoft Docs
description: 瞭解 C/c + + 偵錯工具和 C 執行時間程式庫 (CRT) 如何協助找出記憶體流失。 這些技術包括記憶體流失報告和比較記憶體快照集。
ms.custom: SEO-VS-2020
ms.date: 10/04/2018
ms.topic: how-to
dev_langs:
- C++
helpviewer_keywords:
- breakpoints, on memory allocation
- _CrtMemState
- _CrtMemCheckpoint
- memory leaks
- _CrtMemDifference
- memory leaks, detecting and isolating
- _CrtDumpMemoryLeaks
- _CrtSetBreakAlloc
- _crtBreakAlloc
- _CrtSetReportMode
- memory, debugging
- _CrtMemDumpStatistics
- debugging memory leaks
- _CRTDBG_MAP_ALLOC
- _CrtSetDbgFlag
ms.assetid: cf6dc7a6-cd12-4283-b1b6-ea53915f7ed1
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f98bfb3aca5be844018c4c7d9736ab2fa74ebb71
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99870671"
---
# <a name="find-memory-leaks-with-the-crt-library"></a>尋找 CRT 程式庫的記憶體流失問題

記憶體流失是 C/c + + 應用程式中最微妙和難以偵測的錯誤。 因為無法正確解除配置先前配置的記憶體，導致記憶體流失。 一開始可能不會察覺到小型的記憶體流失，但經過一段時間後可能會造成徵兆，從效能不佳到應用程式用盡記憶體時當機。 使用所有可用記憶體的洩漏應用程式可能會導致其他應用程式損毀，而導致應用程式負責時產生混淆。 即使無害的記憶體流失，也可能指出應該更正的其他問題。

[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]偵錯工具和 C 執行時間程式庫 (CRT) 可協助您偵測並找出記憶體流失。

## <a name="enable-memory-leak-detection"></a>啟用記憶體流失偵測

偵測記憶體流失的主要工具是 C/c + + 偵錯工具和 C 執行時間程式庫 (CRT) debug 堆積函數。

若要啟用所有的 debug 堆積函式，請依照下列順序在 c + + 程式中包含下列語句：

```cpp
#define _CRTDBG_MAP_ALLOC
#include <stdlib.h>
#include <crtdbg.h>
```

`#define` 陳述式會將 CRT 堆積函式的基底版本對應到偵錯版本。 如果您省略 `#define` 語句，記憶體流失傾印將會 [較不詳細](#interpret-the-memory-leak-report)。

包括 *crtdbg.h 裡* 會將和函式對應 `malloc` `free` 至其 debug 版本， [_malloc_dbg](/cpp/c-runtime-library/reference/malloc-dbg) 和 [_free_dbg](/cpp/c-runtime-library/reference/free-dbg)，以追蹤記憶體配置和解除配置。 這種對應只會發生在偵錯組建 (具有 `_DEBUG`) 中。 發行的組建使用一般的 `malloc` 和 `free` 函式。

使用上述語句啟用 debug 堆積函數之後，請在應用程式結束點之前放置 [_CrtDumpMemoryLeaks](/cpp/c-runtime-library/reference/crtdumpmemoryleaks) 的呼叫，以在應用程式結束時顯示記憶體流失報告。

```cpp
_CrtDumpMemoryLeaks();
```

如果您的應用程式有數個結束，您就不需要 `_CrtDumpMemoryLeaks` 在每個結束點手動放置。 若要 `_CrtDumpMemoryLeaks` 在每個結束點上自動呼叫，請在您的 `_CrtSetDbgFlag` 應用程式開始時呼叫，其位欄位如下所示：

```cpp
_CrtSetDbgFlag ( _CRTDBG_ALLOC_MEM_DF | _CRTDBG_LEAK_CHECK_DF );
```

根據預設， `_CrtDumpMemoryLeaks` 會將記憶體流失報告輸出至 [輸出]  視窗的 [偵錯]  窗格。 如果您使用程式庫，該程式庫可能會重設輸出至其他位置。

您可以使用 `_CrtSetReportMode` 將報表重新導向至另一個位置，或重新導向至 [ **輸出** ] 視窗，如下所示：

```cpp
_CrtSetReportMode( _CRT_WARN, _CRTDBG_MODE_DEBUG );
```

## <a name="interpret-the-memory-leak-report"></a>解讀記憶體流失報告

如果您的應用程式未定義 `_CRTDBG_MAP_ALLOC` ， [_CrtDumpMemoryLeaks](/cpp/c-runtime-library/reference/crtdumpmemoryleaks) 會顯示如下的記憶體流失報告：

```cmd
Detected memory leaks!
Dumping objects ->
{18} normal block at 0x00780E80, 64 bytes long.
 Data: <                > CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD
Object dump complete.
```

如果您的應用程式定義了 `_CRTDBG_MAP_ALLOC` ，記憶體流失報告看起來會像這樣：

```cmd
Detected memory leaks!
Dumping objects ->
c:\users\username\documents\projects\leaktest\leaktest.cpp(20) : {18}
normal block at 0x00780E80, 64 bytes long.
 Data: <                > CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD
Object dump complete.
```

第二份報表顯示第一次配置洩漏記憶體的檔案名和行號。

無論您是否定義 `_CRTDBG_MAP_ALLOC` ，記憶體流失報告都會顯示：

- 記憶體配置編號， `18` 在此範例中
- 區塊類型， `normal` 在此範例中。
- 十六進位記憶體位置， `0x00780E80` 在此範例中。
- 區塊的大小， `64 bytes` 在此範例中為。
- 區塊中前 16 個位元組的資料 (十六進位格式)。

記憶體區塊類型為 *一般*、 *用戶端* 或 *CRT*。 *「一般區塊」* (Normal Block) 是您的程式所配置的一般記憶體。 *「用戶端區塊」* (Client Block) 是 MFC 程式專為需要解構函式的物件所使用的一種特殊類型的記憶體區塊。 MFC 的 `new` 運算子會根據所建立的物件來建立一般區塊或用戶端區塊。

*「CRT 區塊」* (CRT Block) 則是 CRT 程式庫配置來供自身使用的記憶體區塊。 CRT 程式庫會處理這些區塊的解除配置，因此 CRT 區塊不會出現在記憶體流失報告中，除非 CRT 程式庫發生嚴重問題。

另外還有兩種絕對不會出現在記憶體流失報告中的記憶體區塊。 *可用區塊* 是已釋放的記憶體，因此不會流失定義。 「 *忽略區塊」（ignore block* ）是您明確標示為從記憶體流失報告中排除的記憶體。

上述技術會識別使用標準 CRT 函數配置的記憶體記憶體流失 `malloc` 。 但是，如果您的程式使用 c + + 運算子來配置記憶體 `new` ，您可能只會看到檔案名和行號，也就 `operator new` `_malloc_dbg` 是記憶體流失報告中的呼叫。 若要建立更有用的記憶體流失報表，您可以撰寫如下所示的宏來報告進行配置的那一行：

```cpp
#ifdef _DEBUG
    #define DBG_NEW new ( _NORMAL_BLOCK , __FILE__ , __LINE__ )
    // Replace _NORMAL_BLOCK with _CLIENT_BLOCK if you want the
    // allocations to be of _CLIENT_BLOCK type
#else
    #define DBG_NEW new
#endif
```

現在您可以 `new` `DBG_NEW` 在程式碼中使用宏來取代操作員。 在 debug 組建中， `DBG_NEW` 會使用 global 的多載，以 `operator new` 接受區塊類型、檔案和行號的其他參數。 `new` `_malloc_dbg` 用於記錄額外資訊的呼叫多載。 記憶體流失報告會顯示已配置遺漏物件的檔案名和行號。 發行組建仍會使用預設值 `new` 。 以下是這項技術的範例：

```cpp
// debug_new.cpp
// compile by using: cl /EHsc /W4 /D_DEBUG /MDd debug_new.cpp
#define _CRTDBG_MAP_ALLOC
#include <cstdlib>
#include <crtdbg.h>

#ifdef _DEBUG
    #define DBG_NEW new ( _NORMAL_BLOCK , __FILE__ , __LINE__ )
    // Replace _NORMAL_BLOCK with _CLIENT_BLOCK if you want the
    // allocations to be of _CLIENT_BLOCK type
#else
    #define DBG_NEW new
#endif

struct Pod {
    int x;
};

void main() {
    Pod* pPod = DBG_NEW Pod;
    pPod = DBG_NEW Pod; // Oops, leaked the original pPod!
    delete pPod;

    _CrtDumpMemoryLeaks();
}
```

當您在 Visual Studio 偵錯工具中執行此程式碼時，呼叫會在 `_CrtDumpMemoryLeaks` **輸出** 視窗中產生報告，如下所示：

```Output
Detected memory leaks!
Dumping objects ->
c:\users\username\documents\projects\debug_new\debug_new.cpp(20) : {75}
 normal block at 0x0098B8C8, 4 bytes long.
 Data: <    > CD CD CD CD
Object dump complete.
```

此輸出報告遺漏的配置是在 *debug_new .cpp* 的第20行上。

>[!NOTE]
>我們不建議您建立名為的預處理器宏 `new` ，或任何其他語言關鍵字。

## <a name="set-breakpoints-on-a-memory-allocation-number"></a>在記憶體配置編號上設定中斷點

記憶體配置編號會指出流失的記憶體區塊是何時配置的。 例如，記憶體配置編號為18的區塊，是在應用程式執行期間所配置的第18個記憶體區塊。 CRT 報表會計算執行期間的所有記憶體區塊配置，包括 CRT 程式庫和其他程式庫（例如 MFC）的配置。 因此，記憶體配置區塊編號18可能不是您的程式碼所配置的第18個記憶體區塊。

您可以使用配置編號在記憶體配置上設定中斷點。

**若要使用監看式視窗設定記憶體配置中斷點：**

1. 在應用程式的開頭附近設定中斷點，然後開始進行偵錯工具。

1. 當應用程式在中斷點暫停時，請選取 [ **Debug** Windows   >    >  **Watch 1** (] 或 **[觀賞 2**]、 **[監看式 3**] 或 **[觀賞 4]**) 開啟 [監看式] 視窗。

1. 在 [ **監看** 式] 視窗中，輸入 `_crtBreakAlloc` [ **名稱** ] 資料行。

   如果您要使用 CRT 程式庫的多執行緒 DLL 版本 (/MD 選項) ，請新增內容運算子： `{,,ucrtbased.dll}_crtBreakAlloc`
   
   請確定已載入 debug 符號。 否則 `_crtBreakAlloc` 將會回報為無法 *識別*。

1. 按 **Enter**。

   偵錯工具會評估呼叫，並將結果放在 [值]  欄中。 如果您尚未在記憶體配置上設定任何中斷點，此值將會是 **-1** 。

1. 在 [ **值** ] 資料行中，將值取代為您想要偵錯工具中斷的記憶體配置的配置編號。

在記憶體配置編號上設定中斷點之後，請繼續進行 debug。 請務必在相同的情況下執行，因此記憶體配置編號不會變更。 當您的程式在指定的記憶體配置中斷時，請使用 [ **呼叫堆疊** ] 視窗和其他偵錯工具視窗，判斷記憶體配置所依據的條件。 然後，您可以繼續執行以觀察物件發生什麼事，並判斷它未正確解除配置的原因。

在物件上設定資料中斷點可能也很有用。 如需詳細資訊，請參閱 [使用中斷點](../debugger/using-breakpoints.md)。

您也可以在程式碼中設定記憶體配置中斷點。 您可以設定：

```cpp
_crtBreakAlloc = 18;
```

 或者：

```cpp
_CrtSetBreakAlloc(18);
```

## <a name="compare-memory-states"></a>比較記憶體狀態

另一種尋找記憶體流失的技術，是使用在關鍵點的應用程式記憶體狀態之快照。 若要在應用程式中的某個時間點建立記憶體狀態的快照，請建立 `_CrtMemState` 結構，並將它傳遞至函式 `_CrtMemCheckpoint` 。

```cpp
_CrtMemState s1;
_CrtMemCheckpoint( &s1 );
```

函數會以 `_CrtMemCheckpoint` 目前記憶體狀態的快照集填滿結構。

若要輸出結構的內容 `_CrtMemState` ，請將結構傳遞給函式 `_ CrtMemDumpStatistics` ：

```cpp
_CrtMemDumpStatistics( &s1 );
```

`_ CrtMemDumpStatistics` 輸出記憶體狀態的傾印，看起來像這樣：

```cmd
0 bytes in 0 Free Blocks.
0 bytes in 0 Normal Blocks.
3071 bytes in 16 CRT Blocks.
0 bytes in 0 Ignore Blocks.
0 bytes in 0 Client Blocks.
Largest number used: 3071 bytes.
Total allocations: 3764 bytes.
```

若要判斷記憶體流失是否發生在程式碼區段裡，您可以建立區段前和區段後的記憶體狀態快照，然後使用 `_ CrtMemDifference` 比較這兩個狀態：

```cpp
_CrtMemCheckpoint( &s1 );
// memory allocations take place here
_CrtMemCheckpoint( &s2 );

if ( _CrtMemDifference( &s3, &s1, &s2) )
   _CrtMemDumpStatistics( &s3 );
```

`_CrtMemDifference` 比較記憶體狀態，並傳回 `s1` `s2` () 中的結果， `s3` 這是與之間的 `s1` 差異 `s2` 。

尋找記憶體流失的其中一種方法 `_CrtMemCheckpoint` ，是在應用程式的開頭和結尾放置呼叫，然後使用 `_CrtMemDifference` 來比較結果。 如果 `_CrtMemDifference` 顯示記憶體流失，您可以 `_CrtMemCheckpoint` 使用二進位搜尋來新增更多呼叫來分割您的程式，直到您隔離出流失的來源為止。

## <a name="false-positives"></a>誤報

 `_CrtDumpMemoryLeaks` 如果程式庫將內部配置標示為一般區塊，而不是 CRT 區塊或用戶端區塊，則可以提供錯誤的記憶體流失指示。 在這種情況下， `_CrtDumpMemoryLeaks` 無法區分使用者配置和內部程式庫配置。 如果在您呼叫 `_CrtDumpMemoryLeaks`之後執行程式庫配置的全域解構函式，則每個內部程式庫配置都會報告為記憶體流失。 早于 Visual Studio .NET 的標準樣板程式庫版本可能會導致 `_CrtDumpMemoryLeaks` 報告這類誤報。

## <a name="see-also"></a>另請參閱

- [CRT 偵錯堆積詳細資料](../debugger/crt-debug-heap-details.md)
- [偵錯工具安全性](../debugger/debugger-security.md)
- [程式碼的偵錯工具](../debugger/debugging-native-code.md)
