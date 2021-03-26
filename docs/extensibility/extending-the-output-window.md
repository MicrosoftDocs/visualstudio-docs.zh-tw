---
title: 擴充輸出視窗 |Microsoft Docs
description: 瞭解如何在 Visual Studio SDK 中擴充輸出視窗，以及如何建立和管理您自己的自訂窗格。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Output window, about Output window
ms.assetid: b02fa88c-f92a-4ff6-ba5f-2eb4d48a643a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: cf875d070d27d307380f23e71af2bda7c4a205b5
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105075025"
---
# <a name="extend-the-output-window"></a>擴充輸出視窗
[ **輸出** ] 視窗是一組讀取/寫入文字窗格。 Visual Studio 具有下列內建窗格： **Build**，其中的專案會傳達有關組建的訊息，而 **一般** 會傳達 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 有關 IDE 的訊息。 專案會透過介面方法自動取得 **組建** 窗格的參考 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> ，而 Visual Studio 可透過服務直接存取 [ **一般** ] 窗格 <xref:Microsoft.VisualStudio.Shell.Interop.SVsGeneralOutputWindowPane> 。 除了內建的窗格之外，您還可以建立和管理自己的自訂窗格。

 您可以直接透過和介面控制 **輸出** 視窗 <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> 。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow>服務所提供的介面 <xref:Microsoft.VisualStudio.Shell.Interop.SVsOutputWindow> ，會定義用來建立、取出和終結 **輸出** 視窗窗格的方法。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane>介面會定義方法來顯示窗格、隱藏窗格，以及操作其文字。 控制 **輸出** 視窗的另一種方式是透過 <xref:EnvDTE.OutputWindow> <xref:EnvDTE.OutputWindowPane> Visual Studio Automation 物件模型中的和物件。 這些物件幾乎會封裝和介面的所有功能 <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> 。 此外， <xref:EnvDTE.OutputWindow> 和物件也 <xref:EnvDTE.OutputWindowPane> 會加入一些較高層級的功能，讓您更輕鬆地列舉 **輸出** 視窗窗格，以及從窗格中取出文字。

## <a name="create-an-extension-that-uses-the-output-pane"></a>建立使用 [輸出] 窗格的延伸模組
 您可以進行延伸，以執行輸出窗格的不同層面。

1. `TestOutput`使用名為 **為 testoutput.txt** 的功能表命令來建立名為的 VSIX 專案。 如需詳細資訊，請參閱 [使用功能表命令建立延伸](../extensibility/creating-an-extension-with-a-menu-command.md)模組。

2. 加入下列參考：

    1. EnvDTE

    2. EnvDTE80

3. 在 *為 testoutput.txt* 中，新增下列 using 語句：

    ```f#
    using EnvDTE;
    using EnvDTE80;
    ```

4. 在 *為 testoutput.txt* 中刪除 `ShowMessageBox` 方法。 新增下列方法存根：

    ```csharp
    private void OutputCommandHandler(object sender, EventArgs e)
    {
    }
    ```

5. 在為 testoutput.txt 函式中，將命令處理常式變更為 OutputCommandHandler。 以下是新增命令的部分：

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

6. 下列各節具有不同的方法，這些方法會顯示處理輸出窗格的不同方式。 您可以將這些方法呼叫至方法的主體 `OutputCommandHandler()` 。 例如，下列程式碼會新增 `CreatePane()` 下一節中提供的方法。

    ```csharp
    private void OutputCommandHandler(object sender, EventArgs e)
    {
        CreatePane(new Guid(), "Created Pane", true, false);
    }
    ```

## <a name="create-an-output-window-with-ivsoutputwindow"></a>使用 IVsOutputWindow 建立輸出視窗
 這個範例示範如何使用介面建立新的 **輸出** 視窗窗格 <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> 。

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

 如果您將此方法新增到上一節中提供的擴充功能，則當您按一下 [叫用 **為 testoutput.txt** ] 命令時，應該會看到 [ **輸出** ] 視窗，其中包含標頭 **顯示 [顯示輸出來源： CreatedPane** ] 和 [ **這是窗格本身的已建立] 窗格** 。

## <a name="create-an-output-window-with-outputwindow"></a>使用 OutputWindow 建立輸出視窗
 這個範例示範如何使用物件來建立 **輸出** 視窗窗格 <xref:EnvDTE.OutputWindow> 。

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

 雖然 <xref:EnvDTE.OutputWindowPanes> 集合可讓您依標題取得 **輸出** 視窗窗格，但不保證窗格標題是唯一的。 當您不確定標題的唯一性時，請使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow.GetPane%2A> 方法，依 GUID 來取得正確的窗格。

 如果您將此方法新增至上一節中提供的擴充功能，則當您按一下 [叫用 **為 testoutput.txt** ] 命令時，應該會看到 [輸出] 視窗，其中包含標頭 **顯示 [顯示來源輸出來源： DTEPane** ] 和 [ **新增 DTE] 窗格** 的標題。

## <a name="delete-an-output-window"></a>刪除輸出視窗
 此範例顯示如何刪除 [ **輸出** 視窗] 窗格。

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

 如果您將此方法新增到上一節中提供的擴充功能，則當您按一下 [叫用 **為 testoutput.txt** ] 命令時，應該會看到 [輸出] 視窗，其中包含標頭 **顯示 [顯示輸出來源：新增] 窗格** ，而 [ **已建立** 的文字] 窗格會顯示在窗格中 如果您再次按一下 [叫用 **為 testoutput.txt** ] 命令，就會刪除窗格。

## <a name="get-the-general-pane-of-the-output-window"></a>取得輸出視窗的一般窗格
 這個範例會示範如何取得 **輸出** 視窗的內建 **一般** 窗格。

```csharp
IVsOutputWindowPane GetGeneralPane()
{
    return (IVsOutputWindowPane)GetService(
        typeof(SVsGeneralOutputWindowPane));
}
```

 如果您將此方法加入至上一節所提供的擴充功能，當您按一下 [叫用 **為 testoutput.txt** ] 命令時，您應該會看到 [ **輸出** ] 視窗顯示窗格中 [ **找到的一般] 窗格** 。

## <a name="get-the-build-pane-of-the-output-window"></a>取得輸出視窗的 [組建] 窗格
 此範例示範如何尋找 **組建** 窗格並加以寫入。 由於預設不會啟用 [ **組建** ] 窗格，因此它也會啟用。

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
