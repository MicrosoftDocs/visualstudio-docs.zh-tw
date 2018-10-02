---
title: ResolveNonMSBuildProjectOutput 工作 | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, ResolveNonMSBuildProjectOutput task
- ResolveNonMSBuildProjectOutput task [MSBuild]
ms.assetid: a0b8fcec-8c8d-4867-85ac-5304c5108e5e
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 48a67d895c08d5966c2ea4b40140382db9157763
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47489277"
---
# <a name="resolvenonmsbuildprojectoutput-task"></a>ResolveNonMSBuildProjectOutput 工作
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[ResolveNonMSBuildProjectOutput 工作](https://docs.microsoft.com/visualstudio/msbuild/resolvenonmsbuildprojectoutput-task)。  
  
  
決定非 MSBuild 專案參考的輸出檔。  
  
## <a name="parameters"></a>參數  
 下表說明 `ResolveNonMSBuildProjectOutput` 工作的參數。  
  
|參數|描述|  
|---------------|-----------------|  
|`PreresolvedProjectOutputs`|選擇性的 `String` 參數。<br /><br /> 指定 XML 字串，其中包含已解析的專案輸出。|  
|`ProjectReferences`|必要的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 指定專案參考。|  
|`ResolvedOutputPaths`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 輸出參數。<br /><br /> 包含已解析的參考路徑清單 (並保留原始專案參考屬性)。|  
|`UnresolvedProjectReferences`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 輸出參數。<br /><br /> 包含無法使用預先解析的輸出清單來解析的專案參考項目清單。<br /><br /> 由於 Visual Studio 只會預先解析非 MSBuild 的專案，因此這表示此份清單中的專案參考為 MSBuild 格式。|  
  
## <a name="remarks"></a>備註  
 除了具有表格中所列的參數之外，此工作也繼承 <xref:Microsoft.Build.Tasks.TaskExtension> 類別的參數，而該類別本身又繼承 <xref:Microsoft.Build.Utilities.Task> 類別。 如需這些其他參數的清單及其說明，請參閱 [TaskExtension Base Class](../msbuild/taskextension-base-class.md)。  
  
## <a name="see-also"></a>另請參閱  
 [工作](../msbuild/msbuild-tasks.md)   
 [工作參考](../msbuild/msbuild-task-reference.md)



