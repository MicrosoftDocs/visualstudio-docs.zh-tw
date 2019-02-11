---
title: VS Shell 部署
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 70f39dd23851a2ebc0a48afd05da54b0d8deb24a
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2019
ms.locfileid: "55955670"
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