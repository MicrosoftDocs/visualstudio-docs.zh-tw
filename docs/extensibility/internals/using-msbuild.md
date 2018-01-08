---
title: "使用 MSBuild |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSPackages, compiling with MSBuild
- MSBuild, extensibility
- packages, compiling with MSBuild
ms.assetid: 9d38c388-1f64-430e-8f6c-e88bc99a4260
caps.latest.revision: "20"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 3b9d05b85cacfcdf90a883ffd08d4dec316eaafc
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="using-msbuild"></a>使用 MSBuild
MSBuild 提供妥善定義、 可延伸的 XML 格式，來建立專案檔案的完整描述可建置、 建置工作，與組建組態的專案項目。  
  
## <a name="general-msbuild-considerations"></a>一般 MSBuild 考量  
 MSBuild 專案檔，例如[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)].csproj 和[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)].vbproj 檔案包含在建置時，會使用，但也可以包含在設計階段使用的資料的資料。 建置時間資料會儲存使用 MSBuild 基本項目，包括[item 項目 (MSBuild)](../../msbuild/item-element-msbuild.md)和[屬性項目 (MSBuild)](../../msbuild/property-element-msbuild.md)。 設計階段資料，這是特定專案類型，以及任何相關的專案子類型的資料，會儲存在保留給它的任意 XML。  
  
 MSBuild 並沒有原生支援的組態物件，只針對指定的特定組態中的資料提供條件式屬性。 例如:   
  
```xml  
<OutputDir Condition="'$(Configuration)'=="release'">Bin\MyReleaseConfig</OutputDir>  
```  
  
 如需條件式屬性的詳細資訊，請參閱[條件式建構](../../msbuild/msbuild-conditional-constructs.md)。  
  
### <a name="extending-msbuild-for-your-project-type"></a>適用於您的專案類型擴充 MSBuild  
 MSBuild 介面和應用程式開發介面是未來的版本中可能會變更[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 因此，最好使用 managed 的封裝架構 (MPF) 類別，因為它們提供防護的變更。  
  
 Managed Package Framework 的專案 (MPFProj) 提供建立和管理新的專案系統的 helper 類別。 您可以找到來源的程式碼與編譯指示[專案的 Visual Studio 2013 的 MPF](http://mpfproj12.codeplex.com/)。  
  
 特定專案的 MPF 類別如下所示：  
  
|類別|實作|  
|-----------|--------------------|  
|`Microsoft.VisualStudio.Package.ProjectNode`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents>|  
|`Microsoft.VisualStudio.Package.ProjectFactory`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>|  
|`Microsoft.VisualStudio.Package.HierarchyNode`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>|  
|`Microsoft.VisualStudio.Package.ProjectConfig`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>|  
|`Microsoft.VisualStudio.Package.SettingsPage`|<xref:Microsoft.VisualStudio.OLE.Interop.IPropertyPageSite>|  
  
 `Microsoft.VisualStudio.Package.ProjectElement`類別是 MSBuild 項目包裝函式。  
  
#### <a name="single-file-generators-vs-msbuild-tasks"></a>單一檔案產生器與MSBuild 工作  
 單一檔案產生器是可存取在執行階段，但 MSBuild 工作可用來在設計階段和建置時間。 最大的彈性，因此，使用 MSBuild 工作來轉換，並產生程式碼。 如需詳細資訊，請參閱[自訂工具](../../extensibility/internals/custom-tools.md)。  
  
## <a name="see-also"></a>請參閱  
 [MSBuild 參考](../../msbuild/msbuild-reference.md)   
 [MSBuild](../../msbuild/msbuild.md)   
 [自訂工具](../../extensibility/internals/custom-tools.md)