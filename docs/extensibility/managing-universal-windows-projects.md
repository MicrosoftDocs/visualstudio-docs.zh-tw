---
title: 管理通用 Windows 專案 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 47926aa1-3b41-410d-bca8-f77fc950cbe7
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 06bfb109ce58ee822a32bc3a92d7e6e45578fb05
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "55005500"
---
# <a name="manage-universal-windows-projects"></a>管理通用 Windows 專案
通用 Windows 應用程式是以 Windows 8.1 和 Windows Phone 8.1，讓開發人員可以使用兩種平台的程式碼和其他資產為目標的應用程式。 共用程式碼和資源會保留在共用的專案，而平台特定程式碼和資源會保留在不同的專案，一個用於 Windows，另一個則用於 Windows Phone。 如需通用 Windows 應用程式的詳細資訊，請參閱[通用 Windows 應用程式](https://msdn.microsoft.com/library/windows/apps/dn609832.aspx)。 管理專案的 visual Studio 擴充功能應該要知道通用 Windows 應用程式專案具有不同於單一平台應用程式的結構。 本逐步解說會示範如何瀏覽共用的專案和管理共用的項目。  

## <a name="prerequisites"></a>必要條件  
 從 Visual Studio 2015 中，從下載中心取得未安裝 Visual Studio SDK。 包含為 Visual Studio 安裝程式的選用功能。 您也可以在稍後安裝 VS SDK。 如需詳細資訊，請參閱 <<c0> [ 安裝 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  

### <a name="navigate-the-shared-project"></a>瀏覽共用的專案  

1.  建立名為 C# VSIX 專案**TestUniversalProject**。 (**檔案** > **新** > **專案**，然後**C#**  >  **擴充性** > **Visual Studio 套件**)。 新增**自訂命令**專案項目範本 (在**方案總管**，以滑鼠右鍵按一下專案節點，然後選取**新增** > **新項目**，然後移至**擴充性**)。 將檔案命名**TestUniversalProject**。  

2.  將參考加入*Microsoft.VisualStudio.Shell.Interop.12.1.DesignTime.dll*並*Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime.dll* (在**延伸**一節)。  

3.  開啟*TestUniversalProject.cs*並新增下列`using`陳述式：  

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

4.  在 `TestUniversalProject`類別新增私用欄位，指向**輸出**視窗。  

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

6.  移除現有的程式碼，從`ShowMessageBox`方法：  

    ```csharp  
    private void ShowMessageBox(object sender, EventArgs e)   
    {  
    }  
    ```  

7.  取得 DTE 物件，我們會用來在這個逐步解說幾個不同的用途。 此外，請確定載入方案時按下功能表按鈕時。  

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

8.  尋找共用的專案。 共用的專案是純粹的容器;它不會建置或產生的輸出。 下列方法在方案內尋找第一個共用的專案，藉由尋找<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>共用的專案匯入功能的物件。  

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

9. 在 [`ShowMessageBox`方法，輸出標題 (會出現在專案名稱**方案總管] 中**) 共用專案。  

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

10. 取得使用中平台專案。 平台專案會包含平台特定程式碼和資源的專案。 下列方法會使用新的欄位<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID7>取得使用中平台專案。  

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

11. 在 `ShowMessageBox`方法，輸出的使用中平台專案的標題。  

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

12. 逐一查看的平台專案。 下列方法會取得所有匯入的 （平台） 專案，從共用的專案。  

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
    >  如果使用者已開啟的 c + + 通用 Windows 應用程式專案中的實驗執行個體，上述程式碼會擲回例外狀況。 這是已知的問題。 若要避免此例外狀況，取代`foreach`含有下列區塊上方：  

    ```csharp  
    var importingProjects = sharedAssetsProject.EnumImportingProjects();  
    for (int i = 0; i < importingProjects.Count; ++i)  
    {  
        yield return importingProjects[i];  
    }   
    ```  

13. 在 `ShowMessageBox`方法，輸出每個平台專案的標題。 輸出標題的使用中平台專案的行之後插入下列程式碼。 只載入的平台專案會出現在這份清單中。  

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

14. 變更使用中平台專案。 下列方法可讓您設定作用中的專案使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetProperty%2A>。  

    ```csharp  
    private int SetActiveProjectContext(IVsHierarchy hierarchy, IVsHierarchy activeProjectContext)  
    {  
        return hierarchy.SetProperty((uint)VSConstants.VSITEMID.Root, (int)__VSHPROPID7.VSHPROPID_SharedItemContextHierarchy, activeProjectContext);  
    }  
    ```  

15. 在 `ShowMessageBox`方法中，變更使用中平台專案。 插入此程式碼內`foreach`區塊。  

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

16. 現在試試看。按下 F5 來啟動實驗執行個體。 在實驗執行個體中建立 C# 通用中樞應用程式專案 (在**新的專案** 對話方塊中， **Visual C#** > **Windows**  >  **Windows 8** > **通用** > **中樞應用程式**)。 載入方案之後，請前往**工具**功能表，然後按一下**叫用 TestUniversalProject**，然後簽入的 文字**輸出**窗格。 您應該會看到類似下列的畫面：  

    ```  
    Found shared project: HubApp.Shared  
    The active platform project: HubApp.Windows  
    Platform projects:  
     * HubApp.Windows  
     * HubApp.WindowsPhone  
    set active project: HubApp.WindowsPhone  
    ```  

### <a name="manage-the-shared-items-in-the-platform-project"></a>管理平台專案中的共用項目  

1.  平台專案中找到共用的項目。 共用專案中的項目會出現，平台專案中做為共用的項目。 看不到它們**方案總管 中**，但您可以逐步專案階層架構，以找出它們。 下列方法會引導階層，並且收集所有共用的項目。 （選擇性），它會輸出每個項目的標題。 共用的項目由新的屬性識別<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID7>。  

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

2.  在 `ShowMessageBox`方法，加入下列程式碼，逐步引導的平台專案階層項目。 將其內部插入`foreach`區塊。  

    ```csharp  
    output.OutputStringThreadSafe("Walk the active platform project:\n");  
    var sharedItemIds = new List<uint>();  
    this.InspectHierarchyItems(activePlatformHier, (uint)VSConstants.VSITEMID.Root, 1, sharedItemIds, true, true);  
    ```  

3.  讀取共用的項目。 為隱藏的連結檔案，共用的項目會出現，平台專案中，您可以閱讀為一般連結的檔案的所有屬性。 下列程式碼會讀取第一個共用的項目完整路徑。  

    ```csharp  
    var sharedItemId = sharedItemIds[0];  
    string fullPath;  
    ErrorHandler.ThrowOnFailure(((IVsProject)activePlatformHier).GetMkDocument(sharedItemId, out fullPath));  
    output.OutputStringThreadSafe(string.Format("Shared item full path: {0}\n", fullPath));  
    ```  

4.  現在試試看。按下**F5**來啟動實驗執行個體。 建立C#實驗執行個體中的通用中樞應用程式專案 (在**新的專案**] 對話方塊中，**視覺化C#**   >  **Windows**  > **Windows 8** > **通用** > **中樞應用程式**) 移至**工具**功能表，按一下**叫用 TestUniversalProject**，然後簽入的 [文字**輸出**窗格。 您應該會看到類似下列的畫面：  

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

### <a name="detect-changes-in-platform-projects-and-shared-projects"></a>偵測平台專案和共用的專案中的變更  

1. 如同您用於平台專案，您可以使用階層和專案的事件在共用專案中，偵測變更。 不過，共用專案中的專案項目不是可見的這表示共用的專案項目變更時，並不會引發特定事件。  

    請考慮重新命名專案中的檔案時的事件順序：  

   1. 檔案名稱是在磁碟上變更。  

   2. 專案檔會更新以包含新的檔案名稱。  

      階層架構事件 (例如<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents>) 通常會追蹤變更顯示在 UI 中，依照**方案總管 中**。 階層架構事件，請考慮包含刪除的檔案，然後檔案新增的檔案重新命名作業。 不過，不可見的項目變更時，階層事件系統會引發<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A>事件，但不是<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A>事件。 因此，如果您重新命名的平台專案中的檔案，您可以同時<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A>並<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A>，但如果您重新命名共用專案中的檔案，您會收到僅<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A>。  

      若要追蹤變更專案項目中的，您可以處理 DTE 專案項目事件 (在中找到的<xref:EnvDTE.ProjectItemsEventsClass>)。 不過，如果您要處理大量的事件數目，您可以取得更佳的效能處理中的事件<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>。 在本逐步解說示範階層事件以及 DTE 事件。 在此程序中，您可以加入事件接聽程式為共用的專案，而且平台專案。 然後，當您重新命名共用專案中的一個檔案與平台專案中的另一個檔案，您可以看到每個重新命名作業會引發的事件。  

      在此程序中，您可以加入事件接聽程式為共用的專案，而且平台專案。 然後，當您重新命名共用專案中的一個檔案與平台專案中的另一個檔案，您可以看到每個重新命名作業會引發的事件。  

2. 加入事件接聽程式。 將新的類別檔案加入專案，並呼叫它*HierarchyEventListener.cs*。  

3. 開啟*HierarchyEventListener.cs*檔案，並新增下列 using 陳述式：  

   ```csharp  
   using Microsoft.VisualStudio.Shell.Interop;  
   using Microsoft.VisualStudio;  
   using System.IO;  

   ```  

4. 已`HierarchyEventListener`類別會實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents>:  

   ```csharp  
   class HierarchyEventListener : IVsHierarchyEvents  
   { }  

   ```  

5. 實作的成員<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents>，如下列程式碼。  

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

6. 在相同類別中新增 DTE 事件的另一個事件處理常式<xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed>，就會出現每當重新命名專案項目。  

   ```csharp  
   public void OnItemRenamed(EnvDTE.ProjectItem projItem, string oldName)  
   {  
       output.OutputStringThreadSafe(string.Format("[Event] Renamed {0} to {1} in project {2}\n",  
            oldName, Path.GetFileName(projItem.get_FileNames(1)), projItem.ContainingProject.Name));  
   }  
   ```  

7. 註冊的階層架構事件。 您需要另外註冊您要追蹤每個專案。 新增下列程式碼中的`ShowMessageBox`，一個適用於共用的專案中，而另一個則用於其中一個平台專案。  

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

8. DTE 專案項目事件註冊<xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed>。 您將連結的第二個接聽程式之後，請新增下列程式碼。  

   ```csharp  
   // hook up DTE events for project items  
   Events2 dteEvents = (Events2)dte.Events;  
   dteEvents.ProjectItemsEvents.ItemRenamed += listener1.OnItemRenamed;  

   ```  

9. 修改共用的項目。 您無法修改共用的項目，在平台專案中;相反地，您必須修改它們實際的擁有者，這些項目之共用專案中。 您可以使用共用專案中取得對應的項目 ID <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.IsDocumentInProject%2A>，讓它共用的項目完整路徑。 然後您可以修改共用的項目。 變更會傳播到平台專案中。  

    > [!IMPORTANT]
    >  您應該了解專案項目為共用的項目再加以修改。  

     下列方法修改專案項目檔案的名稱。  

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

10. 畢竟中的其他程式碼呼叫此方法`ShowMessageBox`修改的檔案名稱的共用專案中的項目。 共用專案中取得項目的完整路徑的程式碼之後插入此項。  

    ```csharp  
    // change the file name of an item in a shared project  
    this.InspectHierarchyItems(activePlatformHier, (uint)VSConstants.VSITEMID.Root, 1, sharedItemIds, true, true);  
    ErrorHandler.ThrowOnFailure(((IVsProject)activePlatformHier).GetMkDocument(sharedItemId, out fullPath));   
    output.OutputStringThreadSafe(string.Format("Shared project item ID = {0}, full path = {1}\n", sharedItemId, fullPath));  
    this.ModifyFileNameInProject(sharedHier, fullPath);  
    ```  

11. 建置並執行專案。 建立 C# 通用中樞應用程式中的實驗執行個體，請前往**工具**功能表，然後按一下**叫用 TestUniversalProject**，並檢查一般輸出窗格中的文字。 共用專案中的第一個項目名稱 (我們預期*App.xaml*檔案) 應該變更，您應該會看到<xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed>已引發事件。 在此情況下，因為重新命名*App.xaml*會導致*App.xaml.cs*要一併重新命名，您應該會看到四個事件 （針對每個平台專案的兩個）。 （DTE 事件進行追蹤共用的專案中的項目）。您應該會看到兩個<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A>事件 （一個用於每個平台專案），但不是<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A>事件。  

12. 現在，請嘗試重新命名檔案，以在平台專案中，與您所見取得引發事件的差異。 新增下列程式碼`ShowMessageBox`呼叫後面`ModifyFileName`。  

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

13. 建置並執行專案。 在實驗執行個體中建立 C# 通用專案，請前往**工具**功能表，然後按一下**叫用 TestUniversalProject**，並檢查一般輸出窗格中的文字。 平台專案中的檔案重新命名之後，您應該會看到兩者<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A>事件和<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A>事件。 因為變更檔案造成的變更，沒有其他檔案，因為平台專案中的項目已變更不在任何位置取得傳播，都只有一個每個事件。
