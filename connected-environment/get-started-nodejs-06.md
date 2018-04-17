---
title: 在雲端中以使用 Kubernetes 的容器建立 Node.js 開發環境 - 步驟 6 - 了解小組開發 | Microsoft Docs
author: johnsta
ms.author: johnsta
ms.date: 02/20/2018
ms.topic: get-started-article
ms.technology: vsce-kubernetes
description: 在 Azure 上使用容器和微服務快速開發 Kubernetes
keywords: Docker, Kubernetes, Azure, AKS, Azure Container Service, 容器
manager: ghogen
ms.openlocfilehash: 4db1d71c96da29a06884e562a277a7ca427910d4
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2018
---
# <a name="get-started-on-connected-environment-with-nodejs"></a>使用 Node.js 開始使用已連線的環境

上一個步驟：[呼叫在不同容器中執行的服務](get-started-nodejs-05.md)

[!INCLUDE[](includes/team-development-1.md)]

我們來觀看實作示範：
1. 移至 `mywebapi` 的 VS Code 視窗，編輯預設 GET `/` 處理常式的程式碼，例如：

```javascript
app.get('/', function (req, res) {
    res.send('mywebapi now says something new');
});
```

[!INCLUDE[](includes/team-development-2.md)]

> [!div class="nextstepaction"]
> [下一步](get-started-nodejs-07.md)

