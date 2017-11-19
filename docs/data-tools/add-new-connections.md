---
title: "加入新連接 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8a93c287-2834-4a83-a590-bdc3fe8d293f
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: accf99d7a1d230bac64ebd8ebf9c9f1071ad1876
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="add-new-connections"></a>加入新的連線
您可以測試您的連線到資料庫或服務，並使用瀏覽資料庫內容和結構描述，**伺服器總管**， **Cloud Explorer**，或**SQL Server 物件總管**. 這些視窗的功能會重疊在某個程度。 基本的差異如下：  
  
 - 伺服器總管  
 在 Visual Studio 中的預設安裝。 可用來測試連線並檢視 SQL Server 資料庫、 已安裝，ADO.NET 提供者的任何其他資料庫和某些 Azure 服務。 低層級物件，例如系統效能計數器、 事件記錄檔，以及訊息佇列也會顯示。 如果資料來源沒有任何 ADO.NET 提供者，它將不會顯示在這裡，但您仍然可以使用它從 Visual Studio 以程式設計方式連接。  
  
 - Cloud Explorer  
 選取此視窗手動安裝 Visual Studio 擴充功能為**工具** > **擴充功能和更新** > **線上** >  **Visual Studio 組件庫**。 瀏覽及連接到 Azure 的服務提供特殊的功能。  
  
 - SQL Server 物件總管  
 已安裝 SQL Server Data tools 和底下看見**檢視**功能表。 如果您沒有看到那里，請移至**程式和功能**在控制台中，尋找 Visual Studio，然後選取**變更**重新執行安裝程式的 SQL Server Data Tools 中選取核取方塊之後。 使用**SQL Server 物件總管**到檢視的 SQL 資料庫 （如果它們有 ADO.NET 提供者），建立新的資料庫中修改結構描述、 建立預存程序，擷取連接字串，檢視資料，以及進行其他。 不已安裝任何 ADO.NET 提供者的 SQL 資料庫不會顯示在這裡，但您仍然連接至模型以程式設計的方式。  
  
## <a name="add-a-connection-in-server-explorer"></a>在 伺服器總管加入連接  
 若要建立資料庫的連接，請按一下**加入連接**中的圖示**伺服器總管**，或以滑鼠右鍵按一下**伺服器總管**上**資料連線**節點，然後選取**加入連接**。 從這裡，您也可以連接到另一部伺服器、 SharePoint 服務或 Azure 服務的資料庫。  
  
 ![伺服器總管 的新連接圖示](../data-tools/media/raddata-server-explorer-new-connection-icon.png "raddata 伺服器總管 中的新連接圖示")  
  
 這會開啟**加入連接** 對話方塊。 在這裡，我們輸入 SQL Server LocalDB 執行個體的名稱。  
  
 ![加入新的連接](../data-tools/media/raddata-add-new-connection-dialog.png "raddata 新增新的連接對話方塊")  
  
## <a name="change-the-provider"></a>變更提供者  
 如果不想要的資料來源，請按一下**變更**按鈕來選擇新的資料來源及/或新的 ADO.NET 資料提供者。 新的提供者可能會要求您提供認證，根據您設定的方式。  
  
 ![變更 AD0.NET 資料提供者](../data-tools/media/raddata-change-ad0.net-data-provider.png "raddata 變更 AD0.NET 資料提供者")  
  
## <a name="test-the-connection"></a>測試連接  
 您已選擇資料來源之後，請按一下**測試連接**。 如果不成功，您必須疑難排解根據廠商的說明文件。  
  
 ![測試連接](../data-tools/media/raddata-test-connection.png "raddata 測試連接")  
  
 如果測試成功，即準備好建立*資料來源*，這是一個 Visual Studio 詞彙，實際上會*資料模型*為基礎的基礎資料庫或服務。  
  
## <a name="see-also"></a>另請參閱  
 [適用於 .NET 的 Visual Studio Data Tools](../data-tools/visual-studio-data-tools-for-dotnet.md)