---
title: UpdateManifest 工作 | Microsoft Docs
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 79d4eb1d9ea90f2ee10a5b285e8fd841b5405203
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54961292"
---
# <a name="updatemanifest-task"></a>UpdateManifest 工作
更新資訊清單中選取的屬性，並重新簽署。  
  
## <a name="parameters"></a>參數  
 下表說明 `UpdateManifest` 工作的參數。  
  
|參數|說明|  
|---------------|-----------------|  
|`ApplicationManifest`|必要的 <xref:Microsoft.Build.Framework.ITaskItem> 參數。<br /><br /> 指定應用程式資訊清單。|  
|`ApplicationPath`|必要的 `String` 參數。<br /><br /> 指定應用程式資訊清單的路徑。|  
|`InputManifest`|必要的 <xref:Microsoft.Build.Framework.ITaskItem> 參數。<br /><br /> 指定要更新的資訊清單。|  
|`OutputManifest`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem> 輸出參數。<br /><br /> 指定包含更新過之屬性的資訊清單。|  
  
## <a name="remarks"></a>備註  
 除了具有表格中所列的參數之外，此工作會繼承 <xref:Microsoft.Build.Utilities.Task> 類別中的參數。 如需這些額外參數及其說明的清單，請參閱 [Task 基底類別](../msbuild/task-base-class.md)。  
  
## <a name="see-also"></a>另請參閱  
 [工作](../msbuild/msbuild-tasks.md)   
 [工作參考](../msbuild/msbuild-task-reference.md)