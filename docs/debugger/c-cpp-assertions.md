---
title: C/c + + 判斷提示 |Microsoft Docs
description: 瞭解 C/c + + 判斷提示如何在 Visual Studio 的調試中運作。 判斷提示會指定您在程式中的某個點預期會是 true 的條件。
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- cplusplus
ms.openlocfilehash: bc58d125f82a33f982578f9a186d579d280e89e8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99865952"
---
# <a name="cc-assertions"></a>C/C++ 判斷提示
判斷提示語句會指定您在程式中的某個點預期會是 true 的條件。 如果該條件不是 true，判斷提示失敗，程式的執行會中斷，而且出現 [判斷提示 [失敗] 對話方塊](../debugger/assertion-failed-dialog-box.md) 。

Visual Studio 支援以下列結構為基礎的 c + + 判斷提示語句：

- MFC 程式的 MFC 判斷提示。

- 使用 ATL 之程式的[ATLASSERT](/cpp/atl/reference/debugging-and-error-reporting-macros#atlassert) 。

- 使用 C 執行時間程式庫之程式的 CRT 判斷提示。

- 適用于其他 C/c + + 程式的 ANSI [assert 函數](/cpp/c-runtime-library/reference/assert-macro-assert-wassert) 。

  您可以使用判斷提示來攔截邏輯錯誤、檢查作業的結果，以及測試應該已處理的錯誤狀況。

## <a name="in-this-topic"></a><a name="BKMK_In_this_topic"></a> 本主題中
[判斷提示的運作方式](#BKMK_How_assertions_work)

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

## <a name="how-assertions-work"></a><a name="BKMK_How_assertions_work"></a> 判斷提示的運作方式
當偵錯工具因為 MFC 或 C 執行時間程式庫判斷提示而停止時，如果來源可供使用，則偵錯工具會流覽至原始程式檔中發生判斷提示的位置。 判斷提示訊息會出現在 [ [輸出] 視窗](../ide/reference/output-window.md) 和 [判斷提示 **失敗** ] 對話方塊中。 如果您想要儲存判斷提示訊息以供日後參考，可以將它從 [ **輸出** ] 視窗複製到文字視窗。 **輸出** 視窗也可能包含其他錯誤訊息。 請仔細檢查這些訊息，因為它們會提供判斷提示失敗原因的線索。

使用判斷提示來偵測開發期間的錯誤。 作為規則，請針對每個假設使用一個判斷提示。 例如，如果您假設引數不是 Null，請使用判斷提示來測試該假設。

[本主題內容](#BKMK_In_this_topic)

## <a name="assertions-in-debug-and-release-builds"></a><a name="BKMK_Assertions_in_Debug_and_Release_builds"></a> Debug 和 Release 組建中的判斷提示
只有在 `_DEBUG` 已定義時，才會編譯判斷提示語句。 否則，編譯器會將判斷提示視為 null 語句。 因此，判斷提示語句在您的最終發行計畫中不會有額外負荷或效能成本，並可讓您避免使用指示詞 `#ifdef` 。

## <a name="side-effects-of-using-assertions"></a><a name="BKMK_Side_effects_of_using_assertions"></a> 使用判斷提示的副作用
當您將判斷提示加入至程式碼時，請確定判斷提示沒有副作用。 例如，請考慮下列修改值的判斷提示 `nM` ：

```cpp
ASSERT(nM++ > 0); // Don't do this!
```

因為 `ASSERT` 不會在程式的發行版本中評估運算式，所以 `nM` Debug 和發行版本中將會有不同的值。 若要避免在 MFC 中發生這個問題，您可以使用 [驗證](/cpp/mfc/reference/diagnostic-services#verify) 宏，而不是 `ASSERT` 。 `VERIFY` 會評估所有版本中的運算式，但不會檢查發行版本中的結果。

在判斷提示語句中使用函式呼叫時，請特別小心，因為評估函式可能會產生非預期的副作用。

```cpp
ASSERT ( myFnctn(0)==1 ) // unsafe if myFnctn has side effects
VERIFY ( myFnctn(0)==1 ) // safe
```

`VERIFY``myFnctn`在偵錯工具和發行版本中呼叫，因此可接受使用。 不過，使用會在 `VERIFY` 發行版本中強加不必要函式呼叫的額外負荷。

[本主題內容](#BKMK_In_this_topic)

## <a name="crt-assertions"></a><a name="BKMK_CRT_assertions"></a> CRT 判斷提示
CRTDBG.H 裡。H 標頭檔會定義判斷提示檢查的 [_ASSERT 和 _ASSERTE 宏](/cpp/c-runtime-library/reference/assert-asserte-assert-expr-macros) 。

| 巨集 | 結果 |
|------------| - |
| `_ASSERT` | 如果指定的運算式評估為 FALSE，則為的檔案名和行號 `_ASSERT` 。 |
| `_ASSERTE` | 與相同 `_ASSERT` ，加上判斷提示之運算式的字串表示。 |

`_ASSERTE` 的功能更強大，因為它會報告判斷提示的運算式是否為 FALSE。 這可能足以找出問題，而不需要參考原始程式碼。 不過，您的應用程式的 Debug 版本將會包含每個使用判斷提示之運算式的字串常數 `_ASSERTE` 。 如果您使用許多 `_ASSERTE` 宏，這些字串運算式會佔用大量的記憶體。 如果該證明是問題，請使用 `_ASSERT` 來節省記憶體。

當 `_DEBUG` 定義時， `_ASSERTE` 巨集定義如下：

```cpp
#define _ASSERTE(expr) \
    do { \
        if (!(expr) && (1 == _CrtDbgReport( \
            _CRT_ASSERT, __FILE__, __LINE__, #expr))) \
            _CrtDbgBreak(); \
    } while (0)
```

如果判斷提示的運算式評估為 FALSE，則會根據) 預設使用訊息對話方塊來呼叫 [_CrtDbgReport](/cpp/c-runtime-library/reference/crtdbgreport-crtdbgreportw) ，以報告判斷提示失敗 (。 如果您在 [訊息] 對話方塊中選擇 [ **重試** ]，則會傳回 `_CrtDbgReport` 1，並 `_CrtDbgBreak` 透過呼叫偵錯工具 `DebugBreak` 。

### <a name="checking-for-heap-corruption"></a>檢查堆積損毀
下列範例會使用 [_CrtCheckMemory](/cpp/c-runtime-library/reference/crtcheckmemory) 來檢查堆積是否損毀：

```cpp
_ASSERTE(_CrtCheckMemory());
```

### <a name="checking-pointer-validity"></a>檢查指標有效性
下列範例會使用 [_CrtIsValidPointer](/cpp/c-runtime-library/reference/crtisvalidpointer) 來確認指定的記憶體範圍是否適用于讀取或寫入。

```cpp
_ASSERTE(_CrtIsValidPointer( address, size, TRUE );
```

下列範例會使用 [_CrtIsValidHeapPointer](/cpp/c-runtime-library/reference/crtisvalidheappointer) 來確認指標指向本機堆積中的記憶體 (此 C 執行時間程式庫實例所建立和管理的堆積，DLL 可以有自己的程式庫實例，也就是它自己的堆積，而不是在應用程式堆積) 的範圍內。 此判斷提示不僅會攔截 null 或超出範圍的位址，也會捕捉靜態變數、堆疊變數和任何其他非記憶體的指標。

```cpp
_ASSERTE(_CrtIsValidPointer( myData );
```

### <a name="checking-a-memory-block"></a>檢查記憶體區塊
下列範例會使用 [_CrtIsMemoryBlock](/cpp/c-runtime-library/reference/crtismemoryblock) 來確認記憶體區塊位於本機堆積，且具有有效的區塊類型。

```cpp
_ASSERTE(_CrtIsMemoryBlock (myData, size, &requestNumber, &filename, &linenumber));
```

[本主題內容](#BKMK_In_this_topic)

## <a name="mfc-assertions"></a><a name="BKMK_MFC_assertions"></a> MFC 判斷提示
MFC 會為判斷提示檢查定義 [ASSERT](/previous-versions/ew16s3zc(v=vs.140)) 宏。 它也會定義 `MFC ASSERT_VALID` `CObject::AssertValid` 用來檢查衍生物件之內部狀態的和方法 `CObject` 。

如果 MFC 宏的引數 `ASSERT` 評估為零或 false，宏會中止程式執行，並對使用者發出警示，否則會繼續執行。

當判斷提示失敗時，[訊息] 對話方塊會顯示原始程式檔的名稱和判斷提示的行號。 如果您在對話方塊中選擇 [重試]，呼叫 [AfxDebugBreak](/cpp/mfc/reference/diagnostic-services#afxdebugbreak) 會導致執行中斷偵錯工具。 屆時，您可以檢查呼叫堆疊，並使用其他偵錯工具工具來判斷判斷提示失敗的原因。 如果您已啟用 [即時調試](../debugger/just-in-time-debugging-in-visual-studio.md)程式，而偵錯工具尚未執行，則對話方塊可以啟動偵錯工具。

下列範例顯示如何使用 `ASSERT` 來檢查函式的傳回值：

```cpp
int x = SomeFunc(y);
ASSERT(x >= 0);   //  Assertion fails if x is negative
```

您可以使用 ASSERT 搭配 [IsKindOf](/cpp/mfc/reference/cobject-class#iskindof) 函式來提供函數引數的類型檢查：

```cpp
ASSERT( pObject1->IsKindOf( RUNTIME_CLASS( CPerson ) ) );
```

`ASSERT`宏不會在發行版本中產生任何程式碼。 如果您需要評估發行版本中的運算式，請使用 [VERIFY](/cpp/mfc/reference/diagnostic-services#verify) 宏，而不是 ASSERT。

### <a name="mfc-assert_valid-and-cobjectassertvalid"></a><a name="BKMK_MFC_ASSERT_VALID_and_CObject__AssertValid"></a> MFC ASSERT_VALID 和 CObject：： AssertValid
[CObject：： AssertValid](/cpp/mfc/reference/cobject-class#assertvalid)方法提供物件內部狀態的執行時間檢查。 雖然您不需要在 `AssertValid` 衍生類別的情況下覆寫 `CObject` ，但您可以藉由執行此操作來提高類別的可靠性。 `AssertValid` 應該在所有物件的成員變數上執行判斷提示，以確認它們是否包含有效的值。 例如，它應該會檢查指標成員變數是否不是 Null。

下列範例顯示如何宣告函式 `AssertValid` ：

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

當您覆寫時 `AssertValid` ，請先呼叫的基類版本， `AssertValid` 再執行您自己的檢查。 然後使用 ASSERT 宏來檢查衍生類別的唯一成員，如下所示：

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

如果任何成員變數儲存物件，您可以使用 `ASSERT_VALID` 宏來測試其內部有效性 (如果其類別覆寫 `AssertValid`) 。

例如，假設有一個類別 `CMyData` ，它會在其中一個成員變數中儲存 [CObList](/cpp/mfc/reference/coblist-class) 。 `CObList`變數會 `m_DataList` 儲存物件的集合 `CPerson` 。 的縮寫宣告如下所 `CMyData` 示：

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

中的覆 `AssertValid` 寫 `CMyData` 看起來像這樣：

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

`CMyData` 使用 `AssertValid` 機制來測試儲存在其資料成員中之物件的有效性。 的覆寫會 `AssertValid` `CMyData` `ASSERT_VALID` 為它自己的 m_pDataList 成員變數叫用宏。

有效性測試不會在此層級停止，因為類別 `CObList` 也會覆寫 `AssertValid` 。 此覆寫會在清單的內部狀態執行額外的有效性測試。 因此，物件的有效性測試會 `CMyData` 針對儲存的清單物件的內部狀態，產生額外的有效性測試 `CObList` 。

有一些更多工作，您也可以針對 `CPerson` 儲存在清單中的物件，加入有效性測試。 您可以從衍生類別 `CPersonList` `CObList` ，並覆寫 `AssertValid` 。 在覆寫中，您會呼叫， `CObject::AssertValid` 然後逐一查看清單，然後 `AssertValid` 在 `CPerson` 清單中儲存的每個物件上呼叫。 `CPerson`本主題開頭所顯示的類別已覆寫 `AssertValid` 。

這是建立以進行偵錯工具時的強大機制。 當您後續組建發行時，機制會自動關閉。

### <a name="limitations-of-assertvalid"></a><a name="BKMK_Limitations_of_AssertValid"></a> AssertValid 的限制
觸發的判斷提示指出物件絕對不正確，而且會停止執行。 但是，缺乏判斷提示只會指出找不到任何問題，但不保證物件是正確的。

[本主題內容](#BKMK_In_this_topic)

## <a name="using-assertions"></a><a name="BKMK_Using_assertions"></a> 使用判斷提示

### <a name="catching-logic-errors"></a><a name="BKMK_Catching_logic_errors"></a> 捕捉邏輯錯誤
您可以根據程式的邏輯，在必須是 true 的條件上設定判斷提示。 除非發生邏輯錯誤，否則判斷提示沒有任何作用。

例如，假設您正在模擬容器中的天然氣分子，而變數 `numMols` 代表分子的總數目。 此數位不能小於零，因此您可能會包含 MFC 判斷提示語句，如下所示：

```cpp
ASSERT(numMols >= 0);
```

或者，您可以包含如下的 CRT 判斷提示：

```cpp
_ASSERT(numMols >= 0);
```

如果您的程式運作正常，這些語句不會執行任何動作。 但是，如果邏輯錯誤導致 `numMols` 小於零，則判斷提示會停止執行程式，並顯示 [判斷提示 [失敗] 對話方塊](../debugger/assertion-failed-dialog-box.md)。

[本主題內容](#BKMK_In_this_topic)

### <a name="checking-results"></a><a name="BKMK_Checking_results_"></a> 檢查結果
判斷提示對於測試作業而言很重要，因為這些作業的結果不是快速視覺化檢查的明顯。

例如，請考慮下列程式碼，此程式碼會 `iMols` 根據所指向的連結清單內容來更新變數 `mols` ：

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

所計算的分子數目 `iMols` 必須一律小於或等於分子的總數 `numMols` 。 迴圈的視覺化檢查不會顯示這會是這種情況，因此會在迴圈之後使用判斷提示語句來測試該條件。

[本主題內容](#BKMK_In_this_topic)

### <a name="finding-unhandled-errors"></a><a name="BKMK_Testing_error_conditions_"></a> 尋找未處理的錯誤
您可以使用判斷提示，在程式碼中的某個點測試是否有任何錯誤應該處理的錯誤狀況。 在下列範例中，圖形常式會傳回錯誤碼或零表示成功。

```cpp
myErr = myGraphRoutine(a, b);

/* Code to handle errors and
   reset myErr if successful */

ASSERT(!myErr); -- MFC version
_ASSERT(!myErr); -- CRT version
```

如果錯誤處理常式代碼正常運作，則應該在達到判斷提示之前，處理錯誤並將其 `myErr` 重設為零。 如果 `myErr` 有另一個值，判斷提示就會失敗，程式會停止，而且出現 [判斷提示 [失敗] 對話方塊](../debugger/assertion-failed-dialog-box.md) 。

但是，判斷提示語句並非替代錯誤處理常式代碼。 下列範例顯示的判斷提示語句可能會導致最終發行程式碼中的問題：

```cpp
myErr = myGraphRoutine(a, b);

/* No Code to handle errors */

ASSERT(!myErr); // Don't do this!
_ASSERT(!myErr); // Don't do this, either!
```

此程式碼會依賴判斷提示語句來處理錯誤狀況。 如此一來， `myGraphRoutine` 在最終發行程式碼中將無法處理傳回的任何錯誤碼。

[本主題內容](#BKMK_In_this_topic)

## <a name="see-also"></a>另請參閱

- [偵錯工具安全性](../debugger/debugger-security.md)
- [偵錯機器碼](../debugger/debugging-native-code.md)
- [Managed 程式碼中的判斷提示](../debugger/assertions-in-managed-code.md)