---
title: 建立多實例工具視窗 |Microsoft Docs
description: 瞭解如何修改工具視窗，讓它的多個實例可以同時開啟。 根據預設，工具視窗只能開啟一個實例。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- multi
- tool windows
ms.assetid: 4a7872f1-acc9-4f43-8932-5a526b36adea
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ce6122cbf4d6f85ab50e067fbbd643053ac4e4dd
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105089351"
---
# <a name="create-a-multi-instance-tool-window"></a>建立多實例工具視窗
您可以對工具視窗進行程式設計，讓它的多個實例可以同時開啟。 根據預設，工具視窗只能開啟一個實例。

當您使用多重實例工具視窗時，您可以同時顯示多個相關的資訊來源。 例如，您可以 <xref:System.Windows.Forms.TextBox> 在多個實例的工具視窗中放入多行控制項，以便在程式設計會話期間同時提供數個程式碼片段。 例如，您可以將 <xref:System.Windows.Forms.DataGrid> 控制項和下拉式清單方塊放在多個實例的工具視窗中，如此一來，就可以同時追蹤多個即時資料源。

## <a name="create-a-basic-single-instance-tool-window"></a>建立基本 (單一實例) 工具視窗

1. 使用 VSIX 範本來建立名為 **MultiInstanceToolWindow** 的專案，並新增名為 **MIToolWindow** 的自訂工具視窗專案範本。

    > [!NOTE]
    > 如需使用工具視窗建立延伸模組的詳細資訊，請參閱 [使用工具視窗建立延伸](../extensibility/creating-an-extension-with-a-tool-window.md)模組。

## <a name="make-a-tool-window-multi-instance"></a>將工具視窗設為多重實例

1. 開啟 *MIToolWindowPackage .cs* 檔案，然後尋找 `ProvideToolWindow` 屬性。 和 `MultiInstances=true` 參數，如下列範例所示：

    ```csharp
    [PackageRegistration(UseManagedResourcesOnly = true)]
        [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About
        [ProvideMenuResource("Menus.ctmenu", 1)]
        [ProvideToolWindow(typeof(MultiInstanceToolWindow.MIToolWindow), MultiInstances = true)]
        [Guid(MIToolWindowPackage.PackageGuidString)]
        public sealed class MIToolWindowPackage : Package
    {. . .}
    ```

2. 在 *MIToolWindowCommand .cs* 檔案中，尋找 `ShowToolWindos()` 方法。 在這個方法中，請呼叫 <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> 方法，並將其旗標設定 `create` 為，以便在 `false` 找到可用的之後，才逐一查看現有的工具視窗實例 `id` 。

3. 若要建立工具視窗實例，請呼叫 <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> 方法，並將其設定 `id` 為可用的值及其 `create` 旗標 `true` 。

    根據預設，方法的參數值 `id` <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> 為 `0` 。 此值會產生單一實例工具視窗。 若要裝載多個實例，每個實例都必須有自己的唯一 `id` 。

4. <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A>在 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> 工具視窗實例的屬性所傳回的物件上呼叫方法 <xref:Microsoft.VisualStudio.Shell.ToolWindowPane.Frame%2A> 。

5. 依預設， `ShowToolWindow` 工具視窗專案範本所建立的方法會建立單一實例工具視窗。 下列範例示範如何修改 `ShowToolWindow` 方法來建立多個實例。

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
