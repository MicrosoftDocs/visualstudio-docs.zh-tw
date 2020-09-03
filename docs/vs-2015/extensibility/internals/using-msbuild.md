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
ms.openlocfilehash: a1ad59e6d8f4cb88004629b0dfd2cdf0631a7824
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "74297667"
---
# <a name="using-msbuild"></a>使用 MSBuild
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

MSBuild 提供定義完善、可擴充的 XML 格式，可建立專案檔，以完整描述要建立的專案專案、組建工作和組建設定。  
  
 如需以 MSBuild 為基礎之語言專案系統的端對端範例，請參閱[VSSDK 範例](../../misc/vssdk-samples.md)中的 IronPython 範例深入探討。  
  
## <a name="general-msbuild-considerations"></a>一般 MSBuild 考慮  
 MSBuild 專案檔（例如 [!INCLUDE[csprcs](../../includes/csprcs-md.md)] .csproj 和 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] . vbproj 檔案）包含在組建階段使用的資料，但也可以包含在設計階段使用的資料。 組建時間資料是使用 MSBuild 基本專案儲存，包括 [ (msbuild) 的 Item 元素 ](../../msbuild/item-element-msbuild.md) ，以及 [ (Msbuild) 的屬性元素 ](../../msbuild/property-element-msbuild.md)。 設計階段資料是專案類型和任何相關專案子類型的特定資料，會以保留給它的自由格式 XML 來儲存。  
  
 MSBuild 沒有設定物件的原生支援，但會提供條件屬性來指定設定特定的資料。 例如：  
  
```  
<OutputDir Condition="'$(Configuration)'=="release'">Bin\MyReleaseConfig</OutputDir>  
```  
  
 如需條件式屬性的詳細資訊，請參閱 [條件式結構](../../msbuild/msbuild-conditional-constructs.md)。  
  
### <a name="extending-msbuild-for-your-project-type"></a>為您的專案類型擴充 MSBuild  
 MSBuild 介面和 Api 在未來的版本中可能會變更 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 。 因此，請謹慎使用 managed package framework (MPF) 類別，因為它們提供了變更的防護。  
  
 適用于專案的 Managed 封裝架構 (MPFProj) 提供協助程式類別來建立和管理新的專案系統。 您可以在 [適用于專案的 MPF](https://archive.codeplex.com/?p=mpfproj12)上找到原始程式碼和編譯指示-Visual Studio 2013。  
  
 專案特定的 MPF 類別如下所示：  
  
|類別|實作|  
|-----------|--------------------|  
|`Microsoft.VisualStudio.Package.ProjectNode`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents>|  
|`Microsoft.VisualStudio.Package.ProjectFactory`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>|  
|`Microsoft.VisualStudio.Package.HierarchyNode`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>|  
|`Microsoft.VisualStudio.Package.ProjectConfig`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>|  
|`Microsoft.VisualStudio.Package.SettingsPage`|<xref:Microsoft.VisualStudio.OLE.Interop.IPropertyPageSite>|  
  
 `Microsoft.VisualStudio.Package.ProjectElement` 類別是 MSBuild 專案的包裝函式。  
  
#### <a name="single-file-generators-vs-msbuild-tasks"></a>單一檔案產生器與 MSBuild 工作  
 單一檔案產生器只能在設計階段存取，但是 MSBuild 工作可以在設計階段和組建階段使用。 因此，若要獲得最大的彈性，請使用 MSBuild 工作來轉換和產生程式碼。 如需詳細資訊，請參閱 [自訂工具](../../extensibility/internals/custom-tools.md)。  
  
## <a name="see-also"></a>另請參閱  
 [MSBuild 參考](../../msbuild/msbuild-reference.md)   
 [Msbuild](https://msdn.microsoft.com/7c49aba1-ee6c-47d8-9de1-6f29a906e20b)   
 [自訂工具](../../extensibility/internals/custom-tools.md)
