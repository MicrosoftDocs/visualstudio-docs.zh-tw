---
title: VS Shell 部署
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: bc86574b380e0a29042dcc1dc20851258c9f1bc3
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "55033566"
---
# <a name="vs-shell-deployment"></a>VS Shell 部署

獨立模式的 shell 可讓您判斷哪一個 Visual Studio 需要特定領域語言，和如何呈現該解決方案互動的功能。 如需 Visual Studio 隔離 shell 的詳細資訊，請參閱[自訂 Isolated Shell](https://vspartner.com/pages/vsshells)。

若要設定 Visual Studio Shell 做為部署目標：

1. 在  **DslPackage**專案中，開啟**source.extension.tt**。

2. 在下`<SupportedProducts>`插入：

   ```xml
   <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>
   ```

   取代*MyIsolatedShell*獨立模式的 shell 封裝的名稱。