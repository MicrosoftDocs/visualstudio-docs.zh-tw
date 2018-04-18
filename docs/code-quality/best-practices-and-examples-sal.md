---
title: 最佳作法和範例 (SAL) |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
author: mikeblome
ms.author: mblome
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d8910c9b5d36cecec82bf0e386e294759113c76e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="best-practices-and-examples-sal"></a>最佳作法和範例 (SAL)
以下是一些取得大部分超出來源的程式碼的註釋語言 (SAL)，並避免一些常見的問題。

## <a name="in"></a>\_In\_

如果函式應該寫入項目，使用`_Inout_`而不是`_In_`。 這是在從較舊的巨集的自動化轉換到 SAL 的情況下特別有關係。 在 SAL 之前, 許多程式設計人員會使用巨集做為註解 — 已命名的巨集`IN`， `OUT`， `IN_OUT`，或這些名稱的變異數。 雖然我們建議您將這些巨集轉換成 SAL，我們也鼓勵您應特別小心，當您將它們轉換因為程式碼可能已經變更寫入原始的原型，而且舊的巨集可能不再反映程式碼的功能。 要特別小心有關`OPTIONAL`註解巨集，因為它經常置放錯誤 — 例如，在錯誤的側邊的逗號。

```cpp

// Incorrect
void Func1(_In_ int *p1)
{
    if (p1 == NULL)
        return;

    *p1 = 1;
}

// Correct
void Func2(_Inout_ PCHAR p1)
{
    if (p1 == NULL)
        return;

    *p1 = 1;
}
```

## <a name="opt"></a>\_opt\_

不允許呼叫端傳遞 null 指標，如果使用`_In_`或`_Out_`而不是`_In_opt_`或`_Out_opt_`。 即使適用於函式會檢查它的參數，如果它是 NULL 時不應該傳回錯誤。 雖然有非預期的 NULL 檢查它的參數，依正常程序傳回的函式是很好的防衛性程式碼撰寫作法，但它並不表示的參數註釋可以是選擇性的型別 (`_*Xxx*_opt_`)。

```cpp

// Incorrect
void Func1(_Out_opt_ int *p1)
{
    *p = 1;
}

// Correct
void Func2(_Out_ int *p1)
{
    *p = 1;
}

```

## <a name="predefensive-and-postdefensive"></a>\_Pre\_防禦\_和\_Post\_防禦\_

如果函式出現在信任界限中，建議您使用 `_Pre_defensive_` 註釋。  "防禦"修飾詞修改特定的附註，表示呼叫的位置，介面應該嚴格來說，檢查，但實作本文它應該假設可能會收到不正確的參數。 在這種情況下，信任界限中會優先使用 `_In_ _Pre_defensive_`，指出雖然呼叫端嘗試傳遞 NULL 時會發生錯誤，但是仍會分析函式主體，就如同參數可能為 NULL 一樣，而且未先檢查指標是否為 NULL 就嘗試取值，便會加上旗標。  `_Post_defensive_` 註釋也可以用於回呼，其中信任的一方會假設為呼叫端，而不受信任的程式碼為被呼叫的程式碼。

## <a name="outwrites"></a>\_Out\_寫入\_

下列範例將示範一般誤用`_Out_writes_`。

```cpp

// Incorrect
void Func1(_Out_writes_(size) CHAR *pb,
    DWORD size
);

```

註解`_Out_writes_`表示您有一個緩衝區。 它有`cb`初始化結束時的第一個位元組以所配置的位元組。 此註解嚴格錯誤並不會有幫助 express 配置的大小。 不過，它不會告訴函式會初始化的項目數目。

下一個範例顯示正確的三種方式完整指定緩衝區初始化一部分的確切的大小。

```cpp

// Correct
void Func1(_Out_writes_to_(size, *pCount) CHAR *pb,
    DWORD size,
    PDWORD pCount
);

void Func2(_Out_writes_all_(size) CHAR *pb,
    DWORD size
);

void Func3(_Out_writes_(size) PSTR pb,
    DWORD size
);

```

## <a name="out-pstr"></a>\_Out\_ PSTR

使用`_Out_ PSTR`幾乎都是錯誤。 這會解譯為擁有輸出參數指向的字元緩衝區，它是以 NULL 結束。

```cpp

// Incorrect
void Func1(_Out_ PSTR pFileName, size_t n);

// Correct
void Func2(_Out_writes_(n) PSTR wszFileName, size_t n);

```

註解喜歡`_In_ PCSTR`是常用與實用。 它所指向的 NULL 終止，因為輸入字串的前置條件`_In_`可辨識的以 NULL 結束的字串。

## <a name="in-wchar-p"></a>\_在\_WCHAR * p

`_In_ WCHAR* p` 指出輸入的指標`p`，它會指向一個字元。 不過，在大部分情況下，這是可能不是規格。 相反地，可能想要的結果是以 NULL 結束陣列; 的規格若要這樣做，請使用`_In_ PWSTR`。

```cpp

// Incorrect
void Func1(_In_ WCHAR* wszFileName);

// Correct
void Func2(_In_ PWSTR wszFileName);

```

遺漏 NULL 終止的適當的規格是很常見。 使用適當`STR`版本來取代類型，如下列範例所示。

```cpp

// Incorrect
BOOL StrEquals1(_In_ PCHAR p1, _In_ PCHAR p2)
{
    return strcmp(p1, p2) == 0;
}

// Correct
BOOL StrEquals2(_In_ PSTR p1, _In_ PSTR p2)
{
    return strcmp(p1, p2) == 0;
}

```

## <a name="outrange"></a>\_Out_range\_

如果參數是指標，且您想要表示指向指標所使用的項目值的範圍`_Deref_out_range_`而不是`_Out_range_`。 在下列範例中，範圍 * pcbFilled 會表示，不 pcbFilled。

```cpp

// Incorrect
void Func1(
    _Out_writes_bytes_to_(cbSize, *pcbFilled) BYTE *pb,
    DWORD cbSize,
    _Out_range_(0, cbSize) DWORD *pcbFilled
);

// Correct
void Func2(
    _Out_writes_bytes_to_(cbSize, *pcbFilled) BYTE *pb,
    DWORD cbSize,
    _Deref_out_range_(0, cbSize) _Out_ DWORD *pcbFilled
);

```

 `_Deref_out_range_(0, cbSize)` 不是絕對必要的某些工具可以從推斷出`_Out_writes_to_(cbSize,*pcbFilled)`，但它如下所示的完整性。

## <a name="wrong-context-in-when"></a>錯誤的內容中\_時\_

另一個常見的錯誤是後置狀態評估用於前置條件。 在下列範例中，`_Requires_lock_held_`的前置條件。

```cpp

// Incorrect
_When_(return == 0, _Requires_lock_held_(p->cs))
int Func1(_In_ MyData *p, int flag);

// Correct
_When_(flag == 0, _Requires_lock_held_(p->cs))
int Func2(_In_ MyData *p, int flag);

```

 運算式`result`參考後置狀態的值不在前的狀態。

## <a name="true-in-success"></a>在中，則為 TRUE\_成功\_

如果函式成功則為非零的傳回值時，使用`return != 0`成功狀況，而不是為`return == TRUE`。 非零不一定表示編譯器所提供的實際值的等價`TRUE`。 `_Success_` 的參數是運算式，而且下列運算式會評估為相等：`return != 0`、`return != false`、`return != FALSE` 和 `return`，且不含參數或比較。

```cpp

// Incorrect
_Success_(return == TRUE, _Acquires_lock_(*lpCriticalSection))
BOOL WINAPI TryEnterCriticalSection(
  _Inout_ LPCRITICAL_SECTION lpCriticalSection
);

// Correct
_Success_(return != 0, _Acquires_lock_(*lpCriticalSection))
BOOL WINAPI TryEnterCriticalSection(
  _Inout_ LPCRITICAL_SECTION lpCriticalSection
);

```

## <a name="reference-variable"></a>參考變數

參考變數，舊版的 SAL 隱含的指標做為註解目標和所需的加法`__deref`附加到參考變數的註解。 這個版本會使用物件本身，而且不需要額外`_Deref_`。

```cpp

// Incorrect
void Func1(
    _Out_writes_bytes_all_(cbSize) BYTE *pb,
    _Deref_ _Out_range_(0, 2) _Out_ DWORD &cbSize
);

// Correct
void Func2(
    _Out_writes_bytes_all_(cbSize) BYTE *pb,
    _Out_range_(0, 2) _Out_ DWORD &cbSize
);

```

## <a name="annotations-on-return-values"></a>傳回值上的註解

下列範例會顯示傳回值的註釋中常見的問題。

```cpp

// Incorrect
_Out_opt_ void *MightReturnNullPtr1();

// Correct
_Ret_maybenull_ void *MightReturnNullPtr2();

```

在此範例中，`_Out_opt_`指出指標可能是 NULL，做為前置條件的一部分。 不過，前置條件不適用於傳回的值。 在此情況下，正確的註解是`_Ret_maybenull_`。

## <a name="see-also"></a>另請參閱

[使用 SAL 註釋減少 C/c + + 程式碼缺失](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)
[了解 SAL](../code-quality/understanding-sal.md)
[註釋函式參數和傳回值](../code-quality/annotating-function-parameters-and-return-values.md)
[註釋函式行為](../code-quality/annotating-function-behavior.md)
[註釋結構和類別](../code-quality/annotating-structs-and-classes.md)
[註釋鎖定行為](../code-quality/annotating-locking-behavior.md)
[指定套用註釋的時機和位置](../code-quality/specifying-when-and-where-an-annotation-applies.md)
[內建函式](../code-quality/intrinsic-functions.md)