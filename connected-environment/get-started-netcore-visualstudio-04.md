---
title: 使用 Visual Studio 在雲端中以使用 Kubernetes 的容器建立 .NET Core 開發環境 - 步驟 4 - 在 Kubernetes 中偵錯容器 | Microsoft Docs
author: ghogen
ms.author: ghogen
ms.date: 02/20/2018
ms.topic: tutorial
ms.prod: visual-studio-dev15
ms.technology: vs-azure
description: 在 Azure 上使用容器和微服務快速開發 Kubernetes
keywords: Docker, Kubernetes, Azure, AKS, Azure Container Service, 容器
manager: douge
ms.openlocfilehash: 75588fcabbba739c4670da42e24665428ff89130
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="get-started-on-connected-environment-with-net-core-and-visual-studio"></a>使用 .NET Core 和 Visual Studio 開始使用已連線的環境

上一個步驟：[在 Azure 中建立開發環境](get-started-netcore-visualstudio-03.md)

## <a name="debug-a-container-in-kubernetes"></a>在 Kubernetes 中偵錯容器
成功建立開發環境之後，您就可以偵錯應用程式。 在程式碼中設定中斷點，例如在已設定 `Message` 變數之檔案 `HomeController.cs` 的行 20。 按一下 **F5** 開始偵錯。 

Visual Studio 會與開發環境通訊，以建置和部署應用程式，然後以執行中的 Web 應用程式開啟瀏覽器。 容器可能看起來像是在本機執行，但實際上是在我們的 Azure 開發環境中執行。 之所以使用本機位址，是因為已連線的環境會建立在 Azure 中執行之容器的暫存 SSH 通道。

按一下頁面頂端的 [關於] 連結觸發中斷點。 您擁有完整的存取權，可像程式碼在本機執行一樣偵錯資訊，例如呼叫堆疊、區域變數、例外狀況資訊等等。

> [!div class="nextstepaction"]
> [呼叫其他容器](get-started-netcore-visualstudio-05.md)