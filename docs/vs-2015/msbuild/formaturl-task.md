---
title: FormatUrl 工作 | Microsoft Docs
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
- MSBuild, FormatUrl task
- FormatUrl task [MSBuild]
ms.assetid: 81114b67-520f-43b5-8891-224f68a78516
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d6f3118515d023f9f57d4578d042a0fa5a702872
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54803340"
---
# <a name="formaturl-task"></a>FormatUrl 工作
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
將 URL 轉換為正確的 URL 格式。  
  
## <a name="parameters"></a>參數  
 下表說明 `FormatUrl` 工作的參數。  
  
|參數|說明|  
|---------------|-----------------|  
|`InputUrl`|選擇性的 `String` 參數。<br /><br /> 指定要格式化的 URL。|  
|`OutputUrl`|選擇性的 `String` 輸出參數。<br /><br /> 指定已格式化 URL。|  
  
## <a name="remarks"></a>備註  
 除了具有表格中所列的參數之外，此工作也繼承 <xref:Microsoft.Build.Tasks.TaskExtension> 類別的參數，而該類別本身又繼承 <xref:Microsoft.Build.Utilities.Task> 類別。 如需這些其他參數的清單及其說明，請參閱 [TaskExtension Base Class](../msbuild/taskextension-base-class.md)。  
  
## <a name="see-also"></a>請參閱  
 [工作](../msbuild/msbuild-tasks.md)   
 [工作參考](../msbuild/msbuild-task-reference.md)
