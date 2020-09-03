---
title: VS Shell 部署
ms.date: 11/04/2016
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d8793312e0ed022fc7210508efdf20a81b293f0f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85535846"
---
# <a name="vs-shell-deployment"></a>VS Shell 部署

獨立模式 shell 可讓您判斷需要哪些 Visual Studio 功能，才能與您的特定領域語言互動，以及該解決方案的顯示方式。 如需 Visual Studio 獨立模式 shell 的詳細資訊，請參閱 [自訂獨立模式 shell](https://docs.microsoft.com/visualstudio/extensibility/customizing-the-isolated-shell)。

若要將 Visual Studio Shell 設定為部署目標：

1. 在 **DslPackage** 專案中，開啟 **source.extension.tt**。

2. 在 [ `<SupportedProducts>` 插入：

   ```xml
   <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>
   ```

   將 *MyIsolatedShell* 取代為隔離式 shell 封裝的名稱。
