---
title: 偵錯工具中的運算式 |Microsoft Docs
description: 瞭解 Visual Studio 偵錯工具中的運算式評估工具不支援哪些語言運算式。
ms.custom: SEO-VS-2020
ms.date: 03/02/2020
ms.topic: conceptual
f1_keywords:
- vs.debug.expressions
helpviewer_keywords:
- expressions [debugger]
- debugging [Visual Studio], expressions
- expression evaluation, debugger evaluator
- native expression evaluation
- expression evaluators
- debugger, evaluating expressions
- debugging [Visual Studio], expression evaluation
- debugging [Visual Studio], variable evaluation
ms.assetid: 70f9b531-44c7-4d77-980d-5eddbf2bff41
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5b05af635ba7774cdb31291ad7c2b7eb52686bcf
ms.sourcegitcommit: d577818d3d8e365baa55c6108fa8159c46ed8b43
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/01/2021
ms.locfileid: "97846726"
---
# <a name="expressions-in-the-visual-studio-debugger"></a>Visual Studio 偵錯工具中的運算式
當您在 [ **快速監看式** ] 對話方塊、[ **監看式** ] 視窗或 [ **即時運算** ] 視窗中輸入運算式時，都能使用 Visual Studio 偵錯工具所包含的運算式評估工具。 在 [ **中斷點** ] 視窗和偵錯工具中的其他許多地方，也都可以使用運算式評估工具。

下列各節描述 Visual Studio 所支援語言的運算式評估限制。

## <a name="f-expressions-are-not-supported"></a>不支援 F# 運算式
無法辨識 F# 運算式。 如果您正在偵錯 F# 程式碼，您要先將運算式轉譯成 C# 語法，才能在偵錯工具視窗或對話方塊方塊中輸入運算式。 當您將運算式從 F# 轉譯為 C# 時，務必記得 C# 使用 `==` 運算子來測試是否相等，而 F# 使用單一 `=`。

## <a name="c-expressions"></a>C++ 運算式
如需 C++ 中，在運算式中使用內容運算子的相關資訊，請參閱 [Context Operator (C++)](../debugger/context-operator-cpp.md)。

### <a name="unsupported-expressions-in-c"></a>C++ 不支援的運算式

#### <a name="constructors-destructors-and-conversions"></a>建構函式、解構函式和轉換
您不能呼叫物件的建構函式或解構函式，明確或隱含都不行。 例如，下列運算式會明確呼叫建構函式，並產生錯誤訊息：

```C++
my_date( 2, 3, 1985 )
```

如果轉換的目的地是類別，您就無法呼叫轉換函式。 這類轉換牽涉到物件的建構。 例如，如果 `myFraction` 是 `CFraction`的執行個體，它負責定義轉換函式運算子 `FixedPoint`，那麼下列運算式將會產生錯誤：

```C++
(FixedPoint)myFraction
```

您無法呼叫 new 或 delete 運算子。 例如，不支援下列運算式：

```C++
new Date(2,3,1985)
```

#### <a name="preprocessor-macros"></a>前置處理器巨集
在偵錯工具中不支援前置處理器巨集。 例如，如果常數 `VALUE` 宣告為： `#define VALUE 3`，您不能在 [監看式] `VALUE`**視窗中使用** 。 為了避免這項限制，您應該盡可能將 `#define`取代為列舉和函式。

### <a name="using-namespace-declarations"></a>使用命名空間宣告
您不能使用 `using namespace` 宣告。  若要存取目前命名空間之外的類型名稱或變數，您必須使用完整限定名稱。

### <a name="anonymous-namespaces"></a>匿名命名空間
不支援匿名命名空間。 如果您有下列的程式碼，您無法將 `test` 加入監看式視窗：

```C++
namespace mars
{
    namespace
    {
        int test = 0;
    }
}
int main()
{
    // Adding a watch on test does not work.
    mars::test++;
    return 0;
}

```

### <a name="using-debugger-intrinsic-functions-to-maintain-state"></a><a name="BKMK_Using_debugger_intrinisic_functions_to_maintain_state"></a> 使用偵錯工具內建函式維持狀態
偵錯工具內建函式可讓您呼叫運算式中的某些 C/C++ 函式，而不需要變更應用程式的狀態。

偵錯工具內建函式：

- 保證是安全的：執行偵錯工具內建函式不會損毀要進行偵錯的處理序。

- 所有運算式中都可使用，即使是在不允許副作用和函式評估的情節中。

- 能夠在無法進行一般函式呼叫的情節中使用，例如對小型傾印進行偵錯。

  偵錯工具內建函式還可以讓運算式評估更方便。 例如，在中斷點條件中撰寫 `strncmp(str, "asd")` 比撰寫 `str[0] == 'a' && str[1] == 's' && str[2] == 'd'`更容易。 )

|區域|內建函式|
|----------|-------------------------|
|**字串長度**|[strlen、wcslen](/cpp/c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l)、 [strnlen、wcsnlen](/cpp/c-runtime-library/reference/strnlen-strnlen-s)|
|**字串比較**|[strcmp、wcscmp](/cpp/c-runtime-library/reference/strcmp-wcscmp-mbscmp)、 [stricmp、wcsicmp](/cpp/c-runtime-library/reference/stricmp-wcsicmp)、 [_stricmp、_strcmpi、_wcsicmp、_wcscmpi](/cpp/c-runtime-library/reference/stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l)、 [strncmp、wcsncmp](/cpp/c-runtime-library/reference/strncmp-wcsncmp-mbsncmp-mbsncmp-l)、 [strnicmp、wcsnicmp](/cpp/c-runtime-library/reference/strnicmp-wcsnicmp)、 [_strnicmp、_wcsnicmp](/cpp/c-runtime-library/reference/strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l)|
|**字串搜尋**|[strchr、wcschr](/cpp/c-runtime-library/reference/strchr-wcschr-mbschr-mbschr-l)、 [memchr、wmemchr](/cpp/c-runtime-library/reference/memchr-wmemchr)、 [strstr、wcsstr](/cpp/c-runtime-library/reference/strstr-wcsstr-mbsstr-mbsstr-l)|
|**Win32**|[CoDecodeProxy](/windows/win32/api/combaseapi/nf-combaseapi-codecodeproxy)、 [DecodePointer](/previous-versions/bb432242(v=vs.85))、 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)、 [TlsGetValue](/windows/win32/api/processthreadsapi/nf-processthreadsapi-tlsgetvalue)|
|**Windows 8**|[RoInspectCapturedStackBackTrace](/windows/win32/api/roerrorapi/nf-roerrorapi-roinspectcapturedstackbacktrace)、 [WindowsCompareStringOrdinal](/windows/win32/api/winstring/nf-winstring-windowscomparestringordinal)、 [WindowsGetStringLen](/windows/win32/api/winstring/nf-winstring-windowsgetstringlen)、 [WindowsGetStringRawBuffer](/windows/win32/api/winstring/nf-winstring-windowsgetstringrawbuffer)<br /><br /> 這些函式要求要進行偵錯的處理序必須在 Windows 8 上執行。 對從 Windows 8 裝置產生的傾印檔案進行偵錯也要求 Visual Studio 電腦必須執行 Windows 8。 不過，如果您是對 Windows 8 裝置進行遠端偵錯，則 Visual Studio 電腦可以執行 Windows 7。|
|**其他**|__log2//傳回指定整數的對數底數2，四捨五入為最接近的整數。<br /><br />__findNonNull、DecodeHString、DecodeWinRTRestrictedException、DynamicCast、DynamicMemberLookup、GetEnvBlockLength<br /><br />Stdext_HashMap_Int_OperatorBracket_idx，Std_UnorderedMap_Int_OperatorBracket_idx<br /><br />ConcurrencyArray_OperatorBracket_idx//Concurrency：： array<>：： operator [index<>] and operator (index<>) <br /><br />ConcurrencyArray_OperatorBracket_int//Concurrency：： array<>：： operator (int，int，... ) <br /><br />ConcurrencyArray_OperatorBracket_tidx//Concurrency：： array<>：： operator [tiled_index<>] 和運算子 (tiled_index<>) <br /><br />ConcurrencyArrayView_OperatorBracket_idx//Concurrency：： array_view<>：： operator [index<>] 和運算子 (index<>) <br /><br />ConcurrencyArrayView_OperatorBracket_int//Concurrency：： array_view<>：： operator (int，int，... ) <br /><br />ConcurrencyArrayView_OperatorBracket_tidx//Concurrency：： array_view<>：： operator [tiled_index<>] 和運算子 (tiled_index<>) <br /><br />TreeTraverse_Init//初始化新的樹狀結構遍歷<br /><br />TreeTraverse_Next//傳回樹狀結構中的節點<br /><br />TreeTraverse_Skip//略過暫止的樹狀結構中的節點|

## <a name="ccli---unsupported-expressions"></a>C++/CLI - 不支援的運算式

- 不支援包含指標的轉換 (cast)，或使用者定義的轉換。

- 不支援物件比較和指派。

- 不支援多載的運算子和多載函式。

- 不支援 Boxing 和 unboxing。

- 不支援`Sizeof` 運算子。

## <a name="c---unsupported-expressions"></a>c# - 不支援的運算式

### <a name="dynamic-objects"></a>動態物件
您可以在偵錯工具運算式中使用靜態設定類型為動態的變數。 當執行的物件 <xref:System.Dynamic.IDynamicMetaObjectProvider> 在監看式視窗中進行評估時，就會加入動態視圖節點。 [動態檢視] 節點會顯示物件成員，但不允許編輯成員的值。

以下是不支援的動態物件功能：

- 複合運算子 `+=`、 `-=`、 `%=`、 `/=`和 `*=`

- 多種轉型，包括數值轉型和類型引數轉型

- 具兩個以上引數的方法呼叫

- 具有兩個以上引數的 getter 屬性

- 具有引數的 setter 屬性

- 指派給索引子

- 布林運算子 `&&` 和 `||`

### <a name="anonymous-methods"></a>匿名方法
不支援建立新的匿名方法。

## <a name="visual-basic---unsupported-expressions"></a>Visual Basic - 不支援的運算式

### <a name="dynamic-objects"></a>動態物件
您可以在偵錯工具運算式中使用靜態設定類型為動態的變數。 在 [監看式] 視窗中評估實作 <xref:System.Dynamic.IDynamicMetaObjectProvider> 的物件時，會加入 [動態檢視] 節點。 [動態檢視] 節點會顯示物件成員，但不允許編輯成員的值。

以下是不支援的動態物件功能：

- 複合運算子 `+=`、 `-=`、 `%=`、 `/=`和 `*=`

- 多種轉型，包括數值轉型和類型引數轉型

- 具兩個以上引數的方法呼叫

- 具有兩個以上引數的 getter 屬性

- 具有引數的 setter 屬性

- 指派給索引子

- 布林運算子 `&&` 和 `||`

### <a name="local-constants"></a>區域常數
不支援區域常數。

### <a name="import-aliases"></a>匯入別名
不支援匯入別名。

### <a name="variable-declarations"></a>變數宣告
您無法在偵錯工具視窗中明確宣告新的變數。 不過，您可以在 [即時運算]  視窗中指派新的隱含變數。 這些隱含變數的範圍限於偵錯工作階段，並且無法在偵錯工具之外存取。 例如，陳述式 `o = 5` 將會隱含地建立新變數 `o` ，並將值 5 指派給該變數。 除非偵錯工具能夠推斷類型，否則這類隱含變數屬於 **Object** 類型。

### <a name="unsupported-keywords"></a>不支援的關鍵字

- `AddressOf`

- `End`

- `Error`

- `Exit`

- `Goto`

- `On Error`

- `Resume`

- `Return`

- `Select/Case`

- `Stop`

- `SyncLock`

- `Throw`

- `Try/Catch/Finally`

- `With`

- 命名空間或模組層級關鍵字，例如 `End Sub` 或 `Module`。

## <a name="see-also"></a>請參閱
- [C + + 中的格式規範](../debugger/format-specifiers-in-cpp.md)
- [ (c + +) 的內容運算子 ](../debugger/context-operator-cpp.md)
- [C 中的格式規範#](../debugger/format-specifiers-in-csharp.md)
- [虛擬變數](../debugger/pseudovariables.md)