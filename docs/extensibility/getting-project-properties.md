---
title: 取得專案屬性 |Microsoft Docs
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- project properties, displaying in tool window
- tool windows, displaying project properties
ms.assetid: 96ba07ca-0811-4013-8602-12550ac4ba79
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cac5c55dd8fdeb1ba231d144d94c8be9b680cc6e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72633174"
---
# <a name="get-project-properties"></a>取得專案屬性

本逐步解說示範如何在工具視窗中顯示專案屬性。

## <a name="prerequisites"></a>Prerequisites

從 Visual Studio 2015 開始，您不會從下載中心安裝 Visual Studio SDK。 它在 Visual Studio 安裝程式中包含為選擇性功能。 您稍後也可以安裝 VS SDK。 如需詳細資訊，請參閱[安裝 VISUAL STUDIO SDK](../extensibility/installing-the-visual-studio-sdk.md)。

### <a name="to-create-a-vsix-project-and-add-a-tool-window"></a>建立 VSIX 專案並加入工具視窗

1. 每個 Visual Studio 延伸模組都是以 VSIX 部署專案為開頭，其中會包含擴充功能資產。 建立名為 `ProjectPropertiesExtension` 的 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] VSIX 專案。 藉由搜尋「vsix」，您可以在 [**新增專案**] 對話方塊中尋找 VSIX 專案範本。

2. 新增名為 `ProjectPropertiesToolWindow` 的自訂工具視窗專案範本，以加入工具視窗。 在 **方案總管**中，以滑鼠右鍵按一下專案節點，然後選取 **加入** > **新專案**。 在 [**新增專案] 對話方塊**中，移至 [**視覺C#效果專案** ** >  擴充**性]，然後選取 [**自訂工具視窗]** 。 在對話方塊底部的 [**名稱**] 欄位中，將檔案名變更為 `ProjectPropertiesToolWindow.cs`。 如需如何建立自訂工具視窗的詳細資訊，請參閱[使用工具視窗建立擴充](../extensibility/creating-an-extension-with-a-tool-window.md)功能。

3. 建置方案，並確認方案編譯無誤。

### <a name="to-display-project-properties-in-a-tool-window"></a>在工具視窗中顯示專案屬性

1. 在 ProjectPropertiesToolWindowCommand.cs 檔案中，新增下列 using 指示詞。

    ```csharp
    using EnvDTE;
    using System.Windows.Controls;

    ```

2. 在*ProjectPropertiesToolWindowControl*中，移除現有的按鈕，並從 [工具箱] 加入 TreeView。 您也可以從*ProjectPropertiesToolWindowControl.xaml.cs*檔案中移除 click 事件處理常式。

3. 在*ProjectPropertiesToolWindowCommand.cs*中，使用 `ShowToolWindow()` 方法來開啟專案並讀取其屬性，然後將屬性新增至 TreeView。 ShowToolWindow 的程式碼看起來應該如下所示：

    ```csharp
    private void ShowToolWindow(object sender, EventArgs e)
    {
        ToolWindowPane window = this.package.FindToolWindow(typeof(ProjectPropertiesToolWindow), 0, true);
        if ((null == window) || (null == window.Frame))
        {
            throw new NotSupportedException("Cannot create window.");
        }
        IVsWindowFrame windowFrame = (IVsWindowFrame)window.Frame;
        Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(windowFrame.Show());

        // Get the tree view and populate it if there is a project open.
        ProjectPropertiesToolWindowControl control = (ProjectPropertiesToolWindowControl)window.Content;
        TreeView treeView = control.treeView;

        // Reset the TreeView to 0 items.
        treeView.Items.Clear();

        DTE dte = (DTE)this.ServiceProvider.GetService(typeof(DTE));
        Projects projects = dte.Solution.Projects;
        if (projects.Count == 0)   // no project is open
        {
            TreeViewItem item = new TreeViewItem();
            item.Name = "Projects";
            item.ItemsSource = new string[]{ "no projects are open." };
            item.IsExpanded = true;
            treeView.Items.Add(item);
            return;
        }

        Project project = projects.Item(1);
        TreeViewItem item1 = new TreeViewItem();
        item1.Header = project.Name + "Properties";
        treeView.Items.Add(item1);

        foreach (Property property in project.Properties)
        {
            TreeViewItem item = new TreeViewItem();
            item.ItemsSource = new string[] { property.Name };
            item.IsExpanded = true;
            treeView.Items.Add(item);
        }
    }
    ```

4. 建置此專案並開始偵錯。 應該會出現實驗實例。

5. 在實驗執行個體中，開啟專案。

6. 在**View**  > **其他視窗** 中，按一下  **ProjectPropertiesToolWindow**。

  您應該會在工具視窗中看到樹狀目錄控制項以及第一個專案的名稱及其所有專案屬性。
