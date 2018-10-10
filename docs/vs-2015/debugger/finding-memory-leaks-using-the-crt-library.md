---
title: 使用 CRT 程式庫尋找記憶體遺漏 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
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
caps.latest.revision: 33
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6d2c45ed2377b400fb00ac264aa2dcf8e5df8410
ms.sourcegitcommit: 71218ffc33da325cc1b886f69ff2ca50d44f5f33
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/09/2018
ms.locfileid: "48879768"
---
# <a name="finding-memory-leaks-using-the-crt-library"></a>使用 CRT 程式庫尋找記憶體遺漏
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[使用 CRT 尋找記憶體流失的程式庫](https://docs.microsoft.com/visualstudio/debugger/finding-memory-leaks-using-the-crt-library)。  
  
記憶體流失 (定義是無法正確解除配置先前配置的記憶體) 是 C/C++ 應用程式中最不易察覺和難以偵測的錯誤之一。 一開始可能只有少許記憶體流失而未察覺，但隨著時間經過，累積的記憶體流失可能愈來愈多而造成一些症狀，包括應用程式效能降低，甚至是因記憶體不足而沒有反應。 情況更嚴重者，發生記憶體流失的應用程式會因為耗盡所有可用的記憶體而造成其他應用程式也沒有反應，以致於難以判斷到底哪一個應用程式才是禍首。 即使看似無害的記憶體流失也可能是其他問題的根源，而應該解決。  
  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 偵錯工具和 C 執行階段 (CRT) 程式庫提供一種偵測和辨識記憶體流失的方法。  
  
## <a name="enabling-memory-leak-detection"></a>啟用記憶體流失偵測  
 偵測記憶體流失的主要工具是偵錯工具和 C 執行階段程式庫 (CRT) 偵錯堆積函式。  
  
 若要啟用偵錯堆積函式，在您的程式裡包含下列陳述式：  
  
```  
#define _CRTDBG_MAP_ALLOC  
#include <stdlib.h>  
#include <crtdbg.h>  
```  
  
 為了讓 CRT 功能正常運作， `#include` 陳述式必須遵循此處的順序。  
  
 加入 crtdbg.h 會將 `malloc` 和 [free](http://msdn.microsoft.com/library/74ded9cf-1863-432e-9306-327a42080bb8) 函式對應至其偵錯版本 ( [_malloc_dbg](http://msdn.microsoft.com/library/c97eca51-140b-4461-8bd2-28965b49ecdb) 和 `free`)，這些偵錯版本的函式會追蹤記憶體配置和解除配置。 這種對應只會發生在偵錯組建 (具有 `_DEBUG`) 中。 發行的組建使用一般的 `malloc` 和 `free` 函式。  
  
 `#define` 陳述式會將 CRT 堆積函式的基底版本對應到偵錯版本。 如果省略 `#define` 陳述式，記憶體流失傾印就不會提供那麼詳細的資料。  
  
 在使用上述陳述式來啟用偵錯堆積函式之後，您可以在應用程式結束點之前加上 `_CrtDumpMemoryLeaks` 呼叫，以便在應用程式結束時顯示記憶體流失報告：  
  
```  
_CrtDumpMemoryLeaks();  
```  
  
 如果您的應用程式有多個結束點，您不需要在每個結束點手動加上 [_CrtDumpMemoryLeaks](http://msdn.microsoft.com/library/71b2eab4-7f55-44e8-a55a-bfea4f32d34c) 呼叫。 只要在應用程式開頭加上 `_CrtSetDbgFlag` 呼叫，就會自動在每個結束點呼叫 `_CrtDumpMemoryLeaks` 。 您必須設定兩個位元欄位，如下所示：  
  
```  
_CrtSetDbgFlag ( _CRTDBG_ALLOC_MEM_DF | _CRTDBG_LEAK_CHECK_DF );  
```  
  
 根據預設， `_CrtDumpMemoryLeaks` 會將記憶體流失報告輸出至 [輸出]  視窗的 [偵錯]  窗格。 您可以使用 `_CrtSetReportMode` 將報告重新導向至其他位置。  
  
 如果您使用程式庫，該程式庫可能會重設輸出至其他位置。 在這種情況下，您可以將輸出位置設回 [輸出]  視窗，如下所示：  
  
```  
_CrtSetReportMode( _CRT_ERROR, _CRTDBG_MODE_DEBUG );  
```  
  
## <a name="interpreting-the-memory-leak-report"></a>解讀記憶體流失報告  
 如果您的應用程式未定義 `_CRTDBG_MAP_ALLOC`， [_CrtDumpMemoryLeaks](http://msdn.microsoft.com/library/71b2eab4-7f55-44e8-a55a-bfea4f32d34c) 會顯示類似如下的記憶體流失報告：  
  
```  
Detected memory leaks!  
Dumping objects ->  
{18} normal block at 0x00780E80, 64 bytes long.  
 Data: <                > CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD  
Object dump complete.  
```  
  
 如果您的應用程式已定義 `_CRTDBG_MAP_ALLOC`，則記憶體流失報告會類似如下：  
  
```  
Detected memory leaks!  
Dumping objects ->  
c:\users\username\documents\projects\leaktest\leaktest.cpp(20) : {18}   
 normal block at 0x00780E80, 64 bytes long.  
 Data: <                > CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD  
Object dump complete.  
```  
  
 差別在於第二份報告會顯示首次配置流失的記憶體的檔案名稱和其內行號。  
  
 無論您是否定義 `_CRTDBG_MAP_ALLOC` ，記憶體流失報告都會顯示下列資訊：  
  
-   記憶體配置編號，在此範例中為 `18`  
  
-   [區塊類型](http://msdn.microsoft.com/en-us/e2f42faf-0687-49e7-aa1f-916038354f97)，在此範例中為 `normal` 。  
  
-   十六進位記憶體位置，在此範例中為 `0x00780E80` 。  
  
-   區塊的大小，在此範例中為 `64 bytes` 。  
  
-   區塊中前 16 個位元組的資料 (十六進位格式)。  
  
 記憶體流失報告會指出記憶體區塊是一般區塊、用戶端區塊還是 CRT 區塊。 *「一般區塊」* (Normal Block) 是您的程式所配置的一般記憶體。 *「用戶端區塊」* (Client Block) 是 MFC 程式專為需要解構函式的物件所使用的一種特殊類型的記憶體區塊。 MFC 的 `new` 運算子會根據所建立的物件來建立一般區塊或用戶端區塊。 *「CRT 區塊」* (CRT Block) 則是 CRT 程式庫配置來供自身使用的記憶體區塊。 CRT 程式庫負責處理這些區塊的解除配置。 因此，除非發生嚴重錯誤 (例如 CRT 程式庫損毀)，否則您通常在記憶體流失報告中不會看到這些資訊。  
  
 另外還有兩種絕對不會出現在記憶體流失報告中的記憶體區塊。 *「可用區塊」* (Free Block) 是已經釋放的記憶體。 按照定義，這種記憶體本身就沒有流失的問題。 *「忽略區塊」* (Ignore Block) 是您已明確標記為要從記憶體流失報告中排除的區塊。  
  
 上述方式適用於以標準 CRT `malloc` 函式配置的記憶體。 如果您的程式將使用 c + + 的記憶體`new`運算子，不過，您可能只會看到的檔案和行號位置的通用實作`operator new`呼叫`_malloc_dbg`記憶體流失報告中。 由於該行為不是很有用，您可以變更它，以回報使用看起來像這樣的巨集時，所配置的那一行： 
 
```cpp  
#ifdef _DEBUG
    #define DBG_NEW new ( _NORMAL_BLOCK , __FILE__ , __LINE__ )
    // Replace _NORMAL_BLOCK with _CLIENT_BLOCK if you want the
    // allocations to be of _CLIENT_BLOCK type
#else
    #define DBG_NEW new
#endif
```  
  
現在您可以取代`new`運算子使用`DBG_NEW`巨集程式碼中的。 在偵錯組建中，這會使用多載的全域`operator new`接受其他參數區塊類型、 檔案和行號。 這個多載`new`呼叫`_malloc_dbg`記錄的額外資訊。 當您使用`DBG_NEW`，記憶體流失報告顯示的檔名和行號遺漏的物件配置的位置。 在零售組建中，它會使用預設`new`。 (我們不建議您建立名為前置處理器巨集`new`，或任何其他的語言關鍵字。)此技術的範例如下：  
  
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
  
當您執行此程式碼偵錯工具在 Visual Studio 中，呼叫`_CrtDumpMemoryLeaks`產生的報表**輸出**視窗看起來如下所示：  
  
```Output  
Detected memory leaks!
Dumping objects ->
c:\users\username\documents\projects\debug_new\debug_new.cpp(20) : {75}
 normal block at 0x0098B8C8, 4 bytes long.
 Data: <    > CD CD CD CD 
Object dump complete.
```  
  
這會告訴您外洩的配置是 debug_new.cpp 第 20 行上。  
  
## <a name="setting-breakpoints-on-a-memory-allocation-number"></a>在記憶體配置編號上設定中斷點  
 記憶體配置編號會指出流失的記憶體區塊是何時配置的。 例如，區塊的記憶體配置編號為 18，代表這是在應用程式執行期間配置的第 18 個記憶體區塊。 CRT 報告會算進所有在執行期間配置的記憶體區塊。 這包括由 CRT 程式庫和其他程式庫 (例如 MFC) 配置的記憶體區塊。 因此，記憶體配置編號為 18 的區塊，不見得是您的程式碼所配置的第 18 個記憶體區塊。 通常情況下並不是。  
  
 您可以使用配置編號在記憶體配置上設定中斷點。  
  
#### <a name="to-set-a-memory-allocation-breakpoint-using-the-watch-window"></a>若要使用 [監看式] 視窗設定記憶體配置中斷點  
  
1.  在靠近應用程式的開頭設定中斷點，然後啟動應用程式。  
  
2.  當應用程式在中斷點中斷時，[監看式]  視窗隨即出現。  
  
3.  在 **監看式**視窗中，輸入`_crtBreakAlloc`中**名稱**資料行。  
  
     如果您使用 CRT 程式庫 (/MD 選項) 的多執行緒 DLL 版本，請包含內容運算子： `{,,ucrtbased.dll}_crtBreakAlloc`  
  
4.  請按 **RETURN**。  
  
     偵錯工具會評估呼叫，並將結果放在 [值]  欄中。 如果您尚未在記憶體配置上設定任何中斷點，此值將會是 –1。  
  
5.  在 [值]  欄中，將顯示的值取代為您要在該處中斷的記憶體配置的配置編號。  
  
 在記憶體配置編號上設定中斷點之後，您可以繼續偵錯。 請務必注意要在上次執行的相同條件下執行程式，這樣記憶體配置順序才不會變更。 當程式在特定的記憶體配置中斷時，您可以使用 [呼叫堆疊]  視窗和其他偵錯工具視窗，判斷記憶體配置所處的條件。 然後再恢復程式的執行，觀察物件有何變化，並判斷未將它適當解除配置的原因。  
  
 在物件上設定資料中斷點可能也很有用。 如需詳細資訊，請參閱 [Using Breakpoints](../debugger/using-breakpoints.md)。  
  
 您也可以在程式碼中設定記憶體配置中斷點。 執行這項作業的方法有兩種：  
  
```  
_crtBreakAlloc = 18;  
```  
  
 或：  
  
```  
_CrtSetBreakAlloc(18);  
```  
  
## <a name="comparing-memory-states"></a>比較記憶體狀態  
 另一種尋找記憶體流失的技術，是使用在關鍵點的應用程式記憶體狀態之快照。 若要建立應用程式中特定時點的記憶體狀態快照，請建立 **_CrtMemState** 結構，並將它傳遞給 `_CrtMemCheckpoint` 函式。 這個函式以目前記憶體狀態的快照填寫結構：  
  
```  
_CrtMemState s1;  
_CrtMemCheckpoint( &s1 );  
  
```  
  
 `_CrtMemCheckpoint` 會以目前記憶體狀態的快照填入該結構。  
  
 若要輸出 **_CrtMemState** 結構的內容，請將結構傳遞給 `_ CrtMemDumpStatistics` 函式：  
  
```  
_CrtMemDumpStatistics( &s1 );  
  
```  
  
 `_ CrtMemDumpStatistics` 會輸出類似如下的記憶體狀態傾印：  
  
```  
0 bytes in 0 Free Blocks.  
0 bytes in 0 Normal Blocks.  
3071 bytes in 16 CRT Blocks.  
0 bytes in 0 Ignore Blocks.  
0 bytes in 0 Client Blocks.  
Largest number used: 3071 bytes.  
Total allocations: 3764 bytes.  
  
```  
  
 若要判斷記憶體流失是否發生在程式碼區段裡，您可以建立區段前和區段後的記憶體狀態快照，然後使用 `_ CrtMemDifference` 比較這兩個狀態：  
  
```  
_CrtMemCheckpoint( &s1 );  
// memory allocations take place here  
_CrtMemCheckpoint( &s2 );  
  
if ( _CrtMemDifference( &s3, &s1, &s2) )  
   _CrtMemDumpStatistics( &s3 );  
```  
  
 `_CrtMemDifference` 會比較記憶體狀態 `s1` 和 `s2` ，然後在`s3`傳回 `s1` 和 `s2`的差異。  
  
 尋找記憶體流失的一個方式是先在應用程式的開頭和結尾加上 `_CrtMemCheckpoint` 呼叫，然後使用 `_CrtMemDifference` 來比較結果。 如果 `_CrtMemDifference` 顯示有記憶體流失，您再加上更多 `_CrtMemCheckpoint` 呼叫以使用二進位搜尋將程式分割，直到找出遺漏的來源為止。  
  
## <a name="false-positives"></a>誤報  
 在某些情況下， `_CrtDumpMemoryLeaks` 會提供錯誤的記憶體流失指示。 如果您使用的程式庫將內部配置標記為 _NORMAL_BLOCKs，而非 `_CRT_BLOCK`s 或 `_CLIENT_BLOCK`s，則可能會發生這種情形。 在這種情況下， `_CrtDumpMemoryLeaks` 無法區分使用者配置和內部程式庫配置。 如果在您呼叫 `_CrtDumpMemoryLeaks`之後執行程式庫配置的全域解構函式，則每個內部程式庫配置都會報告為記憶體流失。 在 Visual Studio .NET 之前的舊版標準樣板程式庫會造成 `_CrtDumpMemoryLeaks` 提出這樣的誤報，但最新版本中已修正這個問題。  
  
## <a name="see-also"></a>另請參閱  
 [CRT 偵錯堆積詳細資料](../debugger/crt-debug-heap-details.md)   
 [偵錯工具安全性](../debugger/debugger-security.md)   
 [偵錯機器碼](../debugger/debugging-native-code.md)



