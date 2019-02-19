---
title: UpdateManifest 工作 | Microsoft Docs
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
- MSBuild, UpdateManifest task
- UpdateManifest task [MSBuild]
ms.assetid: 1291fd33-b89e-4e15-8fb1-69f9625cf2d2
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 54364f40c25deb4a32431c42f74d76bbdd42b155
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2019
ms.locfileid: "54802143"
---
# <a name="updatemanifest-task"></a>UpdateManifest 工作
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
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
  
## <a name="see-also"></a>請參閱  
 [工作](../msbuild/msbuild-tasks.md)   
 [工作參考](../msbuild/msbuild-task-reference.md)
