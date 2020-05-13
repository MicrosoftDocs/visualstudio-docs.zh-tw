---
title: MSBuild .目的檔案 |微軟文檔
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
ms.openlocfilehash: 3faa9ca73592722a950f9914437884c33122070e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633352"
---
# <a name="msbuild-targets-files"></a>MSBuild .targets 檔案

MSBuild 包括多個 *.target*檔，其中包含常見方案的專案、屬性、目標和任務。 這些檔會自動導入到大多數 Visual Studio 專案檔案中，以簡化維護和可讀性。

 專案通常會匯入一或多個 *.targets* 檔案，用於定義其建置流程。 例如，Visual Studio 創建的 C# 專案將導入*Microsoft.CSharp.目標*，該目標導入*Microsoft.Common.target*。 C# 專案本身將定義特定于該專案的項和屬性，但 C# 專案的標準建置規則在導入的 *.targets*檔中定義。

 `$(MSBuildToolsPath)` 值會指定這些通用 *.targets* 檔案的路徑。 如果`ToolsVersion`為 4.0，則檔位於以下位置*\<：Windows 安裝路徑>\Microsoft.NET_Framework_v4.0.30319\\ *

> [!NOTE]
> 如需如何自行建立目標的詳細資訊，請參閱[目標](../msbuild/msbuild-targets.md)。 如需如何使用 `Import` 項目來將專案檔插入另一個專案檔的資訊，請參閱 [Import 項目 (MSBuild)](../msbuild/import-element-msbuild.md) 和[如何：在多個專案檔中使用相同的目標](../msbuild/how-to-use-the-same-target-in-multiple-project-files.md)。

## <a name="common-targets-files"></a>通用 .targets 檔案

| *.targets* 檔案 | 描述 |
|---------------------------------| - |
| *Microsoft.Common.targets* | 定義視覺化基本專案和 C# 專案的標準生成流程中的步驟。<br /><br /> 已透過 *Microsoft.CSharp.targets* 和 *Microsoft.VisualBasic.targets* 檔案匯入，其中包含下列陳述式：`<Import Project="Microsoft.Common.targets" />` |
| *Microsoft.CSharp.targets* | 針對 Visual C# 專案定義標準建置程序的步驟。<br /><br /> 已透過 Visual C# 專案檔 (*.csproj*) 匯入，其中包含下列陳述式︰`<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />` |
| *Microsoft.VisualBasic.targets* | 針對 Visual Basic 專案定義標準建置程序的步驟。<br /><br /> 由 Visual Basic 專案檔案 *（.vbproj*） 導入，其中包括以下語句：`<Import Project="$(MSBuildToolsPath)\Microsoft.VisualBasic.targets" />` |

## <a name="directorybuildtargets"></a>Directory.Build.targets

*Directory.Build.targets* 是使用者定義的檔案，可讓您自訂目錄下的專案。 除非 **ImportDirectoryBuildTargets** 屬性設定為 **false**，否則系統皆會從 *Microsoft.Common.targets* 自動匯入此檔案。 如需詳細資訊，請參閱[自訂組建](customize-your-build.md)。

## <a name="see-also"></a>另請參閱

- [Import 項目 (MSBuild)](../msbuild/import-element-msbuild.md)
- [MSBuild 參考](../msbuild/msbuild-reference.md)
- [MSBuild](../msbuild/msbuild.md)
