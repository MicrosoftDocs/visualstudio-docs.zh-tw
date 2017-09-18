---
title: "保存專案項目屬性 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "屬性，加入至專案項目"
  - "專案項目，加入屬性"
ms.assetid: d7a0f2b0-d427-4d49-9536-54edfb37c0f3
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# 保存專案項目屬性
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您可能想要保存的屬性，您將加入至專案項目，例如來源檔案的作者。 您可以將屬性儲存在專案檔。  
  
 保存的屬性，在專案檔中的第一個步驟是取得做為專案的階層架構 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> 介面。 您可以取得此介面，使用自動化，或使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>。 一旦您取得的介面，您可以使用它來判斷目前選取的專案項目。 專案項目 ID 之後，您可以使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A> 加入屬性。  
  
 下列程序，您將保存 VsPkg.cs 屬性 `Author` 值 `Tom` 專案檔中。  
  
### 若要取得 DTE 物件的專案階層  
  
1.  下列程式碼加入 VSPackage:  
  
    ```c#  
    EnvDTE.DTE dte = (EnvDTE.DTE)Package.GetGlobalService(typeof(EnvDTE.DTE)); EnvDTE.Project project = dte.Solution.Projects.Item(1); string uniqueName = project.UniqueName; IVsSolution solution = (IVsSolution)Package.GetGlobalService(typeof(SVsSolution)); IVsHierarchy hierarchy; solution.GetProjectOfUniqueName(uniqueName, out hierarchy);  
    ```  
  
### 保存與 DTE 物件的專案項目屬性  
  
1.  將下列程式碼加入至先前的程序中的方法所提供的程式碼:  
  
    ```c#  
    IVsBuildPropertyStorage buildPropertyStorage = hierarchy as IVsBuildPropertyStorage; if (buildPropertyStorage != null) { uint itemId; string fullPath = (string)project.ProjectItems.Item( "VsPkg.cs").Properties.Item("FullPath").Value; hierarchy.ParseCanonicalName(fullPath, out itemId); buildPropertyStorage.SetItemAttribute(itemId, "Author", "Tom"); }  
    ```  
  
### 若要取得使用 IVsMonitorSelection 專案階層架構  
  
1.  下列程式碼加入 VSPackage:  
  
    ```c#  
    IVsHierarchy hierarchy = null; IntPtr hierarchyPtr = IntPtr.Zero; IntPtr selectionContainer = IntPtr.Zero; uint itemid; // Retrieve shell interface in order to get current selection IVsMonitorSelection monitorSelection =     Package.GetGlobalService(typeof(SVsShellMonitorSelection)) as     IVsMonitorSelection; if (monitorSelection == null) throw new InvalidOperationException(); try { // Get the current project hierarchy, project item, and selection container for the current selection // If the selection spans multiple hierachies, hierarchyPtr is Zero IVsMultiItemSelect multiItemSelect = null; ErrorHandler.ThrowOnFailure( monitorSelection.GetCurrentSelection( out hierarchyPtr, out itemid, out multiItemSelect, out selectionContainer)); // We only care if there is only one node selected in the tree if (!(itemid == VSConstants.VSITEMID_NIL || hierarchyPtr == IntPtr.Zero || multiItemSelect != null || itemid == VSConstants.VSITEMID_SELECTION)) { hierarchy = Marshal.GetObjectForIUnknown(hierarchyPtr) as IVsHierarchy; } } finally { if (hierarchyPtr != IntPtr.Zero) Marshal.Release(hierarchyPtr); if (selectionContainer != IntPtr.Zero) Marshal.Release(selectionContainer); }  
    ```  
  
2.  
  
### 保留選取的專案項目屬性，指定專案階層架構  
  
1.  將下列程式碼加入至先前的程序中的方法所提供的程式碼:  
  
    ```  
    IVsBuildPropertyStorage buildPropertyStorage = hierarchy as IVsBuildPropertyStorage; if (buildPropertyStorage != null) { buildPropertyStorage.SetItemAttribute(itemId, "Author", "Tom"); }  
    ```  
  
### 若要確認保存的屬性  
  
1.  啟動 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 然後開啟或建立的方案。  
  
2.  選取專案項目中的 VsPkg.cs **方案總管\] 中**。  
  
3.  使用中斷點或否則決定會載入 VSPackage 和 SetItemAttribute 執行。  
  
    > [!NOTE]
    >  您可以自動載入 VSPackage UI 內 <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_SolutionExists>。 如需詳細資訊，請參閱[載入 Vspackage](../extensibility/loading-vspackages.md)。  
  
4.  關閉 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ，然後在記事本中開啟專案檔案。 您應該看見值 Tom，\< 作者 \> 標記，如下所示:  
  
    ```  
    <Compile Include="VsPkg.cs"> <Author>Tom</Author> </Compile>  
    ```  
  
## 請參閱  
 [自訂工具](../extensibility/internals/custom-tools.md)