---
title: 管理通用 Windows 專案 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 47926aa1-3b41-410d-bca8-f77fc950cbe7
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e542d1cc53fbdfb287d004c15b2a9055d3a0cba1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72647953"
---
# <a name="manage-universal-windows-projects"></a>管理通用 Windows 專案

通用 Windows 應用程式是以 Windows 8.1 和 Windows Phone 8.1 為目標的應用程式，可讓開發人員在這兩個平臺上使用程式碼和其他資產。 共用的程式碼和資源會保留在共用專案中，而平臺專屬的程式碼和資源會保存在個別的專案中，一個用於 Windows，另一個用於 Windows Phone。 如需通用 Windows 應用程式的詳細資訊，請參閱[通用 windows 應用程式](https://msdn.microsoft.com/library/windows/apps/dn609832.aspx)。 管理專案的 Visual Studio 擴充功能應該要注意，通用 Windows 應用程式專案的結構與單一平臺應用程式不同。 本逐步解說會示範如何流覽共用專案和管理共用專案。

## <a name="prerequisites"></a>Prerequisites

從 Visual Studio 2015 開始，您不會從下載中心安裝 Visual Studio SDK。 它在 Visual Studio 安裝程式中包含為選擇性功能。 您稍後也可以安裝 VS SDK。 如需詳細資訊，請參閱[安裝 VISUAL STUDIO SDK](../extensibility/installing-the-visual-studio-sdk.md)。

### <a name="navigate-the-shared-project"></a>流覽共用專案

1. 建立名C#為**TestUniversalProject**的 VSIX 專案。 （**檔案** > **新**的  > **專案**， **C#** 然後 ** >  擴充**性  > **Visual Studio 套件**）。 加入**自訂命令**專案專案範本（在**方案總管**上，以滑鼠右鍵按一下專案節點，然後選取 [**加入** > **新專案**]，然後移至 [擴充性 **]）。** 將檔案命名為**TestUniversalProject**。

2. 在 [擴充功能] 區段中，新增 VisualStudio 的參考。 *DesignTime .dll*和 VisualStudio. *DesignTime. dll* （在 [**延伸**模組] 區段中）。

3. 開啟*TestUniversalProject.cs* ，並新增下列 `using` 指示詞：

    ```csharp
    using EnvDTE;
    using EnvDTE80;
    using Microsoft.VisualStudio;
    using Microsoft.VisualStudio.PlatformUI;
    using Microsoft.Internal.VisualStudio.PlatformUI;
    using System.Collections.Generic;
    using System.IO;
    using System.Windows.Forms;
    ```

4. 在 `TestUniversalProject` 類別中，新增指向 [**輸出**] 視窗的私用欄位。

    ```csharp
    public sealed class TestUniversalProject
    {
        IVsOutputWindowPane output;
    . . .
    }
    ```

5. 在 TestUniversalProject 的函式內設定輸出窗格的參考：

    ```csharp
    private TestUniversalProject(Package package)
    {
        if (package == null)
        {
            throw new ArgumentNullException("package");
        }

        this.package = package;

        OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;
        if (commandService != null)
        {
            CommandID menuCommandID = new CommandID(MenuGroup, CommandId);
            EventHandler eventHandler = this.ShowMessageBox;
            MenuCommand menuItem = new MenuCommand(eventHandler, menuCommandID);
            commandService.AddCommand(menuItem);
        }
        // get a reference to the Output window
                    output = (IVsOutputWindowPane)ServiceProvider.GetService(typeof(SVsGeneralOutputWindowPane));
    }
    ```

6. 從 `ShowMessageBox` 方法中移除現有的程式碼：

    ```csharp
    private void ShowMessageBox(object sender, EventArgs e)
    {
    }
    ```

7. 取得 DTE 物件，我們將在本逐步解說中用於數個不同的用途。 此外，請確定在按一下功能表按鈕時，已載入解決方案。

    ```csharp
    private void ShowMessageBox(object sender, EventArgs e)
    {
        var dte = (EnvDTE.DTE)this.ServiceProvider.GetService(typeof(EnvDTE.DTE));
        if (dte.Solution != null)
        {
            . . .
        }
        else
        {
            MessageBox.Show("No solution is open");
            return;
        }
    }
    ```

8. 尋找共用的專案。 共用的專案是純容器;它不會建立或產生輸出。 下列方法會尋找具有共用專案功能的 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> 物件，以在方案中找到第一個共用的專案。

    ```csharp
    private IVsHierarchy FindSharedProject()
    {
        var sln = (IVsSolution)this.ServiceProvider.GetService(typeof(SVsSolution));
        Guid empty = Guid.Empty;
        IEnumHierarchies enumHiers;

        //get all the projects in the solution
        ErrorHandler.ThrowOnFailure(sln.GetProjectEnum((uint)__VSENUMPROJFLAGS.EPF_LOADEDINSOLUTION, ref empty, out enumHiers));
        foreach (IVsHierarchy hier in ComUtilities.EnumerableFrom(enumHiers))
        {
            if (PackageUtilities.IsCapabilityMatch(hier, "SharedAssetsProject"))
            {
                return hier;
            }
        }
        return null;
    }
    ```

9. 在 [`ShowMessageBox`] 方法中，輸出共用專案的標題（出現在**方案總管**中的專案名稱）。

    ```csharp
    private void ShowMessageBox(object sender, EventArgs e)
    {
        var dte = (DTE)this.ServiceProvider.GetService(typeof(DTE));

        if (dte.Solution != null)
        {
            var sharedHier = this.FindSharedProject();
            if (sharedHier != null)
            {
                string sharedCaption = HierarchyUtilities.GetHierarchyProperty<string>(sharedHier, (uint)VSConstants.VSITEMID.Root,
                     (int)__VSHPROPID.VSHPROPID_Caption);
                output.OutputStringThreadSafe(string.Format("Found shared project: {0}\n", sharedCaption));
            }
            else
            {
                MessageBox.Show("Solution has no shared project");
                return;
            }
                }
        else
        {
            MessageBox.Show("No solution is open");
            return;
        }
    }
    ```

10. 取得使用中的平臺專案。 平臺專案是包含平臺特定程式碼和資源的專案。 下列方法會使用新的欄位 <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID7.VSHPROPID_SharedItemContextHierarchy> 來取得作用中的平臺專案。

    ```csharp
    private IVsHierarchy GetActiveProjectContext(IVsHierarchy hierarchy)
    {
        IVsHierarchy activeProjectContext;
        if (HierarchyUtilities.TryGetHierarchyProperty(hierarchy, (uint)VSConstants.VSITEMID.Root,
             (int)__VSHPROPID7.VSHPROPID_SharedItemContextHierarchy, out activeProjectContext))
        {
            return activeProjectContext;
        }
        else
        {
            return null;
        }
    }
    ```

11. 在 `ShowMessageBox` 方法中，輸出作用中平臺專案的標題。

    ```csharp
    private void ShowMessageBox(object sender, EventArgs e)
    {
        var dte = (DTE)this.ServiceProvider.GetService(typeof(DTE));

        if (dte.Solution != null)
        {
            var sharedHier = this.FindSharedProject();
            if (sharedHier != null)
            {
                string sharedCaption = HierarchyUtilities.GetHierarchyProperty<string>(sharedHier, (uint)VSConstants.VSITEMID.Root,
                     (int)__VSHPROPID.VSHPROPID_Caption);
                output.OutputStringThreadSafe(string.Format("Shared project: {0}\n", sharedCaption));

                var activePlatformHier = this.GetActiveProjectContext(sharedHier);
                if (activePlatformHier != null)
                {
                    string activeCaption = HierarchyUtilities.GetHierarchyProperty<string>(activePlatformHier,
                         (uint)VSConstants.VSITEMID.Root, (int)__VSHPROPID.VSHPROPID_Caption);
                    output.OutputStringThreadSafe(string.Format("Active platform project: {0}\n", activeCaption));
                }
                else
                {
                MessageBox.Show("Shared project has no active platform project");
                }
            }
            else
            {
                MessageBox.Show("Solution has no shared project");
                return;
            }
        }
        else
            {
                MessageBox.Show("No solution is open");
                return;
            }
        }
    }
    ```

12. 逐一查看平臺專案。 下列方法會從共用專案取得所有匯入（平臺）專案。

    ```csharp
    private IEnumerable<IVsHierarchy> EnumImportingProjects(IVsHierarchy hierarchy)
    {
        IVsSharedAssetsProject sharedAssetsProject;
        if (HierarchyUtilities.TryGetHierarchyProperty(hierarchy, (uint)VSConstants.VSITEMID.Root,
            (int)__VSHPROPID7.VSHPROPID_SharedAssetsProject, out sharedAssetsProject)
            && sharedAssetsProject != null)
        {
            foreach (IVsHierarchy importingProject in sharedAssetsProject.EnumImportingProjects())
            {
                yield return importingProject;
            }
        }
    }
    ```

    > [!IMPORTANT]
    > 如果使用者已在實驗實例C++中開啟通用 Windows 應用程式專案，上述程式碼就會擲回例外狀況。 這是已知的問題。 若要避免例外狀況，請將上述的 `foreach` 區塊取代為下列內容：

    ```csharp
    var importingProjects = sharedAssetsProject.EnumImportingProjects();
    for (int i = 0; i < importingProjects.Count; ++i)
    {
        yield return importingProjects[i];
    }
    ```

13. 在 `ShowMessageBox` 方法中，輸出每個平臺專案的標題。 在輸出作用中平臺專案標題的行之後，插入下列程式碼。 只有載入的平臺專案才會出現在此清單中。

    ```csharp
    output.OutputStringThreadSafe("Platform projects:\n");

    IEnumerable<IVsHierarchy> projects = this.EnumImportingProjects(sharedHier);

    bool isActiveProjectSet = false;
    foreach (IVsHierarchy platformHier in projects)
    {
        string platformCaption = HierarchyUtilities.GetHierarchyProperty<string>(platformHier, (uint)VSConstants.VSITEMID.Root,
            (int)__VSHPROPID.VSHPROPID_Caption);
        output.OutputStringThreadSafe(string.Format(" * {0}\n", platformCaption));
    }
    ```

14. 變更使用中的平臺專案。 下列方法會使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetProperty%2A> 設定作用中的專案。

    ```csharp
    private int SetActiveProjectContext(IVsHierarchy hierarchy, IVsHierarchy activeProjectContext)
    {
        return hierarchy.SetProperty((uint)VSConstants.VSITEMID.Root, (int)__VSHPROPID7.VSHPROPID_SharedItemContextHierarchy, activeProjectContext);
    }
    ```

15. 在 `ShowMessageBox` 方法中，變更作用中的平臺專案。 將此程式碼插入 `foreach` 區塊內。

    ```csharp
    bool isActiveProjectSet = false;
    string platformCaption = null;
    foreach (IVsHierarchy platformHier in projects)
    {
        platformCaption = HierarchyUtilities.GetHierarchyProperty<string>(platformHier, (uint)VSConstants.VSITEMID.Root,
             (int)__VSHPROPID.VSHPROPID_Caption);
        output.OutputStringThreadSafe(string.Format(" * {0}\n", platformCaption));

        // if this project is neither the shared project nor the current active platform project,
        // set it to be the active project
        if (!isActiveProjectSet && platformHier != activePlatformHier)
        {
            this.SetActiveProjectContext(sharedHier, platformHier);
            activePlatformHier = platformHier;
            isActiveProjectSet = true;
        }
    }
    output.OutputStringThreadSafe("set active project: " + platformCaption +'\n');
    ```

16. 現在就試試看。按 F5 啟動實驗實例。 在實驗C#性實例中建立通用中樞應用程式專案（在 [**新增專案**] 對話方塊中， **Visual C#**   > **windows**  > **windows 8**  > **通用**0**中樞應用程式**）。 載入方案之後，移至 [**工具**] 功能表並按一下 [叫用**TestUniversalProject**]，然後檢查 [**輸出**] 窗格中的文字。 您應該會看到類似下列的畫面：

    ```
    Found shared project: HubApp.Shared
    The active platform project: HubApp.Windows
    Platform projects:
     * HubApp.Windows
     * HubApp.WindowsPhone
    set active project: HubApp.WindowsPhone
    ```

### <a name="manage-the-shared-items-in-the-platform-project"></a>管理平臺專案中的共用專案

1. 尋找平臺專案中的共用專案。 共用專案中的專案會顯示在平臺專案中做為共用專案。 您在**方案總管**中看不到它們，但是您可以逐步進行專案階層來尋找它們。 下列方法會引導階層，並收集所有共用專案。 它會選擇性地輸出每個專案的標題。 共用的專案是由 <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID7.VSHPROPID_IsSharedItem> 的新屬性所識別。

    ```csharp
    private void InspectHierarchyItems(IVsHierarchy hier, uint itemid, int level, List<uint> itemIds, bool getSharedItems, bool printItems)
    {
        string caption = HierarchyUtilities.GetHierarchyProperty<string>(hier, itemid, (int)__VSHPROPID.VSHPROPID_Caption);
        if (printItems)
            output.OutputStringThreadSafe(string.Format("{0}{1}\n", new string('\t', level), caption));

        // if getSharedItems is true, inspect only shared items; if it's false, inspect only unshared items
        bool isSharedItem;
        if (HierarchyUtilities.TryGetHierarchyProperty(hier, itemid, (int)__VSHPROPID7.VSHPROPID_IsSharedItem, out isSharedItem)
            && (isSharedItem == getSharedItems))
        {
            itemIds.Add(itemid);
        }

        uint child;
        if (HierarchyUtilities.TryGetHierarchyProperty(hier, itemid, (int)__VSHPROPID.VSHPROPID_FirstChild, Unbox.AsUInt32, out child)
            && child != (uint)VSConstants.VSITEMID.Nil)
        {
            this.InspectHierarchyItems(hier, child, level + 1, itemIds, isSharedItem, printItems);

            while (HierarchyUtilities.TryGetHierarchyProperty(hier, child, (int)__VSHPROPID.VSHPROPID_NextSibling, Unbox.AsUInt32, out child)
                && child != (uint)VSConstants.VSITEMID.Nil)
            {
                this.InspectHierarchyItems(hier, child, level + 1, itemIds, isSharedItem, printItems);
            }
                    }
    }
    ```

2. 在 `ShowMessageBox` 方法中，加入下列程式碼來逐步執行平臺專案階層專案。 將它插入 `foreach` 區塊內。

    ```csharp
    output.OutputStringThreadSafe("Walk the active platform project:\n");
    var sharedItemIds = new List<uint>();
    this.InspectHierarchyItems(activePlatformHier, (uint)VSConstants.VSITEMID.Root, 1, sharedItemIds, true, true);
    ```

3. 讀取共用專案。 共用專案在平臺專案中會顯示為隱藏連結檔案，而且您可以將所有屬性讀取為一般連結檔案。 下列程式碼會讀取第一個共用專案的完整路徑。

    ```csharp
    var sharedItemId = sharedItemIds[0];
    string fullPath;
    ErrorHandler.ThrowOnFailure(((IVsProject)activePlatformHier).GetMkDocument(sharedItemId, out fullPath));
    output.OutputStringThreadSafe(string.Format("Shared item full path: {0}\n", fullPath));
    ```

4. 現在就試試看。按**F5**啟動實驗實例。 在實驗C#性實例中建立通用中樞應用程式專案（在 [**新增專案**] 對話方塊中， **Visual C#**   > **windows**  > **windows 8**  > **通用**0**中樞應用程式**）移至 [**工具**] 功能表並按一下 [叫用**TestUniversalProject**]，然後檢查 [**輸出**] 窗格中的文字。 您應該會看到類似下列的畫面：

    ```
    Found shared project: HubApp.Shared
    The active platform project: HubApp.Windows
    Platform projects:
     * HubApp.Windows
     * HubApp.WindowsPhone
    set active project: HubApp.WindowsPhone
    Walk the active platform project:
        HubApp.WindowsPhone
            <HubApp.Shared>
                App.xaml
                    App.xaml.cs
                Assets
                    DarkGray.png
                    LightGray.png
                    MediumGray.png
                Common
                    NavigationHelper.cs
                    ObservableDictionary.cs
                    RelayCommand.cs
                    SuspensionManager.cs
                DataModel
                    SampleData.json
                    SampleDataSource.cs
                HubApp.Shared.projitems
                Strings
                    en-US
                        Resources.resw
            Assets
                HubBackground.theme-dark.png
                HubBackground.theme-light.png
                Logo.scale-240.png
                SmallLogo.scale-240.png
                SplashScreen.scale-240.png
                Square71x71Logo.scale-240.png
                StoreLogo.scale-240.png
                WideLogo.scale-240.png
            HubPage.xaml
                HubPage.xaml.cs
            ItemPage.xaml
                ItemPage.xaml.cs
            Package.appxmanifest
            Properties
                AssemblyInfo.cs
            References
                .NET for Windows Store apps
                HubApp.Shared
                Windows Phone 8.1
            SectionPage.xaml
                SectionPage.xaml.cs
    ```

### <a name="detect-changes-in-platform-projects-and-shared-projects"></a>偵測平臺專案和共用專案中的變更

1. 您可以使用階層和專案事件來偵測共用專案中的變更，就像您針對平臺專案所做的一樣。 不過，不會顯示共用專案中的專案專案，這表示當共用專案專案變更時，不會引發特定事件。

    當專案中的檔案重新命名時，請考慮事件的順序：

   1. 檔案名已在磁片上變更。

   2. 專案檔會更新，以包含檔案的新名稱。

      階層事件（例如 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents>）通常會追蹤 UI 中顯示的變更，如**方案總管**中所示。 階層事件會考慮檔案重新命名作業，以包含檔案刪除，然後是新增檔案。 不過，當不可見的專案變更時，階層事件系統就會引發 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> 事件，而不是 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A> 事件。 因此，如果您在平臺專案中重新命名檔案，就會同時取得 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> 和 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A>，但如果您重新命名共用專案中的檔案，則只會取得 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A>。

      若要追蹤專案專案中的變更，您可以處理 DTE 專案專案事件（在 <xref:EnvDTE.ProjectItemsEventsClass> 中找到）。 不過，如果您要處理大量的事件，您可以在 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> 中取得更佳的效能處理事件。 在此逐步解說中，我們只會顯示階層事件和 DTE 事件。 在這個程式中，您會將事件接聽程式加入至共用專案和平臺專案。 然後，當您重新命名共用專案中的一個檔案和平臺專案中的另一個檔案時，您可以看到每個重新命名作業所引發的事件。

      在這個程式中，您會將事件接聽程式加入至共用專案和平臺專案。 然後，當您重新命名共用專案中的一個檔案和平臺專案中的另一個檔案時，您可以看到每個重新命名作業所引發的事件。

2. 加入事件接聽程式。 將新的類別檔案新增至專案，並呼叫它*HierarchyEventListener.cs*。

3. 開啟*HierarchyEventListener.cs*檔案，並新增下列 using 指示詞：

   ```csharp
   using Microsoft.VisualStudio.Shell.Interop;
   using Microsoft.VisualStudio;
   using System.IO;
   ```

4. 讓 `HierarchyEventListener` 類別執行 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents>：

   ```csharp
   class HierarchyEventListener : IVsHierarchyEvents
   { }
   ```

5. 執行 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents> 的成員，如下列程式碼所示。

   ```csharp
   class HierarchyEventListener : IVsHierarchyEvents
   {
       private IVsHierarchy hierarchy;
       IVsOutputWindowPane output;

       internal HierarchyEventListener(IVsHierarchy hierarchy, IVsOutputWindowPane outputWindow) {
            this.hierarchy = hierarchy;
            this.output = outputWindow;
       }

       int IVsHierarchyEvents.OnInvalidateIcon(IntPtr hIcon) {
           return VSConstants.S_OK;
       }

       int IVsHierarchyEvents.OnInvalidateItems(uint itemIDParent) {
           return VSConstants.S_OK;
       }

       int IVsHierarchyEvents.OnItemAdded(uint itemIDParent, uint itemIDSiblingPrev, uint itemIDAdded) {
           output.OutputStringThreadSafe("IVsHierarchyEvents.OnItemAdded: " + itemIDAdded + "\n");
           return VSConstants.S_OK;
       }

       int IVsHierarchyEvents.OnItemDeleted(uint itemID) {
           output.OutputStringThreadSafe("IVsHierarchyEvents.OnItemDeleted: " + itemID + "\n");
           return VSConstants.S_OK;
       }

       int IVsHierarchyEvents.OnItemsAppended(uint itemIDParent) {
           output.OutputStringThreadSafe("IVsHierarchyEvents.OnItemsAppended\n");
           return VSConstants.S_OK;
       }

       int IVsHierarchyEvents.OnPropertyChanged(uint itemID, int propID, uint flags) {
           output.OutputStringThreadSafe("IVsHierarchyEvents.OnPropertyChanged: item ID " + itemID + "\n");
           return VSConstants.S_OK;
       }
   }
   ```

6. 在相同的類別中，新增 DTE 事件 <xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed> 的另一個事件處理常式，這會在專案專案重新命名時發生。

   ```csharp
   public void OnItemRenamed(EnvDTE.ProjectItem projItem, string oldName)
   {
       output.OutputStringThreadSafe(string.Format("[Event] Renamed {0} to {1} in project {2}\n",
            oldName, Path.GetFileName(projItem.get_FileNames(1)), projItem.ContainingProject.Name));
   }
   ```

7. 註冊階層事件。 您必須分別針對您要追蹤的每個專案註冊。 在 `ShowMessageBox` 中新增下列程式碼，一個用於共用專案，另一個用於其中一個平臺專案。

   ```csharp
   // hook up the event listener for hierarchy events on the shared project
   HierarchyEventListener listener1 = new HierarchyEventListener(sharedHier, output);
   uint cookie1;
   sharedHier.AdviseHierarchyEvents(listener1, out cookie1);

   // hook up the event listener for hierarchy events on the
   active project
   HierarchyEventListener listener2 = new HierarchyEventListener(activePlatformHier, output);
   uint cookie2;
   activePlatformHier.AdviseHierarchyEvents(listener2, out cookie2);
   ```

8. 註冊 DTE 專案專案事件 <xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed>。 連結第二個接聽程式之後，請新增下列程式碼。

   ```csharp
   // hook up DTE events for project items
   Events2 dteEvents = (Events2)dte.Events;
   dteEvents.ProjectItemsEvents.ItemRenamed += listener1.OnItemRenamed;
   ```

9. 修改共用專案。 您無法修改平臺專案中的共用專案;相反地，您必須在這兩個專案的實際擁有者共用專案中修改它們。 您可以使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.IsDocumentInProject%2A> 取得共用專案中對應的專案識別碼，並為其提供共用專案的完整路徑。 然後您就可以修改共用專案。 變更會傳播至平臺專案。

    > [!IMPORTANT]
    > 在修改專案專案之前，您應該先找出它是否為共用專案。

     下列方法會修改專案專案檔的名稱。

    ```csharp
    private void ModifyFileNameInProject(IVsHierarchy project, string path)
    {
        int found;
        uint projectItemID;
        VSDOCUMENTPRIORITY[] priority = new VSDOCUMENTPRIORITY[1];
        if (ErrorHandler.Succeeded(((IVsProject)project).IsDocumentInProject(path, out found, priority, out projectItemID))
            && found != 0)
        {
            var name = DateTime.Now.Ticks.ToString() + Path.GetExtension(path);
            project.SetProperty(projectItemID, (int)__VSHPROPID.VSHPROPID_EditLabel, name);
            output.OutputStringThreadSafe(string.Format("Renamed {0} to {1}\n", path,name));
        }
    }
    ```

10. 在 `ShowMessageBox` 中的所有其他程式碼之後，呼叫這個方法，以修改共用專案中的專案檔案名。 在取得共用專案中專案的完整路徑的程式碼後面插入這個。

    ```csharp
    // change the file name of an item in a shared project
    this.InspectHierarchyItems(activePlatformHier, (uint)VSConstants.VSITEMID.Root, 1, sharedItemIds, true, true);
    ErrorHandler.ThrowOnFailure(((IVsProject)activePlatformHier).GetMkDocument(sharedItemId, out fullPath));
    output.OutputStringThreadSafe(string.Format("Shared project item ID = {0}, full path = {1}\n", sharedItemId, fullPath));
    this.ModifyFileNameInProject(sharedHier, fullPath);
    ```

11. 建置並執行專案。 在實驗C#實例中建立通用中樞應用程式，移至 [**工具**] 功能表並按一下 [叫用**TestUniversalProject**]，然後檢查 [一般輸出] 窗格中的文字。 共用專案中第一個專案的名稱（我們預期它是*app.xaml*檔案）應該變更，您應該會看到 <xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed> 事件已引發。 在此情況下，因為重新命名*應用程式。 xaml*也會造成*App.xaml.cs*重新命名，您應該會看到四個事件（每個平臺專案兩個）。 （DTE 事件不會追蹤共用專案中的專案）。您應該會看到兩個 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> 事件（每個平臺專案一個），但沒有任何 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A> 事件。

12. 現在嘗試在平臺專案中重新命名檔案，您可以在引發的事件中看到差異。 在呼叫 `ModifyFileName` 之後，在 `ShowMessageBox` 中新增下列程式碼。

    ```csharp
    // change the file name of an item in a platform project
    var unsharedItemIds = new List<uint>();
    this.InspectHierarchyItems(activePlatformHier, (uint)VSConstants.VSITEMID.Root, 1, unsharedItemIds, false, false);

    var unsharedItemId = unsharedItemIds[0];
    string unsharedPath;
    ErrorHandler.ThrowOnFailure(((IVsProject)activePlatformHier).GetMkDocument(unsharedItemId, out unsharedPath));
    output.OutputStringThreadSafe(string.Format("Platform project item ID = {0}, full path = {1}\n", unsharedItemId, unsharedPath));

    this.ModifyFileNameInProject(activePlatformHier, unsharedPath);
    ```

13. 建置並執行專案。 在實驗C#實例中建立通用專案，移至 [**工具**] 功能表並按一下 [叫用**TestUniversalProject**]，然後檢查 [一般輸出] 窗格中的文字。 重新命名平臺專案中的檔案之後，您應該會看到 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A> 事件和 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> 事件。 由於變更檔案不會造成其他檔案變更，而且由於平臺專案中專案的變更不會傳播到任何位置，因此每個事件只有一個。
