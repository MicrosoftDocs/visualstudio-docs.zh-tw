---
title: C/C++判斷提示 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [MFC], assertions
- results, checking
- result checking
- Call Stack window, assertion failures
- debugging [C++], assertions
- VERIFY macro
- assertions, side effects
- assertions
- ASSERT macro
- errors [C++], catching with assertions
- testing, error conditions with assertion statements
- _DEBUG macro
- Assertion Failed dialog box
- failures, finding locations
ms.assetid: 2d7b0121-71aa-414b-bbb6-ede1093d0bfc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 9e2e6d69e4c621d6be81a00a61482b71199bc0fc
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745748"
---
# <a name="cc-assertions"></a>C/C++ 判斷提示
判斷提示語句會指定您在程式中的某個時間點預期為 true 的條件。 如果該條件不是 true，判斷提示就會失敗，程式的執行會中斷，而且 [判斷提示[失敗] 對話方塊](../debugger/assertion-failed-dialog-box.md)隨即出現。

Visual Studio 支援C++以下列結構為基礎的判斷提示語句：

- MFC 程式的 MFC 判斷提示。

- [ATLASSERT](/cpp/atl/reference/debugging-and-error-reporting-macros#atlassert) ，適用于使用 ATL 的程式。

- 使用 C 執行時間程式庫之程式的 CRT 判斷提示。

- 適用于其他 C/C++程式的 ANSI [assert 函數](/cpp/c-runtime-library/reference/assert-macro-assert-wassert)。

  您可以使用判斷提示來攔截邏輯錯誤、檢查作業的結果，以及測試應該已經處理的錯誤狀況。

## <a name="BKMK_In_this_topic"></a>本主題內容
[判斷提示的工作方式](#BKMK_How_assertions_work)

[Debug 和 Release 組建中的判斷提示](#BKMK_Assertions_in_Debug_and_Release_builds)

[使用判斷提示的副作用](#BKMK_Side_effects_of_using_assertions)

[CRT 判斷提示](#BKMK_CRT_assertions)

[MFC 判斷提示](#BKMK_MFC_assertions)

- [MFC ASSERT_VALID 和 CObject：： AssertValid](#BKMK_MFC_ASSERT_VALID_and_CObject__AssertValid)

- [AssertValid 的限制](#BKMK_Limitations_of_AssertValid)

  [使用判斷提示](#BKMK_Using_assertions)

- [捕捉邏輯錯誤](#BKMK_Catching_logic_errors)

- [檢查結果](#BKMK_Checking_results_)

- [尋找未處理的錯誤](#BKMK_Testing_error_conditions_)

## <a name="BKMK_How_assertions_work"></a>判斷提示的工作方式
當偵錯工具因為 MFC 或 C 執行時間程式庫判斷提示而中止時，如果來源可供使用，偵錯工具就會流覽至發生判斷提示之來源檔案中的點。 判斷提示訊息會同時出現在 [[輸出] 視窗](../ide/reference/output-window.md)和 [判斷提示**失敗**] 對話方塊中。 如果您想要加以儲存以供日後參考，您可以從 [**輸出**] 視窗將判斷提示訊息複製到文字視窗。 [**輸出**] 視窗也可能包含其他錯誤訊息。 請仔細檢查這些訊息，因為它們會提供判斷提示失敗原因的線索。

使用判斷提示來偵測開發期間的錯誤。 作為規則，針對每個假設使用一個判斷提示。 例如，如果您假設引數不是 Null，請使用判斷提示來測試該假設。

[本主題內容](#BKMK_In_this_topic)

## <a name="BKMK_Assertions_in_Debug_and_Release_builds"></a>Debug 和 Release 組建中的判斷提示
只有在定義了 `_DEBUG` 時，判斷提示語句才會編譯。 否則，編譯器會將判斷提示視為 null 語句。 因此，判斷提示語句不會在您的最終發行程式中提供任何額外負荷或效能成本，並可讓您避免使用 `#ifdef` 的指示詞。

## <a name="BKMK_Side_effects_of_using_assertions"></a>使用判斷提示的副作用
當您將判斷提示加入至您的程式碼時，請確定判斷提示不會有副作用。 例如，請考慮下列修改 `nM` 值的判斷提示：

```cpp
ASSERT(nM++ > 0); // Don't do this!
```

因為 `ASSERT` 運算式不會在程式的發行版本中進行評估，所以 `nM` 在 Debug 和 Release 版本中會有不同的值。 若要避免在 MFC 中發生這個問題，您可以使用[驗證](/cpp/mfc/reference/diagnostic-services#verify)宏，而不是 `ASSERT`。 `VERIFY` 會評估所有版本中的運算式，但不會檢查發行版本中的結果。

請特別小心在判斷提示語句中使用函式呼叫，因為評估函式可能會產生非預期的副作用。

```cpp
ASSERT ( myFnctn(0)==1 ) // unsafe if myFnctn has side effects
VERIFY ( myFnctn(0)==1 ) // safe
```

`VERIFY` 會在 Debug 和 Release 版本中呼叫 `myFnctn`，因此可以接受使用。 不過，使用 `VERIFY` 會在發行版本中強加不必要函式呼叫的額外負荷。

[本主題內容](#BKMK_In_this_topic)

## <a name="BKMK_CRT_assertions"></a>CRT 判斷提示
CRTDBG.H 裡。H 標頭檔定義判斷提示檢查的[_ASSERT 和 _ASSERTE 宏](/cpp/c-runtime-library/reference/assert-asserte-assert-expr-macros)。

| 巨集 | 結果 |
|------------| - |
| `_ASSERT` | 如果指定的運算式評估為 FALSE，則為 `_ASSERT`的檔案名和行號。 |
| `_ASSERTE` | 與 `_ASSERT`相同，再加上所判斷運算式的字串表示。 |

`_ASSERTE` 的功能更強大，因為它會報告已關閉為 FALSE 的判斷提示運算式。 這可能足以識別問題，而不需要參考原始程式碼。 不過，您應用程式的 Debug 版本將會包含使用 `_ASSERTE` 判斷提示之每個運算式的字串常數。 如果您使用許多 `_ASSERTE` 宏，這些字串運算式會佔用大量的記憶體。 如果這種情況證明有問題，請使用 `_ASSERT` 來節省記憶體。

定義 `_DEBUG` 時，`_ASSERTE` 巨集定義如下：

```cpp
#define _ASSERTE(expr) \
    do { \
        if (!(expr) && (1 == _CrtDbgReport( \
            _CRT_ASSERT, __FILE__, __LINE__, #expr))) \
            _CrtDbgBreak(); \
    } while (0)
```

如果判斷提示運算式評估為 FALSE，則會呼叫[_CrtDbgReport](/cpp/c-runtime-library/reference/crtdbgreport-crtdbgreportw)來報告判斷提示失敗（預設使用訊息對話方塊）。 如果您在 [訊息] 對話方塊中選擇 [**重試**]，`_CrtDbgReport` 會傳回1，而 `_CrtDbgBreak` 會透過 `DebugBreak` 呼叫偵錯工具。

### <a name="checking-for-heap-corruption"></a>檢查堆積損毀
下列範例會使用[_CrtCheckMemory](/cpp/c-runtime-library/reference/crtcheckmemory)來檢查堆積是否損毀：

```cpp
_ASSERTE(_CrtCheckMemory());
```

### <a name="checking-pointer-validity"></a>檢查指標有效性
下列範例會使用[_CrtIsValidPointer](/cpp/c-runtime-library/reference/crtisvalidpointer)來驗證指定的記憶體範圍是否有效以進行讀取或寫入。

```cpp
_ASSERTE(_CrtIsValidPointer( address, size, TRUE );
```

下列範例會使用[_CrtIsValidHeapPointer](/cpp/c-runtime-library/reference/crtisvalidheappointer)來驗證指標指向本機堆積中的記憶體（此 C 執行時間程式庫實例所建立和管理的堆積），DLL 可以有自己的程式庫實例，也因此它自己的堆積。在應用程式堆積外部）。 此判斷提示不只會攔截 null 或超出範圍的位址，也會攔截靜態變數、堆疊變數和任何其他非任意記憶體的指標。

```cpp
_ASSERTE(_CrtIsValidPointer( myData );
```

### <a name="checking-a-memory-block"></a>檢查記憶體區塊
下列範例會使用[_CrtIsMemoryBlock](/cpp/c-runtime-library/reference/crtismemoryblock)來確認記憶體區塊位於本機堆積中，而且具有有效的區塊類型。

```cpp
_ASSERTE(_CrtIsMemoryBlock (myData, size, &requestNumber, &filename, &linenumber));
```

[本主題內容](#BKMK_In_this_topic)

## <a name="BKMK_MFC_assertions"></a>MFC 判斷提示
MFC 會定義判斷提示檢查的[ASSERT](https://msdn.microsoft.com/Library/1e70902d-d58c-4e7b-9f69-2aeb6cbe476c)宏。 它也會定義 `MFC ASSERT_VALID` 和 `CObject::AssertValid` 方法，以檢查 `CObject` 衍生物件的內部狀態。

如果 MFC `ASSERT` 宏的引數評估為零或 false，則宏會終止程式執行並警示使用者;否則，會繼續執行。

當判斷提示失敗時，[訊息] 對話方塊會顯示原始程式檔的名稱和判斷提示的行號。 如果您在對話方塊中選擇 [重試]，則呼叫[AfxDebugBreak](/cpp/mfc/reference/diagnostic-services#afxdebugbreak)會導致執行中斷至偵錯工具。 此時，您可以檢查呼叫堆疊，並使用其他偵錯工具功能來判定判斷提示失敗的原因。 如果您已啟用[即時的調試](../debugger/just-in-time-debugging-in-visual-studio.md)程式，而且偵錯工具尚未執行，則對話方塊可以啟動偵錯工具。

下列範例顯示如何使用 `ASSERT` 來檢查函數的傳回值：

```cpp
int x = SomeFunc(y);
ASSERT(x >= 0);   //  Assertion fails if x is negative
```

您可以使用 ASSERT 搭配[IsKindOf](https://docs.microsoft.com/cpp/mfc/reference/cobject-class#iskindof)函數來提供函數引數的類型檢查：

```cpp
ASSERT( pObject1->IsKindOf( RUNTIME_CLASS( CPerson ) ) );
```

@No__t_0 宏在發行版本中不會產生任何程式碼。 如果您需要評估發行版本中的運算式，請使用[VERIFY](https://msdn.microsoft.com/library/s8c29sw2.aspx#verify)宏而不是 ASSERT。

### <a name="BKMK_MFC_ASSERT_VALID_and_CObject__AssertValid"></a>MFC ASSERT_VALID 和 CObject：： AssertValid
[CObject：： AssertValid](https://docs.microsoft.com/cpp/mfc/reference/cobject-class#assertvalid)方法提供物件內部狀態的執行時間檢查。 雖然當您從 `CObject` 衍生類別時，不需要覆寫 `AssertValid`，但是您可以藉由執行此動作，讓類別更可靠。 `AssertValid` 應該在物件的所有成員變數上執行判斷提示，以確認它們包含有效的值。 例如，它應該檢查指標成員變數是否不是 Null。

下列範例顯示如何宣告 `AssertValid` 函式：

```cpp
class CPerson : public CObject
{
protected:
    CString m_strName;
    float   m_salary;
public:
#ifdef _DEBUG
    // Override
    virtual void AssertValid() const;
#endif
    // ...
};
```

當您覆寫 `AssertValid` 時，請先呼叫 `AssertValid` 的基類版本，然後再執行自己的檢查。 然後，使用 ASSERT 宏來檢查衍生類別的唯一成員，如下所示：

```cpp
#ifdef _DEBUG
void CPerson::AssertValid() const
{
    // Call inherited AssertValid first.
    CObject::AssertValid();

    // Check CPerson members...
    // Must have a name.
    ASSERT( !m_strName.IsEmpty());
    // Must have an income.
    ASSERT( m_salary > 0 );
}
#endif
```

如果您有任何成員變數儲存物件，您可以使用 `ASSERT_VALID` 宏來測試其內部有效性（如果其類別覆寫 `AssertValid`）。

例如，假設有一個類別 `CMyData`，它會將[CObList](/cpp/mfc/reference/coblist-class)儲存在其中一個成員變數中。 `m_DataList`的 `CObList` 變數會儲存 `CPerson` 物件的集合。 `CMyData` 的縮寫宣告如下所示：

```cpp
class CMyData : public CObject
{
    // Constructor and other members ...
    protected:
        CObList* m_pDataList;
    // Other declarations ...
    public:
#ifdef _DEBUG
        // Override:
        virtual void AssertValid( ) const;
#endif
    // And so on ...
};
```

`CMyData` 中的 `AssertValid` 覆寫看起來像這樣：

```cpp
#ifdef _DEBUG
void CMyData::AssertValid( ) const
{
    // Call inherited AssertValid.
    CObject::AssertValid( );
    // Check validity of CMyData members.
    ASSERT_VALID( m_pDataList );
    // ...
}
#endif
```

`CMyData` 使用 `AssertValid` 機制來測試儲存在其資料成員中之物件的有效性。 覆寫 `AssertValid` 的 `CMyData` 會叫用其本身 m_pDataList 成員變數的 `ASSERT_VALID` 宏。

有效性測試不會在此層級停止，因為類別 `CObList` 也會覆寫 `AssertValid`。 此覆寫會對清單的內部狀態執行額外的有效性測試。 因此，`CMyData` 物件上的有效性測試會導致儲存之 `CObList` 清單物件內部狀態的其他有效性測試。

有一些更多工具，您也可以為儲存在清單中的 `CPerson` 物件加入有效性測試。 您可以從 `CObList` 衍生 `CPersonList` 的類別，並覆寫 `AssertValid`。 在覆寫中，您會呼叫 `CObject::AssertValid`，然後逐一查看清單，並在清單中所儲存的每個 `CPerson` 物件上呼叫 `AssertValid`。 本主題開頭所顯示的 `CPerson` 類別已經覆寫 `AssertValid`。

當您建立以進行偵錯工具時，這是一種強大的機制。 當您後續建立發行時，機制會自動關閉。

### <a name="BKMK_Limitations_of_AssertValid"></a>AssertValid 的限制
觸發的判斷提示表示物件一定是錯誤的，而且會停止執行。 不過，缺少判斷提示只會指出找不到任何問題，但不保證物件的良好。

[本主題內容](#BKMK_In_this_topic)

## <a name="BKMK_Using_assertions"></a>使用判斷提示

### <a name="BKMK_Catching_logic_errors"></a>捕捉邏輯錯誤
您可以根據程式的邏輯，在必須為 true 的條件上設定判斷提示。 除非發生邏輯錯誤，否則判斷提示不會有任何作用。

例如，假設您要在容器中模擬天然氣分子驅使分子，而變數 `numMols` 代表分子驅使分子的總數。 這個數位不能小於零，因此您可能會包含如下的 MFC 判斷提示語句：

```cpp
ASSERT(numMols >= 0);
```

或者，您也可以包含如下所示的 CRT 判斷提示：

```cpp
_ASSERT(numMols >= 0);
```

如果您的程式正常運作，這些語句就不會執行任何動作。 不過，如果邏輯錯誤導致 `numMols` 小於零，則判斷提示會停止執行程式，並顯示 [判斷提示[失敗] 對話方塊](../debugger/assertion-failed-dialog-box.md)。

[本主題內容](#BKMK_In_this_topic)

### <a name="BKMK_Checking_results_"></a>檢查結果
判斷提示對於測試作業的意義很重要，因為它的結果並不容易受到快速的視覺化檢查。

例如，請考慮下列程式碼，根據 `mols` 所指向的連結清單內容，將變數 `iMols`：

```cpp
/* This code assumes that type has overloaded the != operator
 with const char *
It also assumes that H2O is somewhere in that linked list.
Otherwise we'll get an access violation... */
while (mols->type != "H2O")
{
    iMols += mols->num;
    mols = mols->next;
}
ASSERT(iMols<=numMols); // MFC version
_ASSERT(iMols<=numMols); // CRT version
```

`iMols` 所計算的分子驅使分子數目，必須一律小於或等於分子驅使分子的總數，`numMols`。 迴圈的視覺化檢查並不會顯示這種情況，這會是這種情況，因此會在迴圈之後使用判斷提示語句來測試該條件。

[本主題內容](#BKMK_In_this_topic)

### <a name="BKMK_Testing_error_conditions_"></a>尋找未處理的錯誤
您可以使用判斷提示，在程式碼中的某個時間點測試應處理任何錯誤的錯誤狀況。 在下列範例中，圖形常式會傳回錯誤碼或零（表示成功）。

```cpp
myErr = myGraphRoutine(a, b);

/* Code to handle errors and
   reset myErr if successful */

ASSERT(!myErr); -- MFC version
_ASSERT(!myErr); -- CRT version
```

如果錯誤處理常式代碼正常運作，則應該處理錯誤，並在達到判斷提示之前 `myErr` 重設為零。 如果 `myErr` 具有另一個值，則判斷提示會失敗、程式終止，而且 [判斷提示[失敗] 對話方塊](../debugger/assertion-failed-dialog-box.md)隨即出現。

不過，判斷提示語句不會取代錯誤處理常式代碼。 下列範例顯示的判斷提示語句可能會導致最終發行程式碼中的問題：

```cpp
myErr = myGraphRoutine(a, b);

/* No Code to handle errors */

ASSERT(!myErr); // Don't do this!
_ASSERT(!myErr); // Don't do this, either!
```

此程式碼依賴判斷提示語句來處理錯誤狀況。 因此，`myGraphRoutine` 所傳回的任何錯誤碼都會在最終的發行程式碼中未處理。

[本主題內容](#BKMK_In_this_topic)

## <a name="see-also"></a>請參閱

- [偵錯工具安全性](../debugger/debugger-security.md)
- [偵錯機器碼](../debugger/debugging-native-code.md)
- [Managed 程式碼中的判斷提示](../debugger/assertions-in-managed-code.md)