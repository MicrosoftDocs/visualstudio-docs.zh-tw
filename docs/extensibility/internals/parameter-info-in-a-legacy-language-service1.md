---
title: 舊版語言中的參數資訊 Service1 |Microsoft Docs
description: 瞭解如何在舊版語言服務中執行 IntelliSense 參數資訊工具提示，以提供使用者提示。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, method tips
- method tips
- language services, parameter info tooltip
- IVsMethodData interface
- Parameter Info (IntelliSense)
ms.assetid: f367295e-45b6-45d2-9ec8-77481743beef
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 4dade924ef89be22161c598ba0ae64084c0697ea
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105061143"
---
# <a name="parameter-info-in-a-legacy-language-service-1"></a>舊版語言服務1中的參數資訊
IntelliSense 參數資訊工具提示可為使用者提供有關其在語言結構中之位置的提示。

 舊版語言服務會實作為 VSPackage 的一部分，但是執行語言服務功能的較新方法是使用 MEF 延伸模組。 若要深入瞭解，請參閱 [擴充編輯器和語言服務](../../extensibility/extending-the-editor-and-language-services.md)。

> [!NOTE]
> 建議您儘快開始使用新的編輯器 API。 這可改善您的語言服務效能，並讓您利用新的編輯器功能。

## <a name="how-parameter-info-tooltips-work"></a>參數資訊工具提示的運作方式
 當您在編輯器中輸入語句時，VSPackage 會顯示一個小工具提示視窗，其中包含所輸入之語句的定義。 例如，如果您將 MFC) 語句 (輸入為 MFC (例如 `pMainFrame ->UpdateWindow`) ，然後按左括弧鍵以開始列出參數，則會出現方法提示來顯示方法的定義 `UpdateWindow` 。

 參數資訊工具提示通常會與語句完成一起使用。 對於在方法名稱或關鍵字之後具有參數或其他格式化資訊的語言而言，它們最為有用。

 參數資訊工具提示是透過命令攔截，由語言服務起始。 若要攔截使用者字元，您的語言服務物件必須執行 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 介面，並藉 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 由 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> 在介面中呼叫方法，將指標傳遞至您的實作為指標 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 。 命令篩選器會攔截您在程式碼視窗中輸入的命令。 監視命令資訊，以瞭解何時要對使用者顯示參數資訊。 您可以使用相同的命令篩選器來進行語句完成、錯誤標記等等。

 當您輸入語言服務可提供提示的關鍵字時，語言服務會建立 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> 物件，並 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> 在介面中呼叫方法， <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 以通知 IDE 顯示提示。 使用建立 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> 物件 `VSLocalCreateInstance` ，並指定 coclass `CLSID_VsMethodTipWindow` 。 `VsLocalCreateInstance` 是在標頭檔 vsdoc 中定義的函式，它會呼叫 `QueryService` 本機登錄並 `CreateInstance` 在這個物件上呼叫 `CLSID_VsMethodTipWindow` 。

## <a name="providing-a-method-tip"></a>提供方法提示
 若要提供方法提示，請 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> 在介面中呼叫方法 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> ，並將介面的實作為傳遞給它 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> 。

 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>叫用您的類別時，會依下列順序呼叫其方法：

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetContextStream%2A>

     傳回目前文字緩衝區中相關資料的位置和長度。 這會指示 IDE 不會將該資料與工具提示視窗混淆。

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetCurMethod%2A>

     傳回 (以零為基底的索引) 您想要一開始就顯示的方法編號。 例如，如果您傳回零，則一開始會顯示第一個多載的方法。

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetOverloadCount%2A>

     傳回目前內容中適用的多載方法數目。 如果您針對此方法傳回大於1的值，則文字視圖會為您顯示向上和向下箭號。 如果您按一下向下箭號，IDE 就會呼叫 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.NextMethod%2A> 方法。 如果您按一下向上箭號，IDE 就會呼叫 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.PrevMethod%2A> 方法。

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetMethodText%2A>

     參數資訊工具提示的文字是在多個呼叫和方法期間所建立 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetMethodText%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterText%2A> 。

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterCount%2A>

     傳回要在方法中顯示的參數數目。

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterText%2A>

     如果您傳回的方法編號與您想要顯示的多載相對應，則會呼叫這個方法，然後呼叫 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A> 方法。

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A>

     通知您的語言服務在顯示方法提示時，更新編輯器。 在 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A> 方法中，呼叫下列內容：

    ```
    <pTxWin> ->UpdateTipWindow(<pTip>, UTW_CONTENTCHANGED | UTW_CONTEXTCHANGED).
    ```

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A>

     <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A>當您關閉方法提示視窗時，您會收到方法的呼叫。
