---
title: VS Shell 部署
description: 瞭解獨立模式 shell 如何讓您判斷需要與 DSL 互動的 Visual Studio 功能，以及該解決方案的顯示方式。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1293593e71aa57d8e74b9035320b3da5108aba09
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99924221"
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