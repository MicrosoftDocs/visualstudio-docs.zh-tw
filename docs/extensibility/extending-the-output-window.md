---
title: "擴充 [輸出] 視窗 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "關於輸出視窗 [輸出] 視窗"
ms.assetid: b02fa88c-f92a-4ff6-ba5f-2eb4d48a643a
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# 擴充 [輸出] 視窗
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

**輸出** 視窗是一組讀取\/寫入文字窗格。 Visual Studio 有這些內建的窗格: **建置**, ，專案通訊相關的組建中，訊息和 **一般**, ，在其中 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 傳達 IDE 相關的訊息。 專案取得的參考 **建置** 窗格自動透過 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> 介面方法和 Visual Studio 提供直接存取 **一般** 窗格透過 <xref:Microsoft.VisualStudio.Shell.Interop.SVsGeneralOutputWindowPane> 服務。 除了內建的窗格中，您可以建立和管理您自己自訂的窗格。  
  
 您可以控制 **輸出** 視窗直接透過 <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> 和 <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> 介面。<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> 介面，指由 <xref:Microsoft.VisualStudio.Shell.Interop.SVsOutputWindow> 服務，請定義用來建立、 擷取和終結方法 **輸出** 視窗窗格。<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> 介面會定義用於顯示窗格、 隱藏窗格，以及管理其文字的方法。 另一種控制 **輸出** 視窗是透過 <xref:EnvDTE.OutputWindow> 和 <xref:EnvDTE.OutputWindowPane> Visual Studio Automation 物件模型中的物件。 這些物件會封裝幾乎所有的功能 <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> 和 <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> 介面。 此外， <xref:EnvDTE.OutputWindow> 和 <xref:EnvDTE.OutputWindowPane> 物件新增一些較高層級的功能，以便輕鬆地列舉 **輸出** 視窗窗格，並從窗格擷取文字。  
  
## 建立擴充功能會使用 \[輸出\] 窗格  
 您可以運用 \[輸出\] 窗格的不同層面的擴充功能。  
  
1.  建立 VSIX 專案，名為 `TestOutput` 與功能表命令名稱為 **TestOutput**。 如需詳細資訊，請參閱[建立擴充功能的功能表命令](../extensibility/creating-an-extension-with-a-menu-command.md)。  
  
2.  加入下列參考:  
  
    1.  EnvDTE  
  
    2.  EnvDTE80  
  
3.  在 TestOutput.cs，新增下列 using 陳述式:  
  
    ```f#  
    using EnvDTE; using EnvDTE80;  
    ```  
  
4.  在 TestOutput.cs，刪除 ShowMessageBox 方法。 新增下列方法 stub:  
  
    ```c#  
    private void OutputCommandHandler(object sender, EventArgs e) { }  
    ```  
  
5.  TestOutput 建構函式中變為 OutputCommandHandler 中的命令處理常式。 以下是將命令的部分:  
  
    ```c#  
    OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService; if (commandService != null) { CommandID menuCommandID = new CommandID(MenuGroup, CommandId); EventHandler eventHandler = OutputCommandHandler; MenuCommand menuItem = new MenuCommand(eventHandler, menuCommandID); commandService.AddCommand(menuItem); }  
    ```  
  
6.  下列各節會有不同的方法，顯示不同的方式處理 \[輸出\] 窗格。 您可以呼叫這些方法來 OutputCommandHandler\(\) 方法的主體。 例如，下列程式碼加入 CreatePane\(\) 方法下, 一節中所指定。  
  
    ```c#  
    private void OutputCommandHandler(object sender, EventArgs e) { CreatePane(new Guid(), "Created Pane", true, false); }  
    ```  
  
## 使用 IVsOutputWindow 建立輸出視窗  
 這個範例示範如何建立新 **輸出** 視窗窗格使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> 介面。  
  
```c#  
void CreatePane(Guid paneGuid, string title, bool visible, bool clearWithSolution) { IVsOutputWindow output = (IVsOutputWindow)GetService(typeof(SVsOutputWindow)); IVsOutputWindowPane pane; // Create a new pane. output.CreatePane( ref paneGuid, title, Convert.ToInt32(visible), Convert.ToInt32(clearWithSolution)); // Retrieve the new pane. output.GetPane(ref paneGuid, out pane); pane.OutputString("This is the Created Pane \n"); }  
```  
  
 如果您將此方法加入至當您按一下 \[上一節中，指定擴充 **叫用 TestOutput** 命令您應該會看到 **輸出** \] 視窗中顯示的標頭 **顯示輸出來源: CreatedPane** 和文字 **這是 \[建立\] 窗格** 本身的窗格中。  
  
## 使用 OutputWindow 建立輸出視窗  
 這個範例示範如何建立 **輸出** 視窗窗格使用 <xref:EnvDTE.OutputWindow> 物件。  
  
```c#  
void CreatePane(string title) { DTE2 dte = (DTE2)GetService(typeof(DTE)); OutputWindowPanes panes = dte.ToolWindows.OutputWindow.OutputWindowPanes; try { // If the pane exists already, write to it. panes.Item(title); } catch (ArgumentException) { // Create a new pane and write to it. return panes.Add(title); } }  
```  
  
 雖然 <xref:EnvDTE.OutputWindowPanes> 集合可讓您擷取 **輸出** 視窗窗格中的依其標題，窗格標題並非都是唯一的。 當您懷疑是否不重複的項目的時，使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow.GetPane%2A> 方法來擷取 \[正確\] 窗格中的透過其 GUID。  
  
 如果您將此方法加入至當您按一下 \[上一節中，指定擴充 **叫用 TestOutput** 命令，您應該會看到 \[輸出\] 視窗，以指出標頭 **顯示輸出來源: DTEPane** 和文字 **加入 DTE 窗格** 本身的窗格中。  
  
## 刪除輸出視窗  
 這個範例示範如何刪除 **輸出** 視窗窗格。  
  
```c#  
void DeletePane(Guid paneGuid) { IVsOutputWindow output = (IVsOutputWindow)ServiceProvider.GetService(typeof(SVsOutputWindow)); IVsOutputWindowPane pane; output.GetPane(ref paneGuid, out pane); if (pane == null) { CreatePane(paneGuid, "New Pane\n", true, true); } else { output.DeletePane(ref paneGuid); } }  
```  
  
 如果您將此方法加入至當您按一下 \[上一節中，指定擴充 **叫用 TestOutput** 命令，您應該會看到 \[輸出\] 視窗，以指出標頭 **顯示輸出來源: 新窗格** 和文字 **加入建立窗格** 本身的窗格中。 如果您按一下 **叫用 TestOutput** 命令同樣地，刪除 \[\] 窗格。  
  
## 取得輸出\] 視窗的 \[一般\] 窗格  
 這個範例示範如何取得內建 **一般** 窗格 **輸出** 視窗。  
  
```c#  
void GetGeneralPane() { return (IVsOutputWindowPane)GetService( typeof(SVsGeneralOutputWindowPane)); }  
```  
  
 如果您將此方法加入至當您按一下 \[上一節中，指定擴充 **叫用 TestOutput** 命令，您應該會看到 **輸出** \] 視窗會顯示幾個字 **找到 \[一般\] 窗格** 在窗格中。  
  
## 取得輸出\] 視窗的 \[建置\] 窗格  
 這個範例示範如何尋找 \[建置\] 窗格和寫入檔案。 依預設是不會啟動 \[組建\] 窗格中，因為它會啟動它也。  
  
```c#  
void OutputTaskItemStringExExample(string buildMessage) { EnvDTE80.DTE2 dte = (EnvDTE80.DTE2)ServiceProvider.GetService(typeof(EnvDTE.DTE)); EnvDTE.OutputWindowPanes panes = dte.ToolWindows.OutputWindow.OutputWindowPanes; foreach (EnvDTE.OutputWindowPane pane in panes) { if (pane.Name.Contains("Build")) { pane.OutputString(buildMessage + "\n"); pane.Activate(); return; } } }  
```