---
title: 如何手動執行受控碼的舊版程式碼分析
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- code analysis, running
ms.assetid: 5086d228-f92e-4515-9708-c5b89b9e9a03
author: Mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 44190f8e828f9a971f15b57266978603dcac8139
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85462058"
---
# <a name="how-to-run-legacy-code-analysis-manually-for-managed-code"></a>如何：針對受控碼手動執行舊版程式碼分析
程式碼分析工具會為您提供原始程式碼中可能瑕疵的相關資訊。 您可以使用程式碼專案的每個組建自動執行程式碼分析，也可以手動執行程式碼分析。 執行程式碼分析時所檢查的規則會在專案屬性頁的 [程式碼分析] 頁面上指定。 如需詳細資訊，請參閱[如何：針對 Managed 程式碼專案設定程式碼分析](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)。

## <a name="to-run-code-analysis-manually"></a>手動執行程式碼分析

1. 如果您是在 Visual Studio 2019 16.5 版或更新版本，請先在命令提示字元上執行下列命令，再啟動 Visual Studio：

```
set EnableLegacyCodeAnalysis = true
```

2. 在**方案總管**中，按一下專案。

3. 在 [**分析**] 功能表上，按一下 [針對*專案名稱***執行程式碼分析**]。

