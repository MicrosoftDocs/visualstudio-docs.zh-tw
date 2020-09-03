---
title: " (SAL) 的最佳作法和範例 |Microsoft Docs"
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "77275249"
---
# <a name="best-practices-and-examples-sal"></a>最佳作法和範例 (SAL)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

以下是充分利用原始程式碼批註語言 (SAL) 的一些方法，並避免一些常見的問題。  
  
## <a name="_in_"></a>\_位置\_
 如果函式應寫入元素，請使用 `_Inout_` 而非 `_In_` 。 這在從舊版宏自動轉換成 SAL 的情況下特別相關。 在 SAL 之前，許多程式設計人員會使用宏做為批註， `IN` 也就是名稱為、 `OUT` 、 `IN_OUT` 或變數的宏。 雖然我們建議您將這些宏轉換成 SAL，但我們也建議您在轉換它們時小心，因為程式碼在原始原型撰寫後可能已變更，而舊的宏可能不再反映程式碼的用途。 請特別注意 `OPTIONAL` 批註宏，因為它經常會以不正確的方式放置，例如在逗號的錯誤端。  
  
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
 如果不允許呼叫端傳入 null 指標，請使用 `_In_` 或， `_Out_` 而不是 `_In_opt_` 或 `_Out_opt_` 。 這甚至適用于檢查其參數的函式，如果不應該是 Null，則會傳回錯誤。 雖然讓函數檢查其參數是否有未預期的 Null，且正常地傳回是很好的防禦程式碼撰寫作法，但並不表示參數注釋可以是選擇性類型 (\_ *Xxx*_opt \_) 。  
  
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
  
## <a name="_pre_defensive_-and-_post_defensive_"></a>\_Pre_defensive \_ 和 \_ Post_defensive\_  
 如果函式出現在信任界限中，建議您使用 `_Pre_defensive_` 註釋。  「防禦」修飾詞會修改特定的注釋，表示在呼叫時，應嚴格檢查介面，但在實文主體中，應假設可能傳遞的參數不正確。 在這種情況下，信任界限中會優先使用 `_In_ _Pre_defensive_`，指出雖然呼叫端嘗試傳遞 NULL 時會發生錯誤，但是仍會分析函式主體，就如同參數可能為 NULL 一樣，而且未先檢查指標是否為 NULL 就嘗試取值，便會加上旗標。  `_Post_defensive_` 註釋也可以用於回呼，其中信任的一方會假設為呼叫端，而不受信任的程式碼為被呼叫的程式碼。  
  
## <a name="_out_writes_"></a>\_Out_writes\_  
 下列範例示範的常見誤用 `_Out_writes_` 。  
  
```cpp  
  
// Incorrect  
void Func1(_Out_writes_(size) CHAR *pb,   
    DWORD size  
);  
  
```  
  
 批註 `_Out_writes_` 表示您有一個緩衝區。 它有已配置 `cb` 的位元組，並在結束時初始化第一個位元組。 此注釋不是絕對錯誤，而且有助於表示配置的大小。 但是，它不會指出函式初始化的元素數目。  
  
 下一個範例會顯示三個正確的方式，以完整指定緩衝區的已初始化部分的確切大小。  
  
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
  
## <a name="_out_-pstr"></a>\_Out \_ PSTR  
 使用 `_Out_ PSTR` 幾乎一律是錯誤的。 這會被解釋為具有指向字元緩衝區的輸出參數，並以 Null 終止。  
  
```cpp  
  
// Incorrect  
void Func1(_Out_ PSTR pFileName, size_t n);  
  
// Correct  
void Func2(_Out_writes_(n) PSTR wszFileName, size_t n);  
  
```  
  
 類似的注釋 `_In_ PCSTR` 很常見且有用。 它會指向具有 Null 終止的輸入字串，因為的前置條件 `_In_` 允許辨識以 null 終止的字串。  
  
## <a name="_in_-wchar-p"></a>\_\_WCHAR * p  
 `_In_ WCHAR* p` 指出有一個 `p` 指向一個字元的輸入指標。 不過，在大部分情況下，這可能不是預期的規格。 相反地，可能的原因是以 Null 結束陣列的規格;若要這樣做，請使用 `_In_ PWSTR` 。  
  
```cpp  
  
// Incorrect  
void Func1(_In_ WCHAR* wszFileName);  
  
// Correct  
void Func2(_In_ PWSTR wszFileName);  
  
```  
  
 缺少正確的 Null 終止規格是共通的。 使用適當的 `STR` 版本來取代類型，如下列範例所示。  
  
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
 如果參數是指標，而您想要表示指標所指向之元素的值範圍，請使用 `_Deref_out_range_` 而不是 `_Out_range_` 。 在下列範例中，會表示 * pcbFilled 的範圍，而不是 pcbFilled。  
  
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
  
 `_Deref_out_range_(0, cbSize)` 某些工具不是絕對必要的，因為它可以從推斷出來 `_Out_writes_to_(cbSize,*pcbFilled)` ，但在這裡會顯示完整性。  
  
## <a name="wrong-context-in-_when_"></a>發生錯誤的內容 \_\_  
 另一個常見的錯誤是針對前置條件使用後置狀態評估。 在下列範例中， `_Requires_lock_held_` 是前置條件。  
  
```cpp  
  
// Incorrect  
_When_(return == 0, _Requires_lock_held_(p->cs))  
int Func1(_In_ MyData *p, int flag);  
  
// Correct  
_When_(flag == 0, _Requires_lock_held_(p->cs))  
int Func2(_In_ MyData *p, int flag);  
  
```  
  
 運算式 `result` 會參考無法在前置狀態中使用的後置狀態值。  
  
## <a name="true-in-_success_"></a>成功的情況 \_\_  
 如果傳回值為非零值時，此函式會成功，請使用 `return != 0` 做為成功條件，而不是 `return == TRUE` 。 非零不一定表示與編譯器提供的實際值相等 `TRUE` 。 `_Success_` 的參數是運算式，而且下列運算式會評估為相等：`return != 0`、`return != false`、`return != FALSE` 和 `return`，且不含參數或比較。  
  
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
 針對參考變數，舊版 SAL 使用隱含指標做為批註目標，並需要加入 `__deref` 附加至參考變數的加入至批註。 此版本會使用物件本身，而不需要額外的 `_Deref_` 。  
  
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
  
## <a name="annotations-on-return-values"></a>傳回值上的注釋  
 下列範例顯示傳回值注釋中的常見問題。  
  
```cpp  
  
// Incorrect  
_Out_opt_ void *MightReturnNullPtr1();  
  
// Correct  
_Ret_maybenull_ void *MightReturnNullPtr2();  
  
```  
  
 在此範例中， `_Out_opt_` 指出指標可能是 Null 做為前置條件的一部分。 不過，前置條件無法套用至傳回值。 在此情況下，正確的注釋為 `_Ret_maybenull_` 。  
  
## <a name="see-also"></a>另請參閱  
 [使用 SAL 注釋減少 C/c + + 程式碼瑕疵](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [瞭解 SAL](../code-quality/understanding-sal.md)   
 [標注函式參數和傳回值](../code-quality/annotating-function-parameters-and-return-values.md)   
 [標注函式行為](../code-quality/annotating-function-behavior.md)   
 [標注結構和類別](../code-quality/annotating-structs-and-classes.md)   
 [標注鎖定行為](../code-quality/annotating-locking-behavior.md)   
 [指定套用注釋的時機和位置](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [內建函式](../code-quality/intrinsic-functions.md)
