---
title: VS Shell 部署
ms.date: 11/04/2016
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3ca497244a806324d9d2315fa1b1b89404838ff3
ms.sourcegitcommit: 7b60e81414a82c6d34f6de1a1f56115c9cd26943
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2020
ms.locfileid: "81444995"
---
# <a name="vs-shell-deployment"></a>VS Shell 部署

通過隔離的 shell,您可以確定需要與域特定語言交互的 Visual Studio 功能,以及該解決方案的顯示方式。 有關 Visual Studio 隔離外殼的詳細資訊,請參閱[自訂隔離外殼](https://docs.microsoft.com/visualstudio/extensibility/customizing-the-isolated-shell)。

要將可視化工作室外殼設置為部署目標,

1. 在**Dsl 套件**項目中,開啟**source.extension.tt**。

2. 插入`<SupportedProducts>`下:

   ```xml
   <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>
   ```

   用隔離外殼套件的名稱取代*My 隔離外殼*。
