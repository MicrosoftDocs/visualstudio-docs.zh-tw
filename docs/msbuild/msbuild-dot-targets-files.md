---
title: MSBuild .targets 檔案 |Microsoft Docs
description: 瞭解在常見案例中包含專案、屬性、目標和工作的 MSBuild .targets 檔案。
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ee685fc3deada1a3ac36082fa916b50986900f81
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99971241"
---
# <a name="msbuild-targets-files"></a>MSBuild .targets 檔案

MSBuild 包含數個 *.targets* 檔案，其中包含常見案例的專案、屬性、目標和工作。 這些檔案會自動匯入至大部分的 Visual Studio 專案檔，以簡化維護和可讀性。

 專案通常會匯入一或多個 *.targets* 檔案，用於定義其建置流程。 例如，Visual Studio 所建立的 c # 專案將會 *匯入將* 會匯入 *microsoft* 的 .targets。 C # 專案本身將會定義該專案特定的專案和屬性，但 c # 專案的標準組建規則會定義在匯入的 *.targets* 檔案中。

 `$(MSBuildToolsPath)` 值會指定這些通用 *.targets* 檔案的路徑。 如果 `ToolsVersion` 是4.0，則檔案位於下列位置： *\<WindowsInstallationPath> \Microsoft.NET\Framework\v4.0.30319 \\*

> [!NOTE]
> 如需如何自行建立目標的詳細資訊，請參閱[目標](../msbuild/msbuild-targets.md)。 如需如何使用 `Import` 項目來將專案檔插入另一個專案檔的資訊，請參閱 [Import 項目 (MSBuild)](../msbuild/import-element-msbuild.md) 和[如何：在多個專案檔中使用相同的目標](../msbuild/how-to-use-the-same-target-in-multiple-project-files.md)。

## <a name="common-targets-files"></a>通用 .targets 檔案

| *.targets* 檔案 | Description |
|---------------------------------| - |
| *Microsoft.Common.targets* | 定義 Visual Basic 和 c # 專案的標準組建程式中的步驟。<br /><br /> 已透過 *Microsoft.CSharp.targets* 和 *Microsoft.VisualBasic.targets* 檔案匯入，其中包含下列陳述式：`<Import Project="Microsoft.Common.targets" />` |
| *Microsoft.CSharp.targets* | 針對 Visual C# 專案定義標準建置程序的步驟。<br /><br /> 已透過 Visual C# 專案檔 (*.csproj*) 匯入，其中包含下列陳述式︰`<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />` |
| *Microsoft.VisualBasic.targets* | 針對 Visual Basic 專案定義標準建置程序的步驟。<br /><br /> Visual Basic 專案檔匯入 (*vbproj*) ，其中包含下列語句： `<Import Project="$(MSBuildToolsPath)\Microsoft.VisualBasic.targets" />` |

## <a name="directorybuildtargets"></a>Directory.Build.targets

*Directory.Build.targets* 是使用者定義的檔案，可讓您自訂目錄下的專案。 除非 **ImportDirectoryBuildTargets** 屬性設定為 **false**，否則系統皆會從 *Microsoft.Common.targets* 自動匯入此檔案。 如需詳細資訊，請參閱[自訂組建](customize-your-build.md)。

## <a name="see-also"></a>另請參閱

- [Import 項目 (MSBuild)](../msbuild/import-element-msbuild.md)
- [MSBuild 參考](../msbuild/msbuild-reference.md)
- [MSBuild](../msbuild/msbuild.md)
