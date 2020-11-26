---
title: AssignProjectConfiguration 工作 | Microsoft Docs
description: 使用 MSBuild AssignProjectConfiguration 工作接受設定字串的清單，並將它們指派給指定的專案。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 09633a0b-8f6f-4aba-8058-7cb4d13ce2c0
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 496b6d538385473d50baec80e30fbc269e06c1f6
ms.sourcegitcommit: b1b747063ce0bba63ad2558fa521b823f952ab51
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96189702"
---
# <a name="assignprojectconfiguration-task"></a>AssignProjectConfiguration 工作

此工作會接受組態字串清單，並將它們指派給指定的專案。

## <a name="task-parameters"></a>工作參數

 下表說明 `AssignProjectConfiguration` 工作的參數。

|參數|描述|
|---------------|-----------------|
|`ProjectReferences`|必要 <xref:Microsoft.Build.Framework.ITaskItem> `[]` 的輸入參數。<br /><br /> 要設定的專案。|
|`SolutionConfigurationContents`|選擇性的 `string` 輸出參數。<br /><br /> 包含 XML 字串，其中含有每個專案的專案組態。 工作會將組態指派給具名的專案。|
|`DefaultToVcxPlatformMapping`|選擇性的 `string` 輸出參數。<br /><br /> 包含以分號分隔的對應清單，這些對應是從大部分類型所使用之平台名稱到 *.vcxproj* 檔案所使用之平台名稱的對應。<br /><br /> 例如：<br /><br /> `"AnyCPU=Win32;X86=Win32;X64=X64"`|
|`VcxToDefaultPlatformMapping`|選用<br /><br /> `string` 輸出參數。<br /><br /> 包含從 .vcxproj 平臺名稱到大部分類型所使用之平臺名稱的對應清單（以分號分隔） *。*<br /><br /> 例如：<br /><br /> `"Win32=AnyCPU;X64=X64"`|
|`CurrentProjectConfiguration`|選擇性的 `string` 輸出參數。<br /><br /> 包含目前專案的組態。|
|`CurrentProjectPlatform`|選擇性的 `string` 輸出參數。<br /><br /> 包含目前專案的平台。|
|`OnlyReferenceAndBuildProjectsEnabledInSolutionConfiguration`|選擇性的 `bool` 輸出參數。<br /><br /> 包含旗標，指出即使已在專案組態中停用參考，還是應該建置它們。|
|`ShouldUnsetParentConfigurationAndPlatform`|選擇性的 `bool` 輸出參數。<br /><br /> 包含旗標，指出是否應該取消設定父組態與平台。|
|`OutputType`|選擇性的 `string` 輸出參數。<br /><br /> 包含專案的輸出類型。|
|`ResolveConfigurationPlatformUsingMappings`|選擇性的 `bool` 輸出參數。<br /><br /> 包含旗標，指出組建是否應該使用預設對應來解決專案參考中傳遞的組態與平台。|
|`AssignedProjects`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 輸出參數。<br /><br /> 包含已解析的參考路徑清單。|
|`UnassignedProjects`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 輸出參數。<br /><br /> 包含無法使用預先解析的輸出清單來解析的專案參考項目清單。|

## <a name="remarks"></a>備註

 除了上述所列的參數，此項工作還會繼承 <xref:Microsoft.Build.Tasks.TaskExtension> 類別中的參數，而該類別本身又繼承 <xref:Microsoft.Build.Utilities.Task> 類別。 如需這些額外參數的清單及其描述，請參閱 [TaskExtension 基類（base class](../msbuild/taskextension-base-class.md)）。

## <a name="see-also"></a>另請參閱

- [工作](../msbuild/msbuild-tasks.md)
- [工作參考](../msbuild/msbuild-task-reference.md)
