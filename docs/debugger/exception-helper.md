---
title: 檢查例外狀況-Visual Studio |Microsoft Docs
ms.date: 1/18/2020
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JavaScript
helpviewer_keywords:
- exception helper, debugger, exception
- debugging [Visual Studio], exception helper, Examine an exception
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2dae1609486ec4f3462be89b0526467dd7414647
ms.sourcegitcommit: 8cbced0fb46959a3a2494852df1e41db1177a26c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76829786"
---
# <a name="inspect-an-exception-using-the-exception-helper"></a>使用例外狀況協助程式檢查例外狀況 

無論您的技術或專業知識等級為何，處理例外狀況都是常見的問題。 這可能是令人沮喪的經驗，知道為什麼例外狀況會導致程式碼發生問題。 當您在 Visual Studio 中偵測到例外狀況時，我們想要將相關的例外狀況資訊提供給您，協助您更快地對問題進行偵錯工具，以減少這項挫折。

![例外狀況協助程式](media/debugger-exception-helper-default.png)

## <a name="pause-on-the-exception"></a>在例外狀況時暫停
當偵錯工具在例外狀況中斷時，該程式程式碼的右邊會出現例外狀況錯誤圖示。 非強制回應的例外狀況 helper 會出現在例外狀況圖示的附近。

![程式程式碼旁邊的例外狀況 helper](media/debugger-exception-helper-locerror.png)

## <a name="inspect-exception-info"></a>檢查例外狀況資訊
您可以立即讀取例外狀況協助程式中的例外狀況類型和例外狀況訊息，以及例外狀況是否擲回或未處理。 您可以按一下 [ **View Details** ] 連結，檢查和查看例外狀況物件的屬性。

## <a name="analyze-null-references"></a>分析 null 參考
從 Visual Studio 2017 開始，在 .Net 和 C/C++程式碼中，當您遇到 `NullReferenceException` 或 `AccessViolation`時，您會在例外狀況協助程式中看到 null 分析資訊。 分析會顯示為例外狀況訊息底下的文字。 在下面的圖例中，此資訊會顯示為 "**s** is null."。

![例外狀況協助程式 null 分析](media/debugger-exception-helper-default.png)


> [!NOTE]
> 在 managed 程式碼中的 Null 參考分析需要 .NET 版本4.6.2。 通用 Windows 平臺（UWP）和任何其他 .NET Core 應用程式目前不支援 Null 分析。 只有在偵錯工具代碼沒有任何及時（JIT）的程式碼優化時，才可以使用它。

## <a name="configure-exception-settings"></a>設定例外狀況設定 
您可以設定偵錯工具在例外狀況 Helper 的 [**例外狀況設定**] 區段中擲回目前類型的例外狀況時中斷。 如果偵錯工具在擲回的例外狀況暫停，則您可以使用核取方塊來停用在未來擲回之例外狀況類型的中斷。 如果您不想在這個特定的模組中擲回這個特定的例外狀況，請在 [**例外狀況設定**] 視窗中，依據 [**從下列**擲回] 底下的模組名稱來勾選核取方塊。 

## <a name="inspect-inner-exceptions"></a>檢查內部例外狀況 
如果例外狀況有任何內部例外狀況（[InnerException](https://docs.microsoft.com/dotnet/api/system.exception.innerexception)，您可以在例外狀況協助程式中查看它們。 如果有多個例外狀況，您可以使用呼叫堆疊上方顯示的向左和向右箭號在兩者之間流覽。

![內部例外狀況的例外狀況協助程式](media/debugger-exception-helper-innerexception.png)

## <a name="inspect-rethrown-exceptions"></a>檢查重新擲回的例外狀況
在已 `thrown` 例外狀況的情況下，例外狀況協助程式會顯示第一次擲回例外狀況時的呼叫堆疊。 如果擲回例外狀況多次，則只會顯示來自原始例外狀況的呼叫堆疊。

![發生重新擲回例外狀況的例外狀況協助程式](media/debugger-exception-helper-innerexception.png)

## <a name="share-a-debug-session-with-live-share"></a>與 Live Share 共用 debug 會話
在例外狀況協助程式中，您可以使用 [**啟動 Live Share 會話 ...** ] 連結來啟動[Live Share](https://docs.microsoft.com/visualstudio/liveshare/)會話。加入 Live Share 會話的任何人都可以看到例外狀況協助程式，以及任何其他的偵錯工具資訊。
