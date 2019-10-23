---
title: VS Shell 部署 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: be8f2ffe-a322-4ac0-9c9e-873bd28e5d5e
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a42ec6a762655589bfd589ae9dc0354e3a7d1cb5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659309"
---
# <a name="vs-shell-deployment"></a>VS Shell 部署
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

獨立模式 shell 可讓您判斷需要與特定領域語言互動的 Visual Studio 功能，以及該解決方案的顯示方式。 如需有關 Visual Studio 獨立模式 shell 的詳細資訊，請參閱[自訂獨立模式 shell](../extensibility/customizing-the-isolated-shell.md)。 您可以在[自訂獨立模式 shell](https://msdn.microsoft.com/d75463cd-1155-42e4-8b7a-046ed6becbbf)中找到如何自訂獨立模式的詳細資訊。

### <a name="to-set-a-visual-studio-shell-as-the-deployment-target"></a>若要將 Visual Studio Shell 設定為部署目標

1. 在**DslPackage**專案中，開啟**source.extension.tt**。

2. 在 `<SupportedProducts>` 插入 底下：

    ```
    <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>
    ```

     將*MyIsolatedShell*取代為您的獨立 shell 封裝名稱。
