---
title: "ResolveNativeReference 工作 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ResolveNativeReference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, ResolveNativeReference task
- ResolveNativeReference task [MSBuild]
ms.assetid: 56acd101-de77-4eec-92c6-f5c6d2187579
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: a150d36c8bc48d6705b9f3ff1e3cfea0f7c01972
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/09/2018
---
# <a name="resolvenativereference-task"></a>ResolveNativeReference 工作
解析原生參考。 實作 <xref:Microsoft.Build.Tasks.ResolveNativeReference> 類別。 此類別支援的 .NET Framework 結構不適合直接從程式碼使用。  
  
## <a name="task-parameters"></a>工作參數  
 下表說明 `ResolveNativeReference` 工作的參數。  
  
|參數|描述|  
|---------------|-----------------|  
|`AdditionalSearchPaths`|必要的 <xref:System.String?displayProperty=fullName>`[]` 參數。<br /><br /> 取得或設定搜尋路徑，以解析原生參考的組件識別碼。|  
|`ContainedComComponents`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 輸出參數。<br /><br /> 取得或設定原生組譯碼的 COM 元件。|  
|`ContainedLooseEtcFiles`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 輸出參數。<br /><br /> 取得或設定原生資訊清單中列出的鬆散 Etc 檔案。|  
|`ContainedLooseTlbFiles`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 輸出參數。<br /><br /> 取得或設定原生組譯碼的鬆散 .tlb 檔案。|  
|`ContainedPrerequisiteAssemblies`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 輸出參數。<br /><br /> 取得或設定必須存在才能使用資訊清單的組件。|  
|`ContainedTypeLibraries`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 輸出參數。<br /><br /> 取得或設定原生組譯碼的類型程式庫。|  
|`ContainingReferenceFiles`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 輸出參數。<br /><br /> 取得或設定參考檔。|  
|`NativeReferences`|必要的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 取得或設定 Win32 原生組件參考。|  
  
## <a name="remarks"></a>備註  
 除了上述所列的參數，此項工作還會繼承 <xref:Microsoft.Build.Tasks.TaskExtension> 類別中的參數，而該類別本身又繼承 <xref:Microsoft.Build.Utilities.Task> 類別。 如需這些其他參數的清單及其說明，請參閱 [TaskExtension Base Class](../msbuild/taskextension-base-class.md)。  
  
## <a name="see-also"></a>請參閱  
 [工作](../msbuild/msbuild-tasks.md)   
 [工作參考](../msbuild/msbuild-task-reference.md)