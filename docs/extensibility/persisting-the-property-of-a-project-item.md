---
title: 保留項目項目的屬性 :微軟文件
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- properties, adding to a project item
- project items, adding properties
ms.assetid: d7a0f2b0-d427-4d49-9536-54edfb37c0f3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 15c280f15436a5e27bcc0dcc4d2fb9e9bdd82933
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702213"
---
# <a name="persist-the-property-of-a-project-item"></a>保留項目項目的屬性
您可能希望保留新增到專案項目的屬性,例如源檔的作者。 可以通過將屬性存儲在專案檔中來執行此操作。

 在專案檔中保留屬性的第一步是獲取專案的層次結構作為<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>介面。 您可以使用自動化或使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>獲取此介面。 獲取介面后,可以使用它確定當前選擇了哪個專案項。 獲得項目項 ID 後,<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A>可以使用添加 屬性。

 在以下過程中,您將*VsPkg.cs*VsPkg.cs`Author`屬性與專案檔`Tom`中的值 保持一起。

## <a name="to-obtain-the-project-hierarchy-with-the-dte-object"></a>使用 DTE 物件取得項目層次結構

1. 將以下代碼加入 VSPackage:

    ```csharp
    EnvDTE.DTE dte = (EnvDTE.DTE)Package.GetGlobalService(typeof(EnvDTE.DTE));
    EnvDTE.Project project = dte.Solution.Projects.Item(1);

    string uniqueName = project.UniqueName;
    IVsSolution solution = (IVsSolution)Package.GetGlobalService(typeof(SVsSolution));
    IVsHierarchy hierarchy;
    solution.GetProjectOfUniqueName(uniqueName, out hierarchy);
    ```

## <a name="to-persist-the-project-item-property-with-the-dte-object"></a>使用 DTE 物件保留項目屬性

1. 將以下代碼加入到前面的過程中方法中的代碼:

    ```csharp
    IVsBuildPropertyStorage buildPropertyStorage =
        hierarchy as IVsBuildPropertyStorage;
    if (buildPropertyStorage != null)
    {
        uint itemId;
        string fullPath = (string)project.ProjectItems.Item(
            "VsPkg.cs").Properties.Item("FullPath").Value;
        hierarchy.ParseCanonicalName(fullPath, out itemId);
        buildPropertyStorage.SetItemAttribute(itemId, "Author", "Tom");
    }
    ```

## <a name="to-obtain-the-project-hierarchy-using-ivsmonitorselection"></a>使用 IVsMonitor 選擇取得項目層次結構

1. 將以下代碼加入 VSPackage:

    ```csharp
    IVsHierarchy hierarchy = null;
    IntPtr hierarchyPtr = IntPtr.Zero;
    IntPtr selectionContainer = IntPtr.Zero;
    uint itemid;

    // Retrieve shell interface in order to get current selection
    IVsMonitorSelection monitorSelection =     Package.GetGlobalService(typeof(SVsShellMonitorSelection)) as     IVsMonitorSelection;
    if (monitorSelection == null)
        throw new InvalidOperationException();

    try
    {
        // Get the current project hierarchy, project item, and selection container for the current selection
        // If the selection spans multiple hierachies, hierarchyPtr is Zero
        IVsMultiItemSelect multiItemSelect = null;
        ErrorHandler.ThrowOnFailure(
            monitorSelection.GetCurrentSelection(
                out hierarchyPtr, out itemid,
                out multiItemSelect, out selectionContainer));

        // We only care if there is only one node selected in the tree
        if (!(itemid == VSConstants.VSITEMID_NIL ||
            hierarchyPtr == IntPtr.Zero ||
            multiItemSelect != null ||
            itemid == VSConstants.VSITEMID_SELECTION))
        {
            hierarchy = Marshal.GetObjectForIUnknown(hierarchyPtr)
                as IVsHierarchy;
        }
    }
    finally
    {
        if (hierarchyPtr != IntPtr.Zero)
            Marshal.Release(hierarchyPtr);
        if (selectionContainer != IntPtr.Zero)
            Marshal.Release(selectionContainer);
    }
    ```

## <a name="to-persist-the-selected-project-item-property-given-the-project-hierarchy"></a>要保留選定的項目項目屬性,給定專案層次結構

1. 將以下代碼加入到前面的過程中方法中的代碼:

    ```csharp
    IVsBuildPropertyStorage buildPropertyStorage =
        hierarchy as IVsBuildPropertyStorage;
    if (buildPropertyStorage != null)
    {
        buildPropertyStorage.SetItemAttribute(itemId, "Author", "Tom");
    }
    ```

## <a name="to-verify-that-the-property-is-persisted"></a>驗證屬性是否持久化

1. 啟動[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)],然後打開或創建解決方案。

2. 在**解決方案資源管理器**中選擇專案項VsPkg.cs。

3. 使用斷點或以其他方式確定您的 VS 包已載入,並且 SetItem 屬性運行。

   > [!NOTE]
   > 您可以在 UI 上下<xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExists_guid>文中 自動載入 VSPackage。 有關詳細資訊,請參閱載[入 VS 套件](../extensibility/loading-vspackages.md)。

4. 關閉[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)],然後在記事本中打開專案檔。 您應該會看到帶有「Tom」值的\<「作者>」標記,如下所示:

   ```xml
   <Compile Include="VsPkg.cs">
       <Author>Tom</Author>
   </Compile>
   ```

## <a name="see-also"></a>另請參閱

- [自訂工具](../extensibility/internals/custom-tools.md)
