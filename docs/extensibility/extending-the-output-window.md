---
title: 擴充輸出視窗 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Output window, about Output window
ms.assetid: b02fa88c-f92a-4ff6-ba5f-2eb4d48a643a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c6382d4b75d24d88e9fb93b2cf46386392458ebb
ms.sourcegitcommit: 752f03977f45169585e407ef719450dbe219b7fc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/15/2019
ms.locfileid: "56316171"
---
# <a name="extend-the-output-window"></a>擴充 [輸出] 視窗
**輸出**視窗是一組讀取/寫入文字窗格。 Visual Studio 有這些內建的窗格：**建置**，在哪些專案通訊相關的組建中，訊息和**一般**，在其中[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]會傳達有關 IDE 的訊息。 專案取得參照**建置**窗格自動透過<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>介面方法和 Visual Studio 提供直接存取**一般**窗格中的透過<xref:Microsoft.VisualStudio.Shell.Interop.SVsGeneralOutputWindowPane>服務。 除了內建的窗格中，您可以建立和管理您自己自訂的窗格。  
  
 您可以控制**輸出**視窗中直接透過<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow>和<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane>介面。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow>介面，提供<xref:Microsoft.VisualStudio.Shell.Interop.SVsOutputWindow>服務，請定義用來建立、 擷取和終結方法**輸出**視窗窗格。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane>介面會定義用於顯示窗格、 隱藏窗格，以及管理其文字的方法。 控制另一種**輸出** 視窗是透過<xref:EnvDTE.OutputWindow>和<xref:EnvDTE.OutputWindowPane>Visual Studio Automation 物件模型中的物件。 這些物件會封裝幾乎所有的功能<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow>和<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane>介面。 颾魤 ㄛ<xref:EnvDTE.OutputWindow>並<xref:EnvDTE.OutputWindowPane>物件加入一些較高層級的功能，讓您更輕鬆地列舉**輸出**視窗窗格以及從窗格擷取文字。  
  
## <a name="create-an-extension-that-uses-the-output-pane"></a>建立會使用 [輸出] 窗格的擴充功能  
 您可以讓擴充功能執行輸出 窗格的不同層面。  
  
1.  建立 VSIX 專案，名為`TestOutput`功能表命令與名為**TestOutput**。 如需詳細資訊，請參閱 <<c0> [ 建立具有功能表命令的延伸模組](../extensibility/creating-an-extension-with-a-menu-command.md)。  
  
2.  加入下列參考：  
  
    1.  EnvDTE  
  
    2.  EnvDTE80  
  
3.  在  *TestOutput.cs*，新增下列 using 陳述式：  
  
    ```f#  
    using EnvDTE;  
    using EnvDTE80;  
    ```  
  
4.  在  *TestOutput.cs*，刪除`ShowMessageBox`方法。 新增下列方法 stub:  
  
    ```csharp  
    private void OutputCommandHandler(object sender, EventArgs e)  
    {  
    }  
    ```  
  
5.  TestOutput 建構函式，將 OutputCommandHandler 中的命令處理常式。 以下是將命令新增的部分：  
  
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
  
6.  下列各節會有不同的方法，顯示不同的方式處理 [輸出] 窗格。 您可以呼叫這些方法的主體來`OutputCommandHandler()`方法。 例如，下列程式碼加入`CreatePane()`下一節中提供的方法。  
  
    ```csharp  
    private void OutputCommandHandler(object sender, EventArgs e)  
    {  
        CreatePane(new Guid(), "Created Pane", true, false);  
    }  
    ```  
  
## <a name="create-an-output-window-with-ivsoutputwindow"></a>使用 IVsOutputWindow 建立輸出視窗  
 此範例示範如何建立新**輸出**視窗窗格使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow>介面。  
  
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
  
 如果您將下列方法新增至指定上一節中，當您按一下 延伸模組**叫用 TestOutput**命令您應該會看到**輸出**視窗中顯示的標頭**顯示輸出從：CreatedPane**和文字**這是 建立 窗格**本身的窗格中。  
  
## <a name="create-an-output-window-with-outputwindow"></a>使用 OutputWindow 建立輸出視窗  
 此範例示範如何建立**輸出**視窗窗格使用<xref:EnvDTE.OutputWindow>物件。  
  
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
        panes.Add(title);  
    }  
}  
```  
  
 雖然<xref:EnvDTE.OutputWindowPanes>集合，可讓您擷取**輸出**視窗窗格中的依其標題，窗格標題不保證是唯一的。 當您不能確定標題的唯一性時，使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow.GetPane%2A>方法來擷取 [正確] 窗格中的由其 GUID。  
  
 如果您將下列方法新增至指定上一節中，當您按一下 延伸模組**叫用 TestOutput**命令，您應該會看到 輸出 視窗，以標頭指出**顯示輸出來源：DTEPane**和文字**加入 DTE 窗格**本身的窗格中。  
  
## <a name="delete-an-output-window"></a>刪除輸出視窗  
 此範例示範如何刪除**輸出**視窗窗格。  
  
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
  
 如果您將下列方法新增至指定上一節中，當您按一下 延伸模組**叫用 TestOutput**命令，您應該會看到 輸出 視窗，以標頭指出**顯示輸出來源：新窗格**和文字**新增建立窗格**本身的窗格中。 如果您按一下**叫用 TestOutput**同樣地，命令窗格中會被刪除。  
  
## <a name="get-the-general-pane-of-the-output-window"></a>取得輸出 視窗的 一般 窗格  
 此範例示範如何取得內建**一般**窗格**輸出**視窗。  
  
```csharp  
IVsOutputWindowPane GetGeneralPane()  
{  
    return (IVsOutputWindowPane)GetService(  
        typeof(SVsGeneralOutputWindowPane));  
}  
```  
  
 如果您將下列方法新增至指定上一節中，當您按一下 [延伸模組**叫用 TestOutput**命令，您應該會看到**輸出**] 視窗會顯示字組**找到一般窗格**在窗格中。  
  
## <a name="get-the-build-pane-of-the-output-window"></a>取得輸出 視窗的 建置 窗格  
 此範例顯示如何尋找**建置**窗格和 寫入它。 由於**建置**窗格未預設啟用，它也啟動它。  
  
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
