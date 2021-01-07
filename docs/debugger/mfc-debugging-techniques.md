---
title: MFC 調試技術 |Microsoft Docs
description: 學慣用于調試 MFC 程式的技術，包括：編碼中斷點、追蹤、記憶體流失偵測、物件記憶體傾印和程式大小減少。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- AfxEnableMemoryTracking
- CMemoryState
- delayFreeMemDF
- checkAlwaysMemDF
- vs.debug.mfc
- vs.debug.objects.dump
- vs.debug.memory.dump
- allocMemDF
- afxMemDF
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [MFC]
ms.assetid: b154fc31-5e90-4734-8cbd-58dd9fe1f750
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5cf00191aff408b1133c281e10eea17e3a923215
ms.sourcegitcommit: c67dece5ded82a5867148e1f94396954c1ec4398
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/07/2021
ms.locfileid: "97975117"
---
# <a name="mfc-debugging-techniques"></a>MFC 偵錯技術
如果您正在偵錯 MFC 程式，這些偵錯技術可能很有幫助。

## <a name="in-this-topic"></a><a name="BKMK_In_this_topic"></a> 本主題中
[AfxDebugBreak](#BKMK_AfxDebugBreak)

[TRACE 宏](#BKMK_The_TRACE_macro)

[在 MFC 中偵測記憶體流失](#BKMK_Memory_leak_detection_in_MFC)

- [追蹤記憶體配置](#BKMK_Tracking_memory_allocations)

- [啟用記憶體診斷](#BKMK_Enabling_memory_diagnostics)

- [擷取記憶體快照](#BKMK_Taking_memory_snapshots)

- [檢視記憶體統計資料](#BKMK_Viewing_memory_statistics)

- [取得物件傾印](#BKMK_Taking_object_dumps)

  - [解讀記憶體傾印](#BKMK_Interpreting_memory_dumps)

  - [自訂物件傾印](#BKMK_Customizing_object_dumps)

  - [減少 MFC 偵錯組建的大小](#BKMK_Reducing_the_size_of_an_MFC_Debug_build)

  - [使用所選模組的 debug 資訊建立 MFC 應用程式](#BKMK_Building_an_MFC_app_with_debug_information_for_selected_modules)

## <a name="afxdebugbreak"></a><a name="BKMK_AfxDebugBreak"></a> AfxDebugBreak
MFC 提供了一個特殊的 [AfxDebugBreak](/cpp/mfc/reference/diagnostic-services#afxdebugbreak) 函式，可在原始程式碼中直接撰寫 (硬式編碼) 中斷點：

```cpp
AfxDebugBreak( );
```

在 Intel 平台上， `AfxDebugBreak` 會產生下列會在原始程式碼裡而非在核心 (Kernel) 程式碼中斷的程式碼：

```cpp
_asm int 3
```

在其他的平台上， `AfxDebugBreak` 只會呼叫 `DebugBreak`。

當您建立發行的組建或使用 `AfxDebugBreak` 來包圍它們時，請務必要移除 `#ifdef _DEBUG` 陳述式。

[本主題內容](#BKMK_In_this_topic)

## <a name="the-trace-macro"></a><a name="BKMK_The_TRACE_macro"></a> TRACE 巨集
若要在偵錯工具 [輸出視窗](../ide/reference/output-window.md)裡顯示程式的訊息，您可以使用 [ATLTRACE](/previous-versions/6xkxyz08(v=vs.140)) 巨集或 MFC [TRACE](/previous-versions/6w95a4ha(v=vs.140)) 巨集。 像 [判斷提示](../debugger/c-cpp-assertions.md)一樣，追蹤巨集只有在程式的偵錯版本才會啟動而且在發行版本編譯時會消失。

下列範例顯示一些您可以使用 **TRACE** 巨集的方式。 就像 `printf`一樣， **TRACE** 巨集可以處理許多引數。

```cpp
int x = 1;
int y = 16;
float z = 32.0;
TRACE( "This is a TRACE statement\n" );

TRACE( "The value of x is %d\n", x );

TRACE( "x = %d and y = %d\n", x, y );

TRACE( "x = %d and y = %x and z = %f\n", x, y, z );
```

TRACE 宏會適當地處理 char \* 和 wchar_t \* 參數。 下列範例示範搭配不同類型的字串參數來使用 TRACE 巨集。

```cpp
TRACE( "This is a test of the TRACE macro that uses an ANSI string: %s %d\n", "The number is:", 2);

TRACE( L"This is a test of the TRACE macro that uses a UNICODE string: %s %d\n", L"The number is:", 2);

TRACE( _T("This is a test of the TRACE macro that uses a TCHAR string: %s %d\n"), _T("The number is:"), 2);
```

如需 **TRACE** 巨集的詳細資訊，請參閱 [診斷服務](/cpp/mfc/reference/diagnostic-services)。

[本主題內容](#BKMK_In_this_topic)

## <a name="detecting-memory-leaks-in-mfc"></a><a name="BKMK_Memory_leak_detection_in_MFC"></a> 在 MFC 偵測記憶體流失
MFC 提供類別和函式來偵測已配置但從未解除配置的記憶體。

### <a name="tracking-memory-allocations"></a><a name="BKMK_Tracking_memory_allocations"></a> 追蹤記憶體配置
在 MFC 裡，您可以使用 [DEBUG_NEW](/previous-versions/tz7sxz99(v=vs.140)) 巨集取代 **new** 運算子來幫助尋找記憶體流失。 在程式的偵錯版本裡， `DEBUG_NEW` 追蹤每個物件所配置的檔案名稱和行號。 當您編譯程式的發行版本時， `DEBUG_NEW` 解析成簡單而不具檔名和行號資訊的 **new** 操作。 因此，在程式的發行版本中不會有速度負擔。

如果您不要以 `DEBUG_NEW` 取代 **new** 來重新編寫整個程式，您可以在原始程式檔裡定義這個巨集：

```cpp
#define new DEBUG_NEW
```

當您執行 [物件傾印](#BKMK_Taking_object_dumps)，每個以 `DEBUG_NEW` 配置的物件會顯示其配置位置的檔案和行號，讓您可以指出記憶體流失的來源。

MFC 架構的偵錯版本會自動使用 `DEBUG_NEW` ，但是您的程式碼不會。 如果您要擁有 `DEBUG_NEW`的優點，您必須依照上述方式，明確地使用 `DEBUG_NEW` 或 **#define new** 。

[本主題內容](#BKMK_In_this_topic)

### <a name="enabling-memory-diagnostics"></a><a name="BKMK_Enabling_memory_diagnostics"></a> 啟用記憶體診斷
您必須在使用記憶體診斷設施之前啟用診斷追蹤。

**若要啟用或停用記憶體診斷**

- 呼叫全域函式 [AfxEnableMemoryTracking](/previous-versions/hzsxb6e8(v=vs.140)) 來啟用或停用診斷記憶體配置器 (Allocator)。 因為記憶體診斷在偵錯程式庫中預設是啟用的，通常您會使用這個函式將它們暫時地關閉，以增加程式執行速度和減少診斷輸出。

  **若要選取具 afxMemDF 的特定記憶體診斷功能**

- 如果您要更準確地控制記憶體診斷功能，您可以設定 MFC 全域變數 [afxMemDF](/previous-versions/ahe4a83t(v=vs.140))值，選擇性地開啟和關閉各個記憶體診斷功能。 這個變數可以有下列的值，如同列舉類型 **afxMemDF** 所指定。

  |值|描述|
  |-----------|-----------------|
  |**allocMemDF**|開啟診斷記憶體配置器 (預設)。|
  |**delayFreeMemDF**|呼叫 `delete` 或 `free` 時會延遲釋放記憶體，直到程式結束。 這會造成程式配置可能的最大記憶體量。|
  |**checkAlwaysMemDF**|每一次記憶體配置或釋放時都會呼叫 [AfxCheckMemory](/cpp/mfc/reference/diagnostic-services#afxcheckmemory) 。|

  這些值可以藉由執行邏輯 OR 操作用於結合，如下所示：

  ```C++
  afxMemDF = allocMemDF | delayFreeMemDF | checkAlwaysMemDF;
  ```

  [本主題內容](#BKMK_In_this_topic)

### <a name="taking-memory-snapshots"></a><a name="BKMK_Taking_memory_snapshots"></a> 製作記憶體快照集

1. 建立 [CMemoryState](/previous-versions/visualstudio/visual-studio-2010/2ads32e2(v=vs.100)) 物件並呼叫 [CMemoryState::Checkpoint](/cpp/mfc/reference/cmemorystate-structure#checkpoint) 成員函式。 這會建立第一個記憶體快照。

2. 程式執行記憶體配置和解除配置操作之後，會建立另一個 `CMemoryState` 物件並且呼叫此物件的 `Checkpoint` 。 這會取得記憶體使用的第二個快照。

3. 建立第三個 `CMemoryState` 物件並呼叫其 [CMemoryState::Difference](/cpp/mfc/reference/cmemorystate-structure#difference) 成員函式，會提供兩個先前的 `CMemoryState` 物件作為引數。 如果兩種記憶體狀態之間有差異， `Difference` 函式會傳回非零值。 這表示有些記憶體區塊沒有解除配置。

    這個範例會顯示程式碼看起來的樣子：

    ```cpp
    // Declare the variables needed
    #ifdef _DEBUG
        CMemoryState oldMemState, newMemState, diffMemState;
        oldMemState.Checkpoint();
    #endif

        // Do your memory allocations and deallocations.
        CString s("This is a frame variable");
        // The next object is a heap object.
        CPerson* p = new CPerson( "Smith", "Alan", "581-0215" );

    #ifdef _DEBUG
        newMemState.Checkpoint();
        if( diffMemState.Difference( oldMemState, newMemState ) )
        {
            TRACE( "Memory leaked!\n" );
        }
    #endif
    ```

    請注意，記憶體檢查語句會以 #ifdef 的 **_DEBUG/#endif** 區塊括住，因此它們只會在程式的偵錯工具版本中編譯。

    您知道有記憶體流失的狀況存在之後，可以使用另一個成員函式 [CMemoryState::DumpStatistics](/cpp/mfc/reference/cmemorystate-structure#dumpstatistics) 幫助您尋找流失的記憶體。

    [本主題內容](#BKMK_In_this_topic)

### <a name="viewing-memory-statistics"></a><a name="BKMK_Viewing_memory_statistics"></a> 查看記憶體統計資料
[CMemoryState::Difference](/cpp/mfc/reference/cmemorystate-structure#difference) 函式會查看兩個記憶體狀態物件，並偵測開頭和結尾狀態之間任何沒有從堆積解除配置的物件。 在您已擷取記憶體快照並使用 `CMemoryState::Difference`比較這些快照之後，您可以呼叫 [CMemoryState::DumpStatistics](/cpp/mfc/reference/cmemorystate-structure#dumpstatistics) 取得沒有解除配置之物件的詳細資訊。

請考慮下列範例：

```cpp
if( diffMemState.Difference( oldMemState, newMemState ) )
{
    TRACE( "Memory leaked!\n" );
    diffMemState.DumpStatistics();
}
```

從此範例的傾印看起來會像這樣：

```cpp
0 bytes in 0 Free Blocks
22 bytes in 1 Object Blocks
45 bytes in 4 Non-Object Blocks
Largest number used: 67 bytes
Total allocations: 67 bytes
```

自由區塊是指如果 `afxMemDF` 設為 `delayFreeMemDF`則解除配置會延遲的區塊。

一般物件區塊 (顯示在第二行) 會維持在堆積配置。

非物件區塊會以 `new`包含已配置的陣列和結構。 在這種情況下，四個非物件區塊會配置於堆積上而不會解除配置。

`Largest number used` 提供程式在任何時間可以使用的最大記憶體。

`Total allocations` 提供程式所使用的總記憶體量。

[本主題內容](#BKMK_In_this_topic)

### <a name="taking-object-dumps"></a><a name="BKMK_Taking_object_dumps"></a> 取得物件傾印
在 MFC 程式中，您可以使用 [CMemoryState：:D umpallobjectssince](/cpp/mfc/reference/cmemorystate-structure#dumpallobjectssince) 來傾印堆積上尚未解除配置之所有物件的描述。 `DumpAllObjectsSince` 會傾印從上一個 [CMemoryState::Checkpoint](/cpp/mfc/reference/cmemorystate-structure#checkpoint)。 如果沒有發生 `Checkpoint` 呼叫， `DumpAllObjectsSince` 會傾印目前在記憶體的所有物件和非物件。

> [!NOTE]
> 您必須先 [啟用診斷追蹤](#BKMK_Enabling_memory_diagnostics)，才能使用 MFC 物件傾印。

> [!NOTE]
> MFC 會在程式結束時自動傾印所有的流失物件，因此您不需要建立程式碼來傾印這個時候的物件。

下列程式碼會比較兩個記憶體狀態來測試記憶體流失，如果偵測到遺漏便會傾印所有物件：

```cpp
if( diffMemState.Difference( oldMemState, newMemState ) )
{
    TRACE( "Memory leaked!\n" );
    diffMemState.DumpAllObjectsSince();
}
```

傾印的內容看起來像這樣：

```cmd
Dumping objects ->

{5} strcore.cpp(80) : non-object block at $00A7521A, 9 bytes long
{4} strcore.cpp(80) : non-object block at $00A751F8, 5 bytes long
{3} strcore.cpp(80) : non-object block at $00A751D6, 6 bytes long
{2} a CPerson at $51A4

Last Name: Smith
First Name: Alan
Phone #: 581-0215

{1} strcore.cpp(80) : non-object block at $00A7516E, 25 bytes long
```

大多數程式碼一開頭括號裡的數字便指定了物件配置的順序。 最近配置的物件的數字最高，且會出現在傾印的最上方。

若要從物件傾印取得最大量的資訊，您可以覆寫任何 `Dump` 衍生物件的 `CObject`成員函式來自訂物件傾印。

您可以將全域變數 `_afxBreakAlloc` 設定為顯示在括號裡的數字，將中斷點設於特定記憶體配置上。 如果您重新執行該程式，則當此配置發生時，偵錯工具會中斷執行。 然後您可以查看呼叫堆疊來檢視程式如何到達此點。

C 執行階段程式庫中類似的函式是 [_CrtSetBreakAlloc](/cpp/c-runtime-library/reference/crtsetbreakalloc)，其可用於 C 執行階段配置。

[本主題內容](#BKMK_In_this_topic)

#### <a name="interpreting-memory-dumps"></a><a name="BKMK_Interpreting_memory_dumps"></a> 解譯記憶體傾印
請看此物件傾印的詳細內容：

```cmd
{5} strcore.cpp(80) : non-object block at $00A7521A, 9 bytes long
{4} strcore.cpp(80) : non-object block at $00A751F8, 5 bytes long
{3} strcore.cpp(80) : non-object block at $00A751D6, 6 bytes long
{2} a CPerson at $51A4

Last Name: Smith
First Name: Alan
Phone #: 581-0215

{1} strcore.cpp(80) : non-object block at $00A7516E, 25 bytes long
```

產生這種傾印的程式只有兩種明確的配置，一種是在堆疊上，另一種是在堆積上：

```cpp
// Do your memory allocations and deallocations.
CString s("This is a frame variable");
// The next object is a heap object.
CPerson* p = new CPerson( "Smith", "Alan", "581-0215" );
```

`CPerson` 建構函式 (Constructor) 需要三個 `char`指標的引數 (用來初始化 `CString` 成員變數)。 在記憶體傾印裡，您可以看到 `CPerson` 物件和三個非物件區塊 (3、4 和 5)。 這些物件會儲存 `CString` 成員變數字元，且在不會在叫用 (Invoke) `CPerson` 物件解構函式 (Destructor) 刪除。

區塊編號 2 是 `CPerson` 物件本身。 `$51A4` 代表區塊的位址且後面跟著物件的內容 (由 `CPerson`DumpAllObjectsSince`Dump` 呼叫時，由 [::](/cpp/mfc/reference/cmemorystate-structure#dumpallobjectssince)所輸出)。

您可以由區塊編號 1 的順序號碼和大小猜想出它與 `CString` 框架變數相關，這些資訊符合 `CString` 框架變數裡的字元數字。 框架上配置的變數在框架超過範圍 (Scope) 時會自動解除配置。

**框架變數**

一般來說，您不必擔心與框架變數相關的堆積物件，因為它們會在框架變數超過範圍時自動解除配置。 若要避免在記憶體診斷傾印裡發生混亂，您應該定位 `Checkpoint` 呼叫，這樣它們會在框架變數範圍的外部。 例如，將範圍括號放在前述配置程式碼的前後，如下所示：

```cpp
oldMemState.Checkpoint();
{
    // Do your memory allocations and deallocations ...
    CString s("This is a frame variable");
    // The next object is a heap object.
    CPerson* p = new CPerson( "Smith", "Alan", "581-0215" );
}
newMemState.Checkpoint();
```

加了範圍括號，這個範例的記憶體傾印如下：

```cmd
Dumping objects ->

{5} strcore.cpp(80) : non-object block at $00A7521A, 9 bytes long
{4} strcore.cpp(80) : non-object block at $00A751F8, 5 bytes long
{3} strcore.cpp(80) : non-object block at $00A751D6, 6 bytes long
{2} a CPerson at $51A4

Last Name: Smith
First Name: Alan
Phone #: 581-0215
```

**非物件配置**

請注意，有些配置是物件 (例如 `CPerson`)，而有些則是非物件配置。 「非物件配置」為不是衍生自 `CObject` 的物件配置，或基本 C 類型 (例如 `char`、`int` 或 `long`) 的配置。 如果 <strong>CObject</strong>衍生類別配置額外空間 (例如為內部緩衝區)，則該類物件便會顯示物件和非物件配置。

**防止記憶體流失**

請注意，在上面的程式碼中，與 `CString` 框架變數相關聯的記憶體區塊已經自動解除配置，而且不會顯示為記憶體流失。 與範圍規則相關的自動解除配置會處理大多數與框架變數相關的記憶體流失。

然而，對於堆積上的物件配置，您必須明確地刪除物件以防止記憶體流失。 若要清除先前範例裡最後的記憶體流失，請參考下列程式碼，刪除配置在堆積的 `CPerson` 物件：

```cpp
{
    // Do your memory allocations and deallocations.
    CString s("This is a frame variable");
    // The next object is a heap object.
    CPerson* p = new CPerson( "Smith", "Alan", "581-0215" );
    delete p;
}
```

[本主題內容](#BKMK_In_this_topic)

#### <a name="customizing-object-dumps"></a><a name="BKMK_Customizing_object_dumps"></a> 自訂物件傾印
當您從 [CObject](/cpp/mfc/reference/cobject-class)衍生類別時，您可在使用 `Dump` DumpAllObjectsSince [來傾印物件至](/cpp/mfc/reference/cmemorystate-structure#dumpallobjectssince) 輸出視窗 [時，覆寫](../ide/reference/output-window.md)成員函式以提供額外的資訊。

`Dump` 函式將物件的成員變數的文字表示寫入傾印內容 ([CDumpContext](/cpp/mfc/reference/cdumpcontext-class))。 傾印內容類似 I/O 資料流。 您可以使用附加運算子 (**<<**) 將資料傳送至 `CDumpContext` 。

當您覆寫 `Dump` 函式時，您應該先呼叫 `Dump` 的基底類別版本來傾印基底類別物件的內容。 接著輸出衍生類別中每個成員變數的文字說明和值。

`Dump` 函式的宣告看起來像這樣：

```cpp
class CPerson : public CObject
{
public:
#ifdef _DEBUG
    virtual void Dump( CDumpContext& dc ) const;
#endif

    CString m_firstName;
    CString m_lastName;
    // And so on...
};
```

因為只有在偵錯程式時，物件傾印才具有意義， `Dump` 函式的宣告會以 **#ifdef _DEBUG / #endif** 區塊括號起來。

在下列範例裡， `Dump` 函式先呼叫基底類別的 `Dump` 函式。 然後將每個成員變數的簡短說明和成員的值一起寫入至診斷資料流。

```cpp
#ifdef _DEBUG
void CPerson::Dump( CDumpContext& dc ) const
{
    // Call the base class function first.
    CObject::Dump( dc );

    // Now do the stuff for our specific class.
    dc << "last name: " << m_lastName << "\n"
        << "first name: " << m_firstName << "\n";
}
#endif
```

您必須提供 `CDumpContext` 引數來指定傾印的輸出位置。 MFC 的偵錯版本提供一個可以傳送輸出至偵錯工具的預先定義 `CDumpContext` 物件 (名為 `afxDump` )。

```cpp
CPerson* pMyPerson = new CPerson;
// Set some fields of the CPerson object.
//...
// Now dump the contents.
#ifdef _DEBUG
pMyPerson->Dump( afxDump );
#endif
```

[本主題內容](#BKMK_In_this_topic)

## <a name="reducing-the-size-of-an-mfc-debug-build"></a><a name="BKMK_Reducing_the_size_of_an_MFC_Debug_build"></a> 減少 MFC Debug 組建的大小
大型 MFC 應用程式的偵錯資訊可能需要大量的磁碟空間。 您可以使用下列其中一項程序縮減大小：

1. 使用 [/Z7、/zi、/zi (Debug 資訊格式)](/cpp/build/reference/z7-zi-zi-debug-information-format) 選項來重建 MFC 程式庫，而不是 **/Z7**。 這些選項會建置包含整個程式庫的偵錯資訊，以降低重複性並且節省空間的單一程式資料庫 (PDB) 檔。

2. 重建 MFC 程式庫，但不含 debug 資訊 (沒有 [/Z7、/zi、/zi (Debug 資訊格式) ](/cpp/build/reference/z7-zi-zi-debug-information-format) 選項) 。 在這個範例裡，缺乏偵錯資訊讓您無法在 MFC 程式庫程式碼裡使用大多數的偵錯工具設施，然而由於 MFC 程式庫已經充分偵錯過了，所以這不是問題。

3. 只以選取模組的偵錯資訊建置您自己的應用程式，如下所述。

    [本主題內容](#BKMK_In_this_topic)

### <a name="building-an-mfc-app-with-debug-information-for-selected-modules"></a><a name="BKMK_Building_an_MFC_app_with_debug_information_for_selected_modules"></a> 以選取的模組之偵錯資訊來建置 MFC 應用程式
以 MFC 偵錯程式庫建置選取模組，可以讓您在這些模組裡使用逐步執行的方法和其他偵錯設施。 此程式會使用專案的 Debug 和 Release 設定，因此會強制下列步驟中所述的變更 (也會在) 需要完整發行組建時進行「重建全部」。

1. 在 [方案總管] 中選取專案。

2. 從 [ **檢視** ] 功能表中，選取 [ **屬性頁**]。

3. 首先，您要建立新專案組態。

   1. 在 [ **\<Project> 屬性頁**] 對話方塊中，按一下 [ **Configuration Manager** ] 按鈕。

   2. 在 [組態管理員對話方塊](/previous-versions/visualstudio/visual-studio-2010/t1hy4dhz(v=vs.100))裡，在方格中尋找專案。 **在 [設定**] 欄中，選取 **\<New...>** 。

   3. 在 [新增專案組態對話方塊](/previous-versions/visualstudio/visual-studio-2010/0eh8w4cf(v=vs.100))裡，於 [ **專案組態名稱** ] 方塊內輸入新組態的名稱，例如「部分偵錯」。

   4. 在 [ **複製設定值** ] 清單裡，選擇 [ **發行**]。

   5. 按一下 **[確定** ] 以關閉 [ **新增專案** 設定] 對話方塊。

   6. 關閉 [ **組態管理員** ] 對話方塊。

4. 現在，您要為整個專案設定選項。

   1. 在 [ **屬性頁** ] 對話方塊裡，[ **組態屬性** ] 資料夾底下，選取 [ **一般** ] 分類。

   2. 在專案設計方格裡，展開 [ **專案預設值** ] (如果有需要)。

   3. 在 [ **專案預設值**] 底下，尋找 [ **MFC 用法**]。 目前的設定會出現在方格的右欄。 按一下目前設定並且將它變更為 [ **使用 MFC 的靜態程式庫**]。

   4. 在 [ **屬性頁** ] 對話方塊的左窗格裡，開啟 [ **C/C++** ] 資料夾並且選取 [ **前置處理器**]。 在屬性方格裡，尋找 [ **前置處理器定義** ]，並以 "_DEBUG" 取代 "NDEBUG"。

   5. 在 [ **屬性頁** ] 對話方塊的左窗格裡，開啟 [ **連結器** ] 資料夾並且選取 [ **輸入** ] 分類。 在屬性方格裡，尋找 [ **其他相依性**]。 在 [ **其他相依性** ] 設定裡，輸入「NAFXCWD.LIB」和「LIBCMT」。

   6. 按一下 [ **確定** ] 以儲存新組建選項，並且關閉 [ **屬性頁** ] 對話方塊。

5. 從 [ **建置** ] 功能表選取 [ **重建**]。 這會從模組移除所有的偵錯資訊，但是不會影響 MFC 程式庫。

6. 現在您必須將偵錯資訊加回至應用程式裡的選取模組。 記住您只能在以偵錯資訊編譯的模組裡設定中斷點並且執行其他偵錯工具功能。 對於您要包含偵錯資訊的每個專案檔，執行下列步驟：

   1. 在 [方案總管] 裡，開啟位於專案下的 [ **原始程式檔** ] 資料夾。

   2. 選取您要設定偵錯資訊的檔案。

   3. 從 [ **檢視** ] 功能表中，選取 [ **屬性頁**]。

   4. 在 [ **屬性頁** ] 對話方塊的 [ **組態設定** ] 資料夾底下，開啟 [ **C/C++** ] 資料夾，然後選取 [ **一般** ] 分類。

   5. 在屬性方格中，尋找 [偵錯資訊格式]。

   6. 按一下 [ **偵錯資訊格式** ] 設定並且選取偵錯資訊需要的選項 (通常是 [ **/ZI**])。

   7. 如果您要使用應用程式精靈所產生的應用程式，或者您有先行編譯的標頭，則必須關閉先行編譯的標頭，或在編譯其他模組之前重新編譯這些標頭。 否則，您會收到警告 C4650 和錯誤訊息 C2855。 您可以藉由變更 [ **\<Project> 屬性**] 對話方塊中的 [**建立/使用先行編譯頭** 檔]， (設定 **屬性** 資料夾、 **C/c + +** 子資料夾、先行 **編譯標頭** 類別) 來關閉先行編譯標頭檔。

7. 從 [ **建置** ] 功能表，選取 [ **建置** ] 來重建過期的專案檔案。

   除了本主題所說明的技巧以外，您可以使用外部 Makefile 來定義每個檔案的個別選項。 在此情況中，若要連結 MFC 偵錯程式庫，您必須定義每個模組的 [_DEBUG](/cpp/c-runtime-library/debug) 旗標。 如果您要使用 MFC 發行程式庫，您必須定義 NDEBUG。 如需撰寫外部 Makefile 的詳細資訊，請參閱 [NMAKE 參考](/cpp/build/running-nmake)。

   [本主題內容](#BKMK_In_this_topic)

## <a name="see-also"></a>請參閱
[偵錯機器碼](../debugger/debugging-native-code.md)