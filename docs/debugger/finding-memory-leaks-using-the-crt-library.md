---
title: 使用 CRT 程式庫尋找記憶體流失 |Microsoft Docs
ms.date: 10/04/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: eb2729dcaf0da41c0adac24b0e1909a6d2697eb6
ms.sourcegitcommit: 697f2ab875fd789685811687387e9e8e471a38c4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "74829937"
---
# <a name="find-memory-leaks-with-the-crt-library"></a>尋找 CRT 程式庫的記憶體流失問題

記憶體流失是 C/C++應用程式中最微妙且難以偵測的錯誤。 記憶體流失的原因是無法正確地解除配置先前配置的記憶體。 一開始可能不會注意到小型的記憶體流失，但經過一段時間後，可能會導致應用程式用盡記憶體時，效能不佳的徵兆。 洩漏的應用程式若使用所有可用的記憶體，可能會導致其他應用程式損毀，並對應用程式的責任造成混淆。 即使是無害的記憶體流失，也可能表示其他應該更正的問題。

 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 偵錯工具和 C 執行時間程式庫（CRT）可協助您偵測並找出記憶體流失的問題。

## <a name="enable-memory-leak-detection"></a>啟用記憶體流失偵測

偵測記憶體流失的主要工具是 C/C++偵錯工具和 c 執行時間程式庫（CRT）的 debug 堆積函數。

若要啟用所有的 debug 堆積函式，請依照下列順序C++在程式中包含下列語句：

```cpp
#define _CRTDBG_MAP_ALLOC
#include <stdlib.h>
#include <crtdbg.h>
```

`#define` 陳述式會將 CRT 堆積函式的基底版本對應到偵錯版本。 如果您省略 `#define` 語句，記憶體流失傾印將會[較不詳細](#interpret-the-memory-leak-report)。

包括*crtdbg.h 裡*會將 `malloc` 和 `free` 函數對應至其 debug 版本， [_malloc_dbg](/cpp/c-runtime-library/reference/malloc-dbg)和[_free_dbg](/cpp/c-runtime-library/reference/free-dbg)，以追蹤記憶體配置和解除配置。 這種對應只會發生在偵錯組建 (具有 `_DEBUG`) 中。 發行的組建使用一般的 `malloc` 和 `free` 函式。

使用上述語句啟用 debug 堆積函數之後，請在應用程式結束點之前呼叫[_CrtDumpMemoryLeaks](/cpp/c-runtime-library/reference/crtdumpmemoryleaks) ，以在應用程式結束時顯示記憶體流失的報告。

```cpp
_CrtDumpMemoryLeaks();
```

如果您的應用程式有數個結束，您就不需要在每個結束點手動放置 `_CrtDumpMemoryLeaks`。 若要在每個結束點上自動呼叫 `_CrtDumpMemoryLeaks`，請在應用程式開頭處呼叫 `_CrtSetDbgFlag`，其中包含位欄位，如下所示：

```cpp
_CrtSetDbgFlag ( _CRTDBG_ALLOC_MEM_DF | _CRTDBG_LEAK_CHECK_DF );
```

根據預設， `_CrtDumpMemoryLeaks` 會將記憶體流失報告輸出至 [輸出] 視窗的 [偵錯] 窗格。 如果您使用程式庫，該程式庫可能會重設輸出至其他位置。

您可以使用 `_CrtSetReportMode` 將報表重新導向至另一個位置，或回到 [**輸出**] 視窗，如下所示：

```cpp
_CrtSetReportMode( _CRT_ERROR, _CRTDBG_MODE_DEBUG );
```

## <a name="interpret-the-memory-leak-report"></a>解讀記憶體流失報告

如果您的應用程式未定義 `_CRTDBG_MAP_ALLOC`， [_CrtDumpMemoryLeaks](/cpp/c-runtime-library/reference/crtdumpmemoryleaks)會顯示記憶體流失報告，如下所示：

```cmd
Detected memory leaks!
Dumping objects ->
{18} normal block at 0x00780E80, 64 bytes long.
 Data: <                > CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD
Object dump complete.
```

如果您的應用程式定義 `_CRTDBG_MAP_ALLOC`，記憶體流失報告看起來會像這樣：

```cmd
Detected memory leaks!
Dumping objects ->
c:\users\username\documents\projects\leaktest\leaktest.cpp(20) : {18}
normal block at 0x00780E80, 64 bytes long.
 Data: <                > CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD
Object dump complete.
```

第二份報表會顯示第一次配置洩漏記憶體的檔案名和行號。

無論您是否定義 `_CRTDBG_MAP_ALLOC`，記憶體流失報告都會顯示：

- 記憶體配置編號，在範例中 `18`
- 範例中的區塊類型 `normal`。
- 在範例中 `0x00780E80` 的十六進位記憶體位置。
- 區塊的大小，在範例中 `64 bytes`。
- 區塊中前 16 個位元組的資料 (十六進位格式)。

記憶體區塊類型為*normal*、 *client*或*CRT*。 *「一般區塊」* (Normal Block) 是您的程式所配置的一般記憶體。 *「用戶端區塊」* (Client Block) 是 MFC 程式專為需要解構函式的物件所使用的一種特殊類型的記憶體區塊。 MFC 的 `new` 運算子會根據所建立的物件來建立一般區塊或用戶端區塊。

*「CRT 區塊」* (CRT Block) 則是 CRT 程式庫配置來供自身使用的記憶體區塊。 CRT 程式庫會處理這些區塊的解除配置，因此 CRT 區塊不會出現在記憶體流失報告中，除非 CRT 程式庫有嚴重的問題。

另外還有兩種絕對不會出現在記憶體流失報告中的記憶體區塊。 「*可用區塊*」是已釋放的記憶體，因此定義不會洩漏。 「*忽略區塊*」是指您已明確標記為要從記憶體流失報告中排除的記憶體。

上述技巧會識別使用標準 CRT `malloc` 函式所配置記憶體的記憶體流失。 不過，如果您的C++程式使用 `new` 運算子配置記憶體，您可能只會看到 `operator new` 在記憶體流失報告中 `_malloc_dbg` 呼叫的檔案名和行號。 若要建立更有用的記憶體流失報告，您可以撰寫如下所示的宏來報告進行配置的那一行：

```cpp
#ifdef _DEBUG
    #define DBG_NEW new ( _NORMAL_BLOCK , __FILE__ , __LINE__ )
    // Replace _NORMAL_BLOCK with _CLIENT_BLOCK if you want the
    // allocations to be of _CLIENT_BLOCK type
#else
    #define DBG_NEW new
#endif
```

現在您可以在程式碼中使用 `DBG_NEW` 宏來取代 `new` 運算子。 在 debug 組建中，`DBG_NEW` 會使用全域 `operator new` 的多載，以取得區塊類型、檔案和行號的其他參數。 `new` 的多載會呼叫 `_malloc_dbg` 來記錄額外的資訊。 記憶體流失報告會顯示配置遺漏物件的檔案名和行號。 發行組建仍然會使用預設 `new`。 以下是此技巧的範例：

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

當您在 Visual Studio 偵錯工具中執行此程式碼時，`_CrtDumpMemoryLeaks` 的呼叫會在 [**輸出**] 視窗中產生報告，如下所示：

```Output
Detected memory leaks!
Dumping objects ->
c:\users\username\documents\projects\debug_new\debug_new.cpp(20) : {75}
 normal block at 0x0098B8C8, 4 bytes long.
 Data: <    > CD CD CD CD
Object dump complete.
```

此輸出報告遺漏的配置是在*debug_new .cpp*的第20行。

>[!NOTE]
>我們不建議您建立名為 `new`或任何其他 language 關鍵字的預處理器宏。

## <a name="set-breakpoints-on-a-memory-allocation-number"></a>在記憶體配置編號上設定中斷點

記憶體配置編號會指出流失的記憶體區塊是何時配置的。 例如，記憶體配置編號為18的區塊，是在應用程式執行期間所配置的第18個記憶體區塊。 CRT 報表會計算執行期間所有的記憶體區塊配置，包括 CRT 程式庫和其他程式庫（例如 MFC）的配置。 因此，記憶體配置區塊編號18可能不是您的程式碼所配置的第18個記憶體區塊。

您可以使用配置編號在記憶體配置上設定中斷點。

**使用監看式視窗設定記憶體配置中斷點：**

1. 在接近應用程式開頭處設定中斷點，並開始進行偵錯工具。

1. 當應用程式在中斷點暫停時，請選取 [ **Debug** ] > **Windows** > **watch 1** （或**watch 2**、 **Watch 3**或**watch 4**）來開啟 **[監看**式] 視窗。

1. 在 [**監看**式] 視窗的 [**名稱**] 欄中，輸入 `_crtBreakAlloc`。

   如果您使用的是 CRT 程式庫（/MD 選項）的多執行緒 DLL 版本，請新增內容運算子： `{,,ucrtbased.dll}_crtBreakAlloc`
   
   請確定已載入偵錯工具符號。 否則 `_crtBreakAlloc` 會*回報為 [* 無法辨識]。

1. 按 **Enter** 鍵。

   偵錯工具會評估呼叫，並將結果放在 [值] 欄中。 如果您尚未在記憶體配置上設定任何中斷點，此值將會是 **-1**。

1. 在 [**值**] 資料行中，將值取代為您想要偵錯工具中斷之記憶體配置的配置編號。

在記憶體配置編號上設定中斷點之後，請繼續進行 debug。 請務必在相同的條件下執行，因此記憶體配置編號不會變更。 當您的程式在指定的記憶體配置中斷時，請使用 [**呼叫堆疊**] 視窗和其他偵錯工具視窗來判斷配置記憶體所用的條件。 然後，您可以繼續執行以觀察物件會發生什麼情況，並判斷它為何未正確解除配置。

在物件上設定資料中斷點可能也很有用。 如需詳細資訊，請參閱[使用中斷點](../debugger/using-breakpoints.md)。

您也可以在程式碼中設定記憶體配置中斷點。 您可以設定：

```cpp
_crtBreakAlloc = 18;
```

 或：

```cpp
_CrtSetBreakAlloc(18);
```

## <a name="compare-memory-states"></a>比較記憶體狀態
 另一種尋找記憶體流失的技術，是使用在關鍵點的應用程式記憶體狀態之快照。 若要取得應用程式中指定點的記憶體狀態快照，請建立 `_CrtMemState` 結構，並將它傳遞給 `_CrtMemCheckpoint` 函數。

```cpp
_CrtMemState s1;
_CrtMemCheckpoint( &s1 );
```

`_CrtMemCheckpoint` 函數會以目前記憶體狀態的快照填入結構。

若要輸出 `_CrtMemState` 結構的內容，請將結構傳遞給 `_ CrtMemDumpStatistics` 函數：

```cpp
_CrtMemDumpStatistics( &s1 );
```

`_ CrtMemDumpStatistics` 會輸出如下所示的記憶體狀態傾印：

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

`_CrtMemDifference` 會比較 `s1` 和 `s2` 的記憶體狀態，並傳回（`s3`）中的結果，這是 `s1` 和 `s2`之間的差異。

尋找記憶體流失的一項技術，一開始會先將 `_CrtMemCheckpoint` 呼叫放在應用程式的開頭和結尾，然後使用 `_CrtMemDifference` 來比較結果。 如果 `_CrtMemDifference` 顯示記憶體流失，您可以使用二進位搜尋來新增更多 `_CrtMemCheckpoint` 呼叫來分割您的程式，直到您隔離出遺漏的來源為止。

## <a name="false-positives"></a>誤報
 如果程式庫將內部配置標記為一般區塊，而不是 CRT 區塊或用戶端區塊，`_CrtDumpMemoryLeaks` 可以提供錯誤的記憶體流失指示。 在這種情況下， `_CrtDumpMemoryLeaks` 無法區分使用者配置和內部程式庫配置。 如果在您呼叫 `_CrtDumpMemoryLeaks`之後執行程式庫配置的全域解構函式，則每個內部程式庫配置都會報告為記憶體流失。 Versions of the Standard Template Library earlier than Visual Studio .NET may cause `_CrtDumpMemoryLeaks` to report such false positives.

## <a name="see-also"></a>請參閱
- [CRT 偵錯堆積詳細資料](../debugger/crt-debug-heap-details.md)
- [偵錯工具安全性](../debugger/debugger-security.md)
- [對機器碼進行偵錯](../debugger/debugging-native-code.md)
