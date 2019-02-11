---
title: 最佳作法和範例 (SAL)
ms.date: 11/04/2016
ms.topic: conceptual
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 28d17301d81ee5b206feb0c3afefba35e50615cd
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2019
ms.locfileid: "55940577"
---
# <a name="best-practices-and-examples-sal"></a>最佳作法和範例 (SAL)
以下是從來源的程式碼註釋語言 (SAL) 的最大，並避免的一些常見問題的一些方法。

## <a name="in"></a>\_In\_

如果函式應該寫入項目，使用`_Inout_`而不是`_In_`。 這是在較舊的巨集來 SAL 的自動化轉換的情況下特別相關。 在 SAL 之前, 許多程式設計人員，請使用做為註解的巨集 — 命名的巨集`IN`， `OUT`， `IN_OUT`，或這些名稱的變異數。 雖然我們建議您將這些巨集轉換成 SAL，我們也強烈建議您在您將它們轉換因為程式碼可能已經變更寫入原始的原型，而且舊的巨集可能不再反映程式碼的作用時要特別小心。 要特別小心有關`OPTIONAL`註解巨集，因為它經常會不正確地放置 — 例如，在錯誤的側邊的逗號。

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

如果呼叫端不可以傳入 null 指標，請使用`_In_`或是`_Out_`而不是`_In_opt_`或`_Out_opt_`。 即使適用於函式會檢查其參數，如果它是 NULL，不應該將它時，會傳回錯誤。 雖然有非預期的 NULL 檢查其參數，並依正常程序傳回的函式是很好的防禦性程式碼撰寫練習，它並不表示的參數註釋可以是選擇性的型別 (`_*Xxx*_opt_`)。

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

## <a name="predefensive-and-postdefensive"></a>\_Pre\_防禦\_並\_Post\_防禦\_

如果函式出現在信任界限中，建議您使用 `_Pre_defensive_` 註釋。  "防禦性 」 的修飾詞修改特定的附註，表示在呼叫，介面應該嚴格來說，檢查，但實作本文它應該採用的可能會收到不正確的參數。 在這種情況下，信任界限中會優先使用 `_In_ _Pre_defensive_`，指出雖然呼叫端嘗試傳遞 NULL 時會發生錯誤，但是仍會分析函式主體，就如同參數可能為 NULL 一樣，而且未先檢查指標是否為 NULL 就嘗試取值，便會加上旗標。  `_Post_defensive_` 註釋也可以用於回呼，其中信任的一方會假設為呼叫端，而不受信任的程式碼為被呼叫的程式碼。

## <a name="outwrites"></a>\_Out\_寫入\_

下列範例會示範常見的誤用的`_Out_writes_`。

```cpp

// Incorrect
void Func1(_Out_writes_(size) CHAR *pb,
    DWORD size
);
```

註釋`_Out_writes_`表示您有一個緩衝區。 它有`cb`以初始化結束時的第一個位元組所配置的位元組。 此註釋不完全是錯誤，而且很有用來表示配置的大小。 不過，它不會告訴多少項目都初始化函式。

下一個範例示範三個正確的方式，完整指定確切的大小的緩衝區初始化的一部分。

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

使用`_Out_ PSTR`幾乎都是錯誤。 這會解譯成具有指向字元緩衝區的輸出參數，它是以 NULL 結束。

```cpp

// Incorrect
void Func1(_Out_ PSTR pFileName, size_t n);

// Correct
void Func2(_Out_writes_(n) PSTR wszFileName, size_t n);
```

註解喜歡`_In_ PCSTR`很常見而且很有用。 它會指向具有 NULL 終止，因為輸入字串的前置條件`_In_`可辨識的以 NULL 結束的字串。

## <a name="in-wchar-p"></a>\_在 \_ WCHAR * p

`_In_ WCHAR* p` 表示是輸入的指標`p`，它會指向一個字元。 不過，在大部分情況下，這是可能不適合的規格。 相反地，可能的目的為何是 NULL 結束陣列; 的規格若要這樣做，請使用`_In_ PWSTR`。

```cpp

// Incorrect
void Func1(_In_ WCHAR* wszFileName);

// Correct
void Func2(_In_ PWSTR wszFileName);
```

缺少適當的規格，NULL 終止的是很常見。 使用適當`STR`版本來取代類型，如下列範例所示。

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

## <a name="outrange"></a>\_Out\_範圍\_

如果參數是指標，且您想要表達的指標，使用所指向的項目值的範圍`_Deref_out_range_`而不是`_Out_range_`。 在下列範例中，各種 * 表示 pcbFilled，不 pcbFilled。

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

 `_Deref_out_range_(0, cbSize)` 不是絕對必要的一些工具，因為它可以從推斷`_Out_writes_to_(cbSize,*pcbFilled)`，但如下所示的完整性。

## <a name="wrong-context-in-when"></a>錯誤的內容中\_時\_

要用於前置條件中的後置狀態評估是另一個常見的錯誤。 在下列範例中，`_Requires_lock_held_`是前置條件。

```cpp

// Incorrect
_When_(return == 0, _Requires_lock_held_(p->cs))
int Func1(_In_ MyData *p, int flag);

// Correct
_When_(flag == 0, _Requires_lock_held_(p->cs))
int Func2(_In_ MyData *p, int flag);
```

 運算式`result`參考後置狀態的值不在前的狀態中。

## <a name="true-in-success"></a>在中，則為 TRUE\_成功\_

如果函式成功時傳回的值為非零值，使用`return != 0`成功情況，而不是為`return == TRUE`。 Nonzero 不一定表示編譯器為所提供的實際值的等價`TRUE`。 `_Success_` 的參數是運算式，而且下列運算式會評估為相等：`return != 0`、`return != false`、`return != FALSE` 和 `return`，且不含參數或比較。

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

參考變數，舊版的 SAL 隱含的指標做為註釋目標以及所需的`__deref`附加至參考變數的註解。 這個版本會使用物件本身，而且不需要額外`_Deref_`。

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

## <a name="annotations-on-return-values"></a>對傳回值的註解

下列範例會顯示傳回值註釋中常見的問題。

```cpp

// Incorrect
_Out_opt_ void *MightReturnNullPtr1();

// Correct
_Ret_maybenull_ void *MightReturnNullPtr2();
```

在此範例中，`_Out_opt_`指出指標可能是 NULL，做為前置條件的一部分。 不過，前置條件無法套用至傳回值。 在此案例中，是正確的註解`_Ret_maybenull_`。

## <a name="see-also"></a>另請參閱

[使用 SAL 註釋減少 C/c + + 程式碼缺失](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)
[了解 SAL](../code-quality/understanding-sal.md)
[註釋函式參數和傳回值](../code-quality/annotating-function-parameters-and-return-values.md)
[註釋函式行為](../code-quality/annotating-function-behavior.md)
[註釋結構和類別](../code-quality/annotating-structs-and-classes.md)
[註釋鎖定行為](../code-quality/annotating-locking-behavior.md)
[指定套用註釋的時機和位置](../code-quality/specifying-when-and-where-an-annotation-applies.md)
[內建函式](../code-quality/intrinsic-functions.md)