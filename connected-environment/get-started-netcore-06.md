---
title: 在雲端中以使用 Kubernetes 的容器建立 .NET Core 開發環境 - 步驟 6 - 了解小組開發 | Microsoft Docs
author: ghogen
ms.author: ghogen
ms.date: 02/20/2018
ms.topic: tutorial
ms.prod: visual-studio-dev15
ms.technology: vs-azure
description: 在 Azure 上使用容器和微服務快速開發 Kubernetes
keywords: Docker, Kubernetes, Azure, AKS, Azure Container Service, 容器
manager: douge
ms.openlocfilehash: 4da5051b760a12f8fd8837072ada44c8c5a9b239
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
ms.locfileid: "31884339"
---
# <a name="get-started-on-connected-environment-with-net-core"></a>使用 .NET Core 開始使用已連線的環境

上一個步驟：[呼叫其他容器](get-started-netcore-05.md)

[!INCLUDE[](includes/team-development-1.md)]

我們來觀看實作示範：
1. 移至 `mywebapi` 的 VS Code 視窗，編輯 `string Get(int id)` 方法的程式碼，例如：

```csharp
[HttpGet("{id}")]
public string Get(int id)
{
    return "mywebapi now says something new";
}
```

[!INCLUDE[](includes/team-development-2.md)]

> [!div class="nextstepaction"]
> [下一步](get-started-netcore-07.md)
