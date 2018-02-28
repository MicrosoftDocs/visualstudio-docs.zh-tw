---
title: "擴充 [輸出] 視窗 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Output window, about Output window
ms.assetid: b02fa88c-f92a-4ff6-ba5f-2eb4d48a643a
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 8fa99e2c741d11c79cb41226e3958b04d0265621
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="extending-the-output-window"></a>擴充 [輸出] 視窗
**輸出**視窗是一組讀取/寫入文字窗格。 Visual Studio 的這些內建的窗格：**建置**，專案通訊有關組建、 訊息和**一般**，在其中[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]傳達關於在 IDE 的訊息。 專案會取得參考**建置**窗格自動透過<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>介面方法和 Visual Studio 提供直接存取**一般**透過窗格<xref:Microsoft.VisualStudio.Shell.Interop.SVsGeneralOutputWindowPane>服務。 除了內建的窗格中，您可以建立和管理您自己自訂的窗格。  
  
 您可以控制**輸出**視窗直接透過<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow>和<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane>介面。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow>介面，提供<xref:Microsoft.VisualStudio.Shell.Interop.SVsOutputWindow>服務，定義用來建立、 擷取和終結方法**輸出**視窗窗格。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow>介面會定義用於顯示窗格、 隱藏窗格，以及管理其文字的方法。 另一種控制**輸出**視窗都是透過<xref:EnvDTE.OutputWindow>和<xref:EnvDTE.OutputWindowPane>Visual Studio 自動化物件模型中的物件。 這些物件會封裝幾乎所有的功能<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow>和<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane>介面。 此外，<xref:EnvDTE.OutputWindow>和<xref:EnvDTE.OutputWindowPane>物件加入一些較高層級的功能，以更輕鬆地列舉**輸出**視窗窗格以及從窗格中擷取文字。  
  
## <a name="creating-an-extension-that-uses-the-output-pane"></a>建立擴充功能，使用 [輸出] 窗格  
 您可以建立會執行 [輸出] 窗格的不同層面的擴充功能。  
  
1.  建立 VSIX 專案，名為`TestOutput`功能表命令與名稱為**TestOutput**。 如需詳細資訊，請參閱[建立擴充的功能表命令](../extensibility/creating-an-extension-with-a-menu-command.md)。  
  
2.  加入下列參考：  
  
    1.  EnvDTE  
  
    2.  EnvDTE80  
  
3.  在 TestOutput.cs，加入下列 using 陳述式：  
  
    ```f#  
    using EnvDTE;  
    using EnvDTE80;  
    ```  
  
4.  在 TestOutput.cs，刪除 ShowMessageBox 方法。 加入下列的方法虛設常式：  
  
    ```csharp  
    private void OutputCommandHandler(object sender, EventArgs e)  
    {  
    }  
    ```  
  
5.  TestOutput 建構函式中改 OutputCommandHandler 中的命令處理常式。 以下是將命令新增的部分：  
  
    ```csharp  
    OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;  
    if (commandService != null)  
    {  
        CommandID menuCommandID = new CommandID(MenuGroup, CommandId);  
        EventHandler eventHandler = OutputCommandHandler;  
        MenuCommand menuItem = new MenuCommand(eventHandler, menuCommandID);  
        commandService.AddCommand(menuItem);  
    }  
    ```  
  
6.  下列各節會有不同的方法，顯示不同的方式處理 [輸出] 窗格。 您可以呼叫這些方法來 OutputCommandHandler() 方法主體。 例如，下列程式碼加入 CreatePane() 方法下, 一節中所指定。  
  
    ```csharp  
    private void OutputCommandHandler(object sender, EventArgs e)  
    {  
        CreatePane(new Guid(), "Created Pane", true, false);  
    }  
    ```  
  
## <a name="creating-an-output-window-with-ivsoutputwindow"></a>使用 IVsOutputWindow 建立輸出視窗  
 這個範例示範如何建立新**輸出**使用視窗窗格<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow>介面。  
  
```csharp  
void CreatePane(Guid paneGuid, string title,   
    bool visible, bool clearWithSolution)  
{  
    IVsOutputWindow output =   
        (IVsOutputWindow)GetService(typeof(SVsOutputWindow));  
    IVsOutputWindowPane pane;  
  
    // Create a new pane.  
    output.CreatePane(  
        ref paneGuid,   
        title,   
        Convert.ToInt32(visible),   
        Convert.ToInt32(clearWithSolution));  
  
    // Retrieve the new pane.  
    output.GetPane(ref paneGuid, out pane);  
  
     pane.OutputString("This is the Created Pane \n");  
}  
```  
  
 如果您將此方法加入至延伸模組，指定上一節中，當您按一下**叫用 TestOutput**命令您應該會看到**輸出**具有標頭，指出視窗**顯示輸出從： CreatedPane**和文字**這是建立窗格**本身窗格中。  
  
## <a name="creating-an-output-window-with-outputwindow"></a>使用 OutputWindow 建立輸出視窗  
 這個範例示範如何建立**輸出**使用視窗窗格<xref:EnvDTE.OutputWindow>物件。  
  
```csharp  
void CreatePane(string title)  
{  
    DTE2 dte = (DTE2)GetService(typeof(DTE));  
    OutputWindowPanes panes =  
        dte.ToolWindows.OutputWindow.OutputWindowPanes;  
  
    try  
    {  
        // If the pane exists already, write to it.  
        panes.Item(title);  
    }  
    catch (ArgumentException)  
    {  
        // Create a new pane and write to it.  
        return panes.Add(title);  
    }  
}  
```  
  
 雖然<xref:EnvDTE.OutputWindowPanes>集合可讓您擷取**輸出**視窗窗格中的依其標題，窗格標題不保證是唯一的。 當您懷疑標題的唯一性時，使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow.GetPane%2A>方法來擷取正確的窗格透過其 GUID。  
  
 如果您將此方法加入至延伸模組，指定上一節中，當您按一下**叫用 TestOutput**命令，您應該會看到 [輸出] 視窗具有標頭指出**顯示輸出來源： DTEPane**和單字**加入 DTE 窗格**本身窗格中。  
  
## <a name="deleting-an-output-window"></a>刪除輸出視窗  
 這個範例示範如何刪除**輸出**視窗窗格。  
  
```csharp  
void DeletePane(Guid paneGuid)  
{  
    IVsOutputWindow output =  
    (IVsOutputWindow)ServiceProvider.GetService(typeof(SVsOutputWindow));  
  
    IVsOutputWindowPane pane;  
    output.GetPane(ref paneGuid, out pane);  
  
    if (pane == null)  
    {  
        CreatePane(paneGuid, "New Pane\n", true, true);  
    }  
     else  
    {  
        output.DeletePane(ref paneGuid);  
    }  
}  
```  
  
 如果您將此方法加入至延伸模組，指定上一節中，當您按一下**叫用 TestOutput**命令，您應該會看到 [輸出] 視窗具有標頭指出**顯示輸出來源： 新的窗格**和單字**加入建立窗格**本身窗格中。 如果您按一下**叫用 TestOutput**同樣地，命令窗格中會被刪除。  
  
## <a name="getting-the-general-pane-of-the-output-window"></a>取得輸出 視窗的 一般 窗格  
 這個範例示範如何取得內建**一般**窗格**輸出**視窗。  
  
```csharp  
void GetGeneralPane()  
{  
    return (IVsOutputWindowPane)GetService(  
        typeof(SVsGeneralOutputWindowPane));  
}  
```  
  
 如果您將此方法加入至延伸模組，指定上一節中，當您按一下**叫用 TestOutput**命令，您應該會看到**輸出** 視窗會顯示字**找到一般窗格**在窗格中。  
  
## <a name="getting-the-build-pane-of-the-output-window"></a>取得輸出 視窗的 組建 窗格  
 這個範例示範如何尋找 [建置] 窗格，並寫入其中。 因為預設未啟用 [建置] 窗格中，它會啟動它也。  
  
```csharp  
void OutputTaskItemStringExExample(string buildMessage)  
{  
    EnvDTE80.DTE2 dte = (EnvDTE80.DTE2)ServiceProvider.GetService(typeof(EnvDTE.DTE));  
  
    EnvDTE.OutputWindowPanes panes =  
        dte.ToolWindows.OutputWindow.OutputWindowPanes;  
    foreach (EnvDTE.OutputWindowPane pane in panes)  
        {  
            if (pane.Name.Contains("Build"))  
            {  
                pane.OutputString(buildMessage + "\n");  
                pane.Activate();  
                return;  
             }  
        }  
}  
```