---
title: GetFrameworkSdkPath 工作 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#GetFrameworkSdkPath
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- GetFrameworkSdkPath task [MSBuild]
- MSBuild, GetFrameworkSdkPath task
ms.assetid: 2ef82b98-02b6-40cf-a9b5-f0e882fb5064
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 44d128df04ef13ea6ee4b5b20368b5932842cc3d
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/19/2018
ms.locfileid: "31578677"
---
# <a name="getframeworksdkpath-task"></a>GetFrameworkSdkPath 工作
擷取 [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)] 的路徑。  
  
## <a name="task-parameters"></a>工作參數  
 下表說明 `GetFrameworkSdkPath` 工作的參數。  
  
|參數|描述|  
|---------------|-----------------|  
|`FrameworkSdkVersion20Path`|選擇性的 `String` 唯讀輸出參數。<br /><br /> 傳回 .NET SDK 2.0 版的路徑 (如果存在的話)。 否則傳回 `String.Empty`。|  
|`FrameworkSdkVersion35Path`|選擇性的 `String` 唯讀輸出參數。<br /><br /> 傳回 .NET SDK 3.5 版的路徑 (如果存在的話)。 否則傳回 `String.Empty`。|  
|`FrameworkSdkVersion40Path`|選擇性的 `String` 唯讀輸出參數。<br /><br /> 傳回 .NET SDK 4.0 版的路徑 (如果存在的話)。 否則傳回 `String.Empty`。|  
|`Path`|選擇性的 `String` 輸出參數。<br /><br /> 包含最新的 .NET SDK 路徑 (如果已有任何版本的話)。 否則傳回 `String.Empty`。|  
  
## <a name="remarks"></a>備註  
 除了上述所列的參數，此項工作還會繼承 <xref:Microsoft.Build.Tasks.TaskExtension> 類別中的參數，而該類別本身又繼承 <xref:Microsoft.Build.Utilities.Task> 類別。 如需這些其他參數的清單及其說明，請參閱 [TaskExtension Base Class](../msbuild/taskextension-base-class.md)。  
  
## <a name="example"></a>範例  
 下列範例使用 `GetFrameworkSdkPath` 工作，將 [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] 的路徑儲存在 `SdkPath` 屬性中。  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="GetPath">  
        <GetFrameworkSdkPath>  
            <Output  
                TaskParameter="Path"  
                PropertyName="SdkPath" />  
        </GetFrameworkSdkPath>  
        <Message Text="$(SdkPath)"/>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>請參閱  
 [工作](../msbuild/msbuild-tasks.md)   
 [工作參考](../msbuild/msbuild-task-reference.md)