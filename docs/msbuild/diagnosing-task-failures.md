---
title: 診斷工作失敗 |Microsoft Docs
ms.date: 09/25/2019
ms.topic: troubleshooting
f1_keywords:
- MSBuild.ToolTask.ToolCommandFailed
dev_langs:
- VB
- CSharp
- C++
- jsharp
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b77ea7ce288ead0af3d6a9879cab2216ffd6247d
ms.sourcegitcommit: 628eb202a1153ebfe69c668f966f821b98b34b34
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2019
ms.locfileid: "71720795"
---
# <a name="diagnosing-task-failures"></a>診斷工作失敗

如果工作未記錄更特定的錯誤，則當 @no__t 衍生類別執行工具進程來傳回非零結束代碼時，就會發出 `MSB6006`。

## <a name="identifying-the-failing-task"></a>識別失敗的工作

當您遇到工作錯誤時，第一個步驟是識別失敗的工作。

錯誤的文字會指定工具名稱（這是工作的 @no__t 所提供的易記名稱，或可執行檔的名稱）和數值結束代碼。 例如，在

```text
error MSB6006: "custom tool" exited with code 1.
```

工具名稱為 `custom tool`，而結束代碼為 `1`。

### <a name="command-line-builds"></a>命令列組建

如果組建已設定為包含摘要（預設值），摘要將會如下所示：

```text
Build FAILED.

"S:\MSB6006_demo\MSB6006_demo.csproj" (default target) (1) ->
(InvokeToolTask target) ->
  S:\MSB6006_demo\MSB6006_demo.csproj(19,5): error MSB6006: "custom tool" exited with code 1.
```

此結果表示此錯誤發生在專案 `S:\MSB6006_demo\MSB6006_demo.csproj` 之檔案的第19行上，`S:\MSB6006_demo\MSB6006_demo.csproj`，在名為 `InvokeToolTask` 的目標中。

### <a name="in-visual-studio"></a>在 Visual Studio 中

資料行 `Project`、`File` 和 `Line` 中的 Visual Studio 錯誤清單中提供相同的資訊。

## <a name="finding-more-failure-information"></a>尋找更多失敗資訊

當工作未記錄特定的錯誤時，就會發出此錯誤。 記錄錯誤的失敗通常是因為工作未設定為了解它所呼叫的工具所發出的錯誤格式。

正常運作的工具通常會對其標準輸出或錯誤資料流程發出一些內容相關或錯誤資訊，而工作則預設會捕捉並記錄此資訊。 查看發生錯誤之前的記錄專案，以取得其他資訊。 若要保留此資訊，可能需要以較高的記錄層級重新執行組建。

## <a name="next-steps"></a>後續步驟

希望記錄中所識別的其他內容或錯誤顯示問題的根本原因。

如果沒有，您可能必須檢查輸入至失敗工作的屬性和專案，以縮小可能的原因。
