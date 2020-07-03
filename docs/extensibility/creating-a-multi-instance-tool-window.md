---
title: 建立多實例工具視窗 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- multi
- tool windows
ms.assetid: 4a7872f1-acc9-4f43-8932-5a526b36adea
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1bb84ed9961cac5159e15bc0c45fada5426d2f2c
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2020
ms.locfileid: "85904056"
---
# <a name="create-a-multi-instance-tool-window"></a>建立多實例工具視窗
您可以設計工具視窗的程式，讓它的多個實例可以同時開啟。 根據預設，工具視窗只能開啟一個實例。

當您使用多重實例工具視窗時，您可以同時顯示多個相關的資訊來源。 例如，您可以將多行 <xref:System.Windows.Forms.TextBox> 控制項放在多個實例的工具視窗中，以便在程式設計會話期間同時使用數個程式碼片段。 例如，您可以將 <xref:System.Windows.Forms.DataGrid> 控制項和下拉式清單方塊放在多重實例工具視窗中，以便同時追蹤數個即時資料源。

## <a name="create-a-basic-single-instance-tool-window"></a>建立基本（單一實例）工具視窗

1. 使用 VSIX 範本建立名為**MultiInstanceToolWindow**的專案，並加入名為**MIToolWindow**的自訂工具視窗專案範本。

    > [!NOTE]
    > 如需使用工具視窗建立擴充功能的詳細資訊，請參閱[使用工具視窗建立擴充](../extensibility/creating-an-extension-with-a-tool-window.md)功能。

## <a name="make-a-tool-window-multi-instance"></a>將工具視窗設為多重實例

1. 開啟*MIToolWindowPackage.cs*檔案，並尋找 `ProvideToolWindow` 屬性。 和 `MultiInstances=true` 參數，如下列範例所示：

    ```csharp
    [PackageRegistration(UseManagedResourcesOnly = true)]
        [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About
        [ProvideMenuResource("Menus.ctmenu", 1)]
        [ProvideToolWindow(typeof(MultiInstanceToolWindow.MIToolWindow), MultiInstances = true)]
        [Guid(MIToolWindowPackage.PackageGuidString)]
        public sealed class MIToolWindowPackage : Package
    {. . .}
    ```

2. 在*MIToolWindowCommand.cs*檔案中，尋找 `ShowToolWindos()` 方法。 在這個方法中，呼叫 <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> 方法，並將其旗標設定 `create` 為， `false` 如此它就會逐一查看現有的工具視窗實例，直到找到可用的為止 `id` 。

3. 若要建立工具視窗實例，請呼叫 <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> 方法，並將其設 `id` 為可用的值，並將其旗標設定 `create` 為 `true` 。

    根據預設，方法的參數值 `id` <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> 為 `0` 。 這個值會建立單一實例工具視窗。 針對要裝載的多個實例，每個實例都必須有自己的唯一 `id` 。

4. <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A>在 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> 工具視窗實例的屬性所傳回的物件上呼叫方法 <xref:Microsoft.VisualStudio.Shell.ToolWindowPane.Frame%2A> 。

5. 根據預設， `ShowToolWindow` 工具視窗專案範本所建立的方法會建立單一實例工具視窗。 下列範例顯示如何修改 `ShowToolWindow` 方法以建立多個實例。

    ```csharp
    private void ShowToolWindow(object sender, EventArgs e)
    {
        for (int i = 0; i < 10; i++)
        {
            ToolWindowPane window = this.package.FindToolWindow(typeof(MIToolWindow), i, false);
            if (window == null)
            {
                // Create the window with the first free ID.
                window = (ToolWindowPane)this.package.FindToolWindow(typeof(MIToolWindow), i, true);
                if ((null == window) || (null == window.Frame))
                {
                    throw new NotSupportedException("Cannot create tool window");
                }

            IVsWindowFrame windowFrame = (IVsWindowFrame)window.Frame;
            Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(windowFrame.Show());
            break;
            }
        }
    }
    ```
