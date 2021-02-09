---
title: '以手動方式執行舊版程式碼分析 ( .NET) '
description: 瞭解如何在原始程式碼中偵測可能的瑕疵。 瞭解如何在 Visual Studio 中的 managed 程式碼上手動執行舊版程式碼分析。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- code analysis, running
ms.assetid: 5086d228-f92e-4515-9708-c5b89b9e9a03
author: Mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 45f201e2c647a1b1074585d59c7618e1ddeb9084
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99859992"
---
# <a name="how-to-run-legacy-code-analysis-manually-for-managed-code"></a>如何：針對 managed 程式碼手動執行舊版程式碼分析

程式碼分析工具可為您提供原始程式碼中可能瑕疵的相關資訊。 您可以在程式碼專案的每個組建中自動執行程式碼分析，也可以手動執行程式碼分析。 執行程式碼分析時所檢查的規則是在專案屬性頁的 [程式碼分析] 頁面上指定。 如需詳細資訊，請參閱 [如何：設定 Managed 程式碼專案的程式碼分析](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)。

## <a name="to-run-code-analysis-manually"></a>手動執行程式碼分析

1. 如果您是在 Visual Studio 2019 16.5 版或更新版本上，請在命令提示字元上執行下列命令，然後再啟動 Visual Studio：

```
set EnableLegacyCodeAnalysis = true
```

2. 在 **方案總管** 中，按一下專案。

3. 在 [**分析**] 功能表上，按一下 [針對 *專案名稱***執行程式碼分析**]。
