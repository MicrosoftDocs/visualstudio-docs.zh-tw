---
title: "管理通用 Windows 專案 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 47926aa1-3b41-410d-bca8-f77fc950cbe7
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6fdb3585d0b2bba5daf248707fa2848d3d32dfdb
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="managing-universal-windows-projects"></a>管理通用 Windows 專案
通用 Windows 應用程式是以 Windows 8.1 和 Windows Phone 8.1，允許開發人員可以使用兩個平台上的程式碼及其他資產為目標的應用程式。 共用程式碼和資源會保留在共用的專案，而平台專屬的程式碼和資源會保留於不同的專案，一個用於 Windows，另一個用於 Windows Phone。 如需通用 Windows 應用程式的詳細資訊，請參閱[通用 Windows 應用程式](http://msdn.microsoft.com/library/windows/apps/dn609832.aspx)。 管理專案的 visual Studio 擴充功能應該知道的通用 Windows app 專案具有不同於單一平台應用程式的結構。 本逐步解說將示範如何瀏覽共用的專案和管理共用的項目。  
  
## <a name="prerequisites"></a>必要條件  
 啟動 Visual Studio 2015 中，請勿從 「 下載中心 」 未安裝 Visual Studio SDK。 它是包含為 Visual Studio 安裝程式的選用功能。 您也可以在稍後安裝 VS SDK。 如需詳細資訊，請參閱[安裝 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
### <a name="navigate-the-shared-project"></a>瀏覽共用的專案  
  
1.  C# VSIX 專案建立一個名為**TestUniversalProject**。 (**新檔案、 專案**然後**C# 擴充性，Visual Studio 封裝**)。 新增**自訂命令**專案項目範本 (在 [方案總管] 中，以滑鼠右鍵按一下專案節點，然後選取**新增 / 新項目**，然後移至**擴充性**)。 將檔案命名**TestUniversalProject**。  
  
2.  將參考加入 Microsoft.VisualStudio.Shell.Interop.12.1.DesignTime.dll 和 Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime.dll (在**延伸**> 一節)。  
  
3.  開啟 TestUniversalProject.cs 並加入下列`using`陳述式：  
  
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
  
4.  TestUniversalProject 類別中加入私用欄位指向**輸出**視窗。  
  
    ```csharp  
    public sealed class TestUniversalProject   
    {  
        IVsOutputWindowPane output;  
    . . .  
    }  
    ```  
  
5.  設定 TestUniversalProject 建構函式內的 [輸出] 窗格的參考：  
  
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
  
6.  移除現有的程式碼從`ShowMessageBox`方法：  
  
    ```csharp  
    private void ShowMessageBox(object sender, EventArgs e)   
    {  
    }  
    ```  
  
7.  取得 DTE 物件，我們將會使用數個不同的用途，在本逐步解說。 此外，請確定在按下功能表按鈕時，載入方案。  
  
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
  
8.  尋找共用的專案。 共用的專案是純粹的容器。它不建置或產生輸出。 下列方法在方案中尋找第一個共用的專案，藉由尋找<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>共用的專案匯入功能的物件。  
  
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
  
9. 在`ShowMessageBox`方法，輸出標題 (專案名稱會出現在**方案總管 中**) 共用專案。  
  
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
  
10. 取得作用中平台專案。 平台專案所含平台專屬程式碼和資源的專案。 下列方法會使用新的欄位<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID7>取得作用中平台專案。  
  
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
  
11. 在`ShowMessageBox`方法，輸出標題的作用中平台專案。  
  
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
  
    ```  
  
12. 逐一查看平台專案。 下列方法取得從共用專案的所有匯入的 （平台） 專案。  
  
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
    >  如果使用者已開啟的 c + + 通用 Windows 應用程式專案，在實驗執行個體中，上述程式碼會擲回例外狀況。 這是已知的問題。 若要避免此例外狀況，取代`foreach`封鎖上方，以下列：  
  
    ```csharp  
    var importingProjects = sharedAssetsProject.EnumImportingProjects();  
    for (int i = 0; i < importingProjects.Count; ++i)  
    {  
        yield return importingProjects[i];  
    }   
    ```  
  
13. 在`ShowMessageBox`方法，輸出每個平台專案的標題。 輸出的作用中平台專案標題列之後插入下列程式碼。 只有平台專案載入會出現在這份清單。  
  
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
  
14. 變更作用中平台專案。 下列方法設定現用專案使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetProperty%2A>。  
  
    ```csharp  
    private int SetActiveProjectContext(IVsHierarchy hierarchy, IVsHierarchy activeProjectContext)  
    {  
        return hierarchy.SetProperty((uint)VSConstants.VSITEMID.Root, (int)__VSHPROPID7.VSHPROPID_SharedItemContextHierarchy, activeProjectContext);  
    }  
    ```  
  
15. 在`ShowMessageBox`方法中，變更作用中平台專案。 插入這個程式碼內`foreach`區塊。  
  
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
  
16. 現在試試看。按 F5 來啟動實驗執行個體。 在實驗執行個體中建立 C# 通用中樞應用程式專案 (在**新專案**對話方塊中， **Visual C# / Windows / Windows 8 / 通用 / 中樞應用程式**)。 載入方案之後，請移至**工具**功能表，然後按一下**叫用 TestUniversalProject**，文字簽入**輸出**窗格。 您應該會看到類似如下：  
  
    ```  
    Found shared project: HubApp.Shared  
    The active platform project: HubApp.Windows  
    Platform projects:  
     * HubApp.Windows  
     * HubApp.WindowsPhone  
    set active project: HubApp.WindowsPhone  
    ```  
  
### <a name="manage-the-shared-items-in-the-platform-project"></a>管理平台專案中的共用項目  
  
1.  平台專案中，找出共用的項目。 共用專案中的項目會出現在平台專案中做為共用的項目。 您無法看到它們在**方案總管 中**，但您可以逐步專案階層架構來尋找客戶。 下列方法將逐步引導階層，且會收集所有共用的項目。 （選擇性），它會輸出每個項目的標題。 共用的項目由新的屬性所識別<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID7>。  
  
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
  
2.  在`ShowMessageBox`方法，加入下列程式碼，逐步平台專案階層架構項目。 將其內部插入`foreach`區塊。  
  
    ```csharp  
    output.OutputStringThreadSafe("Walk the active platform project:\n");  
    var sharedItemIds = new List<uint>();  
    this.InspectHierarchyItems(activePlatformHier, (uint)VSConstants.VSITEMID.Root, 1, sharedItemIds, true, true);  
    ```  
  
3.  讀取共用項目。 共用的項目會顯示平台專案中為隱藏連結的檔案，而且您可以讀取所有屬性為一般連結的檔案。 下列程式碼會讀取第一個共用項目的完整路徑。  
  
    ```csharp  
    var sharedItemId = sharedItemIds[0];  
    string fullPath;  
    ErrorHandler.ThrowOnFailure(((IVsProject)activePlatformHier).GetMkDocument(sharedItemId, out fullPath));  
    output.OutputStringThreadSafe(string.Format("Shared item full path: {0}\n", fullPath));  
    ```  
  
4.  現在試試看。按 F5 來啟動實驗執行個體。 在實驗執行個體中建立 C# 通用中樞應用程式專案 (在**新專案**對話方塊中， **Visual C# / Windows / Windows 8 / 通用 / 中樞應用程式**) 移至**工具**功能表，然後按一下**叫用 TestUniversalProject**，文字簽入**輸出**窗格。 您應該會看到類似如下：  
  
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
  
### <a name="detecting-changes-in-platform-projects-and-shared-projects"></a>偵測平台專案和共用的專案中的變更  
  
1.  如同您為平台專案中，您可以使用階層和專案事件在共用專案中，偵測變更。 不過，共用專案中的專案項目是不可見的這表示共用的專案項目變更時，並不會引發特定事件。  
  
     請考慮重新命名專案中的檔案時的事件順序：  
  
    1.  在磁碟上變更的檔案名稱。  
  
    2.  專案檔會更新以包含新的檔案名稱。  
  
     階層架構事件 (例如， <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents>) 通常會顯示在 UI 中，以在變更追蹤**方案總管 中**。 階層架構事件，請考慮包含檔案刪除然後再將檔案加入檔案重新命名作業。 不過，當不可見的項目變更時，階層事件系統會引發<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A>事件，但不是<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A>事件。 因此，如果您重新命名平台專案中的檔案，您會獲得兩者<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A>和<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A>，但如果您重新命名共用專案中的檔案，您會收到僅<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A>。  
  
     若要追蹤變更專案項目中的，您可以處理 DTE 專案項目事件 (在中找到的<xref:EnvDTE.ProjectItemsEventsClass>)。 不過，如果您要處理大量的事件數目，您可以取得更佳的效能處理中的事件<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>。 在本逐步解說我們顯示階層架構事件以及 DTE 的事件。 在此程序中，您可以加入事件接聽程式加入共用的專案，並使用平台專案。 然後，當您重新命名共用專案中的一個檔案與另一個平台專案中的檔案，您可以看到每個重新命名作業所引發的事件。  
  
     在此程序中，您可以加入事件接聽程式加入共用的專案，並使用平台專案。 然後，當您重新命名共用專案中的一個檔案與另一個平台專案中的檔案，您可以看到每個重新命名作業所引發的事件。  
  
2.  加入事件接聽程式。 將新的類別檔案加入專案，並呼叫它 HierarchyEventListener.cs。  
  
3.  開啟 HierarchyEventListener.cs 檔案並加入下列 using 陳述式：  
  
    ```csharp  
    using Microsoft.VisualStudio.Shell.Interop;  
    using Microsoft.VisualStudio;  
    using System.IO;  
  
    ```  
  
4.  具有`HierarchyEventListener`類別實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents>:  
  
    ```csharp  
    class HierarchyEventListener : IVsHierarchyEvents  
    { }  
  
    ```  
  
5.  實作的成員<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents>，在下列程式碼中。  
  
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
  
6.  相同類別中加入其他事件處理常式 DTE 事件<xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed>，它發生於已重新命名專案項目。  
  
    ```csharp  
    public void OnItemRenamed(EnvDTE.ProjectItem projItem, string oldName)  
    {  
        output.OutputStringThreadSafe(string.Format("[Event] Renamed {0} to {1} in project {2}\n",  
             oldName, Path.GetFileName(projItem.get_FileNames(1)), projItem.ContainingProject.Name));  
    }  
    ```  
  
7.  註冊階層架構事件。 您需要分別登入您追蹤每個專案。 加入下列程式碼中的`ShowMessageBox`，一個適用於共用的專案中，而另一個則用於其中一個平台專案。  
  
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
  
8.  申請 DTE 專案項目事件<xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed>。 之後您連接的第二個接聽程式，請加入下列程式碼。  
  
    ```csharp  
    // hook up DTE events for project items  
    Events2 dteEvents = (Events2)dte.Events;  
    dteEvents.ProjectItemsEvents.ItemRenamed += listener1.OnItemRenamed;  
  
    ```  
  
9. 修改共用的項目。 您無法修改共用的項目中使用的平台專案。相反地，您必須實際擁有者，這些項目共用專案中修改它們。 您可以使用共用專案中取得對應項目 ID <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.IsDocumentInProject%2A>，讓它共用項目的完整路徑。 然後您可以修改共用的項目。 變更會傳播到平台專案。  
  
    > [!IMPORTANT]
    >  您應該了解專案項目是不是共用的項目之前對其進行修改。  
  
     下列方法修改專案項目檔的名稱。  
  
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
  
10. 在所有其他程式碼中的呼叫這個方法`ShowMessageBox`若要修改的檔案名稱的共用專案中的項目。 插入此共用專案中取得項目的完整路徑的程式碼之後。  
  
    ```csharp  
    // change the file name of an item in a shared project  
    this.InspectHierarchyItems(activePlatformHier, (uint)VSConstants.VSITEMID.Root, 1, sharedItemIds, true, true);  
    ErrorHandler.ThrowOnFailure(((IVsProject)activePlatformHier).GetMkDocument(sharedItemId, out fullPath));   
    output.OutputStringThreadSafe(string.Format("Shared project item ID = {0}, full path = {1}\n", sharedItemId, fullPath));  
    this.ModifyFileNameInProject(sharedHier, fullPath);  
    ```  
  
11. 建置並執行專案。 在實驗執行個體中建立 C# 通用中樞應用程式，請移至**工具**功能表，然後按一下**叫用 TestUniversalProject**，並檢查一般輸出窗格中的文字。 第一個項目共用的名稱 （我們預期 App.xaml 檔案） 的專案應該會變更，而且您應該會看到<xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed>引發事件。 在此情況下，由於重新命名 App.xaml 導致 App.xaml.cs 也要重新命名，您應該會看到四個事件 （針對每個平台專案的兩個）。 （DTE 事件追蹤共用的專案中的項目）。您應該會看到兩個<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A>事件 （一個平台專案中的每個），但不是<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A>事件。  
  
12. 現在，請嘗試重新命名檔案，以在平台專案中，以及您可以查看所引發的事件中的差異。 加入下列程式碼中的`ShowMessageBox`呼叫之後`ModifyFileName`。  
  
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
  
13. 建置並執行專案。 在實驗執行個體中建立 C# 通用專案，請移至**工具**功能表，然後按一下**叫用 TestUniversalProject**，並檢查一般輸出窗格中的文字。 平台專案中的檔案已重新命名之後，您應該會看到兩者<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A>事件和<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A>事件。 因為變更檔案造成變更，沒有其他檔案，因為平台專案中的項目變更不在任何位置取得傳播，只會有一個每個事件。