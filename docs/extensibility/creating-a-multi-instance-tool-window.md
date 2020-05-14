---
title: 建立多實體工具視窗 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- multi
- tool windows
ms.assetid: 4a7872f1-acc9-4f43-8932-5a526b36adea
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 33585f623f846e16200d430ad2c886fe0874b537
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739620"
---
# <a name="create-a-multi-instance-tool-window"></a>建立多實體工具視窗
您可以對工具視窗進行程式設計,以便可以同時打開該工具視窗的多個實例。 預設情況下,工具視窗只能打開一個實例。

使用多實例工具視窗時,可以同時顯示多個相關信息源。 例如,您可以將多行<xref:System.Windows.Forms.TextBox>控制件放在多實例工具視窗中,以便在程式設計作業階段期間同時提供多個程式碼段。 此外,例如,您可以將<xref:System.Windows.Forms.DataGrid>控制件和下拉清單框放在多實例工具視窗中,以便可以同時追蹤多個即時資料來源。

## <a name="create-a-basic-single-instance-tool-window"></a>建立基本(單實體)工具視窗

1. 使用 VSIX 範本建立名為 **「多實例工具視窗**」的專案,並添加名為**MIToolWindow**的自訂工具視窗項範本。

    > [!NOTE]
    > 有關使用工具視窗建立擴充的詳細資訊,請參考[使用工具視窗建立擴充](../extensibility/creating-an-extension-with-a-tool-window.md)。

## <a name="make-a-tool-window-multi-instance"></a>讓工具視窗多實體

1. 打開*MIToolWindowPackage.cs*檔並`ProvideToolWindow`找到該 屬性。 與`MultiInstances=true`參數,如以下範例所示:

    ```csharp
    [PackageRegistration(UseManagedResourcesOnly = true)]
        [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About
        [ProvideMenuResource("Menus.ctmenu", 1)]
        [ProvideToolWindow(typeof(MultiInstanceToolWindow.MIToolWindow), MultiInstances = true)]
        [Guid(MIToolWindowPackage.PackageGuidString)]
        public sealed class MIToolWindowPackage : Package
    {. . .}
    ```

2. *在 MIToolWindowCommand.cs*檔案中,尋找`ShowToolWindos()`方法 。 在此方法中,調用<xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A>方法並將`create`其 標誌`false`設置為 ,以便它將遍接現有工具視窗實例,直到找到可用`id`實例。

3. 要建立工具視窗實體,<xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A>請呼叫方法並將設定`id`為可用值,其`create`旗標設定為`true`。

    預設的選項`id`<xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A>, 方法的參數值`0`為 。 此值創建一個單實例工具視窗。 要託管多個實例,每個實例都必須有自己的唯一`id`。

4. 呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A>工具視窗實體<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame><xref:Microsoft.VisualStudio.Shell.ToolWindowPane.Frame%2A>的屬性傳回的物件上的方法。

5. 預設情況下,`ShowToolWindow`由工具視窗項目樣本建立的方法將建立單實例工具視窗。 下面的範例展示如何修改`ShowToolWindow`方法以創建多個實例。

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
