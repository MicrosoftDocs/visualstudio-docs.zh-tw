---
redirect_url: /visualstudio/extensibility/what-s-new-in-the-visual-studio-2017-sdk/
ms.openlocfilehash: 5706797ed88dce5b2f481b17d99e9501b960ddca
ms.sourcegitcommit: fb751e41929f031d1a9247bc7c8727312539ad35
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/15/2017
---
標題: 「 輕量型方案負載 (LSL) |Microsoft 文件 」 ms.custom:""ms.date:"01/17/2017"ms.reviewer 會:""ms.suite:""ms.technology: 
  - ms.tgt_pltfrm"vs-ide-sdk":""ms.topic: 「 發行項"helpviewer_keywords: 
  - 「 載入 Vspackage，套輕量型方案 」
  - "Vspackage，fast 方案負載"ms.assetid: 0a71d91e-dc71-4d6b-bbfe-9e4ecd9e5fd1 caps.latest.revision: 1 位作者:"gregvanl"ms.author:"gregvanl"管理員： ghogen
---
# <a name="lightweight-solution-load-lsl"></a>輕量型方案負載 (LSL)

## <a name="background-information-on-lsl"></a>LSL 的背景資訊

輕量型方案載入是 VS 2017 會大幅減少方案載入時間，讓您快速地在更有生產力的新功能。 LSL 啟用時，Visual Studio 不會完全載入專案之前您開始加以使用。

LSL 可能會影響 Visual Studio 擴充功能。 擴充功能的功能取決於要載入的專案可能無法運作，或未正確運作，而不遵循本文中詳述的指引。

如需有關 LSL 進一步的背景，請使用下列連結：

* [輕量型方案負載部落格](https://blogs.msdn.microsoft.com/visualstudio/2016/10/11/shorter-solution-load-time-in-visual-studio-15)
* 問題嗎？ 請與我們連絡[lslsupport@microsoft.com](mailto:lslsupport@microsoft.com)

## <a name="enable-the-setting-to-load-projects-in-deferred-mode"></a>啟用載入 「 延遲 」 模式中的專案設定

1. 關閉目前開啟的方案。
2. 移至**工具** > **選項** > **專案和方案** > **一般**設定頁面。
3. 請檢查**套輕量型方案負載**方塊以啟用此設定。

上面的設定，開啟與開啟方案時，IDE 會顯示專案的一般檢視，但不是會載入專案。

## <a name="differences-between-deferred-load-and-regular-load-of-projects"></a>延後的載入和專案的一般負載之間的差異

與載入輕量型方案，開啟方案時，不會載入專案。 這些 「 延後專案 」，會建立虛設常式階層。 [方案總管] 中顯示圖示和名稱的專案，使用預期的檢視沒有 UI 指示的某些或所有的專案是以 「 延遲模式 」。

使用啟用 LSL、 延伸模組不再可以預期觸發作業時已完全載入所需的專案。 呼叫端必須檢查它們是否有相依性，在載入專案。 如果延伸模組需要延後的專案中的資訊，請執行下列擴充功能：

1. 視需要載入專案。
2. 使用新**工作區 Api**能夠資訊從延後的專案，而不會載入它。

新**工作區 Api**允許從延後的專案中取得資訊，例如主控專案的原始程式檔和所有指定的專案的原始程式檔的副檔名。 在某些情況下，僅提供有限的專案需要載入。 此權限的選項為作業的頻率、 方便的替代方法，以及整體的使用者經驗之間取得平衡。

所有專案和方案載入相關 LSL 模式中仍會引發事件。 這讓元件能夠從 VS 得到預期的行為與它們在相同的方式載入專案時的行為。 專案載入相關開啟方案的期間完成的工作就可大幅減少雖然。

## <a name="ui-requirements-and-changes"></a>UI 需求和變更

所有 UI 必須都將載入和延後的專案視為相等。 這表示可以載入的專案執行任何動作必須適用於延後的專案，但有些例外狀況。 為了完成這項作業的功能，有一些現有的平台應用程式開發介面，以及引進的新應用程式開發介面的變更。

### <a name="expectations-for-ui"></a>預期的 UI

1. 功能必須顯示是否專案是載入或延遲差異取決於任何視覺效果。
2. 任何清單或方案的已載入的專案上的列舉必須包含延後的專案。
3. 任何對載入的專案可用的動作應該要有對延遲的專案。
4. 功能必須要求載入專案時，才：
  * 沒有直接的使用者互動功能。 不要先載入專案。
  * 由使用者發出的 「 查看更多結果 」 手勢。 請參閱下面這個 UI 指導方針。
  * 完全載入的專案可以用來滿足動作。 LSL 和開啟專案 Api，您應該盡可能使用和傳送功能要求請求時遺失的功能。

### <a name="changes-in-platform-apis-to-help-drive-ui"></a>平台 Api，協助磁碟機 UI 中的變更

1. 新的應用程式開發介面可供要求方案已開啟輕量型方案負載模式和多少專案都是延後的狀態。
2. 延後的所有專案都載入方案中時，被提供給新的事件。
3. 新的應用程式開發介面會提供以詢問專案會延遲。
4. 現有的應用程式開發介面會更新為包含延後的專案，當要求用已載入的專案。
5. 更新現有的應用程式開發介面，以快速解決方法是完全載入後開啟方案。

### <a name="how-to-add-see-more-results-for-a-feature"></a>如何新增 「 請參閱更多結果 」 功能。

專案的內容執行查詢的功能應考量的延後的專案的影響。 在某些情況下，功能可以取得其查詢的結果從 LSL 與工作區 Api 延後的專案。 在其他情況下，功能的限制會需要載入的專案。 這兩種情況應該提供新的 「 查看更多結果 」 手勢，可讓使用者完全載入專案和重新查詢。 此筆勢啟用當同時提供使用者實際載入專案時取得完整結果的方法有延後的專案時，提供最近似的功能。

功能的一般演算法應該是：

### <a name="when-the-query-is-performed-over-a-single-project"></a>當查詢是透過單一專案來執行

```csharp
// IsInDeferredState() and EnsureProjectIsLoadedHelper() in this sample can be found in the "Helpful code snippets" section of this document
public void Query(IVsHierarchy projectToQuery)
{
    // 1. Perform calculation/query
    DoQuery(projectToQuery);

    // 2. Present results to the user
    ShowResults();

    // 3. If the project was deferred, then present a "See More Results" UI element
    if (IsInDeferredState(projectToQuery))
    {
        ShowSeeMoreResults();
    }
}

public void OnClick_SeeMoreResults()
{
    // 1. Ask ask for the project to be loaded
    IVsHierarchy projectFromLastQuery = GetProjectFromLastQuery();
    IVsHierarchy loadedProject = EnsureProjectIsLoadedHelper(projectFromLastQuery);

    if (loadedProject != null)
    {
        // 2. Re-run the query on the loaded projects
        Query(loadedProject);
    }
    else
    {
        ShowErrorMessage();
    }
}
```

### <a name="when-the-query-is-performed-over-the-whole-solution"></a>當查詢是透過整個方案來執行

```csharp
// Requires Microsoft.VisualStudio.Shell.Interop.15.0.DesignTime.dll
public void Query()
{
    // 1. Perform calculation/query
    DoQuery();

    // 2. Present results to the user
    ShowResults();

    // 3. If there were deferred projects, then present a "See More Results from all projects" UI element
    var solution = // the solution
    object deferredCount = 0;
    int hr = ((IVsSolution)solution).GetProperty((int)__VSPROPID7.VSPROPID_DeferredProjectCount, out deferredCount);
    if (ErrorHandler.Succeeded(hr) && ((int)deferredCount > 0))
    {
        ShowSeeMoreResults();
    }
}

public void OnClick_SeeMoreResults()
{
    // 1. Force the solution to load, as requested by the user. This brings up a UI with a "Cancel" button (unless supppresed with __VSBSLFLAGS.VSBSLFLAGS_NotCancelable)
    var solution = // get IVsSolution4
    int hr = ((IVsSolution4)solution).EnsureSolutionIsLoaded((uint)__VSBSLFLAGS.VSBSLFLAGS_None);
    if (ErrorHandler.Succeeded(hr))
    {
        // 2. Re-run the query
        Query();
    }
    else
    {
        ShowErrorMessage();
    }
}
```

## <a name="api-changes"></a>API 變更

### <a name="new-api"></a>新的 API

IVsSolution7.IsSolutionLoadDeferred (out 延後的 bool)

如果目前的方案已經載入延遲模式，則傳回 true。 請注意，如果一開始載入方案在延後的模式中，即使最後會延後的所有專案載入目前的工作階段 （因為明確的使用者筆勢或強制的作業），這個屬性仍會傳回 true。

__VSPROPID7。VSPROPID_DeferredProjectCount

傳回目前在延後的模式中的專案計數。 此屬性會在範圍 [0，VSPROPID_ProjectCount] 有一個值。

__VSHPROPID9。VSHPROPID_IsDeferred

如果專案階層架構在延後的載入狀態，則傳回 true。

值為 EPF_DEFERRED 和 EPF_NOTDEFERRED __VSENUMPROJFLAGS3

這些旗標可以傳遞至[IVsSolution.GetProjectEnum()](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivssolution.getprojectenum.aspx)來反覆查看延期與非延期的專案。

### <a name="new-events"></a>新的事件

IVsSolutionEvents7.OnAfterLoadAllDeferredProjects()

載入延後的所有專案之後，就會引發這個事件。 此時，VSPROPID_DeferredProjectCount 等於 0。 請注意，此事件就不會引發方案負載的一部分，而且可能不會引發在所有的工作階段中。 它只能被觸發時載入所有延後的專案。

### <a name="changes-to-existing-api"></a>變更現有的應用程式開發介面

* 傳遞[__VSENUMPROJFLAGS](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.__vsenumprojflags.aspx)。若要 EPF_LOADEDINSOLUTION [IVsSolution.GetProjectEnum()](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivssolution.getprojectenum.aspx)傳回延後的專案。
* 傳遞[__VSENUMPROJFLAGS](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.__vsenumprojflags.aspx)。EPF_UNLOADEDINSOLUTION 不會傳回延後的專案。
* [KnownUIContexts.SolutionExistsAndFullyLoadedContext](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.knownuicontexts.solutionexistsandfullyloadedcontext.aspx)設為開啟的方案，則為 true。 延後的專案會被視為載入，所以此內容會設定大部分早於非 LSL 模式。
* [__VSPROPID](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.__vspropid.aspx)。VSPROPID_ProjectCount 傳回延後的載入專案的總和。

## <a name="helpful-code-snippets"></a>有用程式碼片段

### <a name="check-if-a-solution-was-opened-in-deferred-load-mode"></a>檢查是否延後的載入模式中開啟方案

```csharp
/// <summary>
/// Checks if the solution was opened in LSL mode.
/// </summary>
/// <returns>True if the solution was opened in LSL mode, false otherwise.</returns> public static bool IsSolutionLoadDeferred()
{
    IVsSolution7 vsSolution = ServiceProvider.GlobalProvider.GetService(typeof(SVsSolution)) as IVsSolution7;
    Assumes.Present(vsSolution);

    return vsSolution.IsSolutionLoadDeferred();
}
```

### <a name="check-if-a-project-is-deferred"></a>請檢查專案會延後

```csharp
/// <summary>
/// Checks to see if a project is deferred.
/// </summary>
/// <param name="projectsToLoad">A set of deferred and/or loaded projects to ensure are loaded.</param>
/// <returns>True if the project is deferred. False if it is any other state, such as loaded, unloaded, or virtual.</returns>
/// <remarks>Requires Microsoft.VisualStudio.Shell.Interop.15.0.DesignTime.dll</remarks>
public static bool IsInDeferredState(IVsHierarchy vsHierarchy)
{
    object deferred;
    int hr = vsHierarchy.GetProperty((uint)VSConstants.VSITEMID.Root, (int)__VSHPROPID9.VSHPROPID_IsDeferred, out deferred);

    if (ErrorHandler.Succeeded(hr))
    {
        return (bool)deferred;
    }

    return false;
}
```

### <a name="load-a-project"></a>載入專案

```csharp
/// <summary>
/// Ensures a project is fully loaded.
/// </summary> /// <param name="projectToLoad">A deferred or loaded project to ensure is loaded.</param>
/// <remarks>Requires Microsoft.VisualStudio.Shell.15.0.dll and Microsoft.VisualStudio.Shell.Interop.dll</remarks>
public static IVsHierarchy EnsureProjectIsLoadedHelper(IVsHierarchy projectToLoad)
{
    int hr = VSConstants.S_OK;
    var solution = // get the solution

    // 1. Ask the solution to load the required project. To reduce wait time,
    //    we load only the project we need, not the entire solution.
    hr = projectToLoad.GetGuidProperty((uint)VSConstants.VSITEMID.Root, (int)__VSHPROPID.VSHPROPID_ProjectIDGuid, out projectGuid);
    hr = ErrorHandler.ThrowOnFailure(hr);
    hr = ((IVsSolution4)solution).EnsureProjectIsLoaded(projectGuid, (uint)__VSBSLFLAGS.VSBSLFLAGS_None);
    hr = ErrorHandler.ThrowOnFailure(hr);

    // 2. After the project is loaded, grab the latest IVsHierarchy object.
    IVsHierarchy loadedProject = null;
    hr = ((IVsSolution)solution).GetProjectOfGuid(projectGuid, out loadedProject);
    hr = ErrorHandler.ThrowOnFailure(hr);

    return loadedProject;
}
```

### <a name="load-a-set-of-projects"></a>載入專案的集合

```csharp
/// <summary>
/// Ensures a collection of IVsHierarchys are loaded. To be used when deferred projects absolutely cannot be used.
/// </summary>
/// <param name="projectsToLoad">A set of deferred and/or loaded projects to ensure are loaded.</param>
/// <remarks>Requires Microsoft.VisualStudio.Shell.15.0.dll and Microsoft.VisualStudio.Shell.Interop.dll</remarks>
public static IReadOnlyCollection<IVsHierarchy> EnsureProjectsAreLoadedHelper(IReadOnlyCollection<IVsHierarchy> projectsToLoad)
{
    if (projectsToLoad == null || projectsToLoad.Count == 0)
        return projectsToLoad;

    int hr = VSConstants.S_OK;
    List<Guid> projectGuids = new List<Guid>(projectsToLoad.Count);
    List<IVsHierarchy> loadedProjects = new List<IVsHierarchy>(projectsToLoad.Count);
    var solution = // get the solution

    // 1. Collect projects to force load
    foreach (var project in projectsToLoad)
    {
        Guid projectGuid;
        hr = project.GetGuidProperty((uint)VSConstants.VSITEMID.Root, (int)__VSHPROPID.VSHPROPID_ProjectIDGuid, out projectGuid)
        hr = ErrorHandler.ThrowOnFailure(hr);
        projectGuids.Add(projectGuid);
    }

    // 2. Ask the solution to load the required projects. To reduce wait time,
    //    we load only the projects we need, not the entire solution.
    hr = ((IVsSolution4)solution).EnsureProjectsAreLoaded(projectCount, projectGuids.ToArray(), (uint)__VSBSLFLAGS.VSBSLFLAGS_None);
    hr = ErrorHandler.ThrowOnFailure(hr);

    // 3. After the projects are loaded, grab the latest IVsHierarchy objects
    foreach (var projectGuid in projectGuids)
    {
        IVsHierarchy loadedProject = null;
        hr = ((IVsSolution)solution).GetProjectOfGuid(projectGuid, out loadedProject);
        hr = ErrorHandler.ThrowOnFailure(hr);
        loadedProjects.Add(loadedProject);
    }

    return loadedProjects;
}
```

### <a name="checks-if-the-solution-has-deferred-projects"></a>會檢查方案已延後的專案

```csharp
/// <summary>
/// Checks if the solution has deferred projects
/// </summary>
/// <returns>True if the solution has deferred projects, false otherwise.</returns>
public static bool SolutionHasDeferredProjects()
{
    IVsSolution vsSolution = ServiceProvider.GlobalProvider.GetService(typeof(SVsSolution)) as IVsSolution;
    Assumes.Present(vsSolution);
    object varHasDeferredProjects;
    if (ErrorHandler.Succeeded(vsSolution.GetProperty(
        (int)__VSPROPID7.VSPROPID_DeferredProjectCount, out varHasDeferredProjects)))
    {
        return (int)varHasDeferredProjects != 0;
    }

    return false;
}
```

## <a name="getting-detailed-information-with-workspace-apis"></a>取得與工作區的應用程式開發介面的詳細的資訊

### <a name="how-to-get-detailed-info-on-a-lsl-solution"></a>如何取得詳細的資訊，LSL 方案

新的工作區 Api 會公開透過 IVsSolutionWorkspaceService 為了擷取方案的詳細的資訊。

這些 Api 可以用來取得目前的工作區、 使用中方案、 受管理的命令列資訊，以及索引服務工作區中。 這些 Api 可以進一步利用索引服務以取得詳細的資料，例如，所有原始程式檔在專案中，主控專案的原始程式檔中，所有專案中目前的方案，包含所有 P2P 參考專案等等。

下列程式碼片段會示範使用工作區 Api。

### <a name="get-ivssolutionworkspaceservice-initially"></a>一開始取得 IVsSolutionWorkspaceService

>**注意：**請只在 LSL 案例，以避免載入工作區的應用程式開發介面封裝中取得 IVsSolutionWorkspaceService。

```csharp
private readonly Lazy<IVsSolutionWorkspaceService> _solutionWorkspaceService;

[ImportingConstructor]
public DeferredProjectWorkspaceService(SVsServiceProvider serviceProvider)
{
    _solutionWorkspaceService = new Lazy<IVsSolutionWorkspaceService>(
        () => (IVsSolutionWorkspaceService)serviceProvider.GetService(typeof(SVsSolutionWorkspaceService)));
}
```

>**注意：**的下列程式碼片段假設已執行延遲初始化 _solutionWorkspaceService。

### <a name="get-managed-command-line-info-for-deferred-projects-for-active-solution-configuration"></a>取得受管理的命令列資訊之作用中的方案組態時，延後的專案

```csharp
/// <summary>
/// Get the managed command line info for active solution configuration
/// </summary>
/// <param name="cancellationToken"> the cancellation token</param>
/// <returns></returns>
public async Task<IReadOnlyDictionary<string, ManagedCommandLineInfo>> GetManagedCommandLineInfoForConfigurationAsyn(CancellationToken cancellationToken)
{
    var dte = ServiceProvider.GetGlobalService(typeof(EnvDTE.DTE)) as EnvDTE.DTE;
    var solutionConfig = (EnvDTE80.SolutionConfiguration2)dte.Solution.SolutionBuild.ActiveConfiguration;

    // Solution configuration is something like "Debug|Any CPU"
    return await _solutionWorkspaceService.Value.GetManagedCommandLineInfoAsync(
        $"{solutionConfig.Name}|{solutionConfig.PlatformName}", cancellationToken).ConfigureAwait(false);
}
```

### <a name="get-the-active-solution-file-in-lsl"></a>取得使用中的方案中的檔案 LSL

```csharp
/// <summary>
/// Get the active solution file.
/// </summary>
/// <returns>The solution file.</returns>
public string GetActiveSolutionFile()
{
    return _solutionWorkspaceService.Value.SolutionFile;
}
```

### <a name="get-the-owning-project-of-a-source-file"></a>取得主控專案的原始程式檔

```csharp
/// <summary>
/// Get the owning projects of a source file.
/// </summary>
/// <param name="filePath">the source file path.</param>
/// <returns></returns>
public async Task<IEnumerable<string>> GetOwningProjectAsync(string filePath)
{
    var workspace = _solutionWorkspaceService.Value.CurrentWorkspace;
    var indexService = workspace.GetIndexWorkspaceService();
    var result = await indexService.GetFileDependantsAsync(filePath, null, String.Empty, (int)FileReferenceInfoType.Source);
    return result.Select(f => f.Path);
}
```

### <a name="get-all-source-files-from-a-project"></a>取得專案中所有原始程式檔

```csharp
/// <summary>
/// Get all source files from a project.
/// </summary>
/// <param name="projectFilePath">the project file path.</param>
/// <returns></returns>
public async Task<IEnumerable<string>> GetFileReferenceAsync(string projectFilePath)
{
    var workspace = _solutionWorkspaceService.Value.CurrentWorkspace;
    var indexService = workspace.GetIndexWorkspaceService();
    var fileReferenceResult = await indexService.GetFileReferencesAsync(projectFilePath, referenceTypes: (int)FileReferenceInfoType.Source);
    return fileReferenceResult.Select(f => f.Path);
}
```

### <a name="get-the-p2p-references-in-a-project"></a>在專案中取得 P2P 參考

```csharp
/// <summary>
/// Get outputs of project.
/// </summary>
/// <param name="projectFilePath">the project file path.</param>
/// <returns></returns>
public async Task<IEnumerable<string>> GetFileReferenceAsync(string projectFilePath)
{
    var workspace = _solutionWorkspaceService.Value.CurrentWorkspace;
    var indexService = workspace.GetIndexWorkspaceService();
    var fileReferenceResult = await indexService.GetFileReferencesAsync(projectFilePath, context: "Debug|AnyCPU", referenceTypes: (int)FileReferenceInfoType.Output);
    return fileReferenceResult.Select(f => f.Path);
}
```

### <a name="get-all-the-projects-in-a-solution"></a>取得在方案中的所有專案

```csharp
/// <summary>
/// Get the projects in a solution.
/// </summary>
/// <param name="solutionFilePath">the solution file path.</param>
/// <returns></returns>
public async Task<IEnumerable<string>> GetProjectsInSolutionAsync(string solutionFilePath)
{
    var workspace = _solutionWorkspaceService.Value.CurrentWorkspace;
    var indexService = workspace.GetIndexWorkspaceService();

    // Passing the configuration|Platform that projects apply to; passing null will return projects with all configurations.
    var result = await indexService.GetFileReferencesAsync(solutionFilePath, context: "Debug|AnyCPU", referenceTypes: (int)FileReferenceInfoType.ProjectReference);
    return result.Select(f => f.Path);
}
```

## <a name="troubleshooting"></a>疑難排解

由於 LSL 本質，是有意如此，使用者無法看到載入和延後的專案之間的差異。 這可讓功能開發和測試困難。

您可以透過下列方式啟用延後的專案的 UI 中的視覺提示：

1. 關閉 Visual Studio
2. Regedit.exe
3. 選取 HKLM
4. 檔案 > 載入 Hive
5. `%localappdata%\microsoft\visualstudio\15.0_<instance ID>\privateregistry.bin`
6. 輸入 「 VisualStudio"做為索引鍵名稱
7. 設定`HKLM\VisualStudio\Software\Microsoft\VisualStudio\15.0_<instanceID>\FeatureFlags\Solution\Loading\Deferred\Hint\Value=1`(DWORD)
8. 選取 HKLM\VisualStudio
9. 檔案 > 解除載入 Hive
10. 啟動 Visual Studio

如有任何進一步的問題，請連接到[ lslsupport@microsoft.com ](mailto:lslsupport@microsoft.com)。






