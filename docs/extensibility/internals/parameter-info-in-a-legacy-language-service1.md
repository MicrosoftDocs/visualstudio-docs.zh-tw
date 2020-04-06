---
title: 舊語言服務中的參數資訊1 |微軟文件
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
ms.openlocfilehash: c26073252aae5434ba5a8197955948d0d9ec883d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706794"
---
# <a name="parameter-info-in-a-legacy-language-service"></a>舊版語言服務中的參數資訊
IntelliSense 參數資訊工具提示為使用者提供有關他們在語言構造中位置的提示。

 舊語言服務是作為 VSPackage 的一部分實現的,但實現語言服務功能的較新方法是使用 MEF 擴展。 要瞭解更多資訊,請參閱[延伸編輯器和語言服務](../../extensibility/extending-the-editor-and-language-services.md)。

> [!NOTE]
> 我們建議您儘快開始使用新的編輯器 API。 這將提高語言服務的性能,並允許您利用新的編輯器功能。

## <a name="how-parameter-info-tooltips-work"></a>參數資訊工具提示的工作原理
 在編輯器中鍵入語句時,VSPackage 將顯示一個小工具提示視窗,其中包含要鍵入的語句的定義。 例如,如果鍵入 Microsoft 基礎類 (MFC)`pMainFrame ->UpdateWindow`語句(如 ),然後按打開括弧鍵開始列出參數,則會出現一`UpdateWindow`個方法提示,顯示 方法的定義。

 參數資訊工具提示通常與語句完成一起使用。 它們對於在方法名稱或關鍵字之後具有參數或其他格式化資訊的語言最有用。

 參數資訊工具提示由語言服務通過命令攔截啟動。 要攔截<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>用戶字元,語言服務對象必須實現介面,並通過在介面中<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget><xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>調用 方法,將文本視圖傳遞<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>給實現。 命令篩選器攔截您在代碼視窗中鍵入的命令。 監視命令資訊,瞭解何時向使用者顯示參數資訊。 可以使用相同的命令篩選器進行語句完成、錯誤標記等。

 當您鍵入語言服務可以提供提示的關鍵字時,語言服務將創建一個<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow>物件,<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A><xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>並在介面中調用方法通知 IDE 顯示提示。 使用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow>`VSLocalCreateInstance`和指定共類`CLSID_VsMethodTipWindow`創建物件。 `VsLocalCreateInstance`是在標頭檔 vsdoc.h 中定義的函數`QueryService`,用於調用本地註冊表並`CreateInstance`調用`CLSID_VsMethodTipWindow`此物件。

## <a name="providing-a-method-tip"></a>提供方法提示
 要提供方法提示,請調用介面<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A><xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow>中的方法,將其傳遞給介面<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>的 實現。

 呼叫類<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>時,其方法按以下順序調用:

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetContextStream%2A>

     返回當前文本緩衝區中相關數據的位置和長度。 這指示 IDE 不要使用工具提示視窗遮蓋該數據。

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetCurMethod%2A>

     返回要最初顯示的方法編號(零基索引)。 例如,如果返回零,則最初顯示第一個重載方法。

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetOverloadCount%2A>

     返回適用於當前上下文的重載方法的數量。 如果為此方法返回大於 1 的值,則文本視圖將顯示向上和向下的箭頭。 如果單擊向下箭頭,IDE 將調<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.NextMethod%2A>用 方法。 如果單擊向上箭頭,IDE 將調<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.PrevMethod%2A>用 方法。

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetMethodText%2A>

     參數資訊工具提示的文本是在對 和<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetMethodText%2A><xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterText%2A>方法 的多次調用期間構造的。

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterCount%2A>

     傳回要在方法中顯示的參數數。

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterText%2A>

     如果傳回與要顯示的重載對應的方法編號,則呼叫此方法,然後呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A>方法 。

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A>

     在顯示方法提示時,通知語言服務更新編輯器。 在<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A>方法中,呼叫以下內容:

    ```
    <pTxWin> ->UpdateTipWindow(<pTip>, UTW_CONTENTCHANGED | UTW_CONTEXTCHANGED).
    ```

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A>

     關閉方法提示視窗時,<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A>會收到對 方法的呼叫。
