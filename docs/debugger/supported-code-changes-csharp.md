---
title: "支援的程式碼變更 （C# 和 Visual Basic） |Microsoft 文件"
ms.custom: 
ms.date: 10/11/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Edit and Continue [C#], supported code changes
- Edit and Continue [Visual Basic], supported code changes
ms.assetid: c7a48ea9-5a7f-4328-a9d7-f0e76fac399d
caps.latest.revision: "27"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9a0a7d55b19455e22836d4750c0842a47816ee86
ms.sourcegitcommit: 26419ab0cccdc30d279c32d6a841758cfa903806
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/11/2017
---
# <a name="supported-code-changes-c-and-visual-basic"></a>支援的程式碼變更 （C# 和 Visual Basic）
[編輯後繼續] 會處理方法主體內大多數程式碼的變更。 但是在偵錯期間，無法套用方法主體外的變更和方法主體內的某些變更。 若要套用這些不支援的變更，您必須停止偵錯，然後使用新版程式碼重新啟動偵錯。

## <a name="supported-changes-to-code"></a>支援的變更程式碼

下表顯示的變更，可能會對 C# 和 Visual Basic 程式碼偵錯工作階段期間不需要重新啟動工作階段。

|語言項目功能|支援的編輯作業|限制|
|-|-|-|
|類型|加入方法、 欄位、 建構函式、 box|[是](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits)|
|Iterator|加入或修改|否|
|非同步/等候運算式|加入或修改|[是](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits)|
|動態物件|加入或修改|否|
|Lambda 運算式|加入或修改|[是](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits)|
|LINQ 運算式|加入或修改|[Lambda 運算式相同](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits)|

> [!NOTE]
> 較新語言功能，例如，字串插值和 null 條件運算子通常支援編輯後繼續。 最新的資訊，請參閱[Enc 支援編輯](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits)頁面。

## <a name="unsupported-changes-to-code"></a>不支援的變更程式碼
 下列變更無法套用至 C# 和 Visual Basic 程式碼，偵錯工作階段：  
  
-   變更目前的陳述式或任何其他使用中陳述式。  
  
     使用中陳述式包含了在呼叫堆疊的函式中，為了取得目前陳述式而呼叫的任何陳述式。  
  
     目前的陳述式在來源視窗中會以黃色背景標示。 其他使用中陳述式會以灰色背景標示，而且是唯讀的。 在中，可以變更這些預設色彩**選項** 對話方塊。

- 下表顯示不支援的變更程式碼的語言項目。

|語言項目功能|不支援的編輯作業|
|-|-|
|所有的程式碼項目|重新命名|
|命名空間|新增|
|命名空間、 類型、 成員|刪除|
|泛型|加入或修改|
|介面|修改|
|類型|加入抽象或虛擬成員、 新增覆寫 (請參閱[詳細資料](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits))|
|類型|新增解構函式|
|成員|修改成員參考屬於內嵌 interop 類型|
|成員 (Visual Basic)|修改成員使用 On Error 或 Resume 陳述式|
|成員 (Visual Basic)|修改包含 Aggregate、 Group By、 簡單聯結或群組加入 LINQ 查詢子句中的成員|
|方法|修改簽章|
|方法|加入方法主體，藉此抽象方法變成非抽象|
|方法|刪除方法主體|
|屬性|加入或修改|
|事件或屬性|修改型別參數、 基底型別，委派類型，或傳回型別 |
|運算子或索引子|修改型別參數、 基底型別，委派類型，或傳回型別 |
|catch 區塊|它包含現用陳述式時，修改|
|再試一次為 try-catch-finally 區塊|它包含現用陳述式時，修改|
|Using 陳述式|新增|
|非同步方法 lambda|修改非同步方法/lambda 中以.NET Framework 4 為目標的專案，並降低 (請參閱[詳細資料](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits))|
|Iterator|修改.NET Framework 4 為目標的專案中的迭代器，並降低 (請參閱[詳細資料](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits))|
  
## <a name="unsafe-code"></a>Unsafe 程式碼  
 變更 Unsafe 程式碼的限制與變更 Safe 程式碼的限制相同，但前者多了下列這一項額外限制：[編輯後繼續] 不支援對包含 `stackalloc` 運算子之方法內的 Unsafe 程式碼進行變更。  

## <a name="unsupported-app-scenarios"></a>不支援的應用程式案例

不支援的應用程式與平台包括 ASP.NET 5、 Silverlight 5、 Windows Phone 和 Windows Phone 模擬器和 Windows 8.1。

> [!NOTE]
> 支援的應用程式在 Windows 10 和.NET Framework 4.6 為目標的 x86 和 x64 應用程式中包含 UWP （.NET Framework 是僅限桌面版本） 的桌面或更新版本。
  
## <a name="unsupported-scenarios"></a>不支援的情節  
 [編輯後繼續] 無法用於下列偵錯案例中：  
  
-   混合模式 (原生/Managed) 偵錯。  
  
-   SQL 偵錯  
  
-   偵錯 Dr.Watson 傾印。  
  
-   未處理的例外狀況後編輯程式碼時 「**回溯呼叫堆疊上未處理例外狀況**」 選項並未選取。  
  
-   偵錯內嵌的執行階段應用程式。  
  
-   偵錯應用程式使用附加至處理序 (**偵錯 > 附加至處理序**) 而不是執行應用程式選擇**啟動**從**偵錯**功能表。  
  
-   偵錯最佳化程式碼  
  
-   由於建置錯誤以致新版本建置失敗之後，對舊版程式碼進行偵錯。
  
## <a name="see-also"></a>另請參閱  
 [編輯後繼續 (Visual C#)](../debugger/edit-and-continue-visual-csharp.md)   
 [如何：使用編輯後繼續 (C#)](../debugger/how-to-use-edit-and-continue-csharp.md)