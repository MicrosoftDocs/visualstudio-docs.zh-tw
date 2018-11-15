---
title: 如何：使用 MSBuild.exe 在方案中建置特定目標 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, building specific targets in a solution
- msbuild.exe, building specific targets in a solution
- MSBuild, msbuild.exe
ms.assetid: f46feb9b-4c16-4fec-b6e1-36a959692ba3
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fb1dc2885d64999ac9f4d12568fd7da29a783d8e
ms.sourcegitcommit: 71218ffc33da325cc1b886f69ff2ca50d44f5f33
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/09/2018
ms.locfileid: "48880652"
---
# <a name="how-to-build-specific-targets-in-solutions-by-using-msbuildexe"></a>如何：使用 MSBuild.exe 在方案中建置特定目標
您可以使用 *MSBuild.exe*，在方案中建置特定專案的特定目標。  
  
#### <a name="to-build-a-specific-target-of-a-specific-project-in-a-solution"></a>在方案中建置特定專案的特定目標  
  
1.  在命令列中，輸入 `MSBuild.exe <SolutionName>.sln`，其中 `<SolutionName>` 會對應至包含您想要執行之目標的方案檔案名稱。  
  
2. 以 \<ProjectName>:\<TargetName> 格式，在 `-target:` 參數之後指定目標。 如果專案名稱包含以下任何字元：`%`、`$`、`@`、`;`、`.`、`(`、`)` 或 `'`，將其取代為指定目標名稱中的 `_`。
  
## <a name="example"></a>範例  
 下列範例會執行 `NotInSlnFolder` 專案的 `Rebuild` 目標，然後執行 `InSolutionFolder` 專案的 `Clean` 目標，其位於 NewFolder 方案資料夾中。  
  
```cmd
msbuild SlnFolders.sln -target:NotInSlnfolder:Rebuild;NewFolder\InSolutionFolder:Clean
```

## <a name="troubleshooting"></a>疑難排解

如果您想要檢視可用的選項，可以使用 MSBuild 所提供的偵錯選項。 設定環境變數 `MSBUILDEMITSOLUTION=1` 及建置解決方案。 這會產生名為 *\<SolutionName>.sln.metaproj* 的 MSBuild 檔案，在建置階段顯示方案中 MSBuild 的內部檢視。 您可以檢查此檢視來判斷哪些目標可用來建置。

除非您需要這個內部檢視，否則請勿以此環境變數設定來建置。 此設定可能會在解決方案中建置專案時造成問題。

## <a name="see-also"></a>另請參閱  
 [命令列參考](../msbuild/msbuild-command-line-reference.md)   
 [MSBuild 參考](../msbuild/msbuild-reference.md)   
 [MSBuild](../msbuild/msbuild.md)  
 [MSBuild 概念](../msbuild/msbuild-concepts.md)
