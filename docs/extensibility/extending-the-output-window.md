---
title: 延伸輸出視窗 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Output window, about Output window
ms.assetid: b02fa88c-f92a-4ff6-ba5f-2eb4d48a643a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 800b443b079111d1d09fffdd900b246a020578f4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711648"
---
# <a name="extend-the-output-window"></a>延伸輸出視窗
**輸出**視窗是一組讀/寫文字窗格。 Visual Studio 具有這些內置窗格 **:Build**,其中專案會傳達有關生成的消息,[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]在 **「一般」** 中 ,它們傳達有關 IDE 的消息。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>專案透過介面方法自動獲得對 **「生成**」窗格的引用,Visual Studio 提供透過<xref:Microsoft.VisualStudio.Shell.Interop.SVsGeneralOutputWindowPane>服務直接存**取「一般**」窗格。 除了內置窗格之外,您還可以創建和管理自己的自定義窗格。

 您可以<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow>通過<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane>和介面直接控制**輸出**視窗。 <xref:Microsoft.VisualStudio.Shell.Interop.SVsOutputWindow>服務<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow>提供的介面定義用於創建、檢索和銷毀**輸出**視窗窗格的方法。 該<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane>介面定義用於顯示窗格、隱藏窗格和操作其文本的方法。 控制**輸出**視窗的另一種方法是透過 Visual <xref:EnvDTE.OutputWindow> <xref:EnvDTE.OutputWindowPane>Studio 自動化物件模型中 的和 物件。 這些對象幾乎封裝<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow>了<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane>和介面的所有功能。 此外,<xref:EnvDTE.OutputWindow><xref:EnvDTE.OutputWindowPane>和物件添加了一些更高級別的功能,以便更輕鬆地枚舉 **「輸出**」視窗窗格並從窗格中檢索文本。

## <a name="create-an-extension-that-uses-the-output-pane"></a>建立使用輸出表格的延伸
 可以進行擴展,以練習"輸出"窗格的不同方面。

1. 建立`TestOutput`一個 VSIX 專案,該專案名為 **「測試輸出**」的功能表命令。 關於詳細資訊,請參閱[使用選單指令建立延伸](../extensibility/creating-an-extension-with-a-menu-command.md)。

2. 加入下列參考：

    1. EnvDTE

    2. EnvDTE80

3. 在*TestOutput.cs*中,加入以下使用敘述:

    ```f#
    using EnvDTE;
    using EnvDTE80;
    ```

4. 在*TestOutput.cs*`ShowMessageBox`,刪除方法。 新增以下方法存根:

    ```csharp
    private void OutputCommandHandler(object sender, EventArgs e)
    {
    }
    ```

5. 在測試輸出建構函數中,將命令處理程式更改為「輸出命令處理程式」。 下面是新增命令的部分:

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

6. 以下各節具有不同的方法,這些方法顯示了處理"輸出"窗格的不同方法。 可以將這些方法呼叫方法的主體`OutputCommandHandler()`。 例如,以下代碼添加下一`CreatePane()`節中給出的方法。

    ```csharp
    private void OutputCommandHandler(object sender, EventArgs e)
    {
        CreatePane(new Guid(), "Created Pane", true, false);
    }
    ```

## <a name="create-an-output-window-with-ivsoutputwindow"></a>使用 IV 輸出視窗建立輸出視窗
 此範例展示如何使用介面建立新的<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow>**「輸出**」視窗窗格。

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

 如果將此方法添加到上一節中給出的擴展中,則按下 **「調用測試輸出」** 命令時,應看到 **「輸出」** 視窗,該視窗的標題顯示 **:「已創建窗格」** 和「**這是窗格本身中創建窗格」** 字樣。

## <a name="create-an-output-window-with-outputwindow"></a>使用輸出視窗建立輸出視窗
 此範例展示如何使用<xref:EnvDTE.OutputWindow>物件建立**輸出**視窗窗格。

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

 儘管<xref:EnvDTE.OutputWindowPanes>集合允許您按其標題檢索 **「輸出**」視窗窗格,但窗格標題不保證是唯一的。 當您懷疑標題的唯一性時,<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow.GetPane%2A>請使用 方法按其 GUID 檢索正確的窗格。

 如果將此方法新增到上一節中所選取的延伸中,則按下 **「調用測試輸出」** 指令時,應看到「輸出」視窗,該視窗的標題顯示**輸出:DTEPane**和窗格本身**中添加的 DTE 窗格**。

## <a name="delete-an-output-window"></a>移除輸出視窗
 此範例簡報如何刪除 **「輸出」** 視窗窗格。

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

 如果將此方法添加到上一節中給出的擴展中,則按下 **「調用測試輸出」** 命令時,應看到「輸出」視窗,該視窗的標題顯示 **:「新窗格**」和窗格本身中**添加的「已創建窗格」** 字樣。 如果再次按**下 「調用測試輸出」** 命令,窗格將被刪除。

## <a name="get-the-general-pane-of-the-output-window"></a>取得輸出視窗的「一般」 窗格
 此範例展示如何獲取 **「輸出」** 視窗的內建**一般**窗格。

```csharp
IVsOutputWindowPane GetGeneralPane()
{
    return (IVsOutputWindowPane)GetService(
        typeof(SVsGeneralOutputWindowPane));
}
```

 如果將此方法加入到上一個項目中所選取的延伸項目,則按下 **「調用測試輸出」** 指令時,應看到 **「輸出」** 視窗在窗格中顯示單字 **「找到一般」 的窗格**。

## <a name="get-the-build-pane-of-the-output-window"></a>取得輸出「輸出」視窗的產生窗格
 此示例演示如何查找**生成**窗格並將其寫入該窗格。 由於默認情況下不會啟動 **「生成**」窗格,因此還會啟動它。

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
