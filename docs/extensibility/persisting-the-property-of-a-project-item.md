---
title: 保存專案專案的屬性 |Microsoft Docs
description: 瞭解如何將屬性儲存在擴充專案類型的專案檔中，以保存您新增至專案專案的屬性。
ms.custom: SEO-VS-2020
ms.date: 03/22/2018
ms.topic: how-to
helpviewer_keywords:
- properties, adding to a project item
- project items, adding properties
ms.assetid: d7a0f2b0-d427-4d49-9536-54edfb37c0f3
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 63b1a4a7cb6e2d12882794a07e51151effe36716
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99967419"
---
# <a name="persist-the-property-of-a-project-item"></a>保存專案專案的屬性
您可能會想要保存新增至專案專案的屬性，例如原始程式檔的作者。 您可以藉由將屬性儲存在專案檔中，來完成這項作業。

 將屬性保存在專案檔中的第一個步驟是取得專案的階層作為 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> 介面。 您可以使用自動化或使用來取得這個介面 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection> 。 取得介面之後，您可以使用它來判斷目前選取的專案專案。 擁有專案專案識別碼之後，您就可以使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A> 加入屬性。

 在下列程式中，您會 `Author` 使用專案檔中的值來保存 VsPkg.cs 屬性 `Tom` 。

## <a name="to-obtain-the-project-hierarchy-with-the-dte-object"></a>取得具有 DTE 物件的專案階層

1. 將下列程式碼新增至您的 VSPackage：

    ```csharp
    EnvDTE.DTE dte = (EnvDTE.DTE)Package.GetGlobalService(typeof(EnvDTE.DTE));
    EnvDTE.Project project = dte.Solution.Projects.Item(1);

    string uniqueName = project.UniqueName;
    IVsSolution solution = (IVsSolution)Package.GetGlobalService(typeof(SVsSolution));
    IVsHierarchy hierarchy;
    solution.GetProjectOfUniqueName(uniqueName, out hierarchy);
    ```

## <a name="to-persist-the-project-item-property-with-the-dte-object"></a>使用 DTE 物件保存專案專案屬性

1. 將下列程式碼加入至上一個程式中方法提供的程式碼：

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

## <a name="to-obtain-the-project-hierarchy-using-ivsmonitorselection"></a>若要使用 IVsMonitorSelection 取得專案階層

1. 將下列程式碼新增至您的 VSPackage：

    ```csharp
    IVsHierarchy hierarchy = null;
    IntPtr hierarchyPtr = IntPtr.Zero;
    IntPtr selectionContainer = IntPtr.Zero;
    uint itemid;

    // Retrieve shell interface in order to get current selection
    IVsMonitorSelection monitorSelection =     Package.GetGlobalService(typeof(SVsShellMonitorSelection)) as     IVsMonitorSelection;
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

## <a name="to-persist-the-selected-project-item-property-given-the-project-hierarchy"></a>若要保存選取的專案專案屬性，請指定專案階層

1. 將下列程式碼加入至上一個程式中方法提供的程式碼：

    ```csharp
    IVsBuildPropertyStorage buildPropertyStorage =
        hierarchy as IVsBuildPropertyStorage;
    if (buildPropertyStorage != null)
    {
        buildPropertyStorage.SetItemAttribute(itemId, "Author", "Tom");
    }
    ```

## <a name="to-verify-that-the-property-is-persisted"></a>確認屬性已保存

1. 啟動 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 然後開啟或建立解決方案。

2. 選取 **方案總管** 中的專案專案 VsPkg.cs。

3. 使用中斷點，或判斷是否已載入您的 VSPackage 並執行 SetItemAttribute。

   > [!NOTE]
   > 您可以在 UI 內容中自動載入 VSPackage <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExists_guid> 。 如需詳細資訊，請參閱 [Load vspackage](../extensibility/loading-vspackages.md)。

4. 關閉 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 然後在 [記事本] 中開啟專案檔。 您應該會看到 \<Author> 具有 Tom 值的標記，如下所示：

   ```xml
   <Compile Include="VsPkg.cs">
       <Author>Tom</Author>
   </Compile>
   ```

## <a name="see-also"></a>另請參閱

- [自訂工具](../extensibility/internals/custom-tools.md)
