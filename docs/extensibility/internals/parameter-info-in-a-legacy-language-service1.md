---
title: 舊版語言服務 1 中的參數資訊 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, method tips
- method tips
- language services, parameter info tooltip
- IVsMethodData interface
- Parameter Info (IntelliSense)
ms.assetid: f367295e-45b6-45d2-9ec8-77481743beef
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0530e5547fd17e1db84e7164039b507cb4583703
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60086309"
---
# <a name="parameter-info-in-a-legacy-language-service"></a>舊版語言服務中的參數資訊
IntelliSense 的 參數資訊工具提示提供使用者有關他們在語言建構的提示。

 舊版語言服務會實作成 VSPackage 的一部分，但實作語言服務功能的較新的方式是使用 MEF 擴充功能。 若要深入了解，請參閱[擴充編輯器和語言服務](../../extensibility/extending-the-editor-and-language-services.md)。

> [!NOTE]
>  我們建議您開始使用新的編輯器 API 盡。 這會改善您的語言服務的效能，並可讓您充分利用新編輯器功能。

## <a name="how-parameter-info-tooltips-work"></a>參數資訊工具提示的運作方式
 當您在編輯器中輸入陳述式時，則 VSPackage 會顯示小工具提示視窗，其中包含正在鍵入的陳述式的定義。 例如，如果您輸入 Microsoft Foundation Classes (MFC) 陳述式 (例如`pMainFrame ->UpdateWindow`) 並按左括弧鍵開始列出參數，就會顯示的定義顯示方法秘訣`UpdateWindow`方法。

 參數資訊工具提示通常用於搭配陳述式完成。 它們是最適合具有參數或方法名稱或關鍵字之後的其他格式化的資訊的語言。

 參數資訊工具提示所初始化的語言服務，透過命令攔截。 若要攔截使用者的字元，您的語言服務物件必須實作<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>介面，並將 [文字] 檢視的指標，您<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>實作，藉由呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>方法中的<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>介面。 命令篩選器攔截您輸入的程式碼視窗的命令。 監視知道何時要向使用者顯示參數資訊的命令資訊。 您可以使用相同的命令篩選陳述式完成、 錯誤標記和其他等等。

 當您鍵入的關鍵字，為其語言服務可以提供提示時，然後，語言服務會建立<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow>物件並呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A>方法中的<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>通知來顯示一個提示，IDE 的介面。 建立<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow>物件使用`VSLocalCreateInstance`並指定 coclass `CLSID_VsMethodTipWindow`。 `VsLocalCreateInstance` 是函式定義中呼叫的標頭檔 vsdoc.h`QueryService`本機登錄和呼叫`CreateInstance`針對此物件上`CLSID_VsMethodTipWindow`。

## <a name="providing-a-method-tip"></a>提供方法秘訣
 若要提供方法秘訣，請呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A>方法中的<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow>介面，將您的實作傳遞給它<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>介面。

 當您<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>叫用類別時，會呼叫其方法，以下列順序：

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetContextStream%2A>

     傳回目前文字緩衝區中的位置和長度相關的資料。 這會指示 IDE 不會遮住該資料與工具提示視窗。

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetCurMethod%2A>

     傳回方法數目 （以零為起始的索引），您想要一開始顯示。 比方說，如果您傳回零，第一個多載的方法是一開始顯示。

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetOverloadCount%2A>

     傳回適用於目前內容中的多載方法的數目。 如果您傳回值大於 1，此方法，則 [文字] 檢視會顯示向上和向下箭號。 如果您按一下向下箭號時，IDE 就會呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.NextMethod%2A>方法。 如果您按一下向上箭號時，IDE 就會呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.PrevMethod%2A>方法。

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetMethodText%2A>

     參數資訊工具提示的文字建構在數個呼叫的期間<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetMethodText%2A>和<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterText%2A>方法。

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterCount%2A>

     傳回要顯示在方法中的參數數目。

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterText%2A>

     如果您傳回一個對應與您想要顯示的多載的方法數字時，呼叫這個方法是，後面接著呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A>方法。

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A>

     會通知您更新方法提示隨即出現，編輯器的語言服務。 在 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A>方法，呼叫下列：

    ```
    <pTxWin> ->UpdateTipWindow(<pTip>, UTW_CONTENTCHANGED | UTW_CONTEXTCHANGED).
    ```

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A>

     您會收到呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A>方法，當您關閉方法提示視窗。