---
title: MSBuild .targets 檔案 |Microsoft Docs
ms.date: 02/24/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- .targets files
- MSBuild, .targets files
ms.assetid: f6d98eb4-d2fa-49b7-8e3c-bae1ca3cf596
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4dc5df9c4eba4195400b6a41fa50a5c88257d70e
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/01/2020
ms.locfileid: "75566549"
---
# <a name="msbuild-targets-files"></a>MSBuild .targets 檔案
[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 內含數個 .targets 檔案，其中包含適用於通用案例的項目、屬性、目標和工作。 這些檔案會自動匯入大部分的 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 專案檔，以簡化維護和可讀性。

 專案通常會匯入一或多個 *.targets* 檔案，用於定義其建置流程。 例如，[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 所建立的 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 專案將會匯入 *Microsoft.CSharp.targets*，後者會匯入 *Microsoft.Common.targets*。 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 專案本身將會定義該專案特定的項目和屬性，但 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 專案的標準建置規則是定義於匯入的 *.targets* 檔案中。

 `$(MSBuildToolsPath)` 值會指定這些通用 *.targets* 檔案的路徑。 如果 `ToolsVersion` 為 4.0，則檔案位於下列位置︰ *\<WindowsInstallationPath>\Microsoft.NET\Framework\v4.0.30319\\*

> [!NOTE]
> 如需如何自行建立目標的詳細資訊，請參閱[目標](../msbuild/msbuild-targets.md)。 如需如何使用 `Import` 項目來將專案檔插入另一個專案檔的資訊，請參閱 [Import 項目 (MSBuild)](../msbuild/import-element-msbuild.md) 和[如何：在多個專案檔中使用相同的目標](../msbuild/how-to-use-the-same-target-in-multiple-project-files.md)。

## <a name="common-targets-files"></a>通用 .targets 檔案

| *.targets* 檔案 | 描述 |
|---------------------------------| - |
| *Microsoft.Common.targets* | 針對 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 和 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 專案定義標準建置程序的步驟。<br /><br /> 已透過 *Microsoft.CSharp.targets* 和 *Microsoft.VisualBasic.targets* 檔案匯入，其中包含下列陳述式：`<Import Project="Microsoft.Common.targets" />` |
| *Microsoft.CSharp.targets* | 針對 Visual C# 專案定義標準建置程序的步驟。<br /><br /> 已透過 Visual C# 專案檔 ( *.csproj*) 匯入，其中包含下列陳述式︰`<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />` |
| *Microsoft.VisualBasic.targets* | 針對 Visual Basic 專案定義標準建置程序的步驟。<br /><br /> 已透過 Visual Basic 專案檔 ( *.vbproj*) 匯入，其中包含下列陳述式︰`<Import Project="$(MSBuildToolsPath)\Microsoft.VisualBasic.targets" />` |

## <a name="directorybuildtargets"></a>Directory.Build.targets
*Directory.Build.targets* 是使用者定義的檔案，可讓您自訂目錄下的專案。 除非 **ImportDirectoryBuildTargets** 屬性設定為 **false**，否則系統皆會從 *Microsoft.Common.targets* 自動匯入此檔案。 如需詳細資訊，請參閱[自訂組建](customize-your-build.md)。

## <a name="see-also"></a>請參閱
- [Import 項目 (MSBuild)](../msbuild/import-element-msbuild.md)
- [MSBuild 參考](../msbuild/msbuild-reference.md)
- [ MSBuild](../msbuild/msbuild.md)
