---
author: ghogen
ms.author: ghogen
ms.topic: include
ms.date: 4/23/2020
ms.openlocfilehash: d7d4027c53f599b4a17d267d5ebf72eee1ed296b
ms.sourcegitcommit: 7a5c4f60667b5792f876953d55192b49a73f5fe9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/16/2021
ms.locfileid: "98535301"
---
### <a name="tooltaskextension-parameters"></a>ToolTaskExtension 參數

這項工作繼承自類別，該類別繼承自類別，而類別 <xref:Microsoft.Build.Tasks.ToolTaskExtension> <xref:Microsoft.Build.Utilities.ToolTask> 本身繼承自類別 <xref:Microsoft.Build.Utilities.Task> 。 此繼承鏈結將數個參數加入至從它們衍生的工作。

下表描述基類的參數：

| 參數 | 說明 |
| - | - |
| <xref:Microsoft.Build.Utilities.ToolTask.EchoOff%2A> | 選擇性的 `bool` 參數。<br /><br /> 當設定為時 `true` ，此工作會將 **/q** 傳遞到 *cmd.exe* 命令列，讓命令列不會複製到 stdout。 |
| <xref:Microsoft.Build.Utilities.ToolTask.EnvironmentVariables%2A> | 選擇性 `String` 陣列參數。<br /><br /> 環境變數定義的陣列，以分號分隔。 每個定義都應該指定以等號分隔的環境變數名稱和值。 這些變數是在規則環境區塊以外傳遞至繁衍的可執行檔，或選擇性地覆寫。 例如： `Variable1=Value1;Variable2=Value2` 。 |
| <xref:Microsoft.Build.Utilities.ToolTask.ExitCode%2A> | 選擇性 `Int32` 輸出唯讀參數。<br /><br /> 指定已執行命令提供的結束代碼。 如果工作已記錄任何錯誤，但是此程序具有結束代碼 0 (成功)，這會設為 -1。 |
| <xref:Microsoft.Build.Utilities.ToolTask.LogStandardErrorAsError%2A> | 選擇性的 `bool` 參數。<br /><br /> 如果為 `true`，則標準錯誤資料流上收到的所有訊息都會記錄為錯誤。 |
| <xref:Microsoft.Build.Utilities.ToolTask.StandardErrorImportance%2A> | 選擇性的 `String` 參數。<br /><br /> 用來從標準輸出資料流記錄文字的重要性。 |
| <xref:Microsoft.Build.Utilities.ToolTask.StandardOutputImportance%2A> | 選擇性的 `String` 參數。<br /><br /> 用來從標準輸出資料流記錄文字的重要性。 |
| <xref:Microsoft.Build.Utilities.ToolTask.Timeout%2A> | 選擇性的 `Int32` 參數。<br /><br /> 指定時間量 (以毫秒為單位)，在此時間量之後會終止工作可執行檔。 預設值是 `Int.MaxValue`，表示沒有逾時期間。 逾時是以毫秒為單位。 |
| <xref:Microsoft.Build.Utilities.ToolTask.ToolExe%2A> | 選擇性的 `string` 參數。<br /><br /> 專案可能會實作此項目以覆寫 ToolName。 工作可能會覆寫此項目以保留 ToolName。 |
| <xref:Microsoft.Build.Utilities.ToolTask.ToolPath%2A> | 選擇性的 `string` 參數。<br /><br /> 指定位置，工作會從該位置載入基礎可執行檔。 如果未指定此參數，工作會使用 SDK 安裝路徑，該路徑會對應至執行 MSBuild 的 framework 版本。 |
| <xref:Microsoft.Build.Utilities.ToolTask.UseCommandProcessor%2A> | 選擇性的 `bool` 參數。<br /><br /> 當設為 `true` 時，這項工作會針對命令列建立批次檔，並且使用命令處理器來執行，而不是直接執行命令。 |
| <xref:Microsoft.Build.Utilities.ToolTask.YieldDuringToolExecution%2A> | 選擇性的 `bool` 參數。<br /><br /> 當設為 `true` 時，這項工作在執行其工作時，會產生節點。 |
