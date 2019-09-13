---
title: 支援的程式碼C#變更（和 Visual Basic） |Microsoft Docs
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
ms.openlocfilehash: c5f54a2b50447125b0abffd8cc62ba9c2a1d2b37
ms.sourcegitcommit: 4dfe098ac0df294aad63e6b384d6575980798ca3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/11/2019
ms.locfileid: "70887781"
---
# <a name="supported-code-changes-c-and-visual-basic"></a>支援的程式碼C#變更（和 Visual Basic）
[編輯後繼續] 會處理方法主體內大多數程式碼的變更。 但是在偵錯期間，無法套用方法主體外的變更和方法主體內的某些變更。 若要套用這些不支援的變更，您必須停止偵錯，然後使用新版程式碼重新啟動偵錯。

## <a name="supported-changes-to-code"></a>支援的程式碼變更

下表顯示在不需重新開機會話的情況C#下，可能會對程式碼進行的變更，以及在偵錯工具中 Visual Basic 程式碼。

|語言元素/功能|支援的編輯作業|限制|
|-|-|-|
|型別|加入方法、欄位、構造函式、et al|[是](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits)|
|迭代器|新增或修改|否|
|async/await 運算式|新增或修改|[是](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits)|
|動態物件|新增或修改|否|
|Lambda 運算式|新增或修改|[是](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits)|
|LINQ 運算式|新增或修改|[與 lambda 運算式相同](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits)|

> [!NOTE]
> [編輯後繼續] 通常會支援較新的語言功能，例如字串插補和 null 條件運算子。 如需最新的資訊，請參閱[Enc 支援的編輯](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits)頁面。

## <a name="unsupported-changes-to-code"></a>不支援的程式碼變更
 在偵錯工具期間，無法將C#下列變更套用至和 Visual Basic 程式碼：

- 變更目前的陳述式或任何其他使用中陳述式。

     使用中陳述式包含了在呼叫堆疊的函式中，為了取得目前陳述式而呼叫的任何陳述式。

     目前的陳述式在來源視窗中會以黃色背景標示。 其他使用中陳述式會以灰色背景標示，而且是唯讀的。 這些預設色彩可以在 [選項] 對話方塊中進行變更。

- 下表顯示不支援的程式碼變更（依語言元素）。

|語言元素/功能|不支援的編輯作業|
|-|-|
|所有程式碼元素|重新命名|
|命名空間|新增|
|命名空間、類型、成員|刪除|
|泛型|新增或修改|
|介面|修改|
|型別|新增抽象或虛擬成員，新增覆寫（請參閱[詳細資料](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits)）|
|型別|新增解構函式|
|成員|修改參考內嵌 interop 類型的成員|
|成員|在已執行程式碼存取之後修改靜態成員|
|成員（Visual Basic）|在 Error 或 Resume 語句上修改成員|
|成員（Visual Basic）|修改包含匯總、群組依據、簡單聯結或群組聯結 LINQ 查詢子句的成員|
|方法|修改簽章|
|方法|藉由新增方法主體，讓抽象方法變成非抽象|
|方法|刪除方法主體|
|屬性|新增或修改|
|事件或屬性|修改型別參數、基底型別、委派型別或傳回型別 |
|運算子或索引子|修改型別參數、基底型別、委派型別或傳回型別 |
|catch 區塊|當它包含作用中的語句時進行修改|
|try-catch-finally 區塊|當它包含作用中的語句時進行修改|
|Using 陳述式|新增|
|async 方法/lambda|在目標為 .NET Framework 4 和更低版本的專案中修改非同步方法/lambda （請參閱[詳細資料](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits)）|
|迭代器|修改專案中以 .NET Framework 4 和更低版本為目標的反覆運算器（請參閱[詳細資料](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits)）|

## <a name="unsafe-code"></a>Unsafe 程式碼
 變更 Unsafe 程式碼的限制與變更 Safe 程式碼的限制相同，但前者多了下列這一項額外限制：[編輯後繼續] 不支援變更在包含`stackalloc`運算子的方法內結束的 unsafe 程式碼。

## <a name="unsupported-app-scenarios"></a>不支援的應用程式案例

不支援的應用程式和平臺包括 ASP.NET 5、Silverlight 5 和 Windows 8.1。

> [!NOTE]
> 支援的應用程式包括 Windows 10 中的 UWP，以及以 .NET Framework 4.6 desktop 或更新版本為目標的 x86 和 x64 應用程式（.NET Framework 僅限桌上出版）。

## <a name="unsupported-scenarios"></a>不支援的情節
 [編輯後繼續] 無法用於下列偵錯案例中：

- 混合模式 (原生/Managed) 偵錯。

- SQL 偵錯

- 偵錯 Dr.Watson 傾印。

- 偵錯內嵌的執行階段應用程式。

- 從 [**調試**程式] 功能表選擇 [**啟動**]，而不是執行應用程式，而是使用 [附加至進程] （**Debug > 附加至進程**）來進行應用程式的

- 偵錯最佳化程式碼

- 由於建置錯誤以致新版本建置失敗之後，對舊版程式碼進行偵錯。

## <a name="see-also"></a>另請參閱
- [編輯後繼續 (Visual C#)](../debugger/edit-and-continue-visual-csharp.md)
- [如何：使用編輯後繼續 (C#)](../debugger/how-to-use-edit-and-continue-csharp.md)