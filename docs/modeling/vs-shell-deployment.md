---
title: VS Shell 部署
description: 瞭解獨立模式 shell 如何讓您判斷需要與 DSL 互動的 Visual Studio 功能，以及該解決方案的顯示方式。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 94cffbf5ea1f7ac3c437a4c22f27f881d5493e79
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/12/2020
ms.locfileid: "97361257"
---
# <a name="vs-shell-deployment"></a>VS Shell 部署

獨立模式 shell 可讓您判斷需要哪些 Visual Studio 功能，才能與您的特定領域語言互動，以及該解決方案的顯示方式。 如需 Visual Studio 獨立模式 shell 的詳細資訊，請參閱 [自訂獨立模式 shell](https://visualstudio.microsoft.com/vs/older-downloads/isolated-shell/)。

若要將 Visual Studio Shell 設定為部署目標：

1. 在 **DslPackage** 專案中，開啟 **source.extension.tt**。

2. 在 [ `<SupportedProducts>` 插入：

   ```xml
   <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>
   ```

   將 *MyIsolatedShell* 取代為隔離式 shell 封裝的名稱。