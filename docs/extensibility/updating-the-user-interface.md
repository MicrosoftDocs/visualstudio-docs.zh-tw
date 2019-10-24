---
title: 更新使用者介面 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- user interfaces, updating
- commands, updating UI
ms.assetid: 376e2f56-e7bf-4e62-89f5-3dada84a404b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bf41a41e68aa73e07bdcafe8bcdcd335fff6e6eb
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72718790"
---
# <a name="updating-the-user-interface"></a>更新使用者介面
在您執行命令之後，您可以加入程式碼，以新命令的狀態來更新使用者介面。

 在一般的 Win32 應用程式中，命令集可以持續輪詢，而個別命令的狀態可以在使用者進行流覽時調整。 不過，由於 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] shell 可以裝載無限數量的 Vspackage，因此廣泛的輪詢可能會降低回應能力，尤其是在 managed 程式碼和 COM 之間的交互操作元件之間輪詢。

### <a name="to-update-the-ui"></a>若要更新 UI

1. 請執行下列其中一個步驟：

    - 呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> 方法。

         @No__t_0 介面可以從 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> 服務取得，如下所示。

        ```csharp
        void UpdateUI(Microsoft.VisualStudio.Shell.ServiceProvider sp)
        {
            IVsUIShell vsShell = (IVsUIShell)sp.GetService(typeof(IVsUIShell));
            if (vsShell != null)
            {
                int hr = vsShell.UpdateCommandUI(0);
                Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(hr);
            }
        }

        ```

         如果 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> 的參數為非零（`TRUE`），則會以同步且立即的方式執行更新。 我們建議您為此參數傳遞零（`FALSE`），以協助維持良好的效能。 如果您想要避免快取，請在 .vsct 檔案中建立命令時套用 `DontCache` 旗標。 不過，請小心使用旗標，否則可能會降低效能。 如需有關命令旗標的詳細資訊，請參閱[命令旗標元素](../extensibility/command-flag-element.md)檔。

    - 在視窗中使用就地啟用模型裝載 ActiveX 控制項的 Vspackage 中，使用 <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A> 方法可能會比較方便。 @No__t_1 介面中的 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> 方法和 <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> 介面中的 <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A> 方法，在功能上是相同的。 這兩種情況都會導致環境重新查詢所有命令的狀態。 通常不會立即執行更新。 相反地，更新會延遲到閒置時間為止。 Shell 會快取命令狀態，以協助維持良好的效能。 如果您想要避免快取，請在 .vsct 檔案中建立命令時套用 `DontCache` 旗標。 不過，請小心使用旗標，因為效能可能會降低。

         請注意，您可以在 <xref:Microsoft.VisualStudio.Shell.Interop.IOleComponentUIManager> 物件上呼叫 `QueryInterface` 方法，或從 <xref:Microsoft.VisualStudio.Shell.Interop.SOleComponentUIManager> 服務取得介面，藉以取得 <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> 介面。

## <a name="see-also"></a>請參閱
- [VSPackage 如何新增使用者介面元素](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [實作](../extensibility/internals/command-implementation.md)