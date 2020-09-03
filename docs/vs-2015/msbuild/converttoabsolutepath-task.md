---
title: ConvertToAbsolutePath 工作 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ConvertToAbsolutePath
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ConvertToAbsolutePath task [MSBuild]
- MSBuild, ConvertToAbsolutePath task
ms.assetid: f1af2cb8-b4ef-4a72-be80-22fa526c4491
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 399ffeae65ba935e3682b54eff5ee1b0b687aa9d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184076"
---
# <a name="converttoabsolutepath-task"></a>ConvertToAbsolutePath 工作
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

將相對路徑或參考轉換為絕對路徑。  
  
## <a name="task-parameters"></a>工作參數  
 下表說明 `ConvertToAbsolutePath` 工作的參數。  
  
|參數|描述|  
|---------------|-----------------|  
|`Paths`|必要的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 要轉換為絕對路徑的相對路徑清單。|  
|`AbsolutePaths`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 輸出參數。<br /><br /> 已傳入項目的絕對路徑清單。|  
  
## <a name="remarks"></a>備註  
 除了上述所列的參數，此項工作還會繼承 <xref:Microsoft.Build.Tasks.TaskExtension> 類別中的參數，而該類別本身又繼承 <xref:Microsoft.Build.Utilities.Task> 類別。 如需這些其他參數的清單及其說明，請參閱 [TaskExtension 基底類別](../msbuild/taskextension-base-class.md)。  
  
## <a name="see-also"></a>另請參閱  
 [任務](../msbuild/msbuild-tasks.md)   
 [工作參考](../msbuild/msbuild-task-reference.md)
