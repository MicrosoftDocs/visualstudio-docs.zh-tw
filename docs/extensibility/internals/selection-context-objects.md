---
title: 選取專案內容物件 |Microsoft Docs
description: 瞭解 Visual Studio IDE 如何使用全域選取內容物件，以判斷應該在 IDE 中顯示的內容。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- selection, tracking
- selection, context objects
ms.assetid: 7308ea8f-a42c-47e5-954e-7dee933dce7a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bf5e54f00ecbac03eaebe68c6fb4de410987b63f
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/05/2021
ms.locfileid: "97875566"
---
# <a name="selection-context-objects"></a>選取項目內容物件
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]整合式開發環境 (IDE) 會使用全域選取內容物件來判斷應該在 IDE 中顯示的內容。 IDE 中的每個視窗都可以將自己的選取內容物件推送至全域選取內容。 當視窗具有焦點時，IDE 會使用視窗中的值來更新全域選取範圍內容。 如需詳細資訊，請參閱 [對使用者的意見](../../extensibility/internals/feedback-to-the-user.md)反應。

 IDE 中的每個視窗框架或網站都有一個稱為的服務 <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> 。 由您的 VSPackage 所建立的物件（放置於視窗框架中）必須呼叫 `QueryService` 方法以取得介面的指標 <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> 。

 框架視窗可以在啟動時，將部分選取內容資訊的部分，從傳播到全域選取內容。 這項功能適用于可能需要以空白選取範圍開頭的工具視窗。

 修改全域選取範圍內容會觸發 Vspackage 可以監視的事件。 Vspackage 可以藉由執行和介面來執行下列工作 `IVsTrackSelectionEx` <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection> ：

- 更新階層中目前的使用中檔案。

- 監視特定類型專案的變更。 例如，如果您的 VSPackage 使用特殊的 [ **屬性** ] 視窗，您可以在 [作用中 **屬性** ] 視窗中監視變更，並在需要時重新開機。

  下列順序顯示選取專案追蹤的一般的過程。

1. IDE 會從新開啟的視窗抓取選取內容，並將它放在全域選取內容中。 如果選取內容使用 HIERARCHY_DONTPROPAGATE 或 SELCONTAINER_DONTPROPAGATE，該資訊就不會傳播到全域內容。 如需詳細資訊，請參閱 [對使用者的意見](../../extensibility/internals/feedback-to-the-user.md)反應。

2. 通知事件會廣播到任何要求的 VSPackage。

3. VSPackage 藉由執行活動（例如更新階層、重新開機工具或其他類似工作），來對它所收到的事件採取動作。

## <a name="see-also"></a>請參閱
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>
- [Visual Studio 中的階層](../../extensibility/internals/hierarchies-in-visual-studio.md)
- [IDE 中的選取項目和貨幣](../../extensibility/internals/selection-and-currency-in-the-ide.md)
- [專案類型](../../extensibility/internals/project-types.md)
