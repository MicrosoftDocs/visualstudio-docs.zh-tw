---
title: GetReferenceAssemblyPaths 工作 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 178ef49c-5dee-405b-a14b-a37f41dc0609
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4563e1c28c17a173c211f979d2ca46503a6d19a7
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2019
ms.locfileid: "54805126"
---
# <a name="getreferenceassemblypaths-task"></a>GetReferenceAssemblyPaths 工作
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
傳回各種架構的參考組件路徑。  
  
## <a name="parameters"></a>參數  
 下表說明 `GetReferenceAssemblyPaths` 工作的參數。  
  
|參數|描述|  
|---------------|-----------------|  
|`ReferenceAssemblyPaths`|選擇性的 `String[]` 輸出參數。<br /><br /> 根據 `TargetFrameworkMoniker` 參數傳回路徑。 如果 `TargetFrameworkMoniker` 是 Null 或空白，則此路徑為 `String.Empty`。|  
|`FullFrameworkReferenceAssemblyPaths`|選擇性的 `String[]` 輸出參數。<br /><br /> 根據 `TargetFrameworkMoniker` 參數傳回路徑，而不考慮 Moniker 的設定檔部分。 如果 `TargetFrameworkMoniker` 是 Null 或空白，則此路徑為 `String.Empty`。|  
|`TargetFrameworkMoniker`|選擇性的 `String` 參數。<br /><br /> 指定與參考組件路徑建立關聯的目標 Framework Moniker。|  
|`RootPath`|選擇性的 `String` 參數。<br /><br /> 指定要用來產生參考組件路徑的根路徑。|  
|`BypassFrameworkInstallChecks`|選擇性 [布林值](<!-- TODO: review code entity reference <xref:assetId:///Boolean?qualifyHint=False&amp;autoUpgrade=True>  -->) 參數。<br /><br /> 如果為 `true`，則會略過 `GetReferenceAssemblyPaths` 預設執行的基本檢查，以確定已根據目標 Framework 來安裝特定執行階段 Framework。|  
|`TargetFrameworkMonikerDisplayName`|選擇性的 `String` 輸出參數。<br /><br /> 指定目標 Framework Moniker 的顯示名稱。|  
  
## <a name="remarks"></a>備註  
 除了具有表格中所列的參數之外，此工作也繼承 <xref:Microsoft.Build.Tasks.TaskExtension> 類別的參數，而該類別本身又繼承 <xref:Microsoft.Build.Utilities.Task> 類別。 如需這些其他參數的清單及其說明，請參閱 [TaskExtension Base Class](../msbuild/taskextension-base-class.md)。  
  
## <a name="see-also"></a>請參閱  
 [工作](../msbuild/msbuild-tasks.md)   
 [工作參考](../msbuild/msbuild-task-reference.md)
