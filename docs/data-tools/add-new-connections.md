---
title: 新增連線
description: 使用伺服器總管、Cloud Explorer 或 SQL Server 物件總管，將 Visual Studio 中的連接新增至 DB 或服務，以及探索 DB 內容和架構。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: ddcc5dd06a4e71d445c94c860b2a3ab92429ab2e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99859381"
---
# <a name="add-new-connections"></a>新增連線

您可以使用 **伺服器總管**、 **Cloud Explorer** 或 **SQL Server 物件總管**，測試與資料庫或服務的連接，以及探索資料庫內容和架構。 這些視窗的功能與某個程度重迭。 基本差異如下：

- Server Explorer

   預設會安裝在 Visual Studio 中。 可以用來測試連接和查看 SQL Server 資料庫、已安裝 ADO.NET 提供者的任何其他資料庫，以及某些 Azure 服務。 也會顯示低層級的物件，例如系統效能計數器、事件記錄檔和訊息佇列。 如果資料來源沒有 ADO.NET 提供者，它就不會顯示在這裡，但是您仍然可以透過程式設計方式來使用 Visual Studio。

- Cloud Explorer

   以手動方式將此視窗安裝為 [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.CloudExplorerForVS)的 Visual Studio 延伸模組。 提供探索及連接到 Azure 服務的特殊功能。

- SQL Server 物件總管

   隨 SQL Server Data Tools 安裝並顯示在 [ **View** ] 功能表底下。 如果您沒有看到它，請移至主控台中的 [ **程式和功能** ]、[尋找 Visual Studio]，然後選取 [ **變更** ]，在選取 [SQL Server Data Tools] 的核取方塊後重新執行安裝程式。 如果 SQL 資料庫具有 ADO.NET 提供者) 、建立新的資料庫、修改架構、建立預存程式、取出連接字串、查看資料等，請使用 **SQL Server 物件總管** 來查看 SQL database (。 未安裝任何 ADO.NET 提供者的 SQL database 將不會顯示在這裡，但您仍然可以透過程式設計方式連接到這些資料庫。

## <a name="add-a-connection-in-server-explorer"></a>在伺服器總管中新增連接

若要建立資料庫的連接，請按一下 **伺服器總管** 中的 [**加入連接**] 圖示，或以滑鼠右鍵按一下 [**資料連線**] 節點上的 **伺服器總管**，然後選取 [**加入連接**]。 您也可以從這裡連接到另一部伺服器、SharePoint 服務或 Azure 服務上的資料庫。

![伺服器總管新的連接圖示](../data-tools/media/raddata-server-explorer-new-connection-icon.png)

這會顯示 [ **加入連接** ] 對話方塊。 在這裡，我們輸入了 SQL Server LocalDB 實例的名稱。

![新增連線](../data-tools/media/raddata-add-new-connection-dialog.png)

## <a name="change-the-provider"></a>變更提供者

如果資料來源不是您想要的，請按一下 [ **變更** ] 按鈕，選擇新的資料來源和/或新的 ADO.NET 資料提供者。 新的提供者可能會要求您提供認證，端視您的設定方式而定。

![變更 AD0.NET Data Provider](../data-tools/media/raddata-change-ad0.net-data-provider.png)

## <a name="test-the-connection"></a>測試連線

選擇資料來源之後，請按一下 [ **測試連接**]。 如果不成功，您將需要根據廠商的檔進行疑難排解。

![[測試連接]](../data-tools/media/raddata-test-connection.png)

如果測試成功，您就可以建立 *資料來源*，這是一個 Visual Studio 詞彙，這是真正表示以基礎資料庫或服務為基礎的 *資料模型* 。

## <a name="see-also"></a>另請參閱

- [適用於 .NET 的 Visual Studio Data Tools](../data-tools/visual-studio-data-tools-for-dotnet.md)
