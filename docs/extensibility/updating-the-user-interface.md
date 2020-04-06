---
title: 更新使用者介面 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- user interfaces, updating
- commands, updating UI
ms.assetid: 376e2f56-e7bf-4e62-89f5-3dada84a404b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1c51ae790eb35645fbe9aec5d9c422e1051aaa69
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698879"
---
# <a name="updating-the-user-interface"></a>更新使用者介面
實現命令後,可以添加代碼以使用新命令的狀態更新用戶介面。

 在典型的 Win32 應用程式中,可以連續輪詢命令集,並在使用者查看命令時調整各個命令的狀態。 但是,由於[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]shell 可以承載無限數量的 VSPackages,因此大量輪詢可能會降低回應能力,尤其是在託管代碼和 COM 之間的內部程式集中輪詢。

### <a name="to-update-the-ui"></a>更新 UI

1. 請執行下列其中一個步驟：

    - 呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> 方法。

         可以從<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>服務獲取介面<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>, 如下所示。

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

         如果的參數<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A>是非零 (),`TRUE`則更新將同步並立即執行。 我們建議您透過此參數的`FALSE`0 ( ), 以説明保持良好的效能. 如果要避免快取,`DontCache`請在 .vsct 檔案中建立命令時應用標誌。 但是,謹慎使用標誌,否則性能可能會下降。 有關命令標誌的詳細資訊,請參閱[命令標誌元素](../extensibility/command-flag-element.md)文檔。

    - 在透過在視窗中使用就地啟動模型承載 ActiveX 控制件的 VS<xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A>包中,使用該方法可能更方便。 介面<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A><xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>中<xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A><xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager>的方法和 介面中的方法在功能上等效。 兩者都會導致環境重新查詢所有命令的狀態。 通常,不會立即執行更新。 相反,更新會延遲到空閒時間。 shell 緩存命令狀態以説明保持良好的性能。 如果要避免快取,`DontCache`請在 .vsct 檔案中建立命令時應用標誌。 但是,謹慎使用標誌,因為性能可能會下降。

         請注意<xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager>,您可以`QueryInterface`<xref:Microsoft.VisualStudio.Shell.Interop.IOleComponentUIManager>通過在 物件上調用<xref:Microsoft.VisualStudio.Shell.Interop.SOleComponentUIManager>方法或從 服務獲取介面來獲取介面。

## <a name="see-also"></a>另請參閱
- [VSPackage 如何新增使用者介面項目](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [實作](../extensibility/internals/command-implementation.md)
