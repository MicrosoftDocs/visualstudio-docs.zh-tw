---
title: CombinePath 工作 | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
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
- MSBuild, CombinePath task
- CombinePath task [MSBuild]
ms.assetid: c20edbf4-3d4f-4f66-b1d5-753a0d858ed8
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 71176722443cc2e7f858bbfea85d526a4f4d772d
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49192682"
---
# <a name="combinepath-task"></a>CombinePath 工作
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
將指定的路徑結合成單一路徑。  
  
## <a name="task-parameters"></a>工作參數  
 下表說明 [CombinePath 工作](../msbuild/combinepath-task.md)的參數。  
  
|參數|描述|  
|---------------|-----------------|  
|`BasePath`|必要的 `String` 參數。<br /><br /> 要與其他路徑結合的基底路徑。 可以是相對路徑、絕對路徑或空白。|  
|`Paths`|必要的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 要與 BasePath 結合以形成結合路徑的個別路徑清單。 路徑可為相對或絕對路徑。|  
|`CombinedPaths`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 輸出參數。<br /><br /> 此工作所建立的結合路徑。|  
  
## <a name="remarks"></a>備註  
 除了上述所列的參數，此項工作還會繼承 <xref:Microsoft.Build.Tasks.TaskExtension> 類別中的參數，而該類別本身又繼承 <xref:Microsoft.Build.Utilities.Task> 類別。 如需這些其他參數的清單及其說明，請參閱 [TaskExtension Base Class](../msbuild/taskextension-base-class.md)。  
  
## <a name="see-also"></a>另請參閱  
 [工作](../msbuild/msbuild-tasks.md)   
 [工作參考](../msbuild/msbuild-task-reference.md)



