---
title: CRT 偵錯堆積詳細資料 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
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
- C++
helpviewer_keywords:
- debug heap, accessing
- heap functions
- _CRTDBG_CHECK_ALWAYS_DF macro
- _CrtMemDumpStatistics function
- debugging [C++], debug heap
- _CRT_BLOCK macro
- DBGINT.H file
- _CrtMemDumpAllObjectsSince function
- _crtBreakAlloc global variable
- _CrtMemState function
- _CLIENT_BLOCK macro
- _FREE_BLOCK block
- _CrtMemBlockHeader function
- heap state reporting functions
- _CRTDBG_ALLOC_MEM_DF macro
- _CrtSetBreakAlloc function
- memory blocks, allocation types on debug heap
- debugging [C++], CRT debug support
- debug heap, tracking heap allocation requests
- memory allocation, debug heap
- _NORMAL_BLOCK block
- crtBreakAlloc global variable
- _CrtDoForAllClientObjects function
- new operator, using debug heap from C++
- _CrtSetDumpClient function
- debugging [CRT], heap-related problems
- debug heap, solving memory allocation problems
- _CrtMemCheckpoint function
- debug builds, linking to debug heap
- _IGNORE_BLOCK block
- _crtDbgFlag function
- client blocks, specifying subtypes
- memory leaks, tracking
- _CrtSetDbgFlag function
- nBlockUse method
- memory leaks, CRT debug library functions
- _CRTDBG_DELAY_FREE_MEM_DF macro
- allocation request numbers
- _CRTDBG_LEAK_CHECK_DF macro
- debug heap
- memory, debugging
- _CrtReportBlockType function
- _CrtDumpMemoryLeaks function
- _CrtCheckMemory function
- debug heap, CRT
- memory blocks, free
- _BLOCK_TYPE macro
- debug heap, memory blocks
- heap allocation, debug
- debugging memory leaks
- _BLOCK_SUBTYPE macro
- debug heap, using from C++
- _CrtMemDifference function
- heap allocation, tracking requests
- debugging [Visual Studio], debug heap
- delete operator, using debug heap from C++
- blocks, types of on the debug heap
- _CRTDBG_CHECK_CRT_DF macro
- debug heap, reporting functions
ms.assetid: bf78ace6-28e4-4a04-97c6-39e0cdd00ba4
caps.latest.revision: 22
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a97054db575d1d92f2077efe46d89573fba02dfd
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49297727"
---
# <a name="crt-debug-heap-details"></a>CRT 偵錯堆積詳細資料
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題提供 CRT 偵錯堆積的詳細檢視。  
  
##  <a name="BKMK_Contents"></a> 內容  
 [使用偵錯堆積尋找緩衝區滿溢](#BKMK_Find_buffer_overruns_with_debug_heap)  
  
 [偵錯堆積上的區塊類型](#BKMK_Types_of_blocks_on_the_debug_heap)  
  
 [檢查堆積的完整性和記憶體流失](#BKMK_Check_for_heap_integrity_and_memory_leaks)  
  
 [設定偵錯堆積](#BKMK_Configure_the_debug_heap)  
  
 [新功能、 delete 和 _client_block c + + 偵錯堆積](#BKMK_new__delete__and__CLIENT_BLOCKs_in_the_C___debug_heap)  
  
 [堆積狀態報告函式](#BKMK_Heap_State_Reporting_Functions)  
  
 [追蹤堆積配置要求](#BKMK_Track_Heap_Allocation_Requests)  
  
##  <a name="BKMK_Find_buffer_overruns_with_debug_heap"></a> 使用偵錯堆積尋找緩衝區滿溢  
 開發人員最常面臨的兩種難解決的問題是，覆寫配置緩衝區的結尾和記憶體流失 (無法在不再需要時釋放配置)。 偵錯堆積提供的強大工具，可以解決這類的記憶體配置問題。  
  
 堆積函式的偵錯版本是呼叫發行版本裡使用之函式的標準或基底版本。 當您要求記憶體區塊時，偵錯堆積管理員會從基底堆積配置比要求稍微大一點的記憶體區塊，並且傳回此區塊部分的指標。 例如，假設您的應用程式包含呼叫：`malloc( 10 )`。 在發行組建，而[malloc](http://msdn.microsoft.com/library/144fcee2-be34-4a03-bb7e-ed6d4b99eea0)會呼叫要求 10 位元組配置基底堆積配置常式。 在偵錯組建中，不過，`malloc`會呼叫[_malloc_dbg](http://msdn.microsoft.com/library/c97eca51-140b-4461-8bd2-28965b49ecdb)，它會呼叫要求 10 位元組的配置，再加上大約 36 位元組的額外記憶體基底堆積配置常式。 偵錯堆積裡所有產生的記憶體區塊會在單向連結串列 (Single-Linked List) 中完成連接 (依配置時間排列順序)。  
  
 偵錯堆積常式配置的額外記憶體是用於簿記資訊，這些資訊可能為將偵錯記憶體區塊連結在一起的指標，和用來捕捉配置區域覆寫的資料每端的小型緩衝區。  
  
 目前，用於儲存偵錯堆積的簿記資訊的區塊標頭結構會根據 DBGINT.H 標頭檔來宣告：  
  
```  
typedef struct _CrtMemBlockHeader  
{  
// Pointer to the block allocated just before this one:  
    struct _CrtMemBlockHeader *pBlockHeaderNext;  
// Pointer to the block allocated just after this one:  
    struct _CrtMemBlockHeader *pBlockHeaderPrev;  
    char *szFileName;    // File name  
    int nLine;           // Line number  
    size_t nDataSize;    // Size of user block  
    int nBlockUse;       // Type of block  
    long lRequest;       // Allocation number  
// Buffer just before (lower than) the user's memory:  
    unsigned char gap[nNoMansLandSize];  
} _CrtMemBlockHeader;  
  
/* In an actual memory block in the debug heap,  
 * this structure is followed by:  
 *   unsigned char data[nDataSize];  
 *   unsigned char anotherGap[nNoMansLandSize];  
 */  
```  
  
 `NoMansLand`區塊的使用者資料區的任一端使用緩衝區目前是 4 位元組的大小，而且會填入已知的位元組值，由偵錯堆積常式用來驗證不覆寫使用者的記憶體區塊的限制。 偵錯堆積也會以一個已知值來填寫新的記憶體區塊。 如果您打算像以下的說明所述，維持堆積連結串列中的釋放區塊，這些釋放區塊也會填入一個已知值。 目前，使用的實際位元組值如下：  
  
 NoMansLand (0xFD)  
 在應用程式使用記憶體的每端的 "NoMansLand" 緩衝區目前是填入 0xFD。  
  
 釋放區塊 (0xDD)  
 當 `_CRTDBG_DELAY_FREE_MEM_DF` 旗標設定時，偵錯堆積中的連結串列保持未使用的釋放區塊目前是填入 0xDD。  
  
 新物件 (0xCD)  
 新物件在配置時會填入 0xCD。  
  
 ![回到頁首](../debugger/media/pcs-backtotop.png "PCS_BackToTop")  
  
 ![回到頁首](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [內容](#BKMK_Contents)  
  
##  <a name="BKMK_Types_of_blocks_on_the_debug_heap"></a> 偵錯堆積上的區塊類型  
 偵錯堆積裡的每個記憶體區塊會設定成五種配置類型的其中一種。 這些類型可以針對不同的流失偵測和狀態報告目的來追蹤和報告。 您可以配置使用下列其中一個偵錯堆積配置函式直接呼叫它來指定區塊類型[_malloc_dbg](http://msdn.microsoft.com/library/c97eca51-140b-4461-8bd2-28965b49ecdb)。 五種類型的偵錯堆積中的記憶體區塊 (在中設定**nBlockUse**隸屬**lrequest**結構) 如下所示：  
  
 **_NORMAL_BLOCK**  
 呼叫[malloc](http://msdn.microsoft.com/library/144fcee2-be34-4a03-bb7e-ed6d4b99eea0)或是[calloc](http://msdn.microsoft.com/library/17bb79a1-98cf-4096-90cb-1f9365cd6829)建立一般區塊。 如果您想要使用一般區塊，而且不需要用戶端區塊時，您可能想要定義[_CRTDBG_MAP_ALLOC](http://msdn.microsoft.com/library/435242b8-caea-4063-b765-4a608200312b)，因而導致所有堆積配置呼叫對應至偵錯組建中的偵錯對應項。 這可將每個配置呼叫的相關檔名和行號資訊儲存在對應的區塊標頭裡。  
  
 `_CRT_BLOCK`  
 由許多執行階段程式庫函式內部所配置的記憶體區塊標記為 CRT 區塊，以便分別處理。 因此，流失偵測和其他操作不會受到影響。 配置必須從未配置、重新配置或釋放任何 CRT 類型的區塊。  
  
 `_CLIENT_BLOCK`  
 應用程式可以使用這種記憶體區塊類型配置、使用偵錯堆積函式的明確呼叫，繼續追蹤指定的配置群組，以達到偵錯的目的。 MFC，比方說，會配置所有**CObjects**為用戶端區塊; 其他應用程式可能會在用戶端區塊中讓不同的記憶體物件。 也可以為達更細微的追蹤而設定用戶端區塊的子類型。 若要指定用戶端區塊的子類型，將數字向左移位 (Left Shift) 16 個位元並且以 `OR` 將之 `_CLIENT_BLOCK` 起來。 例如:   
  
```  
#define MYSUBTYPE 4  
freedbg(pbData, _CLIENT_BLOCK|(MYSUBTYPE<<16));  
```  
  
 可以使用安裝的用戶端提供的攔截函式傾印儲存在用戶端區塊的物件[_CrtSetDumpClient](http://msdn.microsoft.com/library/f3dd06d0-c331-4a12-b68d-25378d112033)，並就會被呼叫時用戶端區塊傾印偵錯函式。 此外， [_CrtDoForAllClientObjects](http://msdn.microsoft.com/library/d0fdb835-3cdc-45f1-9a21-54208e8df248)可以用來呼叫指定的函式中偵錯堆積區塊的每個用戶端應用程式所提供。  
  
 **_FREE_BLOCK**  
 一般來說，此清單會移除釋放的區塊。 若要檢查釋放記憶體是否仍然不能寫入，或模擬低記憶體條件，您可以選擇保留連結串列上的釋放區塊，將其標記為可用，並填入已知位元組值 (目前是 0xDD)。  
  
 **_IGNORE_BLOCK**  
 可以在某段時間關閉偵錯堆積操作。 在這段期間，記憶體區塊會保留於清單終上，但是標記為忽略區塊。  
  
 若要判斷指定區塊的子類型的類型，使用 函式[_CrtReportBlockType](http://msdn.microsoft.com/library/0f4b9da7-bebb-4956-9541-b2581640ec6b)和巨集 **_BLOCK_TYPE**並 **_BLOCK_SUBTYPE**。 巨集會定義 (在 crtdbg.h 裡)，參見下例：  
  
```  
#define _BLOCK_TYPE(block)          (block & 0xFFFF)  
#define _BLOCK_SUBTYPE(block)       (block >> 16 & 0xFFFF)  
```  
  
 ![回到頁首](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [內容](#BKMK_Contents)  
  
##  <a name="BKMK_Check_for_heap_integrity_and_memory_leaks"></a> 檢查堆積的完整性和記憶體流失  
 許多偵錯堆積的功能必須從程式碼內存取。 下一節將說明一些功能以及如何使用這些功能。  
  
 `_CrtCheckMemory`  
 您可以使用呼叫[_CrtCheckMemory](http://msdn.microsoft.com/library/457cc72e-60fd-4177-ab5c-6ae26a420765)，例如，若要檢查堆積的完整性，在任何時間點。 這個函式檢查堆積裡的每個記憶體區塊，確認記憶體區塊標頭資訊是有效的，並且確認緩衝區未經修改。  
  
 `_CrtSetDbgFlag`  
 您可以控制如何偵錯堆積追蹤的配置使用的內部的旗標[_crtDbgFlag](http://msdn.microsoft.com/library/9e7adb47-8ab9-4e19-81d5-e2f237979973)，它可以讀取及使用設定[_CrtSetDbgFlag](http://msdn.microsoft.com/library/b5657ffb-6178-4cbf-9886-1af904ede94c)函式。 您可以變更這個旗標，來指示偵錯堆積在程式結束時檢查記憶體流失，並且報告任何偵測到的遺漏。 同樣地，您可以指定連結串列不要移除釋放的記憶體區塊，以模擬低記憶體情況。 檢查堆積時，這些釋放的區塊會在它們的項目裡檢查以確定它們沒有被干擾。  
  
 **_CrtDbgFlag**旗標包含下列的位元欄位：  
  
|位元欄位|預設<br /><br /> value|描述|  
|---------------|-----------------------|-----------------|  
|**_CRTDBG_ALLOC_MEM_DF**|開啟|開啟偵錯配置。 當這個位元為關閉，配置鏈結在一起，但其區塊型別是 **_IGNORE_BLOCK**。|  
|**_CRTDBG_DELAY_FREE_MEM_DF**|Off|防止真的釋放記憶體，這是為了模擬低記憶體情況。 當這個位元開啟時，釋放的區塊會保留在偵錯堆積的連結清單，但是會標記為 **_FREE_BLOCK**並填入一個特殊位元組值。|  
|**_CRTDBG_CHECK_ALWAYS_DF**|Off|會導致 **_CrtCheckMemory**若要在每個配置和解除配置時呼叫。 這會減緩執行，但可以快速捕捉錯誤。|  
|**_CRTDBG_CHECK_CRT_DF**|Off|造成區塊標記為類型 **_CRT_BLOCK**要包含在流失偵測和狀態差異作業中。 當這個位元關閉時，會忽略在這類操作期間執行階段程式庫內部所使用的記憶體。|  
|**_CRTDBG_LEAK_CHECK_DF**|Off|若要執行在程式結束時，透過對呼叫的流失檢查 **_CrtDumpMemoryLeaks**。 如果應用程式無法釋放它所配置的所有記憶體，會產生錯誤報告。|  
  
 ![回到頁首](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [內容](#BKMK_Contents)  
  
##  <a name="BKMK_Configure_the_debug_heap"></a> 設定偵錯堆積  
 所有堆積函式的呼叫，例如 `malloc`、`free`、`calloc`、`realloc`、`new` 和 `delete` 都會解析成操作於偵錯堆積裡的這些函式之偵錯版本。 當您釋放記憶體區塊時，偵錯堆積會自動檢查配置區域每端的緩衝區之完整性，如果發生覆寫發便會發出錯誤報告。  
  
 **若要使用偵錯堆積**  
  
-   以 C 執行階段程式庫的偵錯版本連結您應用程式的偵錯組建。  
  
 **若要變更一個或多個 _crtDbgFlag 位元欄位，並建立新的狀態旗標**  
  
1.  使用設為 `_CrtSetDbgFlag` (為取得目前的 `newFlag` 狀態) 的 `_CRTDBG_REPORT_FLAG` 參數來呼叫 `_crtDbgFlag`，且將傳回值儲存在暫存變數中。  
  
2.  開啟任何位元`OR`-ing (位元&#124;符號) 暫存變數和對應的位元遮罩 （由應用程式程式碼中的資訊清單常數）。  
  
3.  使用 `AND` (位元 & 符號) 變數和適當位元遮罩的 `NOT` (位元 ~ 符號) 來關閉其他位元。  
  
4.  使用設成儲存於暫存變數值的 `_CrtSetDbgFlag` 參數呼叫 `newFlag`，以便建立 `_crtDbgFlag` 的新狀態。  
  
 例如，下列程式碼開啟自動流失偵測並且關閉類型 `_CRT_BLOCK` 的區塊檢查：  
  
```  
// Get current flag  
int tmpFlag = _CrtSetDbgFlag( _CRTDBG_REPORT_FLAG );  
  
// Turn on leak-checking bit.  
tmpFlag |= _CRTDBG_LEAK_CHECK_DF;  
  
// Turn off CRT block checking bit.  
tmpFlag &= ~_CRTDBG_CHECK_CRT_DF;  
  
// Set flag to the new value.  
_CrtSetDbgFlag( tmpFlag );  
```  
  
 ![回到頁首](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [內容](#BKMK_Contents)  
  
##  <a name="BKMK_new__delete__and__CLIENT_BLOCKs_in_the_C___debug_heap"></a> 新功能、 delete 和 _client_block c + + 偵錯堆積  
 C 執行階段程式庫的偵錯版本包含 C++ `new` 及 `delete` 運算子的偵錯版本。 如果您使用 `_CLIENT_BLOCK` 配置類型，則必須直接呼叫 `new` 運算子的偵錯版本，或建立可以取代偵錯模式中 `new` 運算子的巨集，如同下列範例所示：  
  
```  
/* MyDbgNew.h  
 Defines global operator new to allocate from  
 client blocks  
*/  
  
#ifdef _DEBUG  
   #define DEBUG_CLIENTBLOCK   new( _CLIENT_BLOCK, __FILE__, __LINE__)  
#else  
   #define DEBUG_CLIENTBLOCK  
#endif // _DEBUG  
  
/* MyApp.cpp  
        Use a default workspace for a Console Application to  
 *      build a Debug version of this code  
*/  
  
#include "crtdbg.h"  
#include "mydbgnew.h"  
  
#ifdef _DEBUG  
#define new DEBUG_CLIENTBLOCK  
#endif  
  
int main( )   {  
    char *p1;  
    p1 =  new char[40];  
    _CrtMemDumpAllObjectsSince( NULL );  
}  
```  
  
 `delete` 運算子的偵錯版本會作用在所有的區塊類型上，當您編譯發行版本時不需要在程式裡做任何的變更。  
  
 ![回到頁首](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [內容](#BKMK_Contents)  
  
##  <a name="BKMK_Heap_State_Reporting_Functions"></a> 堆積狀態報告函式  
 **_CrtMemState**  
  
 若要捕捉指定時間的堆積狀態之摘要快照，請使用定義在 CRTDBG.H 裡的 _CrtMemState 結構：  
  
```  
typedef struct _CrtMemState  
{  
    // Pointer to the most recently allocated block:  
    struct _CrtMemBlockHeader * pBlockHeader;  
    // A counter for each of the 5 types of block:  
    size_t lCounts[_MAX_BLOCKS];  
    // Total bytes allocated in each block type:  
    size_t lSizes[_MAX_BLOCKS];  
    // The most bytes allocated at a time up to now:  
    size_t lHighWaterCount;  
    // The total bytes allocated at present:  
    size_t lTotalCount;  
} _CrtMemState;  
```  
  
 這個結構會儲存偵錯堆積的連結串列裡第一個 (最近配置) 區塊的指標。 接著，它會在兩個陣列裡，記錄每一種記憶體區塊 (_NORMAL_BLOCK、`_CLIENT_BLOCK`、_FREE_BLOCK 等等) 類型在清單中的數目和每一種區塊類型裡配置的位元組數目。 最後，它會記錄堆積裡配置的最高位元組數目來當做此時的總數，和目前配置的位元組數目。  
  
 **其他 CRT 報告函式**  
  
 下列函式報告堆積的狀態和內容，並且使用資訊來幫助偵測記憶體流失和其他問題。  
  
|功能|描述|  
|--------------|-----------------|  
|[_CrtMemCheckpoint](http://msdn.microsoft.com/library/f1bacbaa-5a0c-498a-ac7a-b6131d83dfbc)|將儲存在堆積的快照集 **_CrtMemState**應用程式所提供的結構。|  
|[_CrtMemDifference](http://msdn.microsoft.com/library/0f327278-b551-482f-958b-76941f796ba4)|比較兩個記憶體狀態結構，將它們之間的差異儲存在第三個狀態結構，如果兩個狀態不同則傳回 TRUE。|  
|[_CrtMemDumpStatistics](http://msdn.microsoft.com/library/27b9d731-3184-4a2d-b9a7-6566ab28a9fe)|傾印給定 **_CrtMemState**結構。 結構可能包含指定時間裡偵錯堆積的狀態快照或者是兩個快照之間的差異。|  
|[_CrtMemDumpAllObjectsSince](http://msdn.microsoft.com/library/c48a447a-e6bb-475c-9271-a3021182a0dc)|傾印從堆積的指定快照使用後或從執行開始的所有配置物件之相關資訊。 每次它傾印 **_CLIENT_BLOCK**區塊中，如果其中一個已安裝使用，它會呼叫應用程式時，所提供的攔截函式 **_CrtSetDumpClient**。|  
|[_CrtDumpMemoryLeaks](http://msdn.microsoft.com/library/71b2eab4-7f55-44e8-a55a-bfea4f32d34c)|判斷自從程式執行開始時，是否有任何的記憶體流失發生，如果有的話，傾印所有配置的物件。 每次 **_CrtDumpMemoryLeaks**傾印 **_CLIENT_BLOCK**區塊中，它會呼叫應用程式時，所提供的攔截函式，如果其中一個已安裝使用 **_CrtSetDumpClient**.|  
  
 ![回到頁首](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [內容](#BKMK_Contents)  
  
##  <a name="BKMK_Track_Heap_Allocation_Requests"></a> 追蹤堆積配置要求  
 雖然指出判斷提示或報告巨集執行的原始程式檔名稱和行號通常在找出問題原因很有用，但是對於堆積配置函式可能就不是這樣。 雖然巨集可以插入到許多在應用程式邏輯樹狀圖裡合適的點，但是配置通常是在許多不同時間裡由許多不同地方的特殊常式呼叫。 問題通常不是哪一行程式碼做了錯誤的配置，而是上千個配置中，哪一個配置是由哪一錯誤程式碼所造成，以及其錯誤原因為何。  
  
 **唯一配置要求號碼和 _crtBreakAlloc**  
  
 最簡單的辨識發生錯誤的特定堆積配置呼叫方法，是利用與偵錯堆積裡每個區塊相關的唯一配置要求編號。 當區塊的相關資訊由其中一個傾印函式報告時，這個配置要求編號會包含在大括號 (例如，"{36}」)。  
  
 一旦您知道不適當配置區塊的配置要求編號時，您可以將這個數字[_CrtSetBreakAlloc](http://msdn.microsoft.com/library/33bfc6af-a9ea-405b-a29f-1c2d4d9880a1)建立中斷點。 執行會在配置區塊之前中斷，而您即可回溯追蹤以判斷哪一個常式要對這個錯誤呼叫負責。 若要避免重新編譯，您可以完成相同的動作，在偵錯工具中設定 **_crtBreakAlloc**至您感興趣的配置要求編號。  
  
 **建立配置常式的偵錯版本**  
  
 稍微複雜一點的方法是建立您自己的配置常式，相當於偵錯版本 **_dbg**新版[堆積配置函式](../debugger/debug-versions-of-heap-allocation-functions.md)。 然後您可以傳遞原始程式檔和行號引數到下面的堆積配置常式，而且立即能夠看到錯誤的配置的發生位置。  
  
 例如，假設應用程式包含一個類似下列的一般使用常式：  
  
```  
int addNewRecord(struct RecStruct * prevRecord,  
                 int recType, int recAccess)  
{  
    // ...code omitted through actual allocation...   
    if ((newRec = malloc(recSize)) == NULL)  
    // ... rest of routine omitted too ...   
}  
```  
  
 您可以在標頭檔 (Header File) 裡加入像這樣的程式碼：  
  
```  
#ifdef _DEBUG  
#define  addNewRecord(p, t, a) \  
            addNewRecord(p, t, a, __FILE__, __LINE__)  
#endif  
```  
  
 接著，您可以依照下列示範方式，在記錄建立常式裡變更配置：  
  
```  
int addNewRecord(struct RecStruct *prevRecord,  
                int recType, int recAccess  
#ifdef _DEBUG  
               , const char *srcFile, int srcLine  
#endif  
    )  
{  
    /* ... code omitted through actual allocation ... */  
    if ((newRec = _malloc_dbg(recSize, _NORMAL_BLOCK,  
            srcFile, scrLine)) == NULL)  
    /* ... rest of routine omitted too ... */  
}  
```  
  
 現在，偵錯堆積中每個產生的配置區塊，都會儲存呼叫 `addNewRecord` 位置的原始程式檔名稱和行號，而區塊檢查時也會報告這些資訊。  
  
 ![回到頁首](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [內容](#BKMK_Contents)  
  
## <a name="see-also"></a>另請參閱  
 [偵錯機器碼](../debugger/debugging-native-code.md)



