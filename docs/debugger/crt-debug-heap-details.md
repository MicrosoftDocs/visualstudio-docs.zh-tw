---
title: CRT Debug 堆積詳細資料 |Microsoft Docs
description: Debug 堆積提供強大的工具來協助解決記憶體配置問題。 瞭解這些工具，以及它們如何協助解決問題，例如流失和超支。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
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
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 984253f6c4ccb9d64fc1cefb34b2b5d7962e3eb5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99857658"
---
# <a name="crt-debug-heap-details"></a>CRT 偵錯堆積詳細資料
本主題提供 CRT 偵錯堆積的詳細檢視。

## <a name="contents"></a><a name="BKMK_Contents"></a> 內容
[使用 debug 堆積尋找緩衝區溢位](#BKMK_Find_buffer_overruns_with_debug_heap)

[偵錯堆積上的區塊類型](#BKMK_Types_of_blocks_on_the_debug_heap)

[檢查堆積完整性和記憶體流失](#BKMK_Check_for_heap_integrity_and_memory_leaks)

[設定 debug 堆積](#BKMK_Configure_the_debug_heap)

[c + + debug 堆積中的 new、delete 和 _CLIENT_BLOCKs](#BKMK_new__delete__and__CLIENT_BLOCKs_in_the_C___debug_heap)

[堆積狀態報表函數](#BKMK_Heap_State_Reporting_Functions)

[追蹤堆積配置要求](#BKMK_Track_Heap_Allocation_Requests)

## <a name="find-buffer-overruns-with-debug-heap"></a><a name="BKMK_Find_buffer_overruns_with_debug_heap"></a>使用偵錯堆積尋找緩衝區溢位
開發人員最常面臨的兩種難解決的問題是，覆寫配置緩衝區的結尾和記憶體流失 (無法在不再需要時釋放配置)。 偵錯堆積提供的強大工具，可以解決這類的記憶體配置問題。

堆積函式的偵錯版本是呼叫發行版本裡使用之函式的標準或基底版本。 當您要求記憶體區塊時，偵錯堆積管理員會從基底堆積配置比要求稍微大一點的記憶體區塊，並且傳回此區塊部分的指標。 例如，假設您的應用程式包含呼叫：`malloc( 10 )`。 在發行組建中， [malloc](/cpp/c-runtime-library/reference/malloc) 會呼叫要求10個位元組配置的基底堆積配置常式。 不過，在 Debug 組建中， `malloc` 會呼叫 [_malloc_dbg](/cpp/c-runtime-library/reference/malloc-dbg)，然後呼叫基底堆積配置常式，要求10個位元組的配置加上大約36個位元組的額外記憶體。 偵錯堆積裡所有產生的記憶體區塊會在單向連結串列 (Single-Linked List) 中完成連接 (依配置時間排列順序)。

偵錯堆積常式配置的額外記憶體是用於簿記資訊，這些資訊可能為將偵錯記憶體區塊連結在一起的指標，和用來捕捉配置區域覆寫的資料每端的小型緩衝區。

目前，用於儲存偵錯堆積的簿記資訊的區塊標頭結構會根據 DBGINT.H 標頭檔來宣告：

```cpp
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

目前在區塊使用者資料區每一端的 `NoMansLand` 緩衝區大小是 4 位元組，而且會填入偵錯堆積常式所使用的已知位元組值，以確認沒有覆寫使用者記憶體區塊的限制。 偵錯堆積也會以一個已知值來填寫新的記憶體區塊。 如果您打算像以下的說明所述，維持堆積連結串列中的釋放區塊，這些釋放區塊也會填入一個已知值。 目前，使用的實際位元組值如下：

NoMansLand (0xFD) 應用程式所使用記憶體的任一邊的 "NoMansLand" 緩衝區目前已填入0xFD。

已釋放的區塊 (0xDD) 設定旗標時，會將未使用的已釋放區塊保留在 debug 堆積的連結清單中，且 `_CRTDBG_DELAY_FREE_MEM_DF` 目前已填入0xDD。

新物件 (0xCD) 新物件在配置時，會填入0xCD。

![回到頂端](../debugger/media/pcs_backtotop.png "PCS_BackToTop")[內容](#BKMK_Contents)

## <a name="types-of-blocks-on-the-debug-heap"></a><a name="BKMK_Types_of_blocks_on_the_debug_heap"></a> 偵錯工具堆積上的區塊類型
偵錯堆積裡的每個記憶體區塊會設定成五種配置類型的其中一種。 這些類型可以針對不同的流失偵測和狀態報告目的來追蹤和報告。 您可以透過直接呼叫其中一個偵錯堆積配置函式 (例如 [_malloc_dbg](/cpp/c-runtime-library/reference/malloc-dbg)) 加以配置的方式，來指定區塊類型。 五種偵錯堆積 (設定於 **_CrtMemBlockHeader** 結構的 **nBlockUse** 成員) 中的記憶體區塊類型如下：

**_NORMAL_BLOCK** 對 [malloc](/cpp/c-runtime-library/reference/malloc) 或 [calloc](/cpp/c-runtime-library/reference/calloc) 的呼叫會建立一般區塊。 如果您只要使用一般區塊，而且不需要用戶端區塊，建議您定義 [_CRTDBG_MAP_ALLOC](/cpp/c-runtime-library/crtdbg-map-alloc)，它會造成所有堆積配置呼叫都對應至它們在偵錯組建裡的偵錯對等用法。 這可將每個配置呼叫的相關檔名和行號資訊儲存在對應的區塊標頭裡。

`_CRT_BLOCK`由許多執行階段程式庫函式內部所配置的記憶體區塊標記為 CRT 區塊，以便分別處理。 因此，流失偵測和其他操作不會受到影響。 配置必須從未配置、重新配置或釋放任何 CRT 類型的區塊。

`_CLIENT_BLOCK`應用程式可以使用這種記憶體區塊類型配置、使用偵錯堆積函式的明確呼叫，繼續追蹤指定的配置群組，以達到偵錯的目的。 例如，MFC 將所有 **CObjects** 配置為用戶端區塊；其他應用程式可能會將不同的記憶體物件保持在用戶端區塊中。 也可以為達更細微的追蹤而設定用戶端區塊的子類型。 若要指定用戶端區塊的子類型，將數字向左移位 (Left Shift) 16 個位元並且以 `OR` 將之 `_CLIENT_BLOCK` 起來。 例如：

```cpp
#define MYSUBTYPE 4
freedbg(pbData, _CLIENT_BLOCK|(MYSUBTYPE<<16));
```

可以使用 [_CrtSetDumpClient](/cpp/c-runtime-library/reference/crtsetdumpclient) 安裝用戶端提供的攔截函式 (可用來傾印儲存在用戶端區塊的物件)，每當偵錯函式傾印用戶端區塊時就會予以呼叫。 此外，可使用 [_CrtDoForAllClientObjects](/cpp/c-runtime-library/reference/crtdoforallclientobjects)來呼叫應用程式為偵錯堆積裡每個用戶端區塊所提供的指定函式。

**_FREE_BLOCK** 一般來說，已釋放的區塊會從清單中移除。 若要檢查釋放記憶體是否仍然不能寫入，或模擬低記憶體條件，您可以選擇保留連結串列上的釋放區塊，將其標記為可用，並填入已知位元組值 (目前是 0xDD)。

**_IGNORE_BLOCK** 您可以關閉一段時間的 debug 堆積作業。 在這段期間，記憶體區塊會保留於清單終上，但是標記為忽略區塊。

若要判斷指定區塊的類型和子類型，請使用函式 [_CrtReportBlockType](/cpp/c-runtime-library/reference/crtreportblocktype)，以及巨集 **_BLOCK_TYPE** 和 **_BLOCK_SUBTYPE**。 巨集會定義 (在 crtdbg.h 裡)，參見下例：

```cpp
#define _BLOCK_TYPE(block)          (block & 0xFFFF)
#define _BLOCK_SUBTYPE(block)       (block >> 16 & 0xFFFF)
```

![回到頂端](../debugger/media/pcs_backtotop.png "PCS_BackToTop")[內容](#BKMK_Contents)

## <a name="check-for-heap-integrity-and-memory-leaks"></a><a name="BKMK_Check_for_heap_integrity_and_memory_leaks"></a>檢查堆積完整性和記憶體流失
許多偵錯堆積的功能必須從程式碼內存取。 下一節將說明一些功能以及如何使用這些功能。

`_CrtCheckMemory` 例如，您可以使用 [_CrtCheckMemory](/cpp/c-runtime-library/reference/crtcheckmemory)的呼叫來檢查任何一點的堆積完整性。 這個函式檢查堆積裡的每個記憶體區塊，確認記憶體區塊標頭資訊是有效的，並且確認緩衝區未經修改。

`_CrtSetDbgFlag` 您可以使用內部旗標（ [_crtDbgFlag](/cpp/c-runtime-library/crtdbgflag)）來控制偵錯工具堆積追蹤配置的方式，該旗標可以使用 [_CrtSetDbgFlag](/cpp/c-runtime-library/reference/crtsetdbgflag) 函數進行讀取和設定。 您可以變更這個旗標，來指示偵錯堆積在程式結束時檢查記憶體流失，並且報告任何偵測到的遺漏。 同樣地，您可以指定連結串列不要移除釋放的記憶體區塊，以模擬低記憶體情況。 檢查堆積時，這些釋放的區塊會在它們的項目裡檢查以確定它們沒有被干擾。

**_crtDbgFlag** 旗標包含下列位元欄位：

|位元欄位|預設<br /><br /> value|Description|
|---------------|-----------------------|-----------------|
|**_CRTDBG_ALLOC_MEM_DF**|開啟|開啟偵錯配置。 當這個位元關閉時，配置會繼續鏈結在一起，但是區塊類型是 **_IGNORE_BLOCK**。|
|**_CRTDBG_DELAY_FREE_MEM_DF**|關閉|防止真的釋放記憶體，這是為了模擬低記憶體情況。 當這個位元開啟時，釋放區塊會保持在偵錯堆積的連結清單裡，但是會標記為 **_FREE_BLOCK** 並且會填入一個特殊位元組值。|
|**_CRTDBG_CHECK_ALWAYS_DF**|關閉|造成每次配置和解除配置時都會呼叫 **_CrtCheckMemory**。 這會減緩執行，但可以快速捕捉錯誤。|
|**_CRTDBG_CHECK_CRT_DF**|關閉|造成區塊標記為類型 **_CRT_BLOCK**，以便包含於流失偵測和狀態差異操作中。 當這個位元關閉時，會忽略在這類操作期間執行階段程式庫內部所使用的記憶體。|
|**_CRTDBG_LEAK_CHECK_DF**|關閉|造成透過呼叫 **_CrtDumpMemoryLeaks**，在程式結束時執行流失檢查。 如果應用程式無法釋放它所配置的所有記憶體，會產生錯誤報告。|

![回到頂端](../debugger/media/pcs_backtotop.png "PCS_BackToTop")[內容](#BKMK_Contents)

## <a name="configure-the-debug-heap"></a><a name="BKMK_Configure_the_debug_heap"></a>設定偵錯堆積
所有堆積函式的呼叫，例如 `malloc`、`free`、`calloc`、`realloc`、`new` 和 `delete` 都會解析成操作於偵錯堆積裡的這些函式之偵錯版本。 當您釋放記憶體區塊時，偵錯堆積會自動檢查配置區域每端的緩衝區之完整性，如果發生覆寫發便會發出錯誤報告。

**若要使用偵錯堆積**

- 以 C 執行階段程式庫的偵錯版本連結您應用程式的偵錯組建。

  **若要變更一或多個 _crtDbgFlag 位元欄位並建立旗標的新狀態**

1. 使用設為 `_CrtSetDbgFlag` (為取得目前的 `newFlag` 狀態) 的 `_CRTDBG_REPORT_FLAG` 參數來呼叫 `_crtDbgFlag`，且將傳回值儲存在暫存變數中。

2. 開啟任何位 `OR` (位 &#124; 符號) 暫存變數， (在應用程式程式碼中由資訊清單常數) 表示的對應位。

3. 關閉其他位 `AND` (位 & 符號) 具有 `NOT` 適當位元遮罩之 (位 ~ 符號) 的變數。

4. 使用設成儲存於暫存變數值的 `_CrtSetDbgFlag` 參數呼叫 `newFlag`，以便建立 `_crtDbgFlag` 的新狀態。

   例如，下列程式碼開啟自動流失偵測並且關閉類型 `_CRT_BLOCK` 的區塊檢查：

```cpp
// Get current flag
int tmpFlag = _CrtSetDbgFlag( _CRTDBG_REPORT_FLAG );

// Turn on leak-checking bit.
tmpFlag |= _CRTDBG_LEAK_CHECK_DF;

// Turn off CRT block checking bit.
tmpFlag &= ~_CRTDBG_CHECK_CRT_DF;

// Set flag to the new value.
_CrtSetDbgFlag( tmpFlag );
```

![回到頂端](../debugger/media/pcs_backtotop.png "PCS_BackToTop")[內容](#BKMK_Contents)

## <a name="new-delete-and-_client_blocks-in-the-c-debug-heap"></a><a name="BKMK_new__delete__and__CLIENT_BLOCKs_in_the_C___debug_heap"></a>\_ \_ c + + debug 堆積中的 new、delete 和 CLIENT 區塊
C 執行階段程式庫的偵錯版本包含 C++ `new` 及 `delete` 運算子的偵錯版本。 如果您使用 `_CLIENT_BLOCK` 配置類型，則必須直接呼叫 `new` 運算子的偵錯版本，或建立可以取代偵錯模式中 `new` 運算子的巨集，如同下列範例所示：

```cpp
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

![回到頂端](../debugger/media/pcs_backtotop.png "PCS_BackToTop")[內容](#BKMK_Contents)

## <a name="heap-state-reporting-functions"></a><a name="BKMK_Heap_State_Reporting_Functions"></a>堆積狀態報告函式
 **_CrtMemState**

 若要捕捉指定時間的堆積狀態之摘要快照，請使用定義在 CRTDBG.H 裡的 _CrtMemState 結構：

```cpp
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

|函式|描述|
|--------------|-----------------|
|[_CrtMemCheckpoint](/cpp/c-runtime-library/reference/crtmemcheckpoint)|將堆積的快照儲存在應用程式提供的 **_CrtMemState** 結構中。|
|[_CrtMemDifference](/cpp/c-runtime-library/reference/crtmemdifference)|比較兩個記憶體狀態結構，將它們之間的差異儲存在第三個狀態結構，如果兩個狀態不同則傳回 TRUE。|
|[_CrtMemDumpStatistics](/cpp/c-runtime-library/reference/crtmemdumpstatistics)|傾印指定的 **_CrtMemState** 結構。 結構可能包含指定時間裡偵錯堆積的狀態快照或者是兩個快照之間的差異。|
|[_CrtMemDumpAllObjectsSince](/cpp/c-runtime-library/reference/crtmemdumpallobjectssince)|傾印從堆積的指定快照使用後或從執行開始的所有配置物件之相關資訊。 如果應用程式是使用 **_CrtSetDumpClient** 安裝，則每次當它傾印 **_CLIENT_BLOCK** 區塊時，就會呼叫應用程式提供的攔截函式。|
|[_CrtDumpMemoryLeaks](/cpp/c-runtime-library/reference/crtdumpmemoryleaks)|判斷自從程式執行開始時，是否有任何的記憶體流失發生，如果有的話，傾印所有配置的物件。 如果應用程式是使用 **_CrtSetDumpClient** 安裝，則每次當 **_CrtDumpMemoryLeaks** 傾印 **_CLIENT_BLOCK** 區塊時，它就會呼叫應用程式提供的攔截函式。|

![回到頂端](../debugger/media/pcs_backtotop.png "PCS_BackToTop")[內容](#BKMK_Contents)

## <a name="track-heap-allocation-requests"></a><a name="BKMK_Track_Heap_Allocation_Requests"></a>追蹤堆積配置要求
雖然指出判斷提示或報告巨集執行的原始程式檔名稱和行號通常在找出問題原因很有用，但是對於堆積配置函式可能就不是這樣。 雖然巨集可以插入到許多在應用程式邏輯樹狀圖裡合適的點，但是配置通常是在許多不同時間裡由許多不同地方的特殊常式呼叫。 問題通常不是哪一行程式碼做了錯誤的配置，而是上千個配置中，哪一個配置是由哪一錯誤程式碼所造成，以及其錯誤原因為何。

**唯一配置要求號碼和 _crtBreakAlloc**

最簡單的辨識發生錯誤的特定堆積配置呼叫方法，是利用與偵錯堆積裡每個區塊相關的唯一配置要求編號。 當區塊的相關資訊由其中一個傾印函式回報時，這個配置要求編號會包含在大括弧裡 (例如 "{36}")。

當您知道不適當配置區塊的配置要求編號後，您可以將這個編號傳遞至 [_CrtSetBreakAlloc](/cpp/c-runtime-library/reference/crtsetbreakalloc) 來建立中斷點。 執行會在配置區塊之前中斷，而您即可回溯追蹤以判斷哪一個常式要對這個錯誤呼叫負責。 若要避免重新編譯，您可以在偵錯工具裡將 **_crtBreakAlloc** 設定為您要的配置要求編號，來完成相同的事。

**建立配置常式的偵錯版本**

較複雜的方法是建立您自己的配置常式偵錯版本，與 [堆積配置函式](../debugger/debug-versions-of-heap-allocation-functions.md)的 **_dbg** 版本相似。 然後您可以傳遞原始程式檔和行號引數到下面的堆積配置常式，而且立即能夠看到錯誤的配置的發生位置。

例如，假設應用程式包含一個類似下列的一般使用常式：

```cpp
int addNewRecord(struct RecStruct * prevRecord,
                 int recType, int recAccess)
{
    // ...code omitted through actual allocation...
    if ((newRec = malloc(recSize)) == NULL)
    // ... rest of routine omitted too ...
}
```

您可以在標頭檔 (Header File) 裡加入像這樣的程式碼：

```cpp
#ifdef _DEBUG
#define  addNewRecord(p, t, a) \
            addNewRecord(p, t, a, __FILE__, __LINE__)
#endif
```

接著，您可以依照下列示範方式，在記錄建立常式裡變更配置：

```cpp
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

![回到頂端](../debugger/media/pcs_backtotop.png "PCS_BackToTop")[內容](#BKMK_Contents)

## <a name="see-also"></a>另請參閱
[偵錯機器碼](../debugger/debugging-native-code.md)
