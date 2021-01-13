---
title: " (c # 和 Visual Basic) 支援的程式碼變更 |Microsoft Docs"
description: '瞭解當您在 Visual Studio 中進行 c # 或 Visual Basic 專案的偵錯工具時，使用 [編輯後繼續] 功能時，支援的程式碼變更。'
ms.custom: SEO-VS-2020
ms.date: 10/11/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Edit and Continue [C#], supported code changes
- Edit and Continue [Visual Basic], supported code changes
ms.assetid: c7a48ea9-5a7f-4328-a9d7-f0e76fac399d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 267d9097ebe53b4074bed6c5caf4077006c946eb
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/13/2021
ms.locfileid: "98149205"
---
# <a name="supported-code-changes-c-and-visual-basic"></a> (c # 和 Visual Basic 支援的程式碼變更) 
[編輯後繼續] 會處理方法主體內大多數程式碼的變更。 但是在偵錯期間，無法套用方法主體外的變更和方法主體內的某些變更。 若要套用這些不支援的變更，您必須停止偵錯，然後使用新版程式碼重新啟動偵錯。

## <a name="supported-changes-to-code"></a>支援的程式碼變更

下表顯示在偵錯工具期間可能對 c # 和 Visual Basic 程式碼進行的變更，而不需要重新開機會話。

|Language 元素/功能|支援的編輯作業|限制|
|-|-|-|
|類型|新增方法、欄位、函式、et al|[是](https://github.com/dotnet/roslyn/blob/master/docs/wiki/EnC-Supported-Edits.md)|
|迭代器|新增或修改|否|
|async/await 運算式|新增或修改|[是](https://github.com/dotnet/roslyn/blob/master/docs/wiki/EnC-Supported-Edits.md)|
|動態物件|新增或修改|否|
|Lambda 運算式|新增或修改|[是](https://github.com/dotnet/roslyn/blob/master/docs/wiki/EnC-Supported-Edits.md)|
|LINQ 運算式|新增或修改|[與 lambda 運算式相同](https://github.com/dotnet/roslyn/blob/master/docs/wiki/EnC-Supported-Edits.md)|

> [!NOTE]
> [編輯後繼續] 通常支援較新的語言功能，例如字串插補和 null 條件運算子。 如需最新資訊，請參閱 [Enc 支援的編輯](https://github.com/dotnet/roslyn/blob/master/docs/wiki/EnC-Supported-Edits.md) 頁面。

## <a name="unsupported-changes-to-code"></a>不支援的程式碼變更
 下列變更無法在偵測會話期間套用至 c # 和 Visual Basic 程式碼：

- 變更目前的陳述式或任何其他使用中陳述式。

     使用中陳述式包含了在呼叫堆疊的函式中，為了取得目前陳述式而呼叫的任何陳述式。

     目前的陳述式在來源視窗中會以黃色背景標示。 其他使用中陳述式會以灰色背景標示，而且是唯讀的。 這些預設色彩可以在 [選項] 對話方塊中進行變更。

- 下表顯示不支援的程式碼變更（依語言元素）。

|Language 元素/功能|不支援的編輯作業|
|-|-|
|所有程式碼元素|重新命名|
|命名空間|新增|
|命名空間、類型、成員|刪除|
|泛型|新增或修改|
|介面|修改|
|類型|新增抽象或虛擬成員、新增覆寫 (查看 [詳細資料](https://github.com/dotnet/roslyn/blob/master/docs/wiki/EnC-Supported-Edits.md)) |
|類型|新增解構函式|
|成員|修改參考內嵌 interop 類型的成員|
|成員|在已執行程式碼存取靜態成員之後修改該成員|
|成員 (Visual Basic) |使用 Error 或 Resume 語句修改成員|
|成員 (Visual Basic) |修改包含匯總、群組依據、簡單聯結或群組聯結 LINQ 查詢子句的成員|
|方法|修改簽章|
|方法|藉由新增方法主體來使抽象方法變成非抽象方法|
|方法|刪除方法主體|
|屬性|新增或修改|
|事件或屬性|修改類型參數、基底類型、委派類型或傳回類型 |
|運算子或索引子|修改類型參數、基底類型、委派類型或傳回類型 |
|catch 區塊|在包含使用中語句時修改|
|try-catch-finally 區塊|在包含使用中語句時修改|
|Using 陳述式|新增|
|async 方法/lambda|修改以 .NET Framework 4 和更低版本為目標之專案中的非同步方法/lambda (查看 [詳細資料](https://github.com/dotnet/roslyn/blob/master/docs/wiki/EnC-Supported-Edits.md)) |
|迭代器|在以 .NET Framework 4 和更低版本為目標的專案中修改反覆運算器， (查看 [詳細資料](https://github.com/dotnet/roslyn/blob/master/docs/wiki/EnC-Supported-Edits.md)) |

## <a name="unsafe-code"></a>Unsafe 程式碼
 變更 Unsafe 程式碼的限制與變更 Safe 程式碼的限制相同，但前者多了下列這一項額外限制：[編輯後繼續] 不支援對包含 `stackalloc` 運算子之方法內的 Unsafe 程式碼進行變更。

## <a name="unsupported-app-scenarios"></a>不支援的應用程式案例

不支援的應用程式和平臺包括 ASP.NET 5、Silverlight 5 及 Windows 8.1。

> [!NOTE]
> 支援的應用程式包括 Windows 10 中的 UWP，以及以 .NET Framework 4.6 desktop 或更新版本為目標的 x86 和 x64 應用程式 (.NET Framework 是僅) 桌上出版。

## <a name="unsupported-scenarios"></a>不支援的案例
 [編輯後繼續] 無法用於下列偵錯案例中：

- 混合模式 (原生/Managed) 偵錯。

- SQL 偵錯

- 偵測 Dr. Watson 傾印。

- 偵錯內嵌的執行階段應用程式。

- 使用附加至進程偵錯工具 (**Debug > 附加至進程**) 而不是藉由從 [**調試** 程式] 功能表選擇 [**啟動**] 來執行應用程式。

- 偵錯最佳化程式碼

- 由於建置錯誤以致新版本建置失敗之後，對舊版程式碼進行偵錯。

## <a name="see-also"></a>另請參閱
- [編輯後繼續 (Visual C#)](../debugger/edit-and-continue-visual-csharp.md)
- [如何：使用編輯後繼續 (C#)](../debugger/how-to-use-edit-and-continue-csharp.md)