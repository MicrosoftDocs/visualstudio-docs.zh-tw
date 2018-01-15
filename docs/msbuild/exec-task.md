---
title: "Exec 工作 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/developer/msbuild/2003#Exec
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Exec task [MSBuild]
- MSBuild, Exec task
ms.assetid: c9b7525a-b1c9-40fc-8bce-77a5b8f960d8
caps.latest.revision: "20"
author: kempb
ms.author: kempb
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 0eadf1b5d94a136861d45275ebc5b94b6707cf14
ms.sourcegitcommit: 9357209350167e1eb7e50b483e44893735d90589
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/05/2018
---
# <a name="exec-task"></a>Exec 工作
使用指定的引數來執行指定的程式或命令。  
  
## <a name="parameters"></a>參數  
 下表說明 `Exec` 工作的參數。  
  
|參數|描述|  
|---------------|-----------------|  
|`Command`|必要的 `String` 參數。<br /><br /> 一或多個要執行的命令。 這些可以是系統命令 (例如 attrib) 或可執行檔 (例如 program.exe、runprogram.bat 或 setup.msi)。<br /><br /> 此參數可以包含多行命令。 或者，您可以將多個命令放在一個批次檔中，然後使用此參數來執行該批次檔。|  
|`ConsoleOutput`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 輸出參數。<br /><br /> 每個項目輸出都是工具發出的標準輸出或標準錯誤資料流。 這只有在 `ConsoleToMsBuild` 設為 `true` 時才會擷取。|
|`ConsoleToMsBuild`|選擇性的 `Boolean` 參數。<br /><br /> 如果為 `true`，工作會擷取工具的標準錯誤和標準輸出，讓它們可在 `ConsoleOutput` 輸出參數中使用。 預設值是 `false`。|
|`CustomErrorRegularExpression`|選擇性的 `String` 參數。<br /><br /> 指定在工具輸出中用來檢查錯誤行的規則運算式。 這適用於會產生異常格式之輸出的工具。|  
|`CustomWarningRegularExpression`|選擇性的 `String` 參數。<br /><br /> 指定在工具輸出中用來檢查警告行的規則運算式。 這適用於會產生異常格式之輸出的工具。|  
|`EchoOff`|選擇性的 `Boolean` 參數。<br /><br /> 如果為 `true`，工作不會將 `Command` 的展開表單發出至 MSBuild 記錄。 預設值是 `false`。|
|`ExitCode`|選擇性 `Int32` 輸出唯讀參數。<br /><br /> 指定已執行命令提供的結束代碼。|  
|`IgnoreExitCode`|選擇性的 `Boolean` 參數。<br /><br /> 如果是 `true`，工作就會略過已執行命令提供的結束代碼。 否則，如果已執行的命令傳回非零的結束代碼，工作就會傳回 `false`。|  
|`IgnoreStandardErrorWarningFormat`|選擇性的 `Boolean` 參數。<br /><br /> 如果是 `false`，即會選取符合標準錯誤/警告格式之輸出中的行，並將它們記錄為錯誤/警告。 如果是 `true`，即會停用此行為。 預設值是 `false`。|  
|`Outputs`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 輸出參數。<br /><br /> 包含來自工作的輸出項目。 `Exec` 工作本身不會設定這些項目。 相反地，您可以提供項目，就像工作本身已設定一樣，如此一來，稍後就能在專案中使用它們。|  
|`StdErrEncoding`|選擇性的 `String` 輸出參數。<br /><br /> 指定所擷取工作標準錯誤資料流的編碼方式。 預設值是目前的主控台輸出編碼方式。|  
|`StdOutEncoding`|選擇性的 `String` 輸出參數。<br /><br /> 指定所擷取工作標準輸出資料流的編碼方式。 預設值是目前的主控台輸出編碼方式。|  
|`WorkingDirectory`|選擇性的 `String` 參數。<br /><br /> 指定將執行命令的目錄。|  
  
## <a name="remarks"></a>備註  
 若無法針對您想要執行的作業取得特定的 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 工作，此工作就非常有用。 不過，`Exec` 工作與更特定的工作不同，無法從它執行的工具或命令中收集輸出。  
  
 `Exec` 工作會呼叫 cmd.exe，而不是直接叫用處理序。  
  
 除了本文件所列的參數，此項工作還會繼承 <xref:Microsoft.Build.Tasks.ToolTaskExtension> 類別中的參數，而該類別本身又繼承 <xref:Microsoft.Build.Utilities.ToolTask> 類別。 如需這些其他參數的清單及其說明，請參閱 [ToolTaskExtension 基底類別](../msbuild/tooltaskextension-base-class.md)。  
  
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
  
## <a name="see-also"></a>請參閱  
 [工作](../msbuild/msbuild-tasks.md)   
 [工作參考](../msbuild/msbuild-task-reference.md)
