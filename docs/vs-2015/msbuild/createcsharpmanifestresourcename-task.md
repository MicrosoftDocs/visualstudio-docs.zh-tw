---
title: CreateCSharpManifestResourceName 工作 | Microsoft Docs
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
- MSBuild, CreateCSharpManifestResourceName task
- CreateCSharpManifestResourceName task [MSBuild]
ms.assetid: 2ace88c1-d757-40a7-8158-c1d3f5ff0511
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9308f94e865bfe54384719d8f57f3ad1819c79fb
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 04/17/2019
ms.locfileid: "59664199"
---
# <a name="createcsharpmanifestresourcename-task"></a>CreateCSharpManifestResourceName 工作
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

從指定的 .resx 檔案名稱或其他資源，建立 [!INCLUDE[csprcs](../includes/csprcs-md.md)] 樣式的資訊清單名稱。  
  
## <a name="parameters"></a>參數  
 下表描述 [CreateCSharpManifestResourceName 工作](../msbuild/createcsharpmanifestresourcename-task.md)的參數。  
  
|參數|說明|  
|---------------|-----------------|  
|`ManifestResourceNames`|<xref:Microsoft.Build.Framework.ITaskItem> `[]` 輸出唯讀參數。<br /><br /> 產生的資訊清單名稱。|  
|`ResourceFiles`|必要的 `String` 參數。<br /><br /> 建立 [!INCLUDE[csprcs](../includes/csprcs-md.md)] 資訊清單名稱的來源資源檔名稱。|  
|`RootNamespace`|選擇性的 `String` 參數。<br /><br /> 資源檔的根命名空間，通常取自專案檔。 可以是 `null`。|  
|`PrependCultureAsDirectory`|選擇性的 `Boolean` 參數。<br /><br /> 如果是 `true`，就會在資訊清單資源名稱正前方加入文化特性名稱做為目錄名稱。 預設值為 `true`。|  
|`ResourceFilesWithManifestResourceNames`|選擇性的 `String` 唯讀輸出參數。<br /><br /> 傳回現在包含資訊清單資源名稱的資源檔名稱。|  
  
## <a name="remarks"></a>備註  
 [CreateVisualBasicManifestResourceName 工作](../msbuild/createvisualbasicmanifestresourcename-task.md)會決定要指派給指定的 .resx 或其他資源檔的適當資訊清單資源名稱。 此工作會為資源檔提供邏輯名稱，然後將它附加到輸出參數做為中繼資料。  
  
 除了上述所列的參數，此項工作還會繼承 <xref:Microsoft.Build.Tasks.TaskExtension> 類別中的參數，而該類別本身又繼承 <xref:Microsoft.Build.Utilities.Task> 類別。 如需這些其他參數的清單及其說明，請參閱 [TaskExtension Base Class](../msbuild/taskextension-base-class.md)。  
  
## <a name="see-also"></a>請參閱  
 [工作](../msbuild/msbuild-tasks.md)   
 [工作參考](../msbuild/msbuild-task-reference.md)
