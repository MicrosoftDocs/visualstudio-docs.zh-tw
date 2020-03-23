---
title: 如何：手動運行託管代碼的代碼分析
ms.date: 11/04/2019
ms.topic: conceptual
helpviewer_keywords:
- code analysis, running
- run code analysis
ms.assetid: 5086d228-f92e-4515-9708-c5b89b9e9a03
author: mavasani
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 5fdeb56a0c0f4c5904a00ec53d64dae87aa4e9a5
ms.sourcegitcommit: 92361aac3665a934faa081e1d1ea89a067b01c5b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79431380"
---
# <a name="how-to-run-code-analysis-manually-for-managed-code-requires-visual-studio-2019-version-165-or-later"></a>如何：手動運行託管代碼的代碼分析（需要 Visual Studio 2019 版本 16.5 或更高版本）
預設情況下，.NET 編譯器平臺 （"Roslyn"） 代碼分析器通過執行即時分析以及生成期間，在鍵入時分析 C# 或 Visual Basic 代碼。 因此，您通常不需要手動觸發代碼分析。 但是，在某些情況下，您可能需要手動觸發代碼分析：

- 預設情況下，即時代碼分析僅針對 Visual Studio 中的打開檔執行分析器。 但是，您可能有興趣查看特定專案或解決方案中所有檔的代碼分析警告。 如果是這樣，您需要在專案或解決方案上觸發一次代碼分析。 或者，您可以啟用連續即時代碼分析，以便對整個解決方案執行。 有關詳細資訊，請參閱[如何：為託管代碼配置即時代碼分析範圍](./configure-live-code-analysis-scope-managed-code.md)。
- 與連續即時分析或生成時間分析，您可能更喜歡按需代碼分析執行工作流。 如果是這樣，您可以在即時分析和/或生成期間禁用分析器執行。 有關禁用分析的資訊，請參閱[如何禁用原始程式碼分析](disable-code-analysis.md)。 然後，您希望在專案或解決方案上手動觸發一次代碼分析。 

### <a name="run-code-analysis-manually"></a>手動執行程式碼分析

1. 在**解決方案資源管理器中**，按一下專案。

2. 在 **"分析"** 功能表上，按一下"*在專案名稱***上運行代碼分析**"。

代碼分析將在後臺開始執行。 您應該在面向左下角的視覺化工作室狀態列中看到專案 **>運行代碼分析\<** 消息。 完成代碼分析後，狀態訊息將更改為**完成\<>專案的代碼分析**。 使用所有代碼分析診斷，錯誤清單將很快刷新。
