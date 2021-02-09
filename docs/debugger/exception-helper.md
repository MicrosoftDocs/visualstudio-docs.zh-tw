---
title: 檢查例外狀況
titleSuffix: ''
description: 瞭解 Visual Studio 提供來協助您偵測例外狀況的資訊，以及如何選擇性地停用例外狀況的中斷。
ms.custom: SEO-VS-2020
ms.date: 1/18/2020
ms.topic: how-to
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e10dc341ce33ba91c05348e9d3fba545437ce497
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99870853"
---
# <a name="inspect-an-exception-using-the-exception-helper"></a>使用例外狀況協助程式檢查例外狀況 

無論您的技術或專業等級為何，處理例外狀況都是常見的問題。 這可能是一項令人沮喪的體驗，以找出例外狀況在程式碼中造成問題的原因。 當您在 Visual Studio 中偵測到例外狀況時，我們想要藉由提供相關的例外狀況資訊來協助您更快地對問題進行錯處理，以減少這項挫折。

![例外狀況協助程式](media/debugger-exception-helper-default.png)

## <a name="pause-on-the-exception"></a>在例外狀況時暫停
當偵錯工具在例外狀況中斷時，例外狀況錯誤圖示就會出現在該程式程式碼的右邊。 非強制回應的例外狀況協助程式將會出現在例外狀況圖示附近。

![程式程式碼旁邊的例外狀況 helper](media/debugger-exception-helper-locerror.png)

## <a name="inspect-exception-info"></a>檢查例外狀況資訊
您可以立即讀取例外狀況協助程式中的例外狀況類型和例外狀況訊息，以及例外狀況是否擲回或未處理。 您可以按一下 [ **視圖詳細資料** ] 連結，檢查和查看例外狀況物件的屬性。

## <a name="analyze-null-references"></a>分析 null 參考
從 Visual Studio 2017 開始，針對 .Net 和 C/c + + 程式碼，當您叫用或時， `NullReferenceException` `AccessViolation` 您會在例外狀況協助程式中看到 null 分析資訊。 分析會顯示為例外狀況訊息下方的文字。 在下圖中，資訊會顯示為「**s** 為 null」。

![例外狀況協助程式 null 分析](media/debugger-exception-helper-default.png)


> [!NOTE]
> 在 managed 程式碼中的 Null 參考分析需要 .NET 版本4.6.2。 通用 Windows 平臺 (UWP) 和任何其他 .NET Core 應用程式目前不支援 Null 分析。 只有在對沒有任何及時 (JIT) 程式碼優化的程式碼進行偵錯工具時，才可使用此功能。

## <a name="configure-exception-settings"></a>設定例外狀況設定 
您可以設定偵錯工具，以便在例外狀況協助程式的 **例外狀況設定** 區段中擲回目前類型的例外狀況時中斷。 如果偵錯工具在擲回的例外狀況時暫停，您就可以使用此核取方塊來停用在未來擲回的例外狀況類型。 如果您不想要在這個特定的模組中擲回這個特定的例外狀況時中斷，請在 [**例外狀況設定**] 視窗中的 [擲回 **時除外**] 下，依模組名稱勾選核取方塊。 

## <a name="inspect-inner-exceptions"></a>檢查內部例外狀況 
如果例外狀況 ([InnerException](/dotnet/api/system.exception.innerexception)有任何內部例外狀況，您可以在例外狀況協助程式中查看這些例外狀況。 如果有多個例外狀況，您可以使用呼叫堆疊上方顯示的向左和向右箭號來進行切換。

![具有內部例外狀況的例外狀況 helper](media/debugger-exception-helper-innerexception.png)

## <a name="inspect-rethrown-exceptions"></a>檢查重新擲回的例外狀況
在例外狀況發生的情況下，例外狀況協助程式會 `thrown` 顯示第一次擲回例外狀況時的呼叫堆疊。 如果擲回例外狀況多次，則只會顯示來自原始例外狀況的呼叫堆疊。

![引發例外狀況的例外狀況協助程式](media/debugger-exception-helper-innerexception.png)

## <a name="share-a-debug-session-with-live-share"></a>與 Live Share 共用 debug 會話
從例外狀況協助程式，您可以使用 [**啟動 Live Share 會話**] 連結來啟動 [Live Share](/visualstudio/liveshare/)會話 .。。任何加入 Live Share 會話的人都可以看到例外狀況協助程式，以及任何其他的 debug 資訊。