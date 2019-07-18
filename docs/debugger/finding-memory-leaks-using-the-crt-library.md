---
title: 尋找記憶體流失的 CRT 程式庫 |Microsoft Docs
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
ms.openlocfilehash: e7fdfedbb2f632bdb0fcaa05c7f0fb282a8fcd2b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62849977"
---
# <a name="find-memory-leaks-with-the-crt-library"></a>尋找 CRT 程式庫的記憶體流失問題

記憶體流失是最細微和硬偵測的錯誤以 C /C++應用程式。 記憶體流失結果失敗，無法正確解除配置先前配置的記憶體。 只有少許記憶體流失可能不會在一開始，注意到，但經過一段時間可能會導致舉凡損毀時記憶體不足所執行的應用程式的效能不佳的徵狀。 負責建立有關哪一個應用程式的混淆到遺漏的應用程式，會用完所有可用的記憶體可能會造成其他應用程式當機。 即使是無害的記憶體流失可能表示應該解決其他問題。

 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]偵錯工具和 C 執行階段程式庫 (CRT) 可協助您偵測和找出記憶體流失。

## <a name="enable-memory-leak-detection"></a>啟用記憶體流失偵測

偵測記憶體流失的主要工具是 C /C++偵錯工具和 C 執行階段程式庫 (CRT) 偵錯堆積函式。

若要啟用所有偵錯堆積函式，包括下列的陳述式，在您C++程式中的，依下列順序：

```cpp
#define _CRTDBG_MAP_ALLOC
#include <stdlib.h>
#include <crtdbg.h>
```

`#define` 陳述式會將 CRT 堆積函式的基底版本對應到偵錯版本。 如果您省略`#define`陳述式，記憶體流失傾印將會是[較不詳細](#interpret-the-memory-leak-report)。

包括*crtdbg.h*對應`malloc`並`free`為其偵錯版本中，函式[_malloc_dbg](/cpp/c-runtime-library/reference/malloc-dbg)並[_free_dbg](/cpp/c-runtime-library/reference/free-dbg)，可追蹤記憶體配置和解除配置。 這種對應只會發生在偵錯組建 (具有 `_DEBUG`) 中。 發行的組建使用一般的 `malloc` 和 `free` 函式。

您已啟用偵錯堆積函式，使用先前的陳述式之後，以撥打[_CrtDumpMemoryLeaks](/cpp/c-runtime-library/reference/crtdumpmemoryleaks)之前顯示的記憶體流失報告應用程式結束時的應用程式結束點。

```cpp
_CrtDumpMemoryLeaks();
```

如果您的應用程式會有數個結束，您不需要以手動方式放置`_CrtDumpMemoryLeaks`在每個結束點。 若要讓自動呼叫`_CrtDumpMemoryLeaks`在每個結束點，以撥打`_CrtSetDbgFlag`在您的應用程式，如下所示的位元欄位的開頭：

```cpp
_CrtSetDbgFlag ( _CRTDBG_ALLOC_MEM_DF | _CRTDBG_LEAK_CHECK_DF );
```

根據預設， `_CrtDumpMemoryLeaks` 會將記憶體流失報告輸出至 [輸出]  視窗的 [偵錯]  窗格。 如果您使用程式庫，該程式庫可能會重設輸出至其他位置。

您可以使用`_CrtSetReportMode`將報告重新導向到其他位置，或回到**輸出**視窗如下所示：

```cpp
_CrtSetReportMode( _CRT_ERROR, _CRTDBG_MODE_DEBUG );
```

## <a name="interpret-the-memory-leak-report"></a>解譯記憶體流失報告

如果您的應用程式未定義`_CRTDBG_MAP_ALLOC`， [_CrtDumpMemoryLeaks](/cpp/c-runtime-library/reference/crtdumpmemoryleaks)會顯示如下所示的記憶體流失報告：

```cmd
Detected memory leaks!
Dumping objects ->
{18} normal block at 0x00780E80, 64 bytes long.
 Data: <                > CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD
Object dump complete.
```

如果您的應用程式定義`_CRTDBG_MAP_ALLOC`，記憶體流失報告看起來像：

```cmd
Detected memory leaks!
Dumping objects ->
c:\users\username\documents\projects\leaktest\leaktest.cpp(20) : {18}
normal block at 0x00780E80, 64 bytes long.
 Data: <                > CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD
Object dump complete.
```

第二份報表顯示的檔名和行號，第一次配置流失的記憶體位置。

您的定義，zda bude `_CRTDBG_MAP_ALLOC`，會顯示記憶體流失報告：

- 記憶體配置編號，這是`18`範例
- 區塊型別，`normal`在範例中。
- 十六進位記憶體位置，`0x00780E80`在範例中。
- 區塊大小`64 bytes`在範例中。
- 區塊中前 16 個位元組的資料 (十六進位格式)。

記憶體區塊類型*正常*，*用戶端*，或*CRT*。 *「一般區塊」* (Normal Block) 是您的程式所配置的一般記憶體。 *「用戶端區塊」* (Client Block) 是 MFC 程式專為需要解構函式的物件所使用的一種特殊類型的記憶體區塊。 MFC 的 `new` 運算子會根據所建立的物件來建立一般區塊或用戶端區塊。

*「CRT 區塊」* (CRT Block) 則是 CRT 程式庫配置來供自身使用的記憶體區塊。 CRT 程式庫會處理這些區塊，解除配置，因此 CRT 區塊就不會出現記憶體流失報告中，除非有嚴重的問題，CRT 程式庫。

另外還有兩種絕對不會出現在記憶體流失報告中的記憶體區塊。 A*釋放的區塊*是已發行，因此依定義未流失的記憶體。 *忽略區塊*是您已明確標記為要從記憶體流失報告中排除的記憶體。

上述的技術找出記憶體流失的記憶體配置以標準 crt`malloc`函式。 如果您的程式可讓您配置的記憶體使用C++`new`運算子，不過，您可能只會看到的檔名和行號所在`operator new`呼叫`_malloc_dbg`記憶體流失報告中。 若要建立更有用的記憶體流失報告，您可以撰寫如下所示的報告進行配置的那一行巨集：

```cpp
#ifdef _DEBUG
    #define DBG_NEW new ( _NORMAL_BLOCK , __FILE__ , __LINE__ )
    // Replace _NORMAL_BLOCK with _CLIENT_BLOCK if you want the
    // allocations to be of _CLIENT_BLOCK type
#else
    #define DBG_NEW new
#endif
```

現在您可以取代`new`運算子使用`DBG_NEW`巨集程式碼中的。 在偵錯組建`DBG_NEW`會使用多載的全域`operator new`接受其他參數區塊類型、 檔案和行號。 多載`new`呼叫`_malloc_dbg`記錄的額外資訊。 記憶體流失報告顯示的檔名和行號遺漏的物件配置的位置。 發行組建仍使用預設`new`。 此技術的範例如下：

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

當您在 Visual Studio 中執行此程式碼偵錯工具、 呼叫`_CrtDumpMemoryLeaks`產生的報表**輸出**視窗，如下所示：

```Output
Detected memory leaks!
Dumping objects ->
c:\users\username\documents\projects\debug_new\debug_new.cpp(20) : {75}
 normal block at 0x0098B8C8, 4 bytes long.
 Data: <    > CD CD CD CD
Object dump complete.
```

此輸出外洩的配置是在第 20 行上的報表*debug_new.cpp*。

>[!NOTE]
>我們不建議您建立名為前置處理器巨集`new`，或任何其他的語言關鍵字。

## <a name="set-breakpoints-on-a-memory-allocation-number"></a>記憶體配置編號上設定中斷點

記憶體配置編號會指出流失的記憶體區塊是何時配置的。 比方說，18，記憶體配置編號區塊會是記憶體的 18 的應用程式執行期間配置區塊。 CRT 報告會算所有配置的記憶體區塊執行時，包括由 CRT 程式庫和其他程式庫，例如 MFC 的配置。 因此，記憶體配置區塊第 18 號可能會不 18 您程式碼所配置的記憶體區塊。

您可以使用配置編號在記憶體配置上設定中斷點。

**使用監看式視窗設定記憶體配置中斷點：**

1. 靠近您的應用程式的開頭設定中斷點並開始偵錯。

1. 當應用程式的中斷點處暫停時，開啟**監看式**視窗中的選取**偵錯** > **Windows** > **監看式 1**(或**監看式 2**，**監看式 3**，或**監看式 4**)。

1. 在 **監看式**視窗中，輸入`_crtBreakAlloc`中**名稱**資料行。

   如果您使用多執行緒的 DLL 版本的 CRT 程式庫 （/MD 選項），加入內容運算子： `{,,ucrtbased.dll}_crtBreakAlloc`

1. 按 **Enter** 鍵。

   偵錯工具會評估呼叫，並將結果放在 [值]  欄中。 如果您尚未在記憶體配置上設定任何中斷點，此值將會是 **-1**。

1. 在 **值**資料行值取代為您想要偵錯工具中斷的記憶體配置的配置編號。

記憶體配置編號上設定中斷點之後，繼續進行偵錯。 請務必在相同的情況下執行，因此不會變更的記憶體配置編號。 當程式在特定的記憶體配置中斷時，使用**呼叫堆疊**視窗和其他偵錯工具視窗，判斷記憶體配置的條件。 然後，您可以繼續執行，觀察物件會發生什麼事，並判斷為什麼它不正確解除配置。

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
 另一種尋找記憶體流失的技術，是使用在關鍵點的應用程式記憶體狀態之快照。 若要在指定的時間點的記憶體狀態的快照集應用程式中，建立`_CrtMemState`結構，並將它傳遞給`_CrtMemCheckpoint`函式。

```cpp
_CrtMemState s1;
_CrtMemCheckpoint( &s1 );
```

`_CrtMemCheckpoint`函式填入該結構的目前記憶體狀態快照集。

若要輸出的內容`_CrtMemState`結構，則會傳遞至結構`_ CrtMemDumpStatistics`函式：

```cpp
_CrtMemDumpStatistics( &s1 );
```

`_ CrtMemDumpStatistics` 輸出看起來的記憶體狀態傾印：

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

`_CrtMemDifference` 比較記憶體狀態`s1`並`s2`，並傳回結果中的 (`s3`) 也就是之間的差異`s1`和`s2`。

尋找記憶體流失的其中一種技術一開始會放置`_CrtMemCheckpoint`呼叫的開始和結束您的應用程式，然後使用`_CrtMemDifference`比較的結果。 如果`_CrtMemDifference`顯示有記憶體流失，您可以新增更多`_CrtMemCheckpoint`呼叫將您的程式使用二進位搜尋，直到您已隔離流失的來源。

## <a name="false-positives"></a>誤報
 `_CrtDumpMemoryLeaks` 如果文件庫會將內部配置標記為一般的區塊，而不是 CRT 區塊或用戶端區塊時，就可以提供誤報的記憶體流失。 在這種情況下， `_CrtDumpMemoryLeaks` 無法區分使用者配置和內部程式庫配置。 如果在您呼叫 `_CrtDumpMemoryLeaks`之後執行程式庫配置的全域解構函式，則每個內部程式庫配置都會報告為記憶體流失。 標準範本程式庫的版本早於 Visual Studio.NET 可能會導致`_CrtDumpMemoryLeaks`來報告這類的誤判。

## <a name="see-also"></a>另請參閱
- [CRT 偵錯堆積詳細資料](../debugger/crt-debug-heap-details.md)
- [偵錯工具安全性](../debugger/debugger-security.md)
- [對機器碼進行偵錯](../debugger/debugging-native-code.md)
