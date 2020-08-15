---
title: 舊版語言 Service1 中的參數資訊 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, method tips
- method tips
- language services, parameter info tooltip
- IVsMethodData interface
- Parameter Info (IntelliSense)
ms.assetid: f367295e-45b6-45d2-9ec8-77481743beef
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8f8e5664634d189e8463376761d8fb59543740df
ms.sourcegitcommit: d8609a78b460d4783f5d59c0c89454910a4dbd21
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/14/2020
ms.locfileid: "88238071"
---
# <a name="parameter-info-in-a-legacy-language-service-1"></a>舊版語言服務中的參數資訊1
IntelliSense 的 [參數資訊] 工具提示會提供使用者關於語言結構中之位置的提示。

 舊版語言服務會實作為 VSPackage 的一部分，但執行語言服務功能的較新方法是使用 MEF 延伸模組。 若要深入瞭解，請參閱 [擴充編輯器和語言服務](../../extensibility/extending-the-editor-and-language-services.md)。

> [!NOTE]
> 我們建議您儘快開始使用新的編輯器 API。 這將可改善語言服務的效能，並可讓您利用新的編輯器功能。

## <a name="how-parameter-info-tooltips-work"></a>參數資訊工具提示的工作方式
 當您在編輯器中輸入語句時，VSPackage 會顯示一個小型的工具提示視窗，其中包含所要輸入之語句的定義。 例如，如果您輸入一個 Microsoft Foundation class (MFC) 語句 (例如 `pMainFrame ->UpdateWindow`) ，然後按左括弧鍵開始列出參數，則方法提示會顯示方法的定義 `UpdateWindow` 。

 參數資訊工具提示通常會與語句完成搭配使用。 對於在方法名稱或關鍵字之後有參數或其他格式化資訊的語言而言，它們最有用。

 語言服務會透過命令攔截來起始參數資訊工具提示。 若要攔截使用者的字元，您的語言服務物件必須執行介面， <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 並藉 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 由呼叫介面中的方法，將文字視圖傳遞至您的實作為指標 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 。 命令篩選器會攔截您在程式碼視窗中輸入的命令。 監視命令資訊，以知道何時要向使用者顯示參數資訊。 您可以使用相同的命令篩選器來完成語句、錯誤標記等等。

 當您輸入語言服務可提供提示的關鍵字時，語言服務會建立 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> 物件，並呼叫 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> 介面中的方法， <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 以通知 IDE 顯示提示。 使用建立 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> 物件 `VSLocalCreateInstance` ，並指定 coclass `CLSID_VsMethodTipWindow` 。 `VsLocalCreateInstance` 是在標頭檔 vsdoc 中定義的函式，這個函式會呼叫 `QueryService` 本機登錄並呼叫 `CreateInstance` 這個物件上的 `CLSID_VsMethodTipWindow` 。

## <a name="providing-a-method-tip"></a>提供方法提示
 若要提供方法提示，請呼叫 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> 介面中的方法 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> ，將介面的執行傳遞給它 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> 。

 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>叫用您的類別時，會依下列順序呼叫其方法：

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetContextStream%2A>

     傳回目前文字緩衝區中相關資料的位置和長度。 這會指示 IDE 不要使用 [工具提示] 視窗來隱匿該資料。

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetCurMethod%2A>

     傳回一開始要顯示的方法編號， (以零為基底的索引) 。 例如，如果您傳回零，則一開始會顯示第一個多載的方法。

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetOverloadCount%2A>

     傳回目前內容中適用的多載方法數目。 如果您針對這個方法傳回大於1的值，則文字視圖會為您顯示向上和向下箭號。 如果您按一下向下箭號，IDE 就會呼叫 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.NextMethod%2A> 方法。 如果您按一下向上箭號，IDE 就會呼叫 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.PrevMethod%2A> 方法。

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetMethodText%2A>

     參數資訊工具提示的文字會在數次呼叫 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetMethodText%2A> 和方法時建立 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterText%2A> 。

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterCount%2A>

     傳回要在方法中顯示的參數數目。

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterText%2A>

     如果您傳回的方法編號與您要顯示的多載相對應，則會呼叫這個方法，接著呼叫 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A> 方法。

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A>

     當顯示方法提示時，通知您的語言服務更新編輯器。 在 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A> 方法中，呼叫下列內容：

    ```
    <pTxWin> ->UpdateTipWindow(<pTip>, UTW_CONTENTCHANGED | UTW_CONTEXTCHANGED).
    ```

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A>

     <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A>當您關閉 [方法提示] 視窗時，您會收到方法的呼叫。
