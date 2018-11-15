---
title: 取得專案屬性 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- project properties, displaying in tool window
- tool windows, displaying project properties
ms.assetid: 96ba07ca-0811-4013-8602-12550ac4ba79
caps.latest.revision: 30
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b99e86c4b955471ee10e0eb63cb5ca81fa675263
ms.sourcegitcommit: a34b7d4fdb3872865fcf98ba24a0fced58532adc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/12/2018
ms.locfileid: "51561591"
---
# <a name="getting-project-properties"></a>取得專案屬性
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本逐步解說示範如何在工具視窗中顯示專案內容。  
  
## <a name="prerequisites"></a>必要條件  
 從 Visual Studio 2015 中，從下載中心取得未安裝 Visual Studio SDK。 包含為 Visual Studio 安裝程式的選用功能。 您也可以在稍後安裝 VS SDK。 如需詳細資訊，請參閱 <<c0> [ 安裝 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
### <a name="to-create-a-vsix-project-and-add-a-tool-window"></a>若要建立 VSIX 專案，並加入工具視窗  
  
1.  每個 Visual Studio 擴充功能開始 VSIX 部署專案，以將包含的延伸模組資產。 建立[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]VSIX 專案，名為`ProjectPropertiesExtension`。 您可以找到在 VSIX 專案範本**新的專案**下方的對話方塊**Visual C# / 擴充性**。  
  
2.  藉由新增名為的自訂工具視窗項目範本加入工具視窗`ProjectPropertiesToolWindow`。 在 **方案總管**，以滑鼠右鍵按一下專案節點，然後選取**新增 / 新項目**。 在 [**加入新項目] 對話方塊**，請移至**Visual C# 項目 / 擴充性**，然後選取**自訂工具視窗**。 在 **名稱**底部的對話方塊欄位中，將檔案名稱變更為`ProjectPropertiesToolWindow.cs`。 如需如何建立自訂工具視窗的詳細資訊，請參閱[工具視窗建立擴充](../extensibility/creating-an-extension-with-a-tool-window.md)。  
  
3.  建置方案，並確認方案編譯無誤。  
  
### <a name="to-display-project-properties-in-a-tool-window"></a>若要顯示的工具視窗中的專案屬性  
  
1.  ProjectPropertiesToolWindowCommand.cs 檔案中新增下列 using 陳述式。  
  
    ```csharp  
    using EnvDTE;  
    using System.Windows.Controls;  
  
    ```  
  
2.  在 ProjectPropertiesToolWindowControl.xaml，移除現有的 按鈕，從 工具箱 新增 TreeView。 您也可以從 ProjectPropertiesToolWindowControl.xaml.cs 檔案移除 click 事件處理常式。  
  
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
  
5.  在實驗執行個體中開啟專案。  
  
6.  在 **檢視 / 其他 Windows**按一下  **ProjectPropertiesToolWindow**。  
  
     您應該會看到與名稱的第一個專案和其所有的專案屬性的 [工具] 視窗的樹狀目錄控制項。

