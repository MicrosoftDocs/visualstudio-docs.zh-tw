---
title: 參數資訊，以舊版語言 Service1 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
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
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 50450d1968c626e0a5b32dee4c6f03d005d6ede9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31132759"
---
# <a name="parameter-info-in-a-legacy-language-service"></a>在舊版語言服務中的參數資訊
IntelliSense 的 參數資訊工具提示提供使用者有關的語言建構中的提示。  
  
 舊版語言服務會實作成 VSPackage 的一部分，但實作語言服務功能的較新方法是使用 MEF 擴充功能。 若要深入了解，請參閱[擴充編輯器和語言服務](../../extensibility/extending-the-editor-and-language-services.md)。  
  
> [!NOTE]
>  我們建議您開始使用新的編輯器 API 儘速。 這會提升語言服務的效能，並可讓您充分利用新編輯器功能。  
  
## <a name="how-parameter-info-tooltips-work"></a>參數資訊工具提示的運作方式  
 當您在編輯器中輸入陳述式時，則 VSPackage 會顯示包含所輸入之陳述式定義的小工具提示視窗。 例如，如果您輸入 Microsoft Foundation Classes (MFC) 陳述式 (例如`pMainFrame ->UpdateWindow`) 和按左括弧鍵要開始列出的參數，就會顯示的定義顯示方法秘訣`UpdateWindow`方法。  
  
 參數資訊工具提示通常會用於搭配陳述式完成。 它們是最適合用於具有參數或方法名稱或關鍵字之後的其他格式化的資訊的語言。  
  
 透過命令攔截語言服務不會起始參數資訊工具提示。 若要攔截使用者的字元，您的語言服務物件必須實作<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>介面，並將 [文字] 檢視的指標您<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>實作中的，藉由呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>方法中的<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>介面。 命令篩選器會攔截在程式碼視窗中輸入的命令。 監視命令的資訊可以知道何時要向使用者顯示參數資訊。 您可以使用相同的命令篩選陳述式完成、 錯誤標記和其他等等。  
  
 當您輸入的關鍵字，語言服務可以提供提示時，然後語言服務建立<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow>物件並呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A>方法中的<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>通知 IDE，才能顯示一個提示的介面。 建立<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow>物件使用`VSLocalCreateInstance`並指定 coclass `CLSID_VsMethodTipWindow`。 `VsLocalCreateInstance` 是函式中呼叫標頭檔 vsdoc.h 定義`QueryService`本機登錄和呼叫`CreateInstance`為此物件上`CLSID_VsMethodTipWindow`。  
  
## <a name="providing-a-method-tip"></a>提供方法秘訣  
 若要提供方法秘訣，請呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A>方法中的<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow>介面，將傳遞給它的實作<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>介面。  
  
 當您<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>類別叫用，被呼叫其方法依下列順序：  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetContextStream%2A>  
  
     目前的文字緩衝區中傳回的位置和長度的相關資料。 這會指示 IDE 不會遮住該資料與工具提示視窗。  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetCurMethod%2A>  
  
     傳回方法數目 （以零為起始的索引），您想要一開始顯示。 例如，如果傳回零，第一個多載的方法會一開始顯示。  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetOverloadCount%2A>  
  
     傳回適用於目前內容中的多載方法的數目。 如果您需要傳回值大於 1，此方法，則文字檢視會顯示向上和向下箭號為您。 如果您按一下向下箭號時，IDE 便會呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.NextMethod%2A>方法。 如果您按一下向上箭號時，IDE 便會呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.PrevMethod%2A>方法。  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetMethodText%2A>  
  
     數個呼叫期間建構的參數資訊工具提示文字<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetMethodText%2A>和<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterText%2A>方法。  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterCount%2A>  
  
     傳回要顯示在方法中的參數數目。  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterText%2A>  
  
     如果您傳回一個對應與您想要顯示的多載的方法數字時，呼叫這個方法是，後面接著呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A>方法。  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A>  
  
     會通知您語言的服務更新方法提示會顯示編輯器 中。 在<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A>方法，呼叫下列：  
  
    ```  
    <pTxWin> ->UpdateTipWindow(<pTip>, UTW_CONTENTCHANGED | UTW_CONTEXTCHANGED).  
    ```  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A>  
  
     您會收到呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A>方法，當您關閉方法提示視窗。