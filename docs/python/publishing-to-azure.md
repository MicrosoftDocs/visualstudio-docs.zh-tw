---
title: "從 Visual Studio 將 Python 應用程式發佈至 Azure App Service | Microsoft Docs"
ms.custom: 
ms.date: 7/13/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 85031f91-3a65-463b-a678-1e69f1b843e6
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6d25db4639f2c8391c1e32542701ea359f560178
ms.openlocfilehash: 9bce1901cc86eea29638d4a715c18c6367fa6dc6
ms.contentlocale: zh-tw
ms.lasthandoff: 07/18/2017

---

# <a name="publishing-to-azure-app-service"></a>發佈至 Azure App Service

您可以透過下列步驟快速地在 Visual Studio 中建置 Python 網站，並將它發佈至 Azure App Service：

- [建立 Azure 訂用帳戶](#create-an-azure-subscription)
- [建立並測試初始專案](#create-and-test-the-initial-project)
- [發佈至 Azure App Service](#publish-to-azure-app-service)

如需此程序的簡短逐步解說，請觀看 [Visual Studio Python 教學課程：建置網站 (英文)](https://www.youtube.com/watch?v=FJx5mutt1uk&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=6) (youtube.com，3 分 10 秒)。 

> [!VIDEO https://www.youtube.com/embed/FJx5mutt1uk] 

## <a name="create-an-azure-subscription"></a>建立 Azure 訂用帳戶

發佈至 Azure 將會需要 Azure 訂用帳戶，您也可以使用暫時網站。

針對訂用帳戶，請從[免費的完整 Azure 帳戶](https://azure.microsoft.com/en-us/free/)開始，其中包含適用於 Azure 服務的贈送點數。 此外，請考慮註冊 [Visual Studio Dev Essentials](https://azure.microsoft.com/en-us/pricing/member-offers/vs-dev-essentials/)，您一整年都能在每個月取得美金 $25 的點數。

在無需 Azure 訂用帳戶的情況下，於 Azure App Service 中建立暫時網站：

1. 開啟瀏覽器並移至 [try.azurewebsites.net](https://try.azurewebsites.net)。
1. 選取 [Web 應用程式] 作為應用程式類型，然後選取 [下一步]。
1. 選取 [空白網站] 作為範本，然後選取 [建立 >]。
1. 以您選擇的社交登入進行登入，在經過一小段時間之後，就可以透過顯示的 URL 存取您的網站。
1. 選取 [下載發行設定檔] 並儲存 `.publishsettings` 檔案，稍後您會使用此檔案。

## <a name="create-and-test-the-initial-project"></a>建立並測試初始專案

1. 在 Visual Studio 中，選取 [檔案] > [新增] > [專案]，搜尋 "Bottle"，選取 [Bottle Web 專案]，然後按一下 [確定]。    

1. 當系統提示您安裝外部套件時，選取 [安裝至虛擬環境]。 請注意，對話方塊底部的 [顯示必要套件] 控制項會顯示將安裝的套件：

  ![安裝必要套件](media/tutorials-common-external-packages.png)

1. 針對虛擬環境選取您偏好的基礎解譯器 (例如 **Python 2.7** 或 **Python 3.4**)，然後按一下 [建立]：

  ![在建立專案時新增虛擬環境](media/tutorials-common-add-virtual-environment.png)

1. 當專案建立好之後，透過選取 [偵錯] > [開始偵錯] 或按 F5，在本機測試專案。 根據預設，應用程式會使用不需要進行任何設定的記憶體內部存放庫。 所有資料都會在網頁伺服器停止時遺失。

1. 在應用程式內四處點擊，以測試其作業。

1. 當您完成時，請停止偵錯工具 ([偵錯] > [停止偵錯]，或 Shift-F5)。

## <a name="publish-to-azure-app-service"></a>發佈至 Azure App Service

1. 在 [方案總管] 中，以滑鼠右鍵按一下專案，選取 [發行]。 

1. 在 [發行] 對話方塊中，選取 [Microsoft Azure App Service]：

  ![發佈至 Azure 步驟 1](media/tutorials-common-publish-1.png)

1. 選取目標：

    - 如果您有 Azure 訂用帳戶，請選取 [Microsoft Azure App Service] 作為 發佈目標，然後在下列對話方塊中選取現有的 App Service，或選取 [新增] 以建立新的 App Service。
    - 如果您是使用來自 try.azurewebsites.net 的暫時網站，請選取 [匯入] 作為發佈目標，然後瀏覽至從網站下載的 `.publishsettings` 檔案，並選取 [確定]。

1. App Service 詳細資料會出現在 [發行] 對話方塊的 [連線] 索引標籤中，如下所示。

  ![發佈至 Azure 步驟 2](media/tutorials-common-publish-2.png)

1. 視需要選取 [下一步 >] 以檢閱其他設定。 如果您計畫[在 Azure 上對 Python 程式碼進行遠端偵錯](debugging-azure-remote.md)，您必須將 [組態] 設定為 [偵錯]
1. 選取 [發行]。 將您的應用程式部署至 Azure 之後，就會在該網站上開啟您的預設瀏覽器。 
