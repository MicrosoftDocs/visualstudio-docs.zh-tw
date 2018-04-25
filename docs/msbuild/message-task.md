---
title: Message 工作 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Message
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, Message task
- Message task [MSBuild]
ms.assetid: 2293309d-42b6-46dc-9684-8c146f66bc28
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0555ae538cb473d436727da67af40be037c992a4
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/19/2018
---
# <a name="message-task"></a>訊息工作
在建置期間記錄訊息。  
  
## <a name="parameters"></a>參數  
 下表說明 `Message` 工作的參數。  
  
|參數|描述|  
|---------------|-----------------|  
|`Importance`|選擇性的 `String` 參數。<br /><br /> 指定訊息的重要性。 此參數的值可以是 `high`、`normal` 或 `low`。 預設值是 `normal`。|  
|`Text`|選擇性的 `String` 參數。<br /><br /> 要記錄的錯誤文字。|  
  
## <a name="remarks"></a>備註  
 `Message` 工作可讓 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 專案在建置流程各個步驟期間將訊息發送到記錄器。  
  
 如果 `Condition` 參數評估為 `true`，將會記錄 `Text` 參數的值，而建置將會繼續執行。 如果 `Condition` 參數不存在，便會記錄訊息文字。 如需記錄的詳細資訊，請參閱[取得建置記錄檔](../msbuild/obtaining-build-logs-with-msbuild.md)。  
  
 根據預設，訊息會傳送至 MSBuild 主控台記錄器。 您可以設定 <xref:Microsoft.Build.Tasks.TaskExtension.Log%2A> 參數來變更這項作業。 記錄器會解譯 `Importance` 參數。  
  
 除了上述所列的參數，此項工作還會繼承 <xref:Microsoft.Build.Tasks.TaskExtension> 類別中的參數，而該類別本身又繼承 <xref:Microsoft.Build.Utilities.Task> 類別。 如需這些其他參數的清單及其說明，請參閱 [TaskExtension Base Class](../msbuild/taskextension-base-class.md)。  
  
## <a name="example"></a>範例  
 下列程式碼範例會將訊息記錄到所有已註冊的記錄器。  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="DisplayMessages">  
        <Message Text="Project File Name = $(MSBuildProjectFile)" />  
        <Message Text="Project Extension = $(MSBuildProjectExtension)" />  
    </Target>  
    ...  
</Project>  
```  
  
## <a name="see-also"></a>請參閱  
 [工作參考](../msbuild/msbuild-task-reference.md)   
 [取得組建記錄檔](../msbuild/obtaining-build-logs-with-msbuild.md)