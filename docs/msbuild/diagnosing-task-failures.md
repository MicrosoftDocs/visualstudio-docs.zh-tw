---
title: 診斷任務失敗 |微軟文檔
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 89dcb8bddf2c92406ad5eff952d1f4050d7f9262
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "75593274"
---
# <a name="diagnosing-task-failures"></a>診斷工作失敗

`MSB6006`當<xref:Microsoft.Build.Utilities.ToolTask>_派生類運行一個工具進程，如果任務未記錄更具體的錯誤，則返回非零結束代碼的工具過程時發出。

## <a name="identifying-the-failing-task"></a>識別失敗的任務

遇到任務錯誤時，第一步是確定失敗的任務。

錯誤的文本指定工具名稱（任務實現提供的易記名稱<xref:Microsoft.Build.Utilities.ToolTask.ToolName>或可執行檔的名稱）和數位結束代碼。 例如，在 

```text
error MSB6006: "custom tool" exited with code 1.
```

工具名稱為`custom tool`，結束代碼為`1`。

### <a name="command-line-builds"></a>命令列生成

如果組建組態為包含摘要（預設值），則摘要將如下所示：

```text
Build FAILED.

"S:\MSB6006_demo\MSB6006_demo.csproj" (default target) (1) ->
(InvokeToolTask target) ->
  S:\MSB6006_demo\MSB6006_demo.csproj(19,5): error MSB6006: "custom tool" exited with code 1.
```

此結果表明，錯誤發生在在檔`S:\MSB6006_demo\MSB6006_demo.csproj`第 19 行定義的任務中，在專案中`InvokeToolTask``S:\MSB6006_demo\MSB6006_demo.csproj`名為 的目標中。

### <a name="in-visual-studio"></a>在 Visual Studio 中

列中的 Visual Studio 錯誤清單中`Project`也提供了相同的資訊。 `Line` `File`

## <a name="finding-more-failure-information"></a>查找更多故障資訊

當任務未記錄特定錯誤時，將發出此錯誤。 無法記錄錯誤通常是因為任務未配置為了解它調用的工具發出的錯誤格式。

行為良好的工具通常會向其標準輸出或錯誤流發出一些上下文或錯誤資訊，預設情況下任務捕獲和記錄此資訊。 在錯誤發生之前查看日誌條目以獲取其他資訊。 可能需要使用較高的日誌級別重新運行生成才能保留此資訊。

## <a name="next-steps"></a>後續步驟

希望日誌記錄中標識的其他上下文或錯誤會揭示問題的根本原因。

否則，您可能必須通過檢查作為失敗任務的輸入的屬性和項來縮小潛在原因的範圍。
