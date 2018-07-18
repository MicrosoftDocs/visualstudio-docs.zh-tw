---
title: 取得專案屬性 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project properties, displaying in tool window
- tool windows, displaying project propeties
ms.assetid: 96ba07ca-0811-4013-8602-12550ac4ba79
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d93e941c98293ca1d28f92bce1bc8c21f5ca2121
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31127620"
---
# <a name="getting-project-properties"></a>取得專案屬性
本逐步解說示範如何在工具視窗中顯示專案內容。  
  
## <a name="prerequisites"></a>必要條件  
 啟動 Visual Studio 2015 中，請勿從 「 下載中心 」 未安裝 Visual Studio SDK。 它是包含為 Visual Studio 安裝程式的選用功能。 您也可以在稍後安裝 VS SDK。 如需詳細資訊，請參閱[安裝 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
### <a name="to-create-a-vsix-project-and-add-a-tool-window"></a>建立 VSIX 專案，加入工具視窗  
  
1.  每個 Visual Studio 擴充功能開頭 VSIX 部署專案，以將包含延伸模組資產。 建立[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]VSIX 專案，名為`ProjectPropertiesExtension`。 您可以找到 VSIX 專案範本，在**新專案**對話方塊底下**Visual C# / 擴充性**。  
  
2.  加入名為的自訂工具視窗項目範本加入工具視窗`ProjectPropertiesToolWindow`。 在**方案總管 中**，以滑鼠右鍵按一下專案節點，然後選取**新增 / 新項目**。 在**加入新項目對話方塊**，請移至**Visual C# 項目 / 擴充性**選取**自訂工具視窗**。 在**名稱**在對話方塊底部欄位中，將檔案名稱變更為`ProjectPropertiesToolWindow.cs`。 如需如何建立自訂的工具視窗的詳細資訊，請參閱[建立工具視窗擴充](../extensibility/creating-an-extension-with-a-tool-window.md)。  
  
3.  建置方案，並確認方案編譯無誤。  
  
### <a name="to-display-project-properties-in-a-tool-window"></a>若要顯示工具視窗中的專案屬性  
  
1.  ProjectPropertiesToolWindowCommand.cs 檔案中加入下列 using 陳述式。  
  
    ```csharp  
    using EnvDTE;  
    using System.Windows.Controls;  
  
    ```  
  
2.  ProjectPropertiesToolWindowControl.xaml，移除現有的按鈕，從 [工具箱] 加入 TreeView。 您也可以從 ProjectPropertiesToolWindowControl.xaml.cs 檔案移除 click 事件處理常式。  
  
3.  在 ProjectPropertiesToolWindowCommand.cs，使用 ShowToolWindow() 方法來開啟專案，並讀取其屬性，然後將屬性加入至樹狀檢視。 ShowToolWindow 的程式碼看起來應該如下所示：  
  
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
  
4.  建置此專案並開始偵錯。 實驗執行個體應該會出現。  
  
5.  實驗執行個體中開啟專案。  
  
6.  在**檢視 / 其他視窗**按一下**ProjectPropertiesToolWindow**。  
  
     您應該會看到工具視窗，以及名稱的第一個專案和其所有的專案屬性中的樹狀目錄控制項。