---
title: 使用 MSBuild | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, compiling with MSBuild
- MSBuild, extensibility
- packages, compiling with MSBuild
ms.assetid: 9d38c388-1f64-430e-8f6c-e88bc99a4260
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f961249ff584f7767dc2505bb20b1fb0961b7dd3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704294"
---
# <a name="using-msbuild"></a>使用 MSBuild
MSBuild 提供了定義良好的可擴展 XML 格式,用於創建專案檔,這些檔完全描述要生成的專案項、生成任務和生成配置。

## <a name="general-msbuild-considerations"></a>一般 MS 建置注意事項
 MSBuild 專案檔([!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]例如 .csproj[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]和 .vbproj 檔)包含在生成時使用的數據,但也可能包含在設計時使用的數據。 生成時間數據使用 MSBuild 基元儲存,包括[專案元素 (MSBuild)](../../msbuild/item-element-msbuild.md)和[屬性元素 (MSBuild)。](../../msbuild/property-element-msbuild.md) 設計時資料(特定於項目類型的數據和任何相關的專案子類型)存儲在為其保留的自由格式 XML 中。

 MSBuild 對配置物件沒有本機支援,但確實提供了用於指定特定於配置的數據的條件屬性。 例如：

```xml
<OutputDir Condition="'$(Configuration)'=="release'">Bin\MyReleaseConfig</OutputDir>
```

 有關條件屬性的詳細資訊,請參閱[條件建構](../../msbuild/msbuild-conditional-constructs.md)。

### <a name="extending-msbuild-for-your-project-type"></a>延伸項目型態的 MSBuild
 MSBuild 介面與 API[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]可能會在的未來版本中更改 。 因此,謹慎使用託管包框架 (MPF) 類,因為它們提供遮罩,使其免受更改。

 專案管理套件框架 (MPFProj) 提供用於創建和管理新專案系統的幫助程式類。 您可以在[專案 MPF - Visual Studio 2013](https://github.com/tunnelvisionlabs/MPFProj10)找到原始碼和編譯說明。

 特定於項目的 MPF 類別的以下的名稱:

|類別|實作|
|-----------|--------------------|
|`Microsoft.VisualStudio.Package.ProjectNode`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents>|
|`Microsoft.VisualStudio.Package.ProjectFactory`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>|
|`Microsoft.VisualStudio.Package.HierarchyNode`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>|
|`Microsoft.VisualStudio.Package.ProjectConfig`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>|
|`Microsoft.VisualStudio.Package.SettingsPage`|<xref:Microsoft.VisualStudio.OLE.Interop.IPropertyPageSite>|

 `Microsoft.VisualStudio.Package.ProjectElement`類是MSBuild項的包裝器。

#### <a name="single-file-generators-vs-msbuild-tasks"></a>單個檔案產生器與 MS 建構工作
 單個檔生成器僅在設計時訪問,但 MSBuild 任務可以在設計時間和生成時使用。 因此,為了獲得最佳靈活性,請使用 MSBuild 任務來轉換和生成代碼。 有關詳細資訊,請參閱[自訂工具](../../extensibility/internals/custom-tools.md)。

## <a name="see-also"></a>另請參閱
- [MSBuild 參考](../../msbuild/msbuild-reference.md)
- [MSBuild](../../msbuild/msbuild.md)
- [自訂工具](../../extensibility/internals/custom-tools.md)
