---
title: 傳統語言服務介面 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IVsLanguageInfo interface
- language services, objects
ms.assetid: 03b2d507-f463-417e-bc22-bdac68eeda52
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 89d80d6961f5eaf91721567ccb0efa73bbe31406
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707378"
---
# <a name="legacy-language-service-interfaces"></a>舊版語言服務介面
對於任何特定的程式設計語言,一次只能有一個語言服務的實例。 但是,單一語言服務可以服務多個編輯器。

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]不將語言服務與任何特定編輯器相關聯。 因此,當您請求語言服務操作時,必須將適當的編輯器標識為參數。

## <a name="common-interfaces-associated-with-language-services"></a>與語言服務關聯的通用介面
 編輯器透過調用<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A>相應的 VSPackage 獲得您的語言服務。 在此調用中傳遞的服務 ID (SID) 標識要請求的語言服務。

 您可以在任意數量的單獨類上實現核心語言服務介面。 但是,一種常見方法是在單個類中實現以下介面:

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems>

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageDebugInfo>

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageBlock> (選擇性)

  介面<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>必須在所有語言服務上實現。 它提供有關語言服務的資訊,例如語言的當地語系化名稱、與語言服務關聯的檔名擴展名以及如何檢索著色器。

## <a name="additional-language-service-interfaces"></a>其他語言服務介面
 您的語言服務可以提供其他介面。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]請求這些介面的單獨實例,用於文本緩衝區的每個實例。 因此,您應該在自己的對象上實現每個介面。 下表顯示了每個文本緩衝區實例需要一個實例的介面。

|介面|描述|
|---------------|-----------------|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>|管理代碼視窗修飾,如下拉欄。 您可以使用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A>方法獲取此介面。 每個代碼視窗<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>有一個視窗。|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>|著色語言關鍵字和分隔符。 您可以使用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A>方法獲取此介面。 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>在繪製時調用。 避免計算密集型工作,<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>否則性能可能會受到影響。|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>|提供 IntelliSense 參數工具提示。 當語言服務識別指示應顯示方法數據的字元(如打開的括弧)時,它將調用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A>方法通知文本視圖語言服務已準備好顯示參數資訊工具提示。 然後,文本檢視使用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>介面的方法調用語言服務以獲取顯示工具提示所需的資訊。|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>|提供 IntelliSense 敘述完成。 當語言服務準備好顯示完成清單時,它將調用文本視圖上<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A>的方法。 然後,文本檢視使用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>物件上的方法調用回語言服務。|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter>|允許使用命令處理程式修改文本檢視。 實現介面的<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter>類還必須<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>實現介面。 文本檢視通過查詢傳遞到<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter><xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget><xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>方法的對象來檢索物件。 每個視圖應該有一<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter>個物件。|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|攔截用戶鍵入的代碼視窗中的命令。 監視<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>實作輸出,提供自訂完成資訊和檢視修改<br /><br /> 要將<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>物件傳遞到文字檢視,請呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>。|

## <a name="see-also"></a>另請參閱
- [開發舊版語言服務](../../extensibility/internals/developing-a-legacy-language-service.md)
- [檢查清單︰建立舊版語言服務](../../extensibility/internals/checklist-creating-a-legacy-language-service.md)
