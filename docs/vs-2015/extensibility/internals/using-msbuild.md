---
title: 使用 MSBuild | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, compiling with MSBuild
- MSBuild, extensibility
- packages, compiling with MSBuild
ms.assetid: 9d38c388-1f64-430e-8f6c-e88bc99a4260
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a4338649885c75a81fdd08d5d4dd0ca4d00158ec
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58940483"
---
# <a name="using-msbuild"></a>使用 MSBuild
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

MSBuild 會提供定義完善且可延伸的 XML 格式，來建立專案檔案的完整描述來建置、 建置工作，以及組建組態的專案項目。  
  
 以 MSBuild 為基礎的語言專案系統的端對端範例，請參閱 IronPython 範例深入探討[VSSDK 範例](../../misc/vssdk-samples.md)。  
  
## <a name="general-msbuild-considerations"></a>一般 MSBuild 考量  
 MSBuild 專案檔，例如[!INCLUDE[csprcs](../../includes/csprcs-md.md)].csproj 和[!INCLUDE[vbprvb](../../includes/vbprvb-md.md)].vbproj 檔案，包含資料，會使用在建置階段，但也可以包含在設計階段使用的資料。 建置階段資料會儲存使用 MSBuild 基本項目，包括[項目的項目 (MSBuild)](../../msbuild/item-element-msbuild.md)並[Property 項目 (MSBuild)](../../msbuild/property-element-msbuild.md)。 設計階段資料，也就是特定專案類型，以及任何相關的專案子類型的資料，會儲存在為其保留的自由格式 XML。  
  
 MSBuild 沒有組態物件的原生支援，但未提供條件式屬性指定的特定組態中的資料。 例如:   
  
```  
<OutputDir Condition="'$(Configuration)'=="release'">Bin\MyReleaseConfig</OutputDir>  
```  
  
 如需有關條件式屬性的詳細資訊，請參閱 <<c0> [ 條件式建構](../../msbuild/msbuild-conditional-constructs.md)。  
  
### <a name="extending-msbuild-for-your-project-type"></a>適用於您的專案類型擴充的 MSBuild  
 MSBuild 介面和 Api 會在未來的版本中有所變更[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]。 因此，最好使用 managed 的封裝架構 (MPF) 類別，因為它們提供防護的變更。  
  
 Managed Package Framework 中的專案 (MPFProj) 提供用於建立和管理新的專案系統的協助程式類別。 您可以找到來源的程式碼和編譯指示[專案-Visual Studio 2013 的 MPF](http://mpfproj12.codeplex.com/)。  
  
 特定專案的 MPF 類別如下所示：  
  
|類別|實作|  
|-----------|--------------------|  
|`Microsoft.VisualStudio.Package.ProjectNode`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents>|  
|`Microsoft.VisualStudio.Package.ProjectFactory`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>|  
|`Microsoft.VisualStudio.Package.HierarchyNode`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>|  
|`Microsoft.VisualStudio.Package.ProjectConfig`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>|  
|`Microsoft.VisualStudio.Package.SettingsPage`|<xref:Microsoft.VisualStudio.OLE.Interop.IPropertyPageSite>|  
  
 `Microsoft.VisualStudio.Package.ProjectElement` 類別是 MSBuild 項目包裝函式。  
  
#### <a name="single-file-generators-vs-msbuild-tasks"></a>單一檔案產生器與MSBuild 工作  
 單一檔案產生器是可存取在設計階段，但可以使用 MSBuild 工作，在設計階段和建置時間。 最大的彈性，因此，使用 MSBuild 工作來轉換及產生程式碼。 如需詳細資訊，請參閱 <<c0> [ 自訂工具](../../extensibility/internals/custom-tools.md)。  
  
## <a name="see-also"></a>另請參閱  
 [MSBuild 參考](../../msbuild/msbuild-reference.md)   
 [MSBuild](http://msdn.microsoft.com/7c49aba1-ee6c-47d8-9de1-6f29a906e20b)   
 [自訂工具](../../extensibility/internals/custom-tools.md)
