---
title: 在雲端中以使用 Kubernetes 的容器建立 .NET Core 開發環境 - 步驟 6 - 了解小組開發 | Microsoft Docs
author: johnsta
ms.author: johnsta
ms.date: 02/20/2018
ms.topic: get-started-article
ms.technology: vsce-kubernetes
description: 在 Azure 上使用容器和微服務快速開發 Kubernetes
keywords: Docker, Kubernetes, Azure, AKS, Azure Container Service, 容器
manager: ghogen
ms.openlocfilehash: 80e02e6ce1299278ba1abf530f38cb10b9f36c51
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2018
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
