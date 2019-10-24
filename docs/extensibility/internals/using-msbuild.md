---
title: 使用 MSBuild | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, compiling with MSBuild
- MSBuild, extensibility
- packages, compiling with MSBuild
ms.assetid: 9d38c388-1f64-430e-8f6c-e88bc99a4260
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c199df38f2cd51307861462af49f58996fe84fe4
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72722162"
---
# <a name="using-msbuild"></a>使用 MSBuild
MSBuild 會提供定義完善的可擴充 XML 格式，以建立可完整描述要建立之專案專案、組建工作和組建設定的專案檔。

## <a name="general-msbuild-considerations"></a>一般 MSBuild 考慮
 MSBuild 專案檔（例如 [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] .csproj 和 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] vbproj 檔案）包含在組建階段使用的資料，但也可以包含在設計階段使用的資料。 使用 MSBuild 基本類型來儲存組建時間資料，包括[Item 元素（msbuild）](../../msbuild/item-element-msbuild.md)和[Property 元素（msbuild）](../../msbuild/property-element-msbuild.md)。 設計階段資料（這是專案類型和任何相關專案子類型的特定資料）會儲存為其保留的自由格式 XML。

 MSBuild 沒有設定物件的原生支援，但會提供用來指定設定特定資料的條件式屬性。 例如:

```xml
<OutputDir Condition="'$(Configuration)'=="release'">Bin\MyReleaseConfig</OutputDir>
```

 如需條件式屬性的詳細資訊，請參閱[條件式結構](../../msbuild/msbuild-conditional-constructs.md)。

### <a name="extending-msbuild-for-your-project-type"></a>擴充專案類型的 MSBuild
 MSBuild 介面和 Api 在未來的 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 版本中可能有所變更。 因此，請謹慎使用 managed package framework （MPF）類別，因為它們會提供變更的防護。

 適用于專案的 Managed 封裝架構（MPFProj）會提供 helper 類別來建立和管理新的專案系統。 您可以在[適用于專案的 MPF](https://github.com/tunnelvisionlabs/MPFProj10)上找到原始程式碼和編譯指示-Visual Studio 2013。

 專案特定的 MPF 類別如下所示：

|執行個體|實作|
|-----------|--------------------|
|`Microsoft.VisualStudio.Package.ProjectNode`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents>|
|`Microsoft.VisualStudio.Package.ProjectFactory`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>|
|`Microsoft.VisualStudio.Package.HierarchyNode`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>|
|`Microsoft.VisualStudio.Package.ProjectConfig`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>|
|`Microsoft.VisualStudio.Package.SettingsPage`|<xref:Microsoft.VisualStudio.OLE.Interop.IPropertyPageSite>|

 `Microsoft.VisualStudio.Package.ProjectElement` 類別是 MSBuild 專案的包裝函式。

#### <a name="single-file-generators-vs-msbuild-tasks"></a>單一檔案產生器與 MSBuild 工作的比較
 單一檔案產生器只能在設計階段存取，但是 MSBuild 工作可以在設計階段和組建階段使用。 因此，為了達到最大彈性，請使用 MSBuild 工作來轉換和產生程式碼。 如需詳細資訊，請參閱[自訂工具](../../extensibility/internals/custom-tools.md)。

## <a name="see-also"></a>請參閱
- [MSBuild 參考](../../msbuild/msbuild-reference.md)
- [ MSBuild](../../msbuild/msbuild.md)
- [自訂工具](../../extensibility/internals/custom-tools.md)