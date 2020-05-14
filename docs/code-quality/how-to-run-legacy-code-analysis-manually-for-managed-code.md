---
title: 如何：手動運行託管代碼的舊代碼分析
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- code analysis, running
ms.assetid: 5086d228-f92e-4515-9708-c5b89b9e9a03
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 9d2693bcff8e83839b4171bae60b138c967f10e5
ms.sourcegitcommit: 92361aac3665a934faa081e1d1ea89a067b01c5b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79432228"
---
# <a name="how-to-run-legacy-code-analysis-manually-for-managed-code"></a>如何：手動運行託管代碼的舊代碼分析
代碼分析工具提供有關原始程式碼中可能存在缺陷的資訊。 您可以在代碼專案的每個生成中自動運行代碼分析，也可以手動運行代碼分析。 運行代碼分析時檢查的規則在專案屬性頁的"代碼分析"頁上指定。 有關詳細資訊，請參閱[如何：為託管代碼專案配置代碼分析](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)。

## <a name="to-run-code-analysis-manually"></a>手動運行代碼分析

1. 如果您在 Visual Studio 2019 版本 16.5 或更高版本上，請在啟動 Visual Studio 之前對命令提示符執行以下命令：

```
set EnableLegacyCodeAnalysis = true
```

2. 在**解決方案資源管理器中**，按一下專案。

3. 在 **"分析"** 功能表上，按一下"*在專案名稱***上運行代碼分析**"。

