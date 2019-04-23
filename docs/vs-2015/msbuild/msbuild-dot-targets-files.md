---
title: MSBuild .Targets 檔案 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- .Targets files
- MSBuild, .Targets files
ms.assetid: f6d98eb4-d2fa-49b7-8e3c-bae1ca3cf596
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 74ac0a2c1ab50cf4c707f4fc9414fe4aa4f403b8
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/17/2019
ms.locfileid: "59655058"
---
# <a name="msbuild-targets-files"></a>MSBuild .Targets 檔案
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 內含數個 .targets 檔案，其中包含適用於通用案例的項目、屬性、目標和工作。 這些檔案會自動匯入大部分的 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 專案檔，以簡化維護和可讀性。  
  
 專案通常會匯入一個或多個 .targets 檔案，用於定義其建置流程。 例如，[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 所建立的 [!INCLUDE[csprcs](../includes/csprcs-md.md)] 專案將會匯入 Microsoft.CSharp.targets，後者會匯入 Microsoft.Common.targets。 [!INCLUDE[csprcs](../includes/csprcs-md.md)] 專案本身將會定義該專案特有的項目和屬性，但 [!INCLUDE[csprcs](../includes/csprcs-md.md)] 專案的標準建置規則是定義於匯入的 .targets 檔案中。  
  
 `$(MSBuildToolsPath)` 值會指定這些通用 .targets 檔案的路徑。 如果 `ToolsVersion` 為 4.0，則檔案位於下列位置︰`WindowsInstallationPath\Microsoft.NET\Framework\v4.0.30319\`  
  
> [!NOTE]
>  如需如何自行建立目標的詳細資訊，請參閱[目標](../msbuild/msbuild-targets.md)。 如需有關如何使用資訊`Import`項目將專案檔插入另一個專案檔，請參閱[匯入項目 (MSBuild)](../msbuild/import-element-msbuild.md)和[How to:在多個專案檔中使用相同的目標](../msbuild/how-to-use-the-same-target-in-multiple-project-files.md)。  
  
## <a name="common-targets-files"></a>通用的 .Targets 檔案  
  
|.Targets 檔案|描述|  
|-------------------|-----------------|  
|Microsoft.Common.targets|針對 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 和 [!INCLUDE[csprcs](../includes/csprcs-md.md)] 專案定義標準建置程序的步驟。<br /><br /> 已透過 Microsoft.CSharp.targets 和 Microsoft.VisualBasic.targets 檔案匯入，其中包含下列陳述式：`<Import Project="Microsoft.Common.targets" />`|  
|Microsoft.CSharp.targets|針對 Visual C# 專案定義標準建置程序的步驟。<br /><br /> 已透過 Visual C# 專案檔 (.csproj) 匯入，其中包含下列陳述式︰`<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />`|  
|Microsoft.VisualBasic.targets|針對 Visual Basic 專案定義標準建置程序的步驟。<br /><br /> 已透過 Visual Basic 專案檔 (.vbproj) 匯入，其中包含下列陳述式︰`<Import Project="$(MSBuildToolsPath)\Microsoft.VisualBasic.targets" />`|  
  
## <a name="see-also"></a>另請參閱  
 [Import 項目 (MSBuild)](../msbuild/import-element-msbuild.md)   
 [MSBuild 參考](../msbuild/msbuild-reference.md)  
 [MSBuild](msbuild.md)
