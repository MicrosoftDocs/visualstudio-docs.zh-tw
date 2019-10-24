---
title: 選取範圍內容物件 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- selection, tracking
- selection, context objects
ms.assetid: 7308ea8f-a42c-47e5-954e-7dee933dce7a
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cc4f0aad4dd3f28f28259d0ca439a0cda1a520d9
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72723906"
---
# <a name="selection-context-objects"></a>選取項目內容物件
@No__t_0 的整合式開發環境（IDE）會使用全域選取範圍內容物件，來判斷應該在 IDE 中顯示的內容。 IDE 中的每個視窗都可以有自己的選擇內容物件，並將其推送至全域選取範圍內容。 當該視窗具有焦點時，IDE 會使用視窗中的值來更新全域選取範圍內容。 如需詳細資訊，請參閱對[使用者的意見](../../extensibility/internals/feedback-to-the-user.md)反應。

 IDE 中的每個視窗框架或網站都有一個稱為 <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> 的服務。 您的 VSPackage 所建立的物件（置於視窗框架中）必須呼叫 `QueryService` 方法，才能取得 <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> 介面的指標。

 框架視窗可在啟動時，將部分選取內容資訊，從傳播到全域選取內容。 這項功能適用于可能必須從空白選取範圍開始的工具視窗。

 修改全域選取範圍內容會觸發 Vspackage 可以監視的事件。 Vspackage 可以藉由實 `IVsTrackSelectionEx` 和 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection> 介面來執行下列工作：

- 更新階層中目前使用中的檔案。

- 監視特定元素類型的變更。 例如，如果您的 VSPackage 使用特殊的 [**屬性**] 視窗，您可以在 [作用中**屬性**] 視窗中監視變更，並在需要時重新開機。

  下列順序顯示選取追蹤的一般教學課程。

1. IDE 會從新開啟的視窗中抓取選取內容，並將它放在全域選取內容中。 如果選取範圍內容使用 HIERARCHY_DONTPROPAGATE 或 SELCONTAINER_DONTPROPAGATE，則不會將該資訊傳播至全域內容。 如需詳細資訊，請參閱對[使用者的意見](../../extensibility/internals/feedback-to-the-user.md)反應。

2. 通知事件會廣播到任何要求的 VSPackage。

3. VSPackage 是藉由執行活動（例如更新階層、重新開機工具或其他類似工作）所接收的事件來運作。

## <a name="see-also"></a>請參閱
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>
- [Visual Studio 中的階層](../../extensibility/internals/hierarchies-in-visual-studio.md)
- [IDE 中的選取項目和貨幣](../../extensibility/internals/selection-and-currency-in-the-ide.md)
- [專案類型](../../extensibility/internals/project-types.md)