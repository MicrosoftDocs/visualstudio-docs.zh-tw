---
title: GetFrameworkPath 工作 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#GetFrameworkPath
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- GetFrameworkPath task [MSBuild]
- MSBuild, GetFrameworkPath task
ms.assetid: 5b7bcdd7-d4a0-442d-af29-8aadb3b10598
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d3820cca54cd7d5d2e93e48909627d4200f38983
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2019
ms.locfileid: "54787216"
---
# <a name="getframeworkpath-task"></a>GetFrameworkPath 工作
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
擷取 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 組件的路徑。  
  
## <a name="task-parameters"></a>工作參數  
 下表說明 `GetFrameworkPath` 工作的參數。  
  
|參數|描述|  
|---------------|-----------------|  
|`FrameworkVersion11Path`|選擇性的 `String` 輸出參數。<br /><br /> 包含 Framework 1.1 版組件的路徑 (如果有的話)。 否則傳回 `null`。|  
|`FrameworkVersion20Path`|選擇性的 `String` 輸出參數。<br /><br /> 包含 Framework 2.0 版組件的路徑 (如果有的話)。 否則傳回 `null`。|  
|`FrameworkVersion30Path`|選擇性的 `String` 輸出參數。<br /><br /> 包含 Framework 3.0 版組件的路徑 (如果有的話)。 否則傳回 `null`。|  
|`FrameworkVersion35Path`|選擇性的 `String` 輸出參數。<br /><br /> 包含 Framework 3.5 版組件的路徑 (如果有的話)。 否則傳回 `null`。|  
|`FrameworkVersion40Path`|選擇性的 `String` 輸出參數。<br /><br /> 包含 Framework 4.0 版組件的路徑 (如果有的話)。 否則傳回 `null`。|  
|`Path`|選擇性的 `String` 輸出參數。<br /><br /> 包含最新 Framework 版組件的路徑 (如果有的話)。 否則傳回 `null`。|  
  
## <a name="remarks"></a>備註  
 如果已安裝數個版本的 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]，這項工作會傳回 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 設計上預期執行的版本。  
  
 除了上述所列的參數，此項工作還會繼承 <xref:Microsoft.Build.Tasks.TaskExtension> 類別中的參數，而該類別本身又繼承 <xref:Microsoft.Build.Utilities.Task> 類別。 如需這些其他參數的清單及其說明，請參閱 [TaskExtension Base Class](../msbuild/taskextension-base-class.md)。  
  
## <a name="example"></a>範例  
 下列範例使用 `GetFrameworkPath` 工作，將 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 的路徑儲存在 `FrameworkPath` 屬性中。  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="GetPath">  
        <GetFrameworkPath>  
            <Output  
                TaskParameter="Path"  
                PropertyName="FrameworkPath" />  
        </GetFrameworkPath>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>請參閱  
 [工作](../msbuild/msbuild-tasks.md)   
 [工作參考](../msbuild/msbuild-task-reference.md)
