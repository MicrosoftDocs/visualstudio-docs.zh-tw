---
title: UpdateManifest 工作 | Microsoft Docs
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
- MSBuild, UpdateManifest task
- UpdateManifest task [MSBuild]
ms.assetid: 1291fd33-b89e-4e15-8fb1-69f9625cf2d2
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 39bd26aacba67b8eb87fecdc46bc54f01e600dfe
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47488554"
---
# <a name="updatemanifest-task"></a>UpdateManifest 工作
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[UpdateManifest 工作](https://docs.microsoft.com/visualstudio/msbuild/updatemanifest-task)。  
  
  
更新資訊清單中選取的屬性，並重新簽署。  
  
## <a name="parameters"></a>參數  
 下表說明 `UpdateManifest` 工作的參數。  
  
|參數|描述|  
|---------------|-----------------|  
|`ApplicationManifest`|必要的 <xref:Microsoft.Build.Framework.ITaskItem> 參數。<br /><br /> 指定應用程式資訊清單。|  
|`ApplicationPath`|必要的 `String` 參數。<br /><br /> 指定應用程式資訊清單的路徑。|  
|`InputManifest`|必要的 <xref:Microsoft.Build.Framework.ITaskItem> 參數。<br /><br /> 指定要更新的資訊清單。|  
|`OutputManifest`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem> 輸出參數。<br /><br /> 指定包含更新過之屬性的資訊清單。|  
  
## <a name="remarks"></a>備註  
 除了具有表格中所列的參數之外，此工作會繼承 <xref:Microsoft.Build.Utilities.Task> 類別中的參數。 如需這些其他參數的清單及其說明，請參閱 [Task 基底類別](../msbuild/task-base-class.md)。  
  
## <a name="see-also"></a>另請參閱  
 [工作](../msbuild/msbuild-tasks.md)   
 [工作參考](../msbuild/msbuild-task-reference.md)



