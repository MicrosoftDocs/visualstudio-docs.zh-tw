---
title: CreateProperty 工作 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#CreateProperty
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- CreateProperty task [MSBuild]
- MSBuild, CreateProperty task
ms.assetid: fbc31a88-62d4-43d2-b739-68ef3fac38f5
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4843262862501377fd3740639d6a22a79e77879d
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2018
ms.locfileid: "37946341"
---
# <a name="createproperty-task"></a>CreateProperty 工作
將傳入的值填入屬性中。 這允許將值從某個屬性或字串複製至另一個屬性或字串。  
  
## <a name="attributes"></a>屬性  
 下表說明 `CreateProperty` 工作的參數。  
  
|參數|描述|  
|---------------|-----------------|  
|`Value`|選擇性的 `String` 輸出參數。<br /><br /> 指定要複製至新屬性的值。|  
|`ValueSetByTask`|選擇性的 `String` 輸出參數。<br /><br /> 包含與 `Value` 參數相同的值。 因輸出具有最新資訊而略過封入目標時，只有在您想要避免具有 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 所設定的輸出屬性時，才使用此參數。|  
  
## <a name="remarks"></a>備註  
 除了上述所列的參數，此項工作還會繼承 <xref:Microsoft.Build.Tasks.TaskExtension> 類別中的參數，而該類別本身又繼承 <xref:Microsoft.Build.Utilities.Task> 類別。 如需這些其他參數的清單及其描述，請參閱 [TaskExtension 基底類別](../msbuild/taskextension-base-class.md)。  
  
## <a name="example"></a>範例  
 下列範例使用 `CreateProperty` 工作，以使用 `SourceFilename` 和 `SourceFileExtension` 屬性值組合建立 `NewFile` 屬性。  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <PropertyGroup>  
        <SourceFilename>Module1</SourceFilename>  
        <SourceFileExtension>vb</SourceFileExtension>  
    </PropertyGroup>  
  
    <Target Name="CreateProperties">  
  
        <CreateProperty  
            Value="$(SourceFilename).$(SourceFileExtension)">  
            <Output  
                TaskParameter="Value"  
                PropertyName="NewFile" />  
        </CreateProperty>  
  
    </Target>  
  
</Project>  
```  
  
 執行專案之後，`NewFile` 屬性的值是 *Module1.vb*。  
  
## <a name="see-also"></a>另請參閱  
 [工作參考](../msbuild/msbuild-task-reference.md)   
 [工作](../msbuild/msbuild-tasks.md)