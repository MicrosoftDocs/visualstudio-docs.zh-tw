---
title: 支援的程式碼變更 (C#和 Visual Basic) |Microsoft Docs
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
ms.openlocfilehash: 9e840a8bb19b48c5cd4526ad80526bd62fcf8fa0
ms.sourcegitcommit: 3ca33862c1cfc3ccb83de3e95f1e69e860ab143a
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57526175"
---
# <a name="supported-code-changes-c-and-visual-basic"></a>支援的程式碼變更 (C#和 Visual Basic)
[編輯後繼續] 會處理方法主體內大多數程式碼的變更。 但是在偵錯期間，無法套用方法主體外的變更和方法主體內的某些變更。 若要套用這些不支援的變更，您必須停止偵錯，然後使用新版程式碼重新啟動偵錯。

## <a name="supported-changes-to-code"></a>支援的變更程式碼

下表顯示的變更，可能會對C#和 Visual Basic 程式碼，不需要重新啟動工作階段的偵錯工作階段。

|語言項目/功能|支援的編輯作業|限制|
|-|-|-|
|型別|加入方法、 欄位、 建構函式、 et al|[是](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits)|
|迭代器|新增或修改|否|
|async/await 運算式|新增或修改|[是](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits)|
|動態物件|新增或修改|否|
|Lambda 運算式|新增或修改|[是](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits)|
|LINQ 運算式|新增或修改|[Lambda 運算式與相同](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits)|

> [!NOTE]
> 較新的語言功能，例如字串內插補點和 null 條件運算子通常支援編輯後繼續。 最新的資訊，請參閱[Enc 支援編輯](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits)頁面。

## <a name="unsupported-changes-to-code"></a>不支援的變更程式碼
 下列變更無法套用至C#和 Visual Basic 程式碼偵錯工作階段：

-   變更目前的陳述式或任何其他使用中陳述式。

     使用中陳述式包含了在呼叫堆疊的函式中，為了取得目前陳述式而呼叫的任何陳述式。

     目前的陳述式在來源視窗中會以黃色背景標示。 其他使用中陳述式會以灰色背景標示，而且是唯讀的。 這些預設色彩可以在 [選項] 對話方塊中進行變更。

- 下表顯示不支援的變更程式碼的語言項目。

|語言項目/功能|不支援的編輯作業|
|-|-|
|所有的程式碼項目|重新命名|
|命名空間|新增|
|命名空間、 類型、 成員|刪除|
|泛型|新增或修改|
|介面|修改|
|型別|新增抽象或虛擬成員，並新增覆寫 (請參閱[詳細資料](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits))|
|型別|新增解構函式|
|成員|修改成員，其參考屬於內嵌 interop 類型|
|成員 (Visual Basic)|修改成員，以使用 On Error 或 Resume 陳述式|
|成員 (Visual Basic)|修改成員，其中包含彙總、 Group By、 簡單的聯結，或群組加入 LINQ 查詢子句|
|方法|修改簽章|
|方法|藉由新增 tělo metody 讓抽象方法變成非抽象|
|方法|刪除方法主體|
|屬性|新增或修改|
|事件或屬性|修改類型參數、 基底型別，委派類型，或傳回型別 |
|操作員 」 或 「 索引子|修改類型參數、 基底型別，委派類型，或傳回型別 |
|catch 區塊|它包含現用陳述式時，修改|
|請嘗試為 try-catch-finally 區塊|它包含現用陳述式時，修改|
|Using 陳述式|新增|
|非同步方法/lambda|修改非同步方法/lambda 中以.NET Framework 4 為目標的專案，並降低 (請參閱[詳細資料](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits))|
|迭代器|修改迭代器，在以.NET Framework 4 為目標的專案，並降低 (請參閱[詳細資料](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits))|

## <a name="unsafe-code"></a>Unsafe 程式碼
 變更 Unsafe 程式碼的限制與變更 Safe 程式碼的限制相同，但前者多了下列這一項額外限制：[編輯後繼續] 不支援對包含 `stackalloc` 運算子之方法內的 Unsafe 程式碼進行變更。

## <a name="unsupported-app-scenarios"></a>不支援的應用程式案例

不支援的應用程式與平台包含 ASP.NET 5、 Silverlight 5 和 Windows 8.1。

> [!NOTE]
> 支援的應用程式在 Windows 10 和 x86 和 x64.NET Framework 4.6 為目標的應用程式中包含 UWP 桌面或更新版本的版本 （.NET Framework 是僅限桌面版本）。

## <a name="unsupported-scenarios"></a>不支援的情節
 [編輯後繼續] 無法用於下列偵錯案例中：

-   混合模式 (原生/Managed) 偵錯。

-   SQL 偵錯

-   偵錯 Dr.Watson 傾印。

-   偵錯內嵌的執行階段應用程式。

-   偵錯應用程式使用附加至處理序 (**偵錯 > připojit k procesu**) 而不是藉由選擇執行應用程式**開始**從**偵錯**功能表。

-   偵錯最佳化程式碼

-   由於建置錯誤以致新版本建置失敗之後，對舊版程式碼進行偵錯。

## <a name="see-also"></a>請參閱
- [編輯後繼續 (Visual C#)](../debugger/edit-and-continue-visual-csharp.md)
- [如何：使用編輯後繼續 (C#)](../debugger/how-to-use-edit-and-continue-csharp.md)