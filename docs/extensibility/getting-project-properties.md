---
title: 取得項目屬性 :微軟文件
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- project properties, displaying in tool window
- tool windows, displaying project properties
ms.assetid: 96ba07ca-0811-4013-8602-12550ac4ba79
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9ddfd48827bc762c9189f9b7600cfe9200e5c866
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711418"
---
# <a name="get-project-properties"></a>取得項目屬性

本演練演示如何在工具視窗中顯示項目屬性。

## <a name="prerequisites"></a>Prerequisites

從 Visual Studio 2015 開始,您不會從下載中心安裝 Visual Studio SDK。 它作為可選功能包含在可視化工作室設置中。 以後還可以安裝 VS SDK。 有關詳細資訊,請參閱[安裝可視化工作室 SDK](../extensibility/installing-the-visual-studio-sdk.md)。

### <a name="to-create-a-vsix-project-and-add-a-tool-window"></a>建立 VSIX 專案並加入工具視窗

1. 每個 Visual Studio 擴展都從 VSIX 部署專案開始,該專案將包含擴展資產。 建立[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]名為的`ProjectPropertiesExtension`VSIX 專案。 您可以通過搜尋"vsix"在 **"新項目**"對話框中找到 VSIX 專案範本。

2. 通過添加名為`ProjectPropertiesToolWindow`的自定義工具視窗項範本來添加工具視窗。 在**解決方案資源管理器**中,右鍵單擊專案節點並選擇「**添加新** > **項**」。 在 **「新增新項目」對話框**中,轉到**可視化 C# 項** > **擴充性**並選擇 **「自訂工具視窗**」。 在對話框底部的 **「 名稱」** 欄位中,將檔案`ProjectPropertiesToolWindow.cs`名稱變更為 。 有關如何建立自訂工具視窗的詳細資訊,請參閱[使用工具視窗建立延伸](../extensibility/creating-an-extension-with-a-tool-window.md)。

3. 建置方案，並確認方案編譯無誤。

### <a name="to-display-project-properties-in-a-tool-window"></a>在工具視窗中顯示項目屬性

1. 在ProjectPropertiesToolWindowCommand.cs檔中,使用指令添加以下指令。

    ```csharp
    using EnvDTE;
    using System.Windows.Controls;

    ```

2. 在*ProjectProperties Tool WindowControl.xaml 中*,刪除現有按鈕並從工具箱中添加樹視圖。 您還可以從*ProjectPropertiesToolWindowControl.xaml.cs*檔中刪除按一下事件處理程式。

3. 在*ProjectPropertiesToolWindowCommand.cs*`ShowToolWindow()`中使用 方法打開專案並讀取其屬性,然後將屬性添加到 TreeView。 ShowToolWindow 的代碼應如下所示:

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

4. 建置此專案並開始偵錯。 應出現實驗實例。

5. 在實驗執行個體中，開啟專案。

6. 在 **「查看** > **其他視窗**」中按下 **「項目屬性工具視窗**」。

  您應該在工具視窗中看到樹控制件以及第一個專案及其所有專案屬性的名稱。
