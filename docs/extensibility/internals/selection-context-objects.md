---
title: 選擇上下文物件 |微軟文件
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
ms.openlocfilehash: 4e4f33dd0168a667b8f266ea606cecf0c26d62f1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705516"
---
# <a name="selection-context-objects"></a>選取項目內容物件
集成[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]開發環境 (IDE) 使用全域選擇上下文物件來確定 IDE 中應顯示的內容。 IDE 中的每個視窗都可以將自己的選擇上下文物件推送到全域選擇上下文。 當視窗具有焦點時,IDE 會使用視窗中的值更新全域選擇上下文。 有關詳細資訊,請參閱[向使用者的回饋](../../extensibility/internals/feedback-to-the-user.md)。

 IDE 中的每個視窗框架或網站都有一個稱為<xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>的服務。 由在視窗幀中設置的 VSPackage 創建的物件必須`QueryService`調用 方法以獲取<xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>指向介面的指標。

 框架視窗可以在啟動時防止其選擇上下文資訊的某些部分傳播到全域選擇上下文。 此功能對於可能需要從空選擇開始的工具視窗很有用。

 修改全域選擇上下文將觸發 VSPackages 可以監視的事件。 VS套件可以通過`IVsTrackSelectionEx`實現<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>和 介面執行以下任務:

- 更新層次結構中的當前活動檔。

- 監視對某些類型的元素的更改。 例如,如果您的 VSPackage 使用特殊的**屬性**視窗,則可以監視活動**屬性**視窗中的更改,並在需要時重新啟動。

  以下序列顯示了典型的選擇跟蹤過程。

1. IDE 從新打開的窗口檢索選擇上下文,並將其放入全域選擇上下文中。 如果選擇上下文使用HIERARCHY_DONTPROPAGATE或SELCONTAINER_DONTPROPAGATE,則該資訊不會傳播到全域上下文。 有關詳細資訊,請參閱[向使用者的回饋](../../extensibility/internals/feedback-to-the-user.md)。

2. 通知事件將廣播給請求通知的任何 VSPackage。

3. VSPackage 通過執行更新層次結構、重新啟動工具或其他類似任務等活動來對它接收的事件執行。

## <a name="see-also"></a>另請參閱
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>
- [Visual Studio 中的階層](../../extensibility/internals/hierarchies-in-visual-studio.md)
- [IDE 中的選取項目和貨幣](../../extensibility/internals/selection-and-currency-in-the-ide.md)
- [專案類型](../../extensibility/internals/project-types.md)
