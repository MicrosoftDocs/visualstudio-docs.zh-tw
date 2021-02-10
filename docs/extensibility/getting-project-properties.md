---
title: 取得專案屬性 |Microsoft Docs
description: 瞭解如何在工具視窗中顯示專案屬性。 此範例顯示工具視窗中的樹狀目錄控制項。
ms.custom: SEO-VS-2020
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- project properties, displaying in tool window
- tool windows, displaying project properties
ms.assetid: 96ba07ca-0811-4013-8602-12550ac4ba79
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e89a19ee51a62e8d92c0ec8984e912703e2b92b5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99968186"
---
# <a name="get-project-properties"></a>取得專案屬性

本逐步解說說明如何在工具視窗中顯示專案屬性。

## <a name="prerequisites"></a>必要條件

從 Visual Studio 2015 開始，您不會從下載中心安裝 Visual Studio SDK。 它會在 Visual Studio 安裝程式中包含為選用功能。 您也可以稍後再安裝 VS SDK。 如需詳細資訊，請參閱 [安裝 VISUAL STUDIO SDK](../extensibility/installing-the-visual-studio-sdk.md)。

### <a name="to-create-a-vsix-project-and-add-a-tool-window"></a>若要建立 VSIX 專案並加入工具視窗

1. 每個 Visual Studio 擴充功能都會從 VSIX 部署專案開始，其中包含延伸模組資產。 建立 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 名為的 VSIX 專案 `ProjectPropertiesExtension` 。 您可以藉由搜尋 "vsix"，在 [ **新增專案** ] 對話方塊中找到 VSIX 專案範本。

2. 加入名為的自訂工具視窗專案範本，以新增工具視窗 `ProjectPropertiesToolWindow` 。 在 [**方案總管** 中，以滑鼠右鍵按一下專案節點，然後選取 [**加入**  >  **新專案**]。 在 [**加入新專案] 對話方塊** 中，移至 **Visual c # 專案** 擴充性  >   ，然後選取 [**自訂工具視窗]**。 在對話方塊底部的 [ **名稱** ] 欄位中，將檔案名變更為 `ProjectPropertiesToolWindow.cs` 。 如需有關如何建立自訂工具視窗的詳細資訊，請參閱 [使用工具視窗建立延伸](../extensibility/creating-an-extension-with-a-tool-window.md)模組。

3. 建置方案，並確認方案編譯無誤。

### <a name="to-display-project-properties-in-a-tool-window"></a>在工具視窗中顯示專案屬性

1. 在 ProjectPropertiesToolWindowCommand.cs 檔案中，新增下列 using 指示詞。

    ```csharp
    using EnvDTE;
    using System.Windows.Controls;

    ```

2. 在 *ProjectPropertiesToolWindowControl* 中，移除 [現有] 按鈕，並從 [工具箱] 新增 TreeView。 您也可以從 *ProjectPropertiesToolWindowControl.xaml.cs* 檔中移除 click 事件處理常式。

3. 在 *ProjectPropertiesToolWindowCommand.cs* 中，使用 `ShowToolWindow()` 方法開啟專案並讀取其屬性，然後將屬性新增至 TreeView。 ShowToolWindow 的程式碼看起來應該如下所示：

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

4. 建置此專案並開始偵錯。 實驗實例應會出現。

5. 在實驗執行個體中，開啟專案。

6. **在 [**  >  **其他視窗] 視窗** 中，按一下 [ **ProjectPropertiesToolWindow**]。

  您應該會看到工具視窗中的樹狀目錄控制項，以及第一個專案的名稱及其所有專案屬性。
