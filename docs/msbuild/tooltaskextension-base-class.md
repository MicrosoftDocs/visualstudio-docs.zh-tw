---
title: ToolTaskExtension 基底類別 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- MSBuild.ToolTask.ToolCommandFailed
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 258ae433-f68a-49f1-b276-da20e3472e68
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 01d2abbed85b891378b0a9d5c4a41029bdc46cf3
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/19/2018
ms.locfileid: "31569706"
---
# <a name="tooltaskextension-base-class"></a>ToolTaskExtension 基底類別
許多工作繼承自 <xref:Microsoft.Build.Tasks.ToolTaskExtension> 類別，該類別繼承自 <xref:Microsoft.Build.Utilities.ToolTask> 類別，而其本身是繼承自 <xref:Microsoft.Build.Utilities.Task> 類別。 此繼承鏈結將數個參數加入至從它們衍生的工作。 本文件會列出這些參數。  
  
## <a name="parameters"></a>參數  
 下表說明基底類別的參數。  
  
|參數|描述|  
|---------------|-----------------|  
|<xref:Microsoft.Build.Utilities.Task.BuildEngine%2A>|選擇性的 <xref:Microsoft.Build.Framework.IBuildEngine> 參數。<br /><br /> 指定工作可以使用的建置引擎介面。 建置引擎會自動設定這個參數，以允許工作回呼至它。|  
|<xref:Microsoft.Build.Utilities.Task.BuildEngine2%2A>|選擇性的 <xref:Microsoft.Build.Framework.IBuildEngine2> 參數。<br /><br /> 指定工作可以使用的建置引擎介面。 建置引擎會自動設定這個參數，以允許工作回呼至它。<br /><br /> 這是方便的屬性，讓工作作者繼承自這個類別，不需要將值從 `IBuildEngine` 轉型到 `IBuildEngine2`。|  
|<xref:Microsoft.Build.Utilities.Task.BuildEngine3%2A>|選擇性的 <xref:Microsoft.Build.Framework.IBuildEngine3> 參數。<br /><br /> 指定主機提供的建置引擎介面。|  
|<xref:Microsoft.Build.Utilities.ToolTask.EchoOff%2A>|選擇性的 `bool` 參數。<br /><br /> 設為 `true` 時，此工作會將 **/Q** 傳遞至 cmd.exe 命令列；因此，命令列不會將這類的命令複製到 stdout。|  
|<xref:Microsoft.Build.Utilities.ToolTask.EnvironmentVariables%2A>|選擇性 `String` 陣列參數。<br /><br /> 環境變數組陣列，以等號分隔。 這些變數是在規則環境區塊以外傳遞至繁衍的可執行檔，或選擇性地覆寫。|  
|<xref:Microsoft.Build.Utilities.ToolTask.ExitCode%2A>|選擇性 `Int32` 輸出唯讀參數。<br /><br /> 指定已執行命令提供的結束代碼。 如果工作已記錄任何錯誤，但是此程序具有結束代碼 0 (成功)，這會設為 -1。|  
|<xref:Microsoft.Build.Utilities.Task.HostObject%2A>|選擇性的 <xref:Microsoft.Build.Framework.ITaskHost> 參數。<br /><br /> 指定主機物件執行個體 (可以為 Null)。 如果主機 IDE 讓主機物件與這個特定工作產生關聯，則建置引擎會設定這個屬性。|  
|<xref:Microsoft.Build.Tasks.ToolTaskExtension.Log%2A>|選擇性 <xref:Microsoft.Build.Utilities.TaskLoggingHelper> 唯讀參數。<br /><br /> 取得 <xref:Microsoft.Build.Tasks.TaskLoggingHelperExtension> 類別的執行個體，其中包含工作記錄方法。|  
|<xref:Microsoft.Build.Utilities.ToolTask.LogStandardErrorAsError%2A>|選項 `bool` 參數。<br /><br /> 如果為 `true`，則標準錯誤資料流上收到的所有訊息都會記錄為錯誤。|  
|<xref:Microsoft.Build.Utilities.ToolTask.StandardErrorImportance%2A>|選擇性的 `String` 參數。<br /><br /> 用來從標準輸出資料流記錄文字的重要性。|  
|<xref:Microsoft.Build.Utilities.ToolTask.StandardOutputImportance%2A>|選擇性的 `String` 參數。<br /><br /> 用來從標準輸出資料流記錄文字的重要性。|  
|<xref:Microsoft.Build.Utilities.ToolTask.Timeout%2A>|虛擬選擇性 `Int32` 參數。<br /><br /> 指定時間量 (以毫秒為單位)，在此時間量之後會終止工作可執行檔。 預設值是 `Int.MaxValue`，表示沒有逾時期間。逾時是以毫秒為單位。|  
|<xref:Microsoft.Build.Utilities.ToolTask.ToolExe%2A>|虛擬選擇性 `string` 參數。<br /><br /> 專案可能會實作此項目以覆寫 ToolName。 工作可能會覆寫此項目以保留 ToolName。|  
|<xref:Microsoft.Build.Utilities.ToolTask.ToolPath%2A>|選擇性的 `string` 參數。<br /><br /> 指定位置，工作會從該位置載入基礎可執行檔。 如果未指定這個參數，工作會使用 SDK 安裝路徑，對應於執行 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 之架構的版本。|  
|<xref:Microsoft.Build.Utilities.ToolTask.UseCommandProcessor%2A>|選擇性的 `bool` 參數。<br /><br /> 當設為 `true` 時，這項工作會針對命令列建立批次檔，並且使用命令處理器來執行，而不是直接執行命令。|  
|<xref:Microsoft.Build.Utilities.ToolTask.YieldDuringToolExecution%2A>|選擇性的 `bool` 參數。<br /><br /> 當設為 `true` 時，這項工作在執行其工作時，會產生節點。|  
  
## <a name="see-also"></a>請參閱  
 [工作參考](../msbuild/msbuild-task-reference.md)   
 [工作](../msbuild/msbuild-tasks.md)