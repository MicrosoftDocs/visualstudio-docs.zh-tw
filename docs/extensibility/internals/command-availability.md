---
title: 命令可用性 |Microsoft Docs
description: 瞭解命令內容（根據目前的專案、目前的編輯器和其他因素而變更）如何判斷 Visual Studio 中有哪些可用的命令。
ms.custom: SEO-VS-2020
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- commands, context
- menu items, visibility contexts
ms.assetid: c74e3ccf-d771-48c8-a2f9-df323b166784
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 38ad456c6c946964f3038a712274003bae5732fa
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99932732"
---
# <a name="command-availability"></a>命令可用性

Visual Studio 內容會決定可用的命令。 內容會根據目前的專案、目前的編輯器、載入的 Vspackage，以及整合式開發環境 (IDE) 的其他層面而變更。

## <a name="command-contexts"></a>命令內容

以下是最常見的命令內容：

- IDE：一律可以使用 IDE 所提供的命令。

- VSPackage： Vspackage 可以定義要顯示或隱藏命令的時間。

- 專案：僅針對目前選取的專案顯示專案命令。

- 編輯器：一次只能有一個使用中的編輯器。 使用中編輯器的命令可供使用。 編輯器與語言服務密切合作。 語言服務必須在相關聯編輯器的內容中處理其命令。

- 檔案類型：編輯器可以載入多個檔案類型。 可用的命令可能會根據檔案類型而變更。

- 使用中視窗：最後一個活動文件視窗會設定使用者介面 (UI) 內容來進行索引鍵系結。 不過，具有類似于內部網頁瀏覽器之按鍵系結表的工具視窗也可以設定 UI 內容。 針對多索引標籤式文件視窗（例如 HTML 編輯器），每個索引標籤都有不同的命令內容 GUID。 註冊工具視窗之後，它一律會出現在 [ **View** ] 功能表上。

- UI 內容： UI 內容是由類別的值所識別 <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT> ，例如在 <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionBuilding_guid> 建立方案時，或 <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.Debugging_guid> 偵錯工具為作用中時。 多個 UI 內容可以同時處於作用中狀態。

## <a name="define-custom-context-guids"></a>定義自訂內容 Guid

如果未定義適當的命令內容 GUID，您可以在 VSPackage 中定義一個，然後視需要將其設計為作用中或非作用中，以控制命令的可見度：

1. 藉由呼叫方法來註冊內容 Guid <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCmdUIContextCookie%2A> 。

2. 藉由呼叫方法來取得內容 GUID 的狀態 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> 。

3. 藉由呼叫方法來開啟和關閉內容 Guid <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.SetCmdUIContext%2A> 。

> [!CAUTION]
> 請確定您的 VSPackage 不會影響任何現有的內容 Guid，因為其他 Vspackage 可能相依于這些 Guid。

## <a name="see-also"></a>另請參閱

- [選取專案內容物件](../../extensibility/internals/selection-context-objects.md)
- [Vspackage 如何新增使用者介面元素](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
