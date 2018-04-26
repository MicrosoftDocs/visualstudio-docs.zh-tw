---
title: 使用 Visual Studio 在雲端中以使用 Kubernetes 的容器建立 .NET Core 開發環境 - 步驟 3 - 建立 Kubernetes 開發環境 | Microsoft Docs
author: ghogen
ms.author: ghogen
ms.date: 02/20/2018
ms.topic: tutorial
ms.prod: visual-studio-dev15
ms.technology: vs-azure
description: 在 Azure 上使用容器和微服務快速開發 Kubernetes
keywords: Docker, Kubernetes, Azure, AKS, Azure Container Service, 容器
manager: douge
ms.openlocfilehash: 6226340b1744e95bbb375d47213ae00bb9e76565
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="get-started-on-connected-environment-with-net-core-and-visual-studio"></a>使用 .NET Core 和 Visual Studio 開始使用已連線的環境

上一個步驟：[建立 ASP.NET Web 應用程式](get-started-netcore-visualstudio-02.md)

## <a name="create-a-dev-environment-in-azure"></a>在 Azure 中建立開發環境
使用已連線的環境，您可以建立完全受 Azure 管理且針對開發最佳化的 Kubernetes 型開發環境。 開啟我們剛剛建立的專案，從 [啟動設定] 下拉式清單中選取 [Connected Environment for AKS] (適用於 AKS 之已連線的環境)，如下所示。

![](images/LaunchSettings.png)

在接下來顯示的對話方塊中，確定您已使用適當的帳戶登入，然後選取現有的開發環境，或選取 [<Create New Connected Environment for AKS…>] (<建立新的適用於 AKS 之已連線的環境...>)，建立新的已連線環境。

![](images/ConnectedEnvDialog.png)

您可以使用提供的預設值，或依您的喜好調整它們。 正確設定好值之後，按一下 [確定]。

![](images/NewEnvDialog.png)

回到上一個對話方塊，暫且將 [空間] 下拉式清單預設保留為 `mainline`，我們會在後文中詳細討論。 請勾選 [Publicly Accessible] (可公開存取) 核取方塊，讓 Web 應用程式可透過公用端點存取。 這非必要，但對本逐步解說稍後示範一些概念很有幫助。 請不要擔心，無論何種情況您都能夠使用 Visual Studio 偵錯您的網站。

![](images/ConnectedEnvDialog2.png)

按一下 [確定] 選取或建立開發環境。 背景工作a4d 啟動以完成這項作業，約需數分鐘才能完成。 您可以將滑鼠游標移到狀態列左下角的**背景工作**圖示上方查看它是否仍在建立中 (請見下圖)。

![](images/BackgroundTasks.png)

> [!Note]
成功建立開發環境之後，您就無法偵錯應用程式。

## <a name="look-at-the-files-added-to-project"></a>查看新增至專案的檔案
在等候開發環境建立的這段時間，讓我們看看當您選擇使用開發環境時已新增至您專案的檔案。

首先，您會看到已新增名為 `charts` 的資料夾，內含已包含 Scaffold 的應用程式 [Helm 圖表](https://docs.helm.sh)。 這些檔案會用來將您的應用程式部署到開發環境。

您會看到已新增名為 `Dockerfile` 的檔案。 這個檔案有以標準 Docker 格式封裝您應用程式所需要的資訊。 也會建立 `HeaderPropagation.cs` 檔案，我們稍後會在逐步解說中討論這個檔案。 

最後，您會看到名為 `vsce.yaml` 的檔案，它包含開發環境所需要的組態資訊，例如應用程式是否應該透過公用端點存取。

![](images/ProjectFiles.png)

> [!div class="nextstepaction"]
> [在 Kubernetes 中偵錯容器](get-started-netcore-visualstudio-04.md)