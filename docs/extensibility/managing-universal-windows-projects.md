---
title: 管理通用 Windows 專案 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 47926aa1-3b41-410d-bca8-f77fc950cbe7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fbbf9b6aaf983bb36291611a7b9b50f7886915b7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702691"
---
# <a name="manage-universal-windows-projects"></a>管理通用 Windows 專案

通用 Windows 應用是面向 Windows 8.1 和 Windows Phone 8.1 的應用,允許開發人員在這兩個平臺上使用代碼和其他資產。 共用代碼和資源保存在共用專案中,而特定於平臺的代碼和資源保存在單獨的專案中,一個用於 Windows,另一個用於 Windows Phone。 有關通用 Windows 應用程式的詳細資訊,請參閱[通用 Windows 應用](https://msdn.microsoft.com/library/windows/apps/dn609832.aspx)。 管理專案的 Visual Studio 擴充應注意,通用 Windows 應用專案的結構不同於單平臺應用。 本演練將介紹如何導航共用專案和管理共用專案。

## <a name="prerequisites"></a>Prerequisites

從 Visual Studio 2015 開始,您不會從下載中心安裝 Visual Studio SDK。 它作為可選功能包含在可視化工作室設置中。 以後還可以安裝 VS SDK。 有關詳細資訊,請參閱[安裝可視化工作室 SDK](../extensibility/installing-the-visual-studio-sdk.md)。

### <a name="navigate-the-shared-project"></a>瀏覽分享專案

1. 創建名為**TestUniversal 專案的**C# VSIX 專案。 (**檔案** > **新項目** > **Project**,然後**C#** > **擴展可視化** > **工作室包**)。 添加**自定義命令**專案項範本(在**解決方案資源管理員**上,右鍵單擊專案節點並選擇 **'添加新** > **項**』,然後轉到 **"擴充性**"。。 命名檔案**TestUniversalProject**。

2. 添加對*Microsoft.VisualStudio.shell.Interop.12.1.DesignTime.dll*和*Microsoft.VisualStudio.shell.Interop.14.0.DesignTime.dll*的引用(在**擴展部分**)。

3. 開啟*TestUniversalProject.cs*並`using`新增以下 指令:

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

4. 在類`TestUniversalProject`中添加指向 **「輸出」** 視窗的專用欄位。

    ```csharp
    public sealed class TestUniversalProject
    {
        IVsOutputWindowPane output;
    . . .
    }
    ```

5. 在 TestUniversalProject 建構函式中設定對輸出窗格的參考:

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

6. 從`ShowMessageBox`方法中移除現有代碼:

    ```csharp
    private void ShowMessageBox(object sender, EventArgs e)
    {
    }
    ```

7. 獲取 DTE 物件,在本演練中,我們將用於幾個不同的用途。 此外,請確保在單擊功能表按鈕時載入解決方案。

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

8. 查找共享專案。 共享專案是一個純容器;它不生成或生成輸出。 以下方法通過查找具有共用專案功能<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>的物件來查找解決方案中的第一個共用專案。

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

9. 在`ShowMessageBox`方法中,輸出共用項目的標題(出現在**解決方案資源管理員**中的專案名稱)。

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

10. 獲取活動平台專案。 平臺專案是包含特定於平臺的代碼和資源的專案。 以下方法使用新欄位<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID7.VSHPROPID_SharedItemContextHierarchy>獲取活動平台專案。

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

11. 在`ShowMessageBox`該方法中,輸出活動平臺項目的標題。

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

12. 反覆運算平台專案。 以下方法從共用項目獲取所有導入(平臺)專案。

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
    > 如果使用者已在實驗實例中打開了C++通用 Windows 應用專案,則上述代碼將引發異常。 這是已知的問題。 為避免出現異常,請將上面`foreach`的塊替換為以下內容:

    ```csharp
    var importingProjects = sharedAssetsProject.EnumImportingProjects();
    for (int i = 0; i < importingProjects.Count; ++i)
    {
        yield return importingProjects[i];
    }
    ```

13. 在`ShowMessageBox`該方法中,輸出每個平臺項目的標題。 在輸出活動平台項目標題的行後插入以下代碼。 只有載入的平台專案才會顯示在此清單中。

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

14. 更改活動平台專案。 以下方法使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetProperty%2A>設置活動專案。

    ```csharp
    private int SetActiveProjectContext(IVsHierarchy hierarchy, IVsHierarchy activeProjectContext)
    {
        return hierarchy.SetProperty((uint)VSConstants.VSITEMID.Root, (int)__VSHPROPID7.VSHPROPID_SharedItemContextHierarchy, activeProjectContext);
    }
    ```

15. 在`ShowMessageBox`方法中,更改活動平台專案。 在`foreach`塊內插入此代碼。

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

16. 現在試試看。按 F5 啟動實驗實例。 在實驗實例中創建 C# 通用中心應用專案(在 **"新專案**"對話框中 **,Visual C++** > **Windows** > **8** > **通用** > **中心應用**)。 載入解決方案後,轉到 **「工具」** 選單並按一下 **「調用測試通用專案**」,然後檢查 **「輸出」** 窗格中的文字。 您應該會看到如下的內容：

    ```
    Found shared project: HubApp.Shared
    The active platform project: HubApp.Windows
    Platform projects:
     * HubApp.Windows
     * HubApp.WindowsPhone
    set active project: HubApp.WindowsPhone
    ```

### <a name="manage-the-shared-items-in-the-platform-project"></a>管理平台專案中的分享專案

1. 查找平臺專案中的共享專案。 共用專案中的專案在平臺項目中顯示為共用專案。 在**解決方案資源管理器**中看不到它們,但可以遍歷專案層次結構來查找它們。 以下方法遍走層次結構並收集所有共用項。 它可以選擇輸出每個項目的標題。 共用項由新屬性<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID7.VSHPROPID_IsSharedItem>標識。

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

2. 在`ShowMessageBox`方法中,添加以下代碼以遍歷平台專案層次結構項。 將插入區塊`foreach`內 。

    ```csharp
    output.OutputStringThreadSafe("Walk the active platform project:\n");
    var sharedItemIds = new List<uint>();
    this.InspectHierarchyItems(activePlatformHier, (uint)VSConstants.VSITEMID.Root, 1, sharedItemIds, true, true);
    ```

3. 閱讀共用專案。 分享專案在平台項目中顯示為隱藏連結檔,您可以將所有屬性讀為普通連結檔。 以下代碼讀取第一個共用項的完整路徑。

    ```csharp
    var sharedItemId = sharedItemIds[0];
    string fullPath;
    ErrorHandler.ThrowOnFailure(((IVsProject)activePlatformHier).GetMkDocument(sharedItemId, out fullPath));
    output.OutputStringThreadSafe(string.Format("Shared item full path: {0}\n", fullPath));
    ```

4. 現在試試看。按**F5**啟動實驗實例。 在實驗實例中建立 C# 通用中心應用專案(在 **"新專案**"對話框中 **,Visual C++** > **Windows** > **8** > **通用** > **中心應用**)轉到 **「工具」** 選單並按下 **「調用測試通用專案**」,然後選中 **「輸出**」窗格中的文本。 您應該會看到如下的內容：

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

### <a name="detect-changes-in-platform-projects-and-shared-projects"></a>偵測平台項目與共享項目中變更

1. 您可以使用層次結構和專案事件來檢測共用專案中的更改,就像對平臺項目一樣。 但是,共用專案中的專案項不可見,這意味著當更改共用專案項時,某些事件不會觸發。

    在重新命名項目中的檔案時,請考慮事件序列:

   1. 檔名在磁碟上更改。

   2. 專案檔將更新以包括該檔的新名稱。

      層次結構事件(例如<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents>),通常追蹤 UI 中顯示的更改,如**解決方案資源管理器**中所示。 層次結構事件考慮檔重新命名操作,以包括檔刪除,然後添加檔。 但是,當更改不可見項時,層次結構事件系統將觸發事件<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A>,但不會觸<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A>發 事件。 因此,如果在平台項目中重新命名檔案,則取得與<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A><xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A>,但如果重新命名共享專案中的檔案,則僅<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A>獲取 。

      要追蹤專案項目中的更改,可以處理 DTE 專案項目(中找到<xref:EnvDTE.ProjectItemsEventsClass>的項目)。 但是,如果您正在處理大量事件,則可以在中<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>處理事件時獲得更好的性能。 在本演練中,我們僅顯示層次結構事件和 DTE 事件。 在此過程中,您將事件偵聽器添加到共用專案和平台專案。 然後,當您重新命名共享專案中的一個檔和平台專案中的另一個檔時,您可以看到為每個重新命名操作觸發的事件。

      在此過程中,您將事件偵聽器添加到共用專案和平台專案。 然後,當您重新命名共享專案中的一個檔和平台專案中的另一個檔時,您可以看到為每個重新命名操作觸發的事件。

2. 添加事件偵聽器。 新增新類別檔,並將其呼叫*HierarchyEventListener.cs*。

3. 開啟*HierarchyEventListener.cs*檔案並新增以下使用指令:

   ```csharp
   using Microsoft.VisualStudio.Shell.Interop;
   using Microsoft.VisualStudio;
   using System.IO;
   ```

4. 具有類別`HierarchyEventListener`<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents>:

   ```csharp
   class HierarchyEventListener : IVsHierarchyEvents
   { }
   ```

5. 實現的成員<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents>,如下代碼所示。

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

6. 在同一類中為 DTE<xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed>事件 添加另一個事件處理程式 ,每當重命名專案項時都會發生這種情況。

   ```csharp
   public void OnItemRenamed(EnvDTE.ProjectItem projItem, string oldName)
   {
       output.OutputStringThreadSafe(string.Format("[Event] Renamed {0} to {1} in project {2}\n",
            oldName, Path.GetFileName(projItem.get_FileNames(1)), projItem.ContainingProject.Name));
   }
   ```

7. 註冊層次結構事件。 您需要為正在追蹤的每個項目分別註冊。 在`ShowMessageBox`中 添加以下代碼 ,一個用於共用專案,另一個用於其中一個平台專案。

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

8. 註冊 DTE 項目<xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed>項目 。 掛接第二個偵聽器後,添加以下代碼。

   ```csharp
   // hook up DTE events for project items
   Events2 dteEvents = (Events2)dte.Events;
   dteEvents.ProjectItemsEvents.ItemRenamed += listener1.OnItemRenamed;
   ```

9. 修改共用項。 不能修改平台專案中的共享專案;但是,您可以修改平臺專案中的共用專案。相反,您必須在共用專案中修改它們,這些共用專案是這些項目的實際擁有者。 您可以在共用<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.IsDocumentInProject%2A>項目中獲取相應的專案 ID,從而提供共用項的完整路徑。 然後,您可以修改共用項。 更改將傳播到平台專案。

    > [!IMPORTANT]
    > 在修改專案項之前,應先瞭解專案項是否為共用項。

     以下方法修改項目項檔的名稱。

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

10. 在中的所有其他代碼之後`ShowMessageBox`調用此方法,以修改共用專案中的專案的檔名。 在獲取共享項目中專案的完整路徑的代碼后插入此項。

    ```csharp
    // change the file name of an item in a shared project
    this.InspectHierarchyItems(activePlatformHier, (uint)VSConstants.VSITEMID.Root, 1, sharedItemIds, true, true);
    ErrorHandler.ThrowOnFailure(((IVsProject)activePlatformHier).GetMkDocument(sharedItemId, out fullPath));
    output.OutputStringThreadSafe(string.Format("Shared project item ID = {0}, full path = {1}\n", sharedItemId, fullPath));
    this.ModifyFileNameInProject(sharedHier, fullPath);
    ```

11. 建置並執行專案。 在實驗實例中創建 C# 通用集線器應用,轉到 **「工具」** 選單並按一下 **「調用測試通用專案**」,然後檢查常規輸出窗格中的文本。 應更改共享專案中第一個專案的名稱(我們預計它是*App.xaml*檔),您<xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed>應該看到 事件已觸發。 在這種情況下,由於重命名*App.xaml*也會導致*App.xaml.cs*重新命名,因此應看到四個事件(每個平台專案有兩個事件)。 (DTE 事件不跟蹤共用專案中的專案。您應該看到兩<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A>個事件(每個平台專案一個),但<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A>沒有事件。

12. 現在嘗試重新命名平台專案中的檔案,您可以看到觸發事件的差異。 在呼叫`ShowMessageBox`後`ModifyFileName`將 以下代碼加入 。

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

13. 建置並執行專案。 在實驗實例中建立 C# 通用項目,轉到 **「工具」** 選單並單擊 **「調用測試通用專案**」,然後檢查常規輸出窗格中的文本。 重新命名平台項目中的檔案後,應同時看到<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A>事件和<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A>事件。 由於更改檔不會更改其他檔,並且對平臺專案中項的更改不會在任何地方傳播,因此每個事件只有一個。
