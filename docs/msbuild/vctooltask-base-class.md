---
title: VCToolTask 類別 | Microsoft Docs
ms.date: 03/10/2019
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
author: ghogen
ms.author: ghogen
ms.workload:
- multiple
ms.openlocfilehash: df75bb998d2b8c6486e20c4c3ca0d80347c8f88a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "75591667"
---
# <a name="vctooltask-base-class"></a>VCToolTask 基底類別

許多工作最終繼承自 <xref:Microsoft.Build.Utilities.Task> 類別和 [ToolTask](/dotnet/api/microsoft.build.utilities.tooltask) 類別。 此類別會將數個參數新增至從中衍生它們的工作。 本文件會列出這些參數。

## <a name="parameters"></a>參數

下表說明 **VCToolTask** 基底類別的參數。

|參數|說明|
|---------------|-----------------|
|**ActiveToolSwitchesValues**|選擇性**字典 \<string, ToolSwitch> **參數。|
|**AdditionalOptions**|選擇性的 **字串** 參數。|
|**EffectiveWorkingDirectory**|選擇性的 **字串** 參數。|
|**EnableErrorListRegex**|選擇性的 **bool** 參數。<br/><br/>預設為 `true`。|
|**ErrorListRegex**|選擇性的 **ITaskItem []** 參數。|
|**ErrorListListExclusion**|選擇性的 **ITaskItem []** 參數。|
|**GenerateCommandLine**|選擇性的 **字串** 參數。<br/><br/>使用值 **CommandLineFormat** *format* [default = CommandLineFormat.ForBuildLog] 和 **EscapeFormat** *escapeFormat* [default = EscapeFormat.Default]。|
|**GenerateCommandLineExceptSwitches**|選擇性的 **字串** 參數。<br/><br/>使用值 **string[]** *switchesToRemove*、**CommandLineFormat** *format* [default = CommandLineFormat.ForBuildLog] 和 **EscapeFormat** *escapeFormat* [default = EscapeFormat.Default]。|

## <a name="see-also"></a>另請參閱

[工作參考](../msbuild/msbuild-task-reference.md)<br/>
[工作](../msbuild/msbuild-tasks.md)
