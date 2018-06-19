---
title: 使用 Visual Studio 在雲端中以使用 Kubernetes 的容器建立 .NET Core 開發環境 - 步驟 1 - 安裝工具 | Microsoft Docs
author: ghogen
ms.author: ghogen
ms.date: 04/05/2018
ms.topic: tutorial
ms.prod: visual-studio-dev15
ms.technology: vs-azure
description: 在 Azure 上使用容器和微服務快速開發 Kubernetes
keywords: Docker, Kubernetes, Azure, AKS, Azure Container Service, 容器
manager: douge
ms.openlocfilehash: b2edc476ffd4648f9ddb0e3d076f8eb400458242
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
ms.locfileid: "31884942"
---
# <a name="get-started-on-connected-environment-with-net-core-and-visual-studio"></a>使用 .NET Core 和 Visual Studio 開始使用已連線的環境

在本指南中，您會了解如何：

1. 在 Azure 中建立最適合用於開發的 Kubernetes 型的環境。
1. 在容器中使用 Visual Studio 反覆開發程式碼。
1. 獨立開發兩項不同的服務，並使用 Kubernetes 的 DNS 服務探索呼叫另一項服務。
1. 在小組環境中以具有生產力的方式開發及測試您的程式碼。

[!INCLUDE[](includes/see-troubleshooting.md)]

## <a name="install-the-connected-environment-cli"></a>安裝已連線的環境 CLI
已連線的環境需要基本的本機電腦設定。 您開發環境的大部分組態會儲存在雲端中，可與其他使用者共用。

1. 下載並執行[已連線的環境 CLI 安裝程式](https://aka.ms/get-vsce-windows)。 

## <a name="get-kubernetes-debugging-tools"></a>取得 Kubernetes 偵錯工具
雖然您可以使用已連線的環境 CLI 當作獨立的工具，但使用 **VS Code** 或 **Visual Studio** 的 .NET Core 開發人員仍可使用如 **Kubernetes 偵錯**的豐富功能。

### <a name="visual-studio-debugging"></a>Visual Studio 偵錯 
1. 安裝最新版本的 [Visual Studio 2017](https://www.visualstudio.com/vs/)
1. 在 Visual Studio 安裝程式中，確定選取以下的工作負載：
    * ASP.NET 與網頁程式開發
1. 安裝[已連線環境的 Visual Studio 延伸模組](https://aka.ms/get-vsce-visualstudio)

我們已準備好可以使用 Visual Studio 來建立 ASP.NET Web 應用程式。

> [!div class="nextstepaction"]
> [建立 ASP.NET Web 應用程式](get-started-netcore-visualstudio-02.md)
