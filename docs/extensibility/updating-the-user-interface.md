---
title: 更新消費者介面 |Microsoft Docs
description: 瞭解如何在您的 VSPackage 中執行新命令之後，新增程式碼以更新使用者介面。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- user interfaces, updating
- commands, updating UI
ms.assetid: 376e2f56-e7bf-4e62-89f5-3dada84a404b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: fd088d6887e7c7b60ea5a4101de050149583c5a2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99893447"
---
# <a name="updating-the-user-interface"></a>更新使用者介面
在您執行命令之後，您可以新增程式碼，以使用新命令的狀態來更新使用者介面。

 在一般的 Win32 應用程式中，可以持續輪詢命令集，並在使用者加以查看時調整個別命令的狀態。 不過，因為 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] shell 可以裝載不限數目的 vspackage，所以大量輪詢可能會降低回應性，特別是在 managed 程式碼與 COM 之間的交互操作元件之間進行輪詢。

### <a name="to-update-the-ui"></a>更新 UI

1. 請執行下列其中一個步驟：

    - 呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> 方法。

         您 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> 可以從服務取得介面 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> ，如下所示。

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

         如果的參數 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> 為非零 (`TRUE`) ，則會同步且立即執行更新。 建議您 `FALSE` 為此參數傳遞零 () ，以協助維持良好的效能。 如果您想要避免快取，請在 `DontCache` 您于 .vsct 檔案中建立命令時套用旗標。 不過，請小心使用旗標，否則效能可能會降低。 如需命令旗標的詳細資訊，請參閱 [命令旗標元素](../extensibility/command-flag-element.md) 檔集。

    - 在使用視窗中的就地啟動模型來裝載 ActiveX 控制項的 Vspackage 中，使用方法可能會比較方便 <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A> 。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A>介面中的方法 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> 和 <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A> 介面中的方法在 <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> 功能上相同。 這兩者都會使環境重新查詢所有命令的狀態。 通常不會立即執行更新。 相反地，更新會延遲到閒置時間為止。 Shell 會快取命令狀態，以協助維持良好的效能。 如果您想要避免快取，請在 `DontCache` 您于 .vsct 檔案中建立命令時套用旗標。 不過，請小心使用旗標，因為效能可能會降低。

         請注意，您可以 <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> `QueryInterface` 在物件上呼叫方法， <xref:Microsoft.VisualStudio.Shell.Interop.IOleComponentUIManager> 或從服務取得介面，以取得介面 <xref:Microsoft.VisualStudio.Shell.Interop.SOleComponentUIManager> 。

## <a name="see-also"></a>另請參閱
- [VSPackage 如何新增使用者介面項目](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [實作](../extensibility/internals/command-implementation.md)
