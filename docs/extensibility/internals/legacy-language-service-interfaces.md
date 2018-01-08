---
title: "舊版語言服務介面 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IVsLanguageInfo interface
- language services, objects
ms.assetid: 03b2d507-f463-417e-bc22-bdac68eeda52
caps.latest.revision: "24"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 82555c861a6bf250a818b185de57fc48f143e4f3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="legacy-language-service-interfaces"></a>舊版語言服務介面
任何特定的程式設計語言，可以有只有一個執行個體的語言服務一次。 不過，單一語言服務可以服務多個編輯器。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]不將語言服務關聯的任何特定的編輯器。 因此，當您要求的語言服務作業時，您必須識別適當的編輯器做為參數。  
  
## <a name="common-interfaces-associated-with-language-services"></a>通用語言服務相關聯的介面  
 編輯器 中呼叫以取得語言服務<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A>上適當的 VSPackage。 此呼叫中傳遞識別碼 (SID) 的服務識別所要求的語言服務。  
  
 您可以在任意數目的不同類別上實作的核心語言服務介面。 不過，常見的方法是在單一類別中實作下列介面：  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageDebugInfo>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageBlock> (選擇性)  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>必須在所有語言服務上實作介面。 它提供您的語言服務，例如語言服務，以及如何擷取色彩標示器相關聯的檔案名稱副檔名語言的當地語系化名稱的相關資訊。  
  
## <a name="additional-language-service-interfaces"></a>其他語言服務介面  
 語言服務可以提供其他介面。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]要求每個執行個體的文字緩衝的這些介面的個別執行個體。 因此，您應該在它自己的物件上實作的每一個這些介面。 下表顯示需要文字緩衝區執行個體每一個執行個體的介面。  
  
|介面|描述|  
|---------------|-----------------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>|管理程式碼視窗裝飾，如的下拉式清單列。 您可以使用，以取得此介面<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A>方法。 有一個<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>每個程式碼視窗。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>|以顏色標示語言關鍵字和分隔符號。 您可以使用，以取得此介面<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A>方法。 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>在 [小畫家] 階段呼叫。 避免大量計算工作內<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>或可能降低效能。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>|提供 IntelliSense 參數工具提示。 語言服務能辨識字元，表示該方法的資料應該顯示，例如左括號，它會呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A>方法來通知文字檢視，語言服務是以準備好顯示參數資訊工具提示。 文字檢視然後會呼叫回語言服務所使用的方法<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>介面，以取得所需的資訊顯示工具提示。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>|提供 IntelliSense 陳述式完成。 語言服務準備好顯示完成清單時，它會呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A>文字檢視上的方法。 文字檢視然後會呼叫回由語言服務上使用方法<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>物件。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter>|可讓您使用的命令處理常式 [文字] 檢視修改。 您實作的類別<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter>也必須實作介面<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>介面。 擷取文字檢視<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter>物件藉由查詢<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>物件傳遞到<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>方法。 應該有一個<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter>為每個檢視的物件。|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|攔截使用者輸入到程式碼視窗的命令。 監視輸出您<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>實作，以提供自訂的完成資訊並檢視修改<br /><br /> 將您<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>文字檢視，呼叫的物件<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>。|  
  
## <a name="see-also"></a>請參閱  
 [開發舊版語言服務](../../extensibility/internals/developing-a-legacy-language-service.md)   
 [檢查清單︰建立舊版語言服務](../../extensibility/internals/checklist-creating-a-legacy-language-service.md)