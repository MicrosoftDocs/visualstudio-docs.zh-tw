---
title: VCToolTask 類別 | Microsoft Docs
ms.date: 03/10/2019
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
author: mikeblome
ms.author: Michael.Blome
ms.workload:
- multiple
ms.openlocfilehash: 4c7cc3490735dbd9ac43cd43555ec673cc3afccd
ms.sourcegitcommit: 4ffb7be5384ad566ce46538032bf8561754c61a4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2019
ms.locfileid: "58070391"
---
# <a name="vctooltask-base-class"></a>VCToolTask 基底類別

許多工作最終繼承自 <xref:Microsoft.Build.Utilities.Task> 類別和 [ToolTask](/dotnet/api/microsoft.build.utilities.tooltask) 類別。 此類別會將數個參數新增至從中衍生它們的工作。 此文件會列出這些參數。

## <a name="parameters"></a>參數

下表說明 **VCToolTask** 基底類別的參數。

|參數|說明|
|---------------|-----------------|
|**ActiveToolSwitchesValues**|選擇性的 **Dictionary\<string, ToolSwitch>** 參數。|
|**AdditionalOptions**|選擇性的 **string** 參數。|
|**EffectiveWorkingDirectory**|選擇性的 **string** 參數。|
|**EnableErrorListRegex**|選擇性的 **bool** 參數。<br/><br/>預設為 `true`。|
|**ErrorListRegex**|選擇性的 **ITaskItem[]** 參數。|
|**ErrorListListExclusion**|選擇性的 **ITaskItem[]** 參數。|
|**GenerateCommandLine**|選擇性的 **string** 參數。<br/><br/>使用值 **CommandLineFormat** *format* [default = CommandLineFormat.ForBuildLog] 和 **EscapeFormat** *escapeFormat* [default = EscapeFormat.Default]。|
|**GenerateCommandLineExceptSwitches**|選擇性的 **string** 參數。<br/><br/>使用值 **string[]** *switchesToRemove*、**CommandLineFormat** *format* [default = CommandLineFormat.ForBuildLog] 和 **EscapeFormat** *escapeFormat* [default = EscapeFormat.Default]。|

## <a name="see-also"></a>另請參閱

[工作參考](../msbuild/msbuild-task-reference.md)<br/>
[工作](../msbuild/msbuild-tasks.md)