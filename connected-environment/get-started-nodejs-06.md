---
title: 在雲端中以使用 Kubernetes 的容器建立 Node.js 開發環境 - 步驟 6 - 了解小組開發 | Microsoft Docs
author: ghogen
ms.author: ghogen
ms.date: 02/20/2018
ms.topic: tutorial
ms.prod: visual-studio-dev15
ms.technology: vs-azure
description: 在 Azure 上使用容器和微服務快速開發 Kubernetes
keywords: Docker, Kubernetes, Azure, AKS, Azure Container Service, 容器
manager: douge
ms.openlocfilehash: 6a17dfc3eeebccf1508ea3f69aecb53d067de7af
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
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

