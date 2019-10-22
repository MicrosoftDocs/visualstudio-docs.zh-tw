---
title: 加入新的連接 |Microsoft Docs
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: 8a93c287-2834-4a83-a590-bdc3fe8d293f
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 44146613fb43b6fc4269741ba09b94629f888d5f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72673079"
---
# <a name="add-new-connections"></a>新增連線
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以使用**伺服器總管**、 **Cloud Explorer**或**SQL Server 物件總管**，測試與資料庫或服務的連接，以及流覽資料庫內容和架構。 這些視窗的功能會與某個範圍重迭。 基本的差異如下：

 伺服器總管預設會安裝在 Visual Studio 中。 可以用來測試連接及查看 SQL Server 資料庫、已安裝 ADO.NET 提供者的任何其他資料庫，以及一些 Azure 服務。 也會顯示低層級的物件，例如系統效能計數器、事件記錄檔和訊息佇列。 如果資料來源沒有 ADO.NET 提供者，它就不會顯示在這裡，但是您仍然可以透過程式設計方式連接，從 Visual Studio 使用它。

 Cloud Explorer 選取 **工具**  >  **延伸模組和更新**  > **線上** > **Visual Studio 圖庫**，以手動方式將此視窗安裝為 Visual Studio 延伸模組。 提供探索及連線到 Azure 服務的特殊功能。

 SQL Server 物件總管與 SQL Server Data Tools 一起安裝，並顯示在 [ **View** ] 功能表底下。 如果您沒有看到它，請移至 [控制台] 中的 [**程式和功能**]，尋找 Visual Studio，然後選取 [**變更**]，在選取 [SQL Server Data Tools] 核取方塊之後重新執行安裝程式。 使用**SQL Server 物件總管**來查看 SQL 資料庫（如果有 ADO.NET 提供者）、建立新的資料庫、修改架構、建立預存程式、抓取連接字串、查看資料等等。 未安裝任何 ADO.NET 提供者的 SQL 資料庫將不會顯示在這裡，但您仍然可以透過程式設計方式連接到它們。

## <a name="add-a-connection-in-server-explorer"></a>在伺服器總管中新增連接
 若要建立與資料庫的連接，請按一下**伺服器總管**中的 [**加入連接**] 圖示，或以滑鼠右鍵按一下 [**資料連線**] 節點上的**伺服器總管**，然後選取 [**新增連接**]。 從這裡，您也可以連接到另一部伺服器、SharePoint 服務或 Azure 服務上的資料庫。

 ![伺服器總管新連接圖示](../data-tools/media/raddata-server-explorer-new-connection-icon.png "raddata 伺服器總管新連接圖示")

 這會顯示 [**加入連接**] 對話方塊。 在這裡，我們輸入了 SQL Server LocalDB 實例的名稱。

 ![加入新的連接](../data-tools/media/raddata-add-new-connection-dialog.png "raddata 新增連接 對話方塊")

## <a name="change-the-provider"></a>變更提供者
 如果資料來源不是您想要的，請按一下 [**變更**] 按鈕來選擇新的資料來源及/或新的 ADO.NET 資料提供者。 新的提供者可能會詢問您的認證，視您設定的方式而定。

 ![變更 AD0.NET Data Provider](../data-tools/media/raddata-change-ad0-net-data-provider.png "raddata 變更 AD0.NET Data Provider")

## <a name="test-the-connection"></a>測試連線
 選擇資料來源之後，請按一下 [**測試連接**]。 如果不成功，您將需要根據廠商的檔進行疑難排解。

 ![測試連接](../data-tools/media/raddata-test-connection.png "raddata 測試連接")

 如果測試成功，您就可以開始建立*資料來源*，這是一個 Visual Studio 詞彙，這是一個真正表示以基礎資料庫或服務為基礎的*資料模型*。

## <a name="see-also"></a>請參閱
 [適用於 .NET 的 Visual Studio Data Tools](../data-tools/visual-studio-data-tools-for-dotnet.md)
