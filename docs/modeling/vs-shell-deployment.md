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
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85535846"
---
# <a name="vs-shell-deployment"></a>VS Shell 部署

獨立模式 shell 可讓您判斷需要與特定領域語言互動的 Visual Studio 功能，以及該解決方案的顯示方式。 如需有關 Visual Studio 獨立模式 shell 的詳細資訊，請參閱[自訂獨立模式 shell](https://docs.microsoft.com/visualstudio/extensibility/customizing-the-isolated-shell)。

若要將 Visual Studio Shell 設定為部署目標：

1. 在**DslPackage**專案中，開啟**source.extension.tt**。

2. 在 [插入] 底下 `<SupportedProducts>` ：

   ```xml
   <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>
   ```

   將*MyIsolatedShell*取代為您的獨立 shell 封裝名稱。
