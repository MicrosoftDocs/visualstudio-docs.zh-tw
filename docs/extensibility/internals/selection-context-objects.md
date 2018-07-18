---
title: 選擇內容物件 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- selection, tracking
- selection, context objects
ms.assetid: 7308ea8f-a42c-47e5-954e-7dee933dce7a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 04ccc4a57ac7af144c134761119433b7533e9bec
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31131257"
---
# <a name="selection-context-objects"></a>選擇內容物件
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]整合式的開發環境 (IDE) 以判斷應該顯示在 IDE 中使用全域選取範圍的內容物件。 每個視窗在 IDE 中的可以有自己的選取範圍的內容物件推送至全域範圍內容。 IDE 視窗中的值更新全域選取範圍的內容，該視窗具有焦點時。 如需詳細資訊，請參閱[意見反應給使用者](../../extensibility/internals/feedback-to-the-user.md)。  
  
 每個視窗框架或在 IDE 中的站台有服務呼叫<xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>。 VSPackage 設置視窗框架中所建立的物件必須呼叫`QueryService`方法來取得指向<xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>介面。  
  
 框架視窗可以讓其在啟動時傳播至全域範圍內容的選取項目內容資訊的部分。 這項功能可用於可能必須重新啟動具有空的選取範圍的工具視窗。  
  
 修改 Vspackage 可以監視全域選取範圍內容觸發程序事件。 Vspackage 可以執行下列工作，藉由實作`IVsTrackSelectionEx`和<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>介面：  
  
-   更新階層中目前作用中的檔案。  
  
-   監視變更特定類型的項目。 比方說，如果您的 VSPackage 會使用特殊**屬性**視窗中，您可以監視使用中的變更**屬性**視窗，您需要時重新啟動。  
  
 下列順序顯示選取項目追蹤的典型的課程。  
  
1.  IDE 會擷取新開啟的視窗中的選取項目內容，並將它放在全域範圍內容。 如果選取範圍內容使用 HIERARCHY_DONTPROPAGATE 或 SELCONTAINER_DONTPROPAGATE，該資訊不會傳播至通用的內容。 如需詳細資訊，請參閱[意見反應給使用者](../../extensibility/internals/feedback-to-the-user.md)。  
  
2.  通知事件已廣播給任何要求它們的 VSPackage。  
  
3.  VSPackage 處理程式碼執行活動，例如更新階層時，重新啟動工具或其他類似的工作所收到的事件。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>   
 [在 Visual Studio 中的階層](../../extensibility/internals/hierarchies-in-visual-studio.md)   
 [選取項目及在 IDE 中的貨幣](../../extensibility/internals/selection-and-currency-in-the-ide.md)   
 [專案類型](../../extensibility/internals/project-types.md)