---
title: 準備發佈或部署雲端服務，從 Visual Studio |Microsoft Docs
description: 了解設定雲端與儲存體帳戶服務和設定 Azure 應用程式的程序。
author: ghogen
manager: douge
ms.assetid: 92ee2f9e-ec49-4c7a-900d-620abe5e9d8a
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/10/2017
ms.author: ghogen
ms.openlocfilehash: d7643d87f60b953b9c0928571036c7890e4d11f0
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002028"
---
# <a name="prepare-to-publish-or-deploy-a-cloud-service-from-visual-studio"></a>準備從 Visual Studio 發佈或部署雲端服務

若要發佈雲端服務專案，您必須設定下列服務在這篇文章中所述：

* A**雲端服務**在 Azure 環境中，執行您的角色和 
* A**儲存體帳戶**提供 Blob、 佇列和表格服務的存取權。

## <a name="create-a-cloud-service"></a>建立雲端服務

雲端服務在 Azure 環境中執行角色。 您可以建立雲端服務，在 Visual Studio 或是透過[Azure 入口網站](https://portal.azure.com/)以下各節中所述。

### <a name="create-a-cloud-service-from-visual-studio"></a>從 Visual Studio 建立雲端服務

1. 使用先前建立的雲端服務專案，以滑鼠右鍵按一下專案，選取**發佈**。
1. 如有必要，請使用 Microsoft 或您 Azure 訂用帳戶相關聯的組織帳戶登入，然後選取**下一步**前往**設定**頁面。
1. A**建立雲端服務和儲存體帳戶**對話方塊隨即出現 (如果沒有，請選取**新建**從**雲端服務**清單)。
1. 輸入您的雲端服務，這會形成 URL 的一部分，而且必須是唯一的不區分大小寫名稱。 也選擇區域或同質群組，然後選取 [複寫] 選項。

### <a name="create-a-cloud-service-through-the-azure-portal"></a>建立雲端服務透過 Azure 入口網站

1. 登入 [Azure 入口網站](https://portal.azure.com/)。
1. 選取 **雲端服務 （傳統）** 頁面的左邊。
1. 選取  **+ 新增**，然後提供必要的資訊 （DNS 名稱、 訂用帳戶、 資源群組和位置）。 您不需要將套件上傳在此時因為您稍後在 Visual Studio 中執行的。
1. 選取 **建立**完成程序。

## <a name="create-a-storage-account"></a>建立儲存體帳戶

儲存體帳戶提供 Blob、 佇列和表格服務的存取權。 您可以建立儲存體帳戶，透過 Visual Studio 或[Azure 入口網站](https://portal.azure.com/)。

### <a name="create-a-storage-account-from-visual-studio"></a>從 Visual Studio 中建立儲存體帳戶

1. 在 [**方案總管] 中**先前建立的雲端服務專案中，找出**已連接服務**節點內的角色專案、 按一下滑鼠右鍵，然後選取**加入已連接服務**. (在 Visual Studio 2015 中，以滑鼠右鍵按一下**儲存體**節點，然後選取**建立儲存體帳戶**。)
1. 在 **已連線的服務**顯示清單中，選取**搭配 Azure 儲存體的雲端儲存體**。
1. 在出現 [Azure 儲存體] 對話方塊中，選取 **+ 建立新的儲存體帳戶**，以顯示的對話方塊，您可以在其中指定您的訂用帳戶中，而名稱該帳戶、 定價層、 資源群組和位置。
1. 選取 **建立**完成時。 新的儲存體帳戶會出現在您的訂用帳戶中的可用儲存體帳戶的清單。
1. 選取該帳戶，然後選取**新增**。

### <a name="create-a-storage-account-through-the-azure-portal"></a>建立儲存體帳戶，透過 Azure 入口網站

1. 登入 [Azure 入口網站](https://portal.azure.com/)。
1. 選取  **+ 新增**左上方。
1. 選取 **儲存體**在 「 Azure Marketplace 中，「 再**儲存體帳戶-blob、 檔案、 資料表、 佇列**從右邊算起。
1. 提供必要的資訊 （名稱、 部署模型和其他等等。
1. 選取 **建立**完成程序。

## <a name="configure-your-app-to-use-the-storage-account"></a>設定您的應用程式使用的儲存體帳戶

建立儲存體帳戶之後，連接到它從 Visual Studio 會自動更新服務組態的專案，包括 Url 及存取金鑰。

如果您從使用 Visual Studio 建立雲端服務**加入已連接服務**，您可以開啟連線，請檢查連接`ServiceConfiguration.Cloud.cscfg`和`ServiceConfiguration.Local.cscfg`。

如果您建立雲端服務透過 Azure 入口網站，請依照下列中的相同步驟[從 Visual Studio 中建立儲存體帳戶](#create-a-storage-account-from-visual-studio)但選取現有的帳戶而非建立新帳戶。 Visual Studio，然後更新您的設定。

若要設定設定以手動的方式，使用屬性頁在 Visual Studio 中的雲端服務專案適用角色 (以滑鼠右鍵按一下角色，然後選取**屬性**)。 如需詳細資訊，請參閱 <<c0> [ 設定的儲存體帳戶的連接字串](vs-azure-tools-multiple-services-project-configurations.md#configuring-a-connection-string-for-a-storage-account)。

### <a name="about-access-keys"></a>關於存取金鑰

Azure 入口網站顯示的 Url，您可用來存取每個 Azure 儲存體服務，以及主要和次要存取金鑰，為您的帳戶中的資源。 您可以使用這些金鑰來驗證對儲存體服務提出的要求。

次要存取金鑰提供您的儲存體帳戶的主要存取金鑰與相同的存取，且會產生做為備份您的主要存取金鑰遭到入侵。 此外，建議您重新產生存取金鑰以規則為基礎。 您可以修改連接字串設定為使用次要金鑰，當您重新產生主要金鑰，則您可以修改它以使用已重新產生主索引鍵，而您重新產生次要金鑰。

## <a name="next-steps"></a>後續步驟

若要深入了解應用程式發行至 Azure 從 Visual Studio，請參閱[發佈雲端服務使用 Azure Tools](vs-azure-tools-publishing-a-cloud-service.md)。
