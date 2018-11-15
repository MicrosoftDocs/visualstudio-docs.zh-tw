---
title: 使用 Cloud Explorer 管理 Azure 資源 |Microsoft Docs
description: 了解如何使用雲端總管來瀏覽和管理 Visual Studio 內的 Azure 資源。
author: ghogen
manager: douge
assetId: 6347dc53-f497-49d5-b29b-e8b9f0e939d7
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/25/2017
ms.author: ghogen
ms.openlocfilehash: a5b75aa5e1310e02befe162199472eef987d7cd9
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/05/2018
ms.locfileid: "51001400"
---
# <a name="manage-the-resources-associated-with-your-azure-accounts-in-visual-studio-cloud-explorer"></a>在 Visual Studio Cloud Explorer 中管理與您的 Azure 帳戶關聯的資源

Cloud Explorer 可讓您檢視您的 Azure 資源和資源群組、 檢查其屬性，以及執行重要的開發人員診斷動作，從 Visual Studio 內。 

像是[Azure 入口網站](http://go.microsoft.com/fwlink/p/?LinkID=525040)，Cloud Explorer 建置在 Azure Resource Manager 堆疊。 因此，Cloud Explorer 了解 Azure 資源群組之類的資源和 Azure 服務，例如 Logic apps 和 API 應用程式，並支援[角色型存取控制](/azure/role-based-access-control/role-assignments-portal.md)(RBAC)。 

## <a name="prerequisites"></a>必要條件

* Visual Studio 2015 [Microsoft Azure SDK for.NET 2.9](https://www.microsoft.com/en-us/download/details.aspx?id=51657)。
* Microsoft Azure 帳戶-如果您還沒有帳戶，您可以[申請免費試用](http://go.microsoft.com/fwlink/?LinkId=623901)或是[啟用您的 Visual Studio 訂閱者權益](http://go.microsoft.com/fwlink/?LinkId=623901)。

> [!NOTE]
> 若要檢視 Cloud Explorer，請選取**檢視** > **Cloud Explorer**功能表列上。

## <a name="add-an-azure-account-to-cloud-explorer"></a>將 Azure 新增帳戶至 雲端總管

若要檢視與 Azure 帳戶相關聯的資源，您必須先將帳戶加入 Cloud Explorer。 

1. 在  **Cloud Explorer**，選取**Azure 帳戶設定**。

   ![Cloud explorer 的 [Azure 帳戶設定] 圖示](./media/vs-azure-tools-resources-managing-with-cloud-explorer/azure-account-settings.png)

1. 選取 **管理帳戶**。 

   ![雲端總管新增帳戶 連結](./media/vs-azure-tools-resources-managing-with-cloud-explorer/manage-accounts-link.png)

1. 登入 Azure 帳戶想要瀏覽其的資源。 

1. 一旦登入 Azure 帳戶，便會顯示與該帳戶相關聯的訂用帳戶。 選取您想要瀏覽，然後選取的訂用帳戶的核取方塊**套用**。 

   ![Cloud Explorer： 選取要顯示的 Azure 訂用帳戶](./media/vs-azure-tools-resources-managing-with-cloud-explorer/select-subscriptions.png)

1. 選取您想要瀏覽的資源的訂用帳戶之後, 的訂用帳戶和資源顯示在 [雲端總管]。

   ![Cloud Explorer 資源列出的 Azure 帳戶](./media/vs-azure-tools-resources-managing-with-cloud-explorer/resources-listed.png)

## <a name="remove-an-azure-account-from-cloud-explorer"></a>從 [雲端總管] 中移除 Azure 帳戶 

1. 在  **Cloud Explorer**，選取**帳戶管理**。

   ![Cloud explorer 的 [Azure 帳戶設定] 圖示](./media/vs-azure-tools-resources-managing-with-cloud-explorer/azure-account-settings.png)

1. 旁邊要移除的帳戶，選取**Manage Accounts**。

   ![Cloud explorer 的 [Azure 帳戶設定] 圖示](./media/vs-azure-tools-resources-managing-with-cloud-explorer/remove-account.png)

1. 選擇**移除**移除帳戶。

    ![雲端總管管理帳戶 對話方塊](./media/vs-azure-tools-resources-managing-with-cloud-explorer/accountmanage.PNG)

## <a name="view-resource-types-or-resource-groups"></a>檢視資源類型或資源群組

若要檢視您的 Azure 資源，您可以選擇**資源類型**或是**資源群組**檢視。

1. 在  **Cloud Explorer**，選取 資源檢視下拉式清單。

   ![Cloud Explorer 下拉式清單選取所需的資源檢視](./media/vs-azure-tools-resources-managing-with-cloud-explorer/resources-view-dropdown.png)

1. 從操作功能表中，選取所要的檢視： 

   * **資源類型**檢視-上使用的一般檢視[Azure 入口網站](http://go.microsoft.com/fwlink/p/?LinkID=525040)，顯示依其類型，例如 web apps、 儲存體帳戶和虛擬機器分類您 Azure 資源。 
   * **資源群組**檢視-將 Azure 資源依其所關聯的 Azure 資源群組。 資源群組是通常由特定應用程式的 Azure 資源的組合。 若要深入了解 Azure 資源群組，請參閱[Azure Resource Manager 概觀](/azure/azure-resource-manager/resource-group-overview)。

   下圖顯示兩個資源檢視的比較：

   ![Cloud Explorer 資源檢視比較](./media/vs-azure-tools-resources-managing-with-cloud-explorer/resource-views-comparison.png)

## <a name="view-and-navigate-resources-in-cloud-explorer"></a>檢視和瀏覽在 Cloud Explorer 中的資源

若要瀏覽至 Azure 的資源，並檢視其資訊在 Cloud Explorer 中，展開的項目類型或相關聯的資源群組，然後選取資源。 當您選取資源時，資訊會出現在兩個索引標籤-**動作**並**屬性**-在 Cloud Explorer 底部。

* **動作**索引標籤-列出您可以在 Cloud Explorer 中選取的資源採取的動作。 您也可以檢視這些選項，以滑鼠右鍵按一下要檢視其操作功能表的資源。

* **屬性**索引標籤-顯示資源，例如其類型、 地區設定和資源群組與相關聯的屬性。

下圖顯示您看到每個索引標籤上的 App Service 的範例比較：

  ![雲端總管 的螢幕擷取畫面](./media/vs-azure-tools-resources-managing-with-cloud-explorer/actions-and-properties.png)

每個資源具有動作**在入口網站中開啟**。 當您選擇此動作時，Cloud Explorer 會顯示在選取的資源[Azure 入口網站](http://go.microsoft.com/fwlink/p/?LinkID=525040)。 **在入口網站中開啟**功能可方便您瀏覽至深度巢狀資源。

其他動作和屬性值也可能會出現根據 Azure 資源。 例如，web apps 和 logic apps 也有動作**在瀏覽器中開啟**並**附加偵錯工具**除了**在入口網站中開啟**。 當您選擇儲存體帳戶 blob、 佇列或資料表時，會出現開啟編輯器的動作。 Azure 應用程式具有**URL**並**狀態**屬性，而儲存體資源具有索引鍵和連接字串屬性。

## <a name="find-resources-in-cloud-explorer"></a>在 [雲端總管] 中尋找資源

若要在您 Azure 訂用帳戶中尋找具有特定名稱的資源，請輸入中的名稱**搜尋**方塊在 [雲端總管]。

  ![在 [雲端總管] 中尋找資源](./media/vs-azure-tools-resources-managing-with-cloud-explorer/search-for-resources.png)

當您在輸入中的字元**搜尋** 方塊中，只有符合這些字元的資源才會出現在資源樹狀目錄中。
