---
title: 選取內容物件 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- selection, tracking
- selection, context objects
ms.assetid: 7308ea8f-a42c-47e5-954e-7dee933dce7a
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7e1a43997d56f8d89f194fb83d20c1f160378873
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60092184"
---
# <a name="selection-context-objects"></a>選取項目內容物件
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]整合式的開發環境 (IDE) 來判斷應該顯示在 IDE 中使用全域選取範圍內容物件。 在 IDE 中的每個視窗都可以有它自己的選取範圍的內容物件推送至全域範圍內容。 該視窗具有焦點時，IDE 會更新全域選取範圍內容從視窗的值。 如需詳細資訊，請參閱 <<c0> [ 使用者的意見反應](../../extensibility/internals/feedback-to-the-user.md)。  
  
 每個視窗框架或在 IDE 中的站台有一個稱為服務<xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>。 VSPackage，在視窗框架中設置所建立的物件必須呼叫`QueryService`方法來取得變數的指標，<xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>介面。  
  
 框架視窗可以讓其在啟動時傳播至全球的選取項目內容的選取項目內容資訊的部分。 這項功能可用於工具視窗，可能必須重新啟動使用空的選取項目。  
  
 修改 Vspackage 可以監視的全域選擇內容觸發程序事件。 Vspackage 可以執行下列工作，藉由實作`IVsTrackSelectionEx`和<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>介面：  
  
- 更新階層中目前作用中的檔案。  
  
- 監視器會變更為特定類型的項目。 比方說，如果您的 VSPackage 會使用特殊**屬性** 視窗中，您可以監視作用中的變更**屬性**視窗，然後重新啟動您的需要時。  
  
  下列順序顯示選取項目追蹤的一般程。  
  
1. IDE 會擷取新開啟的視窗中的選取項目內容，並將它放在全域範圍內容。 如果選取範圍內容使用 HIERARCHY_DONTPROPAGATE 或 SELCONTAINER_DONTPROPAGATE，該資訊不會傳播至全球的內容。 如需詳細資訊，請參閱 <<c0> [ 使用者的意見反應](../../extensibility/internals/feedback-to-the-user.md)。  
  
2. 通知事件會廣播到任何要求它們的 VSPackage。  
  
3. VSPackage 是藉由執行活動，例如更新的階層架構中，然後再重新啟動一項工具或其他類似工作收到的事件。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>   
 [在 Visual Studio 中的階層](../../extensibility/internals/hierarchies-in-visual-studio.md)   
 [選取項目及在 IDE 中的貨幣](../../extensibility/internals/selection-and-currency-in-the-ide.md)   
 [專案類型](../../extensibility/internals/project-types.md)
