---
title: 最佳做法和範例（SAL） |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
ms.assetid: 666276fb-99c2-4dc9-8bac-d74861c203ea
caps.latest.revision: 14
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: 5a03d2f64e3facba434de03bb18dbb2ac5bd809b
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/15/2020
ms.locfileid: "77275249"
---
# <a name="best-practices-and-examples-sal"></a>最佳作法和範例 (SAL)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

以下是取得原始程式碼注釋語言（SAL）最大的一些方式，並避免一些常見的問題。  
  
## <a name="_in_"></a>\_位置\_
 如果函式應該寫入專案，請使用 `_Inout_`，而不是 `_In_`。 這在從舊版宏自動轉換為 SAL 的情況下特別相關。 在 SAL 之前，許多程式設計人員會使用宏做為批註，也就是名稱為 `IN`、`OUT`、`IN_OUT`或變數的宏。 雖然我們建議您將這些宏轉換成 SAL，但我們也鼓勵您在轉換它們時小心，因為程式碼在撰寫原始原型之後可能已經變更，而舊的宏可能不再反映程式碼的作用。 請特別留意 `OPTIONAL` comment 宏，因為它經常放在不正確的位置，例如在逗號的錯誤端。  
  
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
  
## <a name="_opt_"></a>\_opt\_  
 如果不允許呼叫端傳入 null 指標，請使用 `_In_` 或 `_Out_`，而不是 `_In_opt_` 或 `_Out_opt_`。 這甚至適用于檢查其參數的函式，如果不應為 Null，則會傳回錯誤。 雖然讓函式檢查其參數以找出非預期的 Null，並且正常地傳回是一個良好的防禦式編碼做法，但並不表示參數注釋可以是選擇性類型（\_*Xxx*_opt\_）。  
  
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
  
## <a name="_pre_defensive_-and-_post_defensive_"></a>\_Pre_defensive\_ 和 \_Post_defensive\_  
 如果函式出現在信任界限中，建議您使用 `_Pre_defensive_` 註釋。  「防禦性」修飾詞會修改某些注釋，以指出在呼叫時，應該嚴格檢查介面，但在執行本文中，它應該會假設可能會傳遞不正確的參數。 在這種情況下，信任界限中會優先使用 `_In_ _Pre_defensive_`，指出雖然呼叫端嘗試傳遞 NULL 時會發生錯誤，但是仍會分析函式主體，就如同參數可能為 NULL 一樣，而且未先檢查指標是否為 NULL 就嘗試取值，便會加上旗標。  `_Post_defensive_` 註釋也可以用於回呼，其中信任的一方會假設為呼叫端，而不受信任的程式碼為被呼叫的程式碼。  
  
## <a name="_out_writes_"></a>\_Out_writes\_  
 下列範例示範 `_Out_writes_`的常見誤用。  
  
```cpp  
  
// Incorrect  
void Func1(_Out_writes_(size) CHAR *pb,   
    DWORD size  
);  
  
```  
  
 批註 `_Out_writes_` 表示您有一個緩衝區。 它已配置 `cb` 個位元組，並在結束時初始化第一個位元組。 此注釋不是嚴格的錯誤，因此表示配置的大小會很有説明。 不過，它不會告訴函式初始化多少元素。  
  
 下一個範例顯示三個正確的方法，以完整指定緩衝區初始化部分的確切大小。  
  
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
  
## <a name="_out_-pstr"></a>\_\_ PSTR  
 `_Out_ PSTR` 的使用幾乎都是錯誤的。 這會被視為具有指向字元緩衝區的輸出參數，而且它是以 Null 結束。  
  
```cpp  
  
// Incorrect  
void Func1(_Out_ PSTR pFileName, size_t n);  
  
// Correct  
void Func2(_Out_writes_(n) PSTR wszFileName, size_t n);  
  
```  
  
 `_In_ PCSTR` 之類的注釋很常見而且很有用。 它會指向具有 Null 終止的輸入字串，因為 `_In_` 的前置條件允許辨識以 Null 結束的字串。  
  
## <a name="_in_-wchar-p"></a>\_ WCHAR * p 中的 \_  
 `_In_ WCHAR* p` 指出有一個指向一個字元的輸入指標 `p`。 不過，在大部分的情況下，這可能不是預期的規格。 相反地，可能的目標是以 Null 結束之陣列的規格。若要這麼做，請使用 `_In_ PWSTR`。  
  
```cpp  
  
// Incorrect  
void Func1(_In_ WCHAR* wszFileName);  
  
// Correct  
void Func2(_In_ PWSTR wszFileName);  
  
```  
  
 缺少正確的 Null 終止規格是常見的。 使用適當的 `STR` 版本來取代類型，如下列範例所示。  
  
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
  
## <a name="_out_range_"></a>\_Out_range\_  
 如果參數是指標，而您想要表示指標所指向之元素值的範圍，請使用 `_Deref_out_range_`，而不是 `_Out_range_`。 在下列範例中，會表示 * pcbFilled 的範圍，而不是 pcbFilled。  
  
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
  
 某些工具不一定需要 `_Deref_out_range_(0, cbSize)`，因為它可以從 `_Out_writes_to_(cbSize,*pcbFilled)`推斷出來，但在此會顯示為完整性。  
  
## <a name="wrong-context-in-_when_"></a>\_ 時 \_中的內容錯誤  
 另一個常見的錯誤是針對前置條件使用後置狀態評估。 在下列範例中，`_Requires_lock_held_` 是前置條件。  
  
```cpp  
  
// Incorrect  
_When_(return == 0, _Requires_lock_held_(p->cs))  
int Func1(_In_ MyData *p, int flag);  
  
// Correct  
_When_(flag == 0, _Requires_lock_held_(p->cs))  
int Func2(_In_ MyData *p, int flag);  
  
```  
  
 運算式 `result` 指的是前置狀態值，在預先狀態中無法使用。  
  
## <a name="true-in-_success_"></a>\_成功\_ 中為 TRUE  
 如果傳回值不是零，函數會成功，請使用 `return != 0` 做為成功條件，而不是 `return == TRUE`。 非零不一定表示編譯器為 `TRUE`所提供的實際值是否相等。 `_Success_` 的參數是運算式，而且下列運算式會評估為相等：`return != 0`、`return != false`、`return != FALSE` 和 `return`，且不含參數或比較。  
  
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
 若為參考變數，舊版 SAL 使用隱含指標做為注釋目標，並要求加入附加至參考變數的批註 `__deref`。 這個版本會使用物件本身，而且不需要額外的 `_Deref_`。  
  
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
  
## <a name="annotations-on-return-values"></a>傳回值的注釋  
 下列範例顯示傳回值注釋的常見問題。  
  
```cpp  
  
// Incorrect  
_Out_opt_ void *MightReturnNullPtr1();  
  
// Correct  
_Ret_maybenull_ void *MightReturnNullPtr2();  
  
```  
  
 在此範例中，`_Out_opt_` 指出，指標在前置條件中可能是 Null。 不過，前置條件無法套用至傳回值。 在此情況下，會 `_Ret_maybenull_`正確的注釋。  
  
## <a name="see-also"></a>另請參閱  
 [使用 SAL 注釋減少 C/C++程式碼](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)缺失   
 [瞭解 SAL](../code-quality/understanding-sal.md)   
 [標注函式參數和傳回值](../code-quality/annotating-function-parameters-and-return-values.md)   
 [批註](../code-quality/annotating-function-behavior.md)函式行為   
 [標注結構和類別](../code-quality/annotating-structs-and-classes.md)   
 [標注鎖定行為](../code-quality/annotating-locking-behavior.md)   
 [指定批註套用的時機和位置](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [內建函式](../code-quality/intrinsic-functions.md)
