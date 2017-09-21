---
title: "管理通用 Windows 專案 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 47926aa1-3b41-410d-bca8-f77fc950cbe7
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# 管理通用 Windows 專案
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

通用 Windows 應用程式是以 Windows 8.1 和 Windows Phone 8.1，讓開發人員可以使用程式碼和其他資產兩種平台為目標的應用程式。 共用程式碼和資源會保留在共用專案中，雖然平台特定程式碼和資源會保留在不同的專案，一個用於 Windows，另一個則用於 Windows Phone。 如需通用 Windows 應用程式的詳細資訊，請參閱 [通用 Windows 應用程式](http://msdn.microsoft.com/library/windows/apps/dn609832.aspx)。 管理專案的 visual Studio 擴充功能應該注意通用 Windows 應用程式專案會有不同於單一平台應用程式的結構。 本逐步解說會示範如何瀏覽共用的專案和管理共用的項目。  
  
## 必要條件  
 啟動 Visual Studio 2015 中，您未安裝 Visual Studio SDK 從 「 下載中心 」。 它是 Visual Studio 安裝程式的選用功能。 您也可以在稍後安裝 VS SDK。 如需詳細資訊，請參閱[安裝 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
### 瀏覽共用的專案  
  
1.  建立 C\# VSIX 專案，名為 **TestUniversalProject**。 \(**檔案\]、 \[新增\]、 \[專案** 然後 **C\# 中，擴充性，Visual Studio 套件**\)。 新增 **自訂命令** 專案項目範本 \(在 \[方案總管\] 中，以滑鼠右鍵按一下專案節點，然後選取 **加入 \/ 新的項目**, ，然後移至 **擴充性**\)。 將檔案命名 **TestUniversalProject**。  
  
2.  新增 Microsoft.VisualStudio.Shell.Interop.12.1.DesignTime.dll 和 Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime.dll 的參考 \(在 **延伸** 一節\)。  
  
3.  開啟 TestUniversalProject.cs，並新增下列 `using` 陳述式︰  
  
    ```c#  
    using EnvDTE;  
    using EnvDTE80;  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.PlatformUI;  
    using Microsoft.Internal.VisualStudio.PlatformUI;   
    using System.Collections.Generic;   
    using System.IO;  
    using System.Windows.Forms;  
    ```  
  
4.  TestUniversalProject 類別中新增私用欄位，指向 **輸出** 視窗。  
  
    ```c#  
    public sealed class TestUniversalProject   
    {  
        IVsOutputWindowPane output;  
    . . .  
    }  
    ```  
  
5.  設定 TestUniversalProject 建構函式內的 \[輸出\] 窗格的參考︰  
  
    ```c#  
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
  
6.  移除現有的程式碼從 `ShowMessageBox` 方法︰  
  
    ```c#  
    private void ShowMessageBox(object sender, EventArgs e)   
    {  
    }  
    ```  
  
7.  取得 DTE 物件，我們會將數個不同的用途，在此逐步解說。 此外，確保載入方案，按一下 \[功能表\] 按鈕時。  
  
    ```c#  
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
  
8.  尋找共用的專案。 共用的專案是純粹的容器。它不會建立或產生的輸出。 下列方法尋找方案中尋找第一個共用的專案 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> 共用的專案匯入功能的物件。  
  
    ```c#  
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
  
9. 在 `ShowMessageBox` 方法，輸出標題 \(專案名稱，會出現在 **方案總管\] 中**\) 的共用專案。  
  
    ```c#  
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
  
10. 取得作用中平台專案。 平台專案會包含平台特定程式碼和資源的專案。 下列方法會使用新的欄位 <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID7> 取得作用中平台專案。  
  
    ```c#  
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
  
11. 在 `ShowMessageBox` 方法，輸出作用中平台專案的標題。  
  
    ```c#  
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
  
    ```  
  
12. 逐一查看平台專案。 下列方法取得從共用專案的所有匯入 （平台） 的專案。  
  
    ```c#  
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
    >  如果使用者在實驗執行個體中開啟 c \+ \+ 的通用 Windows 應用程式專案，上面的程式碼會擲回例外狀況。 這是已知的問題。 若要避免此例外狀況，取代 `foreach` 封鎖上述取代為下列︰  
  
    ```c#  
    var importingProjects = sharedAssetsProject.EnumImportingProjects();  
    for (int i = 0; i < importingProjects.Count; ++i)  
    {  
        yield return importingProjects[i];  
    }   
    ```  
  
13. 在 `ShowMessageBox` 方法，輸出每個平台專案的標題。 輸出標題的作用中平台專案的行之後插入下列程式碼。 只有平台專案載入會出現在這份清單。  
  
    ```c#  
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
  
14. 變更使用中的平台專案。 下列方法會設定使用中的專案使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetProperty%2A>。  
  
    ```c#  
    private int SetActiveProjectContext(IVsHierarchy hierarchy, IVsHierarchy activeProjectContext)  
    {  
        return hierarchy.SetProperty((uint)VSConstants.VSITEMID.Root, (int)__VSHPROPID7.VSHPROPID_SharedItemContextHierarchy, activeProjectContext);  
    }  
    ```  
  
15. 在 `ShowMessageBox` 方法中，變更使用中的平台專案。 插入這個程式碼 `foreach` 區塊。  
  
    ```c#  
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
  
16. 現在試試看。 按 f5 鍵啟動實驗執行個體。 建立 C\# 通用集線器應用程式專案中的實驗執行個體 \(在 **新的專案** 對話方塊中， **Visual C\# \/ Windows \/ Windows 8 \/ 通用 \/ 中樞應用程式**\)。 載入方案之後，請移至 **工具** 功能表，然後按一下 **叫用 TestUniversalProject**, ，然後將文字簽入 **輸出** 窗格。 您應該會看到類似下列畫面︰  
  
    ```  
    Found shared project: HubApp.Shared  
    The active platform project: HubApp.Windows  
    Platform projects:  
     * HubApp.Windows  
     * HubApp.WindowsPhone  
    set active project: HubApp.WindowsPhone  
    ```  
  
### 管理平台專案中共用的項目  
  
1.  平台專案中尋找共用的項目。 共用專案中的項目出現在平台專案中做為共用的項目。 您無法看到它們在 **方案總管\] 中**, ，但您可以逐步專案階層架構，以找出它們。 下列方法瀏覽階層，並收集所有共用的項目。 （選擇性），它會輸出每個項目的標題。 共用的項目由新屬性所識別 <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID7>。  
  
    ```c#  
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
  
2.  在 `ShowMessageBox` 方法中，加入下列程式碼，逐步平台專案的階層項目。 將其內部插入 `foreach` 區塊。  
  
    ```c#  
    output.OutputStringThreadSafe("Walk the active platform project:\n");  
    var sharedItemIds = new List<uint>();  
    this.InspectHierarchyItems(activePlatformHier, (uint)VSConstants.VSITEMID.Root, 1, sharedItemIds, true, true);  
    ```  
  
3.  讀取共用的項目。 平台專案共用項目顯示為隱藏的連結檔案，而且您可以讀取檔案一般連結的所有屬性。 下列程式碼會讀取第一個共用項目的完整路徑。  
  
    ```c#  
    var sharedItemId = sharedItemIds[0];  
    string fullPath;  
    ErrorHandler.ThrowOnFailure(((IVsProject)activePlatformHier).GetMkDocument(sharedItemId, out fullPath));  
    output.OutputStringThreadSafe(string.Format("Shared item full path: {0}\n", fullPath));  
    ```  
  
4.  現在試試看。 按 f5 鍵啟動實驗執行個體。 實驗執行個體中建立 C\# 通用中樞應用程式專案 \(在 **新的專案** \] 對話方塊的 \[ **Visual C\# \/ Windows \/ Windows 8 \/ 通用 \/ 中樞應用程式**\) 移至 **工具** 功能表，然後按一下 **叫用 TestUniversalProject**, ，然後簽入的文字 **輸出** 窗格。 您應該會看到類似下列畫面︰  
  
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
  
### 平台專案和共用的專案中偵測變更  
  
1.  如同您平台專案，您可以使用階層和專案事件在共用專案中，偵測變更。 不過，在共用專案中的專案項目不是可見的這表示共用的專案項目變更時，並不會引發特定事件。  
  
     請考慮重新命名專案中的檔案時的事件順序︰  
  
    1.  檔案名稱會變更磁碟上。  
  
    2.  專案檔會更新以包含新檔案的名稱。  
  
     階層事件 \(例如， <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents>\) 通常會顯示在 UI 中，以在變更追蹤 **方案總管\] 中**。 階層事件，請考慮刪除檔案然後再將檔案加入包含檔案重新命名作業。 不過，不可見的項目變更時，階層事件系統會引發 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> 事件，但不是 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A> 事件。 因此，如果您重新命名平台專案中的檔案，您取得這兩個 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> 和 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A>, ，但如果您重新命名共用專案中的檔案，就只有 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A>。  
  
     若要追蹤專案項目中的變更，您可以處理 DTE 專案項目事件 \(在中找到的 <xref:EnvDTE.ProjectItemsEventsClass>\)。 不過，如果您要處理大量的事件，您可以取得更佳的效能，處理中的事件 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>。 在本逐步解說示範階層事件和 DTE 事件。 在此程序中，您可以加入事件接聽程式共用的專案，並使用平台專案。 然後，當您重新命名共用專案中的一個檔案與另一個平台專案中的檔案，您可以看到每個重新命名作業會引發的事件。  
  
     在此程序中，您可以加入事件接聽程式共用的專案，並使用平台專案。 然後，當您重新命名共用專案中的一個檔案與另一個平台專案中的檔案，您可以看到每個重新命名作業會引發的事件。  
  
2.  加入事件接聽程式。 將新的類別檔案加入至專案，並呼叫 HierarchyEventListener.cs。  
  
3.  開啟 HierarchyEventListener.cs 檔案並新增下列 using 陳述式︰  
  
    ```c#  
    using Microsoft.VisualStudio.Shell.Interop;  
    using Microsoft.VisualStudio;  
    using System.IO;  
  
    ```  
  
4.  有 `HierarchyEventListener` 類別實作 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents>:  
  
    ```c#  
    class HierarchyEventListener : IVsHierarchyEvents  
    { }  
  
    ```  
  
5.  實作的成員 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents>, ，如下列程式碼。  
  
    ```c#  
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
  
6.  相同類別中加入另一個事件處理常式 DTE 事件 <xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed>, ，發生於每當重新命名專案項目時。  
  
    ```c#  
    public void OnItemRenamed(EnvDTE.ProjectItem projItem, string oldName)  
    {  
        output.OutputStringThreadSafe(string.Format("[Event] Renamed {0} to {1} in project {2}\n",  
             oldName, Path.GetFileName(projItem.get_FileNames(1)), projItem.ContainingProject.Name));  
    }  
    ```  
  
7.  註冊階層事件。 您必須註冊個別追蹤每個專案。 加入下列程式碼中的 `ShowMessageBox`, ，一個用於共用的專案中，而另一個則用於其中一個平台專案。  
  
    ```c#  
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
  
8.  申請 DTE 專案項目事件 <xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed>。 您連接的第二個接聽程式之後，請加入下列程式碼。  
  
    ```c#  
    // hook up DTE events for project items  
    Events2 dteEvents = (Events2)dte.Events;  
    dteEvents.ProjectItemsEvents.ItemRenamed += listener1.OnItemRenamed;  
  
    ```  
  
9. 修改共用的項目。 您無法修改共用的項目中的平台專案。相反地，您必須在實際的擁有者，這些項目之共用專案中修改它們。 您可以在共用專案中以取得對應的項目 ID <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.IsDocumentInProject%2A>, ，並賦予它共用項目的完整路徑。 然後您可以修改共用的項目。 變更會傳播到平台專案。  
  
    > [!IMPORTANT]
    >  您應該了解專案項目是不會修改之前，就是共用的項目。  
  
     下列方法修改專案項目檔案的名稱。  
  
    ```c#  
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
  
10. 在所有其他程式碼中的呼叫這個方法 `ShowMessageBox` 若要修改的檔案名稱的共用專案中的項目。 取得項目的完整路徑在共用專案中的程式碼後插入此內容。  
  
    ```c#  
    // change the file name of an item in a shared project  
    this.InspectHierarchyItems(activePlatformHier, (uint)VSConstants.VSITEMID.Root, 1, sharedItemIds, true, true);  
    ErrorHandler.ThrowOnFailure(((IVsProject)activePlatformHier).GetMkDocument(sharedItemId, out fullPath));   
    output.OutputStringThreadSafe(string.Format("Shared project item ID = {0}, full path = {1}\n", sharedItemId, fullPath));  
    this.ModifyFileNameInProject(sharedHier, fullPath);  
    ```  
  
11. 建置並執行專案。 在實驗執行個體中建立 C\# 通用中樞應用程式，請移至 **工具** 功能表，然後按一下 **叫用 TestUniversalProject**, ，並檢查一般輸出窗格中的文字。 第一個項目共用的名稱 （我們預期 App.xaml 檔案） 的專案應該會變更，而且您應該會看到 <xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed> 引發事件。 在此情況下，由於重新命名 App.xaml 會 App.xaml.cs 也要重新命名，您應該會看到四個事件 （針對每個平台專案的兩個）。 （DTE 事件進行追蹤共用的專案中的項目）。 您應該會看到兩個 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> 事件 （一個用於每個平台專案），但不是 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A> 事件。  
  
12. 現在，請嘗試重新命名在平台專案中，檔案，您可以看到所引發的事件中的差異。 加入下列程式碼中的 `ShowMessageBox` 呼叫之後 `ModifyFileName`。  
  
    ```c#  
    // change the file name of an item in a platform project  
    var unsharedItemIds = new List<uint>();  
    this.InspectHierarchyItems(activePlatformHier, (uint)VSConstants.VSITEMID.Root, 1, unsharedItemIds, false, false);  
  
    var unsharedItemId = unsharedItemIds[0];  
    string unsharedPath;  
    ErrorHandler.ThrowOnFailure(((IVsProject)activePlatformHier).GetMkDocument(unsharedItemId, out unsharedPath));  
    output.OutputStringThreadSafe(string.Format("Platform project item ID = {0}, full path = {1}\n", unsharedItemId, unsharedPath));  
  
    this.ModifyFileNameInProject(activePlatformHier, unsharedPath);  
    ```  
  
13. 建置並執行專案。 建立 C\# 通用專案中的實驗執行個體，請移至 **工具** 功能表，然後按一下 **叫用 TestUniversalProject**, ，並檢查一般輸出窗格中的文字。 平台專案中的檔案已重新命名之後，您應該看到兩個 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A> 事件和 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> 事件。 之後變更檔案造成的變更，沒有其他檔案，而且平台專案中的項目變更不在任何地方取得傳播，因為沒有只有其中每個這些事件。