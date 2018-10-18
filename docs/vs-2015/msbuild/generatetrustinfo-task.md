---
title: GenerateTrustInfo 工作 | Microsoft Docs
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
- MSBuild, GenerateTrustInfo task
- GenerateTrustInfo task [MSBuild]
ms.assetid: 3ca60816-4bb0-4fef-ae43-ca0bfb63def3
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a20a50e74f702c1c015f29abde81b2e24a5551b5
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49208690"
---
# <a name="generatetrustinfo-task"></a>GenerateTrustInfo 工作
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
從基底資訊清單，以及從 `TargetZone` 與 `ExcludedPermissions` 參數產生應用程式信任。  
  
## <a name="parameters"></a>參數  
 下表說明 `GenerateTrustInfo` 工作的參數。  
  
|參數|描述|  
|---------------|-----------------|  
|`ApplicationDependencies`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 指定相依組件。|  
|`BaseManifest`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem> 參數。<br /><br /> 指定要從中產生應用程式信任的基底資訊清單。|  
|`ExcludedPermissions`|選擇性的 `String` 參數。<br /><br /> 指定要從區域預設權限集排除的一或多個權限身分識別值，該值以分號分隔。|  
|`TargetZone`|選擇性的 `String` 參數。<br /><br /> 指定取自電腦原則的區域預設權限集合。|  
|`TrustInfoFile`|必要的 <xref:Microsoft.Build.Framework.ITaskItem> 輸出參數。<br /><br /> 指定包含應用程式安全性信任資訊的檔案。|  
  
## <a name="remarks"></a>備註  
 除了具有表格中所列的參數之外，此工作也繼承 <xref:Microsoft.Build.Tasks.TaskExtension> 類別的參數，而該類別本身又繼承 <xref:Microsoft.Build.Utilities.Task> 類別。 如需這些其他參數的清單及其說明，請參閱 [TaskExtension Base Class](../msbuild/taskextension-base-class.md)。  
  
## <a name="see-also"></a>另請參閱  
 [工作](../msbuild/msbuild-tasks.md)   
 [工作參考](../msbuild/msbuild-task-reference.md)



