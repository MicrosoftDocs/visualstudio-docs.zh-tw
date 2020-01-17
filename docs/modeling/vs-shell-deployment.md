---
title: VS Shell 部署
ms.date: 11/04/2016
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 99ef0124c06cd6f1a4d24e29b2c02cd0b50a37b0
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/16/2020
ms.locfileid: "76115279"
---
# <a name="vs-shell-deployment"></a>VS Shell 部署

獨立模式 shell 可讓您判斷需要與特定領域語言互動的 Visual Studio 功能，以及該解決方案的顯示方式。 如需有關 Visual Studio 獨立模式 shell 的詳細資訊，請參閱[自訂獨立模式 shell](https://vspartner.com/pages/vsshells)。

若要將 Visual Studio Shell 設定為部署目標：

1. 在**DslPackage**專案中，開啟**source.extension.tt**。

2. 在 `<SupportedProducts>` 插入 底下：

   ```xml
   <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>
   ```

   將*MyIsolatedShell*取代為您的獨立 shell 封裝名稱。
