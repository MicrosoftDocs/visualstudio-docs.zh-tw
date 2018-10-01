---
title: GenerateTrustInfo 工作 | Microsoft Docs
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
- MSBuild, GenerateTrustInfo task
- GenerateTrustInfo task [MSBuild]
ms.assetid: 3ca60816-4bb0-4fef-ae43-ca0bfb63def3
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6f755994c09e0634df814683b77d925f2293b6cf
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47486049"
---
# <a name="generatetrustinfo-task"></a>GenerateTrustInfo 工作
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[GenerateTrustInfo 工作](https://docs.microsoft.com/visualstudio/msbuild/generatetrustinfo-task)。  
  
  
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



