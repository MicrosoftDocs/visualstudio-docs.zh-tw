---
title: Exec 工作 | Microsoft Docs
description: 瞭解如何使用 MSBuild Exec 工作，以使用指定的引數來執行指定的程式或命令。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Exec
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Exec task [MSBuild]
- MSBuild, Exec task
ms.assetid: c9b7525a-b1c9-40fc-8bce-77a5b8f960d8
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c3b89e074a4c67e8d16a07eb48431ebe1ade694f
ms.sourcegitcommit: 155d5f0fd54ac1d20df2f5b0245365924faa3565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/31/2021
ms.locfileid: "106083564"
---
# <a name="exec-task"></a>Exec 工作

使用指定的引數來執行指定的程式或命令。

## <a name="parameters"></a>參數

下表說明 `Exec` 工作的參數。

|參數|描述|
|---------------|-----------------|
|`Command`|必要的 `String` 參數。<br /><br /> 一或多個要執行的命令。 這些可以是系統命令（如 attrib）或可執行檔，例如 *program.exe*、 *runprogram.bat* 或 *setup.msi*。<br /><br /> 此參數可以包含多行命令。 或者，您可以將多個命令放在一個批次檔中，然後使用此參數來執行該批次檔。|
|`ConsoleOutput`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 輸出參數。<br /><br /> 每個項目輸出都是工具發出的標準輸出或標準錯誤資料流。 這只有在 `ConsoleToMsBuild` 設為 `true` 時才會擷取。|
|`ConsoleToMsBuild`|選擇性的 `Boolean` 參數。<br /><br /> 如果為 `true`，工作會擷取工具的標準錯誤和標準輸出，讓它們可在 `ConsoleOutput` 輸出參數中使用。<br /><br />預設：`false`。|
|`CustomErrorRegularExpression`|選擇性的 `String` 參數。<br /><br /> 指定在工具輸出中用來檢查錯誤行的規則運算式。 這適用於會產生異常格式之輸出的工具。<br /><br />預設值：`null` (沒有自訂處理)。|
|`CustomWarningRegularExpression`|選擇性的 `String` 參數。<br /><br /> 指定在工具輸出中用來檢查警告行的規則運算式。 這適用於會產生異常格式之輸出的工具。<br /><br />預設值：`null` (沒有自訂處理)。|
|`EchoOff`|選擇性的 `Boolean` 參數。<br /><br /> 如果為 `true`，工作不會將 `Command` 的展開表單發出至 MSBuild 記錄。<br /><br />預設：`false`。|
|`ExitCode`|選擇性 `Int32` 輸出唯讀參數。<br /><br /> 指定執行的命令所提供的結束代碼，但如果工作記錄了任何錯誤，但是進程的結束代碼為 0 (成功) ， `ExitCode` 則設定為-1。|
|`IgnoreExitCode`|選擇性的 `Boolean` 參數。<br /><br /> 如果是 `true`，工作就會略過已執行命令提供的結束代碼。 否則，如果已執行的命令傳回非零的結束代碼，工作就會傳回 `false`。<br /><br />預設：`false`。|
|`IgnoreStandardErrorWarningFormat`|選擇性的 `Boolean` 參數。<br /><br /> 如果是 `false`，即會選取符合標準錯誤/警告格式之輸出中的行，並將它們記錄為錯誤/警告。 如果是 `true`，即會停用此行為。<br /><br />預設：`false`。|
|`Outputs`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 輸出參數。<br /><br /> 包含來自工作的輸出項目。 `Exec` 工作本身不會設定這些項目。 相反地，您可以提供項目，就像工作本身已設定一樣，如此一來，稍後就能在專案中使用它們。|
|`StdErrEncoding`|選擇性的 `String` 輸出參數。<br /><br /> 指定所擷取工作標準錯誤資料流的編碼方式。 預設值是目前的主控台輸出編碼方式。|
|`StdOutEncoding`|選擇性的 `String` 輸出參數。<br /><br /> 指定所擷取工作標準輸出資料流的編碼方式。 預設值是目前的主控台輸出編碼方式。|
|`UseUtf8Encoding`|選擇性的 `String` 參數。<br /><br /> 指定在處理命令列以執行命令時，是否要使用 UTF8 字碼頁。 有效值為 `Always`、`Never` 或 `Detect`。 預設值為 `Detect` ，表示只有當非 ANSI 字元存在時，才使用 UTF8 字碼頁。|
|`WorkingDirectory`|選擇性的 `String` 參數。<br /><br /> 指定將執行命令的目錄。<br /><br />預設值：專案的目前工作目錄。|

[!INCLUDE [ToolTaskExtension arguments](includes/tooltaskextension-base-params.md)]

## <a name="remarks"></a>備註

當您想要執行之工作的特定 MSBuild 工作無法使用時，此工作會很有用。 不過，`Exec` 工作不同於更特定的工作，無法根據其執行之工具或命令的結果進行其他處理或條件式作業。

工作會 `Exec` 呼叫 *cmd.exe* ，而不是直接叫用進程。

## <a name="example"></a>範例

下列範例會使用 `Exec` 工作來執行命令。

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <ItemGroup>
        <Binaries Include="*.dll;*.exe"/>
    </ItemGroup>

    <Target Name="SetACL">
        <!-- set security on binaries-->
        <Exec Command="echo y| cacls %(Binaries.Identity) /G everyone:R"/>
    </Target>
</Project>
```

## <a name="see-also"></a>另請參閱

- [工作](../msbuild/msbuild-tasks.md)
- [工作參考](../msbuild/msbuild-task-reference.md)
