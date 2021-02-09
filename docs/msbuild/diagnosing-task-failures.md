---
title: 診斷工作失敗 |Microsoft Docs
description: 瞭解如何藉由識別失敗的工作、工具名稱和其他資訊來診斷 MSBuild 工作失敗。
ms.custom: SEO-VS-2020
ms.date: 09/25/2019
ms.topic: troubleshooting
f1_keywords:
- MSBuild.ToolTask.ToolCommandFailed
dev_langs:
- VB
- CSharp
- C++
- jsharp
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 33aa8787144f185b5bcd2e26df5e7fa90ce3213f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99877235"
---
# <a name="diagnosing-task-failures"></a>診斷工作失敗

`MSB6006` 當 <xref:Microsoft.Build.Utilities.ToolTask> 衍生類別執行的工具進程傳回非零結束代碼時，如果工作未記錄更明確的錯誤，就會發出。

## <a name="identifying-the-failing-task"></a>識別失敗的工作

當您遇到工作錯誤時，第一個步驟是識別失敗的工作。

錯誤的文字會指定工具名稱 (工作的執行所提供的易記名稱 <xref:Microsoft.Build.Utilities.ToolTask.ToolName> ，或可執行檔) 的名稱和數值結束代碼。 例如，在 

```text
error MSB6006: "custom tool" exited with code 1.
```

工具名稱為 `custom tool` ，結束代碼為 `1` 。

### <a name="command-line-builds"></a>命令列組建

如果組建設定為包含 (預設) 的摘要，則摘要將如下所示：

```text
Build FAILED.

"S:\MSB6006_demo\MSB6006_demo.csproj" (default target) (1) ->
(InvokeToolTask target) ->
  S:\MSB6006_demo\MSB6006_demo.csproj(19,5): error MSB6006: "custom tool" exited with code 1.
```

此結果表示在專案的名稱為之檔案的第19行定義的工作中發生錯誤 `S:\MSB6006_demo\MSB6006_demo.csproj` `InvokeToolTask` `S:\MSB6006_demo\MSB6006_demo.csproj` 。

### <a name="in-visual-studio"></a>在 Visual Studio 中

您可以在資料行、和的 Visual Studio 錯誤清單中找到相同的資訊 `Project` `File` `Line` 。

## <a name="finding-more-failure-information"></a>尋找更多失敗資訊

當工作未記錄特定的錯誤時，就會發出此錯誤。 記錄錯誤的失敗通常是因為工作未設定為了解它所呼叫的工具所發出的錯誤格式。

行為良好的工具通常會在其標準輸出或錯誤資料流程中發出部分內容或錯誤資訊，而工作預設會捕捉並記錄這項資訊。 在錯誤發生之前查看記錄專案，以取得其他資訊。 重新執行具有較高記錄層級的組建時，可能需要保留此資訊。

## <a name="next-steps"></a>下一步

希望記錄中識別的其他內容或錯誤顯示問題的根本原因。

如果沒有，您可能必須檢查輸入失敗工作的屬性和專案，以縮小可能的原因。
