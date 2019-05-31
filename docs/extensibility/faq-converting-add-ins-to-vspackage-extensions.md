---
title: 常見問題集：將增益集轉換成 VSPackage 擴充功能 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 3a01d333-6e31-423f-ae06-5091a4fcb7a9
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9e40d9b7ca3d942a78ef9045bc7aaa5d0f7ea74d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66342659"
---
# <a name="faq-converting-add-ins-to-vspackage-extensions"></a>常見問題集：將增益集轉換成 VSPackage 擴充功能
增益集目前已被取代。 若要讓新的 Visual Studio 擴充功能，您需要建立 VSIX 擴充功能。 以下是一些有關如何將轉換的 Visual Studio 增益集，為 VSIX 擴充功能的常見問題集問題的答案。

> [!WARNING]
> 對於 C# 和 Visual Basic 專案，開始在 Visual Studio 2015 中，您就可以使用 VSIX 專案，並加入功能表命令、 工具視窗和 Vspackage 的項目範本。 如需詳細資訊，請參閱 <<c0> [ 的新功能 Visual Studio 2015 SDK](../extensibility/what-s-new-in-the-visual-studio-2015-sdk.md)。

> [!IMPORTANT]
> 在許多情況下您可以只傳輸您的增益集程式碼加入 VSIX 專案 VSPackage 專案項目。 在 <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> 方法中呼叫 <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>，可以取得 DTE 自動化物件。
>
> ```csharp
> DTE2 dte = (DTE2)GetService(typeof(DTE));
> ```
>
> 如需詳細資訊，請參閱 <<c0> [ 如何執行增益集程式碼在 VSPackage 中？](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md#BKMK_RunAddin)如下。

## <a name="what-software-do-i-need-to-develop-vsix-extensions"></a>若要開發 VSIX 擴充功能是否需要哪些軟體？
 從 Visual Studio 2015 中，從下載中心取得未安裝 Visual Studio SDK。 包含為 Visual Studio 安裝程式的選用功能。 您也可以在稍後安裝 VS SDK。 如需詳細資訊，請參閱 <<c0> [ 安裝 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。

## <a name="wheres-the-extension-documentation"></a>延伸模組文件位於何處？
 開頭[開始開發 Visual Studio 擴充功能](../extensibility/starting-to-develop-visual-studio-extensions.md)。 MSDN 上的 VSSDK 延伸模組開發有關的其他文章如下一。

## <a name="can-i-convert-my-add-in-project-to-a-vsix-project"></a>我是否可以將我的增益集專案轉換加入 VSIX 專案？
 增益集專案無法轉換直接加入 VSIX 專案，因為在 VSIX 專案中使用的機制與增益集專案中的項目相同。 VSIX 專案範本，再加上正確的專案項目範本有許多可讓相當容易快速啟動且做為 VSIX 擴充功能執行的程式碼。

## <a name="BKMK_StartDeveloping"></a> 如何開始開發 VSIX 擴充功能？
 以下是讓具有功能表命令的 VSIX 的方式：

### <a name="to-make-a-vsix-extension-that-has-a-menu-command"></a>若要建立具有功能表命令的 VSIX 擴充功能

1. 建立 VSIX 專案。 (**檔案** > **新增** > **專案**，或型別**專案**在搜尋方塊中)。 在 **新的專案**對話方塊方塊中，展開**Visual C#**   > **擴充性**或**Visual Basic**  > **擴充性**，然後選取**VSIX 專案**。 將專案命名為**TestExtension**並為其指定的位置。

2. 新增**自訂命令**項目範本。 (以滑鼠右鍵按一下專案節點，在**方案總管**，然後選取**新增** > **新項目**。 在**加入新項目**] 對話方塊，其中一個視覺效果C#或 [Visual Basic 中，選取**擴充性**節點，然後選取**自訂命令**。)

3. 按下**F5**來建置和偵錯模式中執行專案。

   Visual Studio 的第二個執行個體隨即出現。 第二個執行個體稱為實驗執行個體，其設定可能與您正用來撰寫程式碼的 Visual Studio 執行個體的設定不同。 第一次執行實驗執行個體時，系統會要求您登入 VS Online 並指定佈景主題和設定檔。

   在 **工具**功能表上 （在實驗執行個體中） 您應該會看到名為按鈕**我的命令名稱**。 當您選擇此按鈕時，應該會出現一則訊息：**Inside TestVSPackagePackage.MenuItemCallback()** .

## <a name="BKMK_RunAddin"></a> 如何在 VSPackage 中執行我的增益集程式碼？

增益集程式碼通常以兩種方式之一執行：

- 由功能表命令觸發 (程式碼位於`IDTCommandTarget.Exec`方法。)

- 啟動時自動執行 (程式碼在 `OnConnection` 事件處理常式中。)

您可以在 VSPackage 中執行相同的動作。 以下是如何在回呼方法加入一些增益集程式碼：

### <a name="to-implement-a-menu-command-in-a-vspackage"></a>在 VSPackage 中實作功能表命令

1. 建立具有功能表命令的 VSPackage。 (如需詳細資訊，請參閱 <<c0> [ 建立具有功能表命令的延伸模組](../extensibility/creating-an-extension-with-a-menu-command.md)。)

2. 開啟包含 VSPackage 之定義的檔案。 (在 C# 專案中，它有 *\<您的專案名稱>Package.cs*。)

3. 將下列 `using` 陳述式加入檔案中：

   ```csharp
   using EnvDTE;
   using EnvDTE80;
   ```

4. 尋找 `MenuItemCallback` 方法。 加入 <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> 的呼叫以取得 <xref:EnvDTE80.DTE2> 物件：

   ```csharp
   DTE2 dte = (DTE2)GetService(typeof(DTE));
   ```

5. 在增益集的 `IDTCommandTarget.Exec` 方法中加入其具有的程式碼。 例如，以下是一些程式碼，加入新窗格**輸出**視窗和 [新增] 窗格中的列印"Some Text"。

   ```csharp
   private void MenuItemCallback(object sender, EventArgs e)
   {
       DTE2 dte = (DTE2) GetService(typeof(DTE));
       OutputWindow outputWindow = dte.ToolWindows.OutputWindow;

       OutputWindowPane outputWindowPane = outputWindow.OutputWindowPanes.Add("A New Pane");
       outputWindowPane.OutputString("Some Text");
   }

   ```

6. 建置並執行此專案。 按下**F5**或選取**開始**上**偵錯**工具列。 在 Visual Studio 中，實驗執行個體**工具**功能表應該會有一個按鈕名為**我的命令名稱**。 當您選擇此按鈕時，文字**Some Text**應該會出現在**輸出**視窗窗格。 (您可能必須開啟**輸出**視窗。)

   您也可以讓程式碼在啟動時執行。 不過，通常不鼓勵對 VSPackage 擴充功能採用這種方法。 如果有太多擴充功能在 Visual Studio 啟動時嘗試載入，開始時間可能會變得很長。 較佳的做法是只在符合部分條件 (如開啟方案) 時才自動載入 VSPackage。

   這項程序示範如何在方案開啟時自動載入的 VSPackage 中，執行增益集程式碼：

### <a name="to-autoload-a-vspackage"></a>自動載入 VSPackage

1. 建立 VSIX 專案與 Visual Studio Package 專案項目。 (如需執行這項操作的步驟，請參閱[如何開始開發的 VSIX 擴充功能？](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md#BKMK_StartDeveloping)。 只要加入**Visual Studio Package**改為專案項目。)將專案命名為 VSIX**命名為 TestAutoload**。

2. 開啟*TestAutoloadPackage.cs*。 尋找宣告套件類別的一行：

   ```csharp
   public sealed class <name of your package>Package : Package
   ```

3. 這一行上方是一組屬性。 加入此屬性：

   ```csharp
   [ProvideAutoLoad(UIContextGuids80.SolutionExists)]
   ```

4. 在 設定中斷點`Initialize()`方法，並開始偵錯 (**F5**)。

5. 在實驗執行個體中，開啟專案。 這時 VSPackage 應會載入，並且叫用您的中斷點。

   您可以使用 <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> 的欄位指定要在其中載入 VSPackage 的其他內容。 如需詳細資訊，請參閱 <<c0> [ 載入 Vspackage](../extensibility/loading-vspackages.md)。

## <a name="how-can-i-get-the-dte-object"></a>如何取得 DTE 物件？
 如果您的增益集沒有顯示 UI (例如，功能表命令、工具列按鈕或工具視窗)，只要從 VSPackage 取得 DTE 自動化物件，就可以依現狀使用您的程式碼。 方式如下：

### <a name="to-get-the-dte-object-from-a-vspackage"></a>從 VSPackage 取得 DTE 物件

1. 在 Visual Studio 封裝項目範本的 VSIX 專案，尋找 *\<專案名稱 > Package.cs*檔案。 這是從 <xref:Microsoft.VisualStudio.Shell.Package> 衍生的類別；它可以幫助您與 Visual Studio 互動。 在這個案例中，您會使用其 <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> 取得 <xref:EnvDTE80.DTE2> 物件。

2. 加入以下 `using` 陳述式：

   ```csharp
   using EnvDTE;
   using EnvDTE80;
   ```

3. 尋找 `Initialize` 方法。 這個方法可處理您在套件精靈中指定的命令。 加入 <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> 的呼叫以取得 DTE 物件：

   ```csharp
   DTE dte = (DTE)GetService(typeof(DTE));
   ```

   具有 <xref:EnvDTE.DTE> 自動化物件之後，您可以將其餘的增益集程式碼加入專案。 如果您需要 <xref:EnvDTE80.DTE2> 物件，可以執行相同動作。

## <a name="how-do-i-change-menu-commands-and-toolbar-buttons-in-my-add-in-to-the-vspackage-style"></a>如何將增益集中的功能表命令和工具列按鈕變更為 VSPackage 樣式？
 VSPackage 擴充功能使用 *.vsct*檔案以建立大部分的功能表命令、 工具列、 工具列按鈕和其他 UI。 **自訂命令**專案項目範本可讓您選擇上建立命令**工具**功能表。 如需詳細資訊，請參閱 <<c0> [ 建立具有功能表命令的延伸模組](../extensibility/creating-an-extension-with-a-menu-command.md)。

 如需詳細資訊 *.vsct*檔，請參閱[如何 Vspackage 加入使用者介面項目](../extensibility/internals/how-vspackages-add-user-interface-elements.md)。 如需示範如何使用的逐步解說 *.vsct*檔案以加入功能表項目、 工具列和工具列按鈕，請參閱[擴充功能表和命令](../extensibility/extending-menus-and-commands.md)。

## <a name="how-do-i-add-custom-tool-windows-in-the-vspackage-way"></a>如何以 VSPackage 方式加入自訂工具視窗？
 自訂工具視窗的專案項目範本可讓您建立工具視窗的選項。 如需有關這個專案項目範本的詳細資訊，請參閱 <<c0> [ 建立的擴充功能與工具視窗](../extensibility/creating-an-extension-with-a-tool-window.md)。 工具視窗的相關資訊，請參閱[擴充和自訂工具視窗](../extensibility/extending-and-customizing-tool-windows.md)並在其下方的文章特別[加入工具視窗](../extensibility/adding-a-tool-window.md)。

## <a name="how-do-i-manage-visual-studio-windows-in-the-vspackage-way"></a>如何以 VSPackage 方式管理 Visual Studio 視窗？
 如果您的增益集管理 Visual Studio 視窗，增益集程式碼應該能夠在 VSPackage 中運作。 例如，此程序示範如何將管理的程式碼加入**工作清單**到`MenuItemCallback`VSPackage 的方法。

#### <a name="to-insert-window-management-code-from-an-add-in-into-a-vspackage"></a>將視窗管理程式碼從增益集插入 VSPackage

1. 建立具有功能表命令，為 VSPackage[如何開始開發的 VSIX 擴充功能？](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md#BKMK_StartDeveloping)一節。

2. 開啟包含 VSPackage 之定義的檔案。 (在 C# 專案中，它有 *\<您的專案名稱>Package.cs*。)

3. 加入以下 `using` 陳述式：

    ```csharp
    using EnvDTE;
    using EnvDTE80;
    ```

4. 尋找 `MenuItemCallback` 方法。 加入 <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> 的呼叫以取得 <xref:EnvDTE80.DTE2> 物件：

    ```csharp
    DTE2 dte = (DTE2)GetService(typeof(DTE));
    ```

5. 從增益集加入程式碼。 例如，以下是將新工作加入一些程式碼**工作清單**，會列出許多工作，並再刪除一項工作。

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        DTE2 dte = (DTE2) GetService(typeof(DTE));

        TaskList tl = (TaskList)dte.ToolWindows.TaskList;
        askItem tlItem;

        // Add a couple of tasks to the Task List.
        tlItem = tl.TaskItems.Add(" ", " ", "Test task 1.",
            vsTaskPriority.vsTaskPriorityHigh, vsTaskIcon.vsTaskIconUser,
            true, "", 10, true, true);
        tlItem = tl.TaskItems.Add(" ", " ", "Test task 2.",
            vsTaskPriority.vsTaskPriorityLow, vsTaskIcon.vsTaskIconComment, true, "", 20, true,true);

        // List the total number of task list items after adding the new task items.
        System.Windows.Forms.MessageBox.Show("Task Item 1 description: "+tl.TaskItems.Item(2).Description);
        System.Windows.Forms.MessageBox.Show("Total number of task items: "+tl.TaskItems.Count);

        // Remove the second task item. The items list in reverse numeric order.
        System.Windows.Forms.MessageBox.Show("Deleting the second task item");
        tl.TaskItems.Item(2).Delete();
        System.Windows.Forms.MessageBox.Show("Total number of task items: "+tl.TaskItems.Count);
    }
    ```

## <a name="how-do-i-manage-projects-and-solutions-in-a-vspackage"></a>如何在 VSPackage 中管理專案和方案？
 如果您的增益集管理專案和方案，增益集程式碼應該能夠在 VSPackage 中運作。 例如，這項程序示範如何加入可取得啟動專案的程式碼。

1. 建立具有功能表命令，為 VSPackage[如何開始開發的 VSIX 擴充功能？](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md#BKMK_StartDeveloping)一節。

2. 開啟包含 VSPackage 之定義的檔案。 (在 C# 專案中，它有 *\<您的專案名稱>Package.cs*。)

3. 加入以下 `using` 陳述式：

    ```csharp
    using EnvDTE;
    using EnvDTE80;
    ```

4. 尋找 `MenuItemCallback` 方法。 加入 <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> 的呼叫以取得 <xref:EnvDTE80.DTE2> 物件：

    ```csharp
    DTE2 dte = (DTE2)GetService(typeof(DTE));
    ```

5. 從增益集加入程式碼。 例如，以下程式碼會取得方案中啟動專案的名稱。 (此套件執行時，多專案方案必須已開啟。)

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        DTE2 dte = (DTE2) GetService(typeof(DTE));

        SolutionBuild2 sb = (SolutionBuild2)dte.Solution.SolutionBuild;
        Project startupProj;
        string msg = "";

        foreach (String item in (Array)sb.StartupProjects)
        {
            msg += item;
        }
        System.Windows.Forms.MessageBox.Show("Solution startup Project: "+msg);
        startupProj = dte.Solution.Item(msg);
        System.Windows.Forms.MessageBox.Show("Full name of solution's startup project: "+"/n"+startupProj.FullName);
    }
    ```

## <a name="how-do-i-set-keyboard-shortcuts-in-a-vspackage"></a>如何在 VSPackage 中設定鍵盤快速鍵？
 您使用`<KeyBindings>`項目 *.vsct*檔案。 在下列範例中，此命令的鍵盤快速鍵`idCommand1`已**Alt**+**A**，和命令的鍵盤快速鍵`idCommand2`是**Alt** + **Ctrl**+**A**。 請注意按鍵名稱的語法。

```xml
<KeyBindings>
    <KeyBinding guid="MyProjectCmdSet" id="idCommand1" editor="guidVSStd97" key1="A" mod1="ALT" />
    <KeyBinding guid="MyProjectCmdSet" id="idCommand2" editor="guidVSStd97" key1="A" mod1="CONTROL" mod2="ALT" />
</KeyBindings>
```

## <a name="how-do-i-handle-automation-events-in-a-vspackage"></a>如何在 VSPackage 中處理自動化事件？
 在 VSPackage 中處理自動化事件的方式與在增益集中的方式相同。 下列程式碼將示範如何處理 `OnItemRenamed` 事件。 (這個範例假設您已經取得 DTE 物件。)

```csharp
Events2 dteEvents = (Events2)dte.Events;
dteEvents.ProjectItemsEvents.ItemRenamed += listener1.OnItemRenamed;
. . .
public void OnItemRenamed(EnvDTE.ProjectItem projItem, string oldName)
{
    string s = "[Event] Renamed " + oldName + " to " + Path.GetFileName(projItem.get_FileNames(1) + " in project " + projItem.ContainingProject.Name;
}
```