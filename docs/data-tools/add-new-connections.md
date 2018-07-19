---
title: 新增連線
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 14df0183076125e487873bbb9865b2481e277a5b
ms.sourcegitcommit: ce154aee5b403d5c1c41da42302b896ad3cf8d82
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/07/2018
ms.locfileid: "34845011"
---
# <a name="add-new-connections"></a>新增連線

您可以測試您的連線到資料庫或服務，並瀏覽資料庫內容和結構描述，使用**伺服器總管**， **Cloud Explorer**，或**SQL Server 物件總管**. 這些視窗的功能重疊在某個程度。 基本差異如下：

- 伺服器總管

   在 Visual Studio 中的預設安裝。 可用來測試連線並檢視 SQL Server 資料庫、 已安裝，ADO.NET 提供者的任何其他資料庫和某些 Azure 服務。 也會顯示低層級的物件，例如系統效能計數器、 事件記錄檔，以及訊息佇列。 如果資料來源不有任何 ADO.NET 提供者，它將不會顯示在這裡，但您仍然可以使用它從 Visual Studio 以程式設計方式連接。

- Cloud Explorer

   選取此視窗手動安裝為 Visual Studio 延伸模組**工具** > **擴充功能和更新** > **線上** >  **Visual Studio Markeplace**。 提供探索及連接到 Azure 服務的特製化的功能。

- SQL Server 物件總管

   使用 SQL Server Data Tools 安裝並顯示於下方**檢視**功能表。 如果您沒有看到它那里，請移至**程式和功能**控制台 中尋找 Visual Studio 中，然後**變更**重新執行 SQL Server Data tools 中選取核取方塊之後的 安裝程式。 使用**SQL Server 物件總管**檢視的 SQL 資料庫 （如果他們擁有的 ADO.NET 提供者），以建立新的資料庫、 修改結構描述、 建立預存程序，擷取連接字串、 檢視資料等。 不已安裝任何 ADO.NET 提供者的 SQL database 不會顯示在這裡，但您仍可連線以程式設計的方式給他們。

## <a name="add-a-connection-in-server-explorer"></a>在 [伺服器總管] 新增連線

若要建立資料庫的連接，請按一下**加入連接**中的圖示**伺服器總管**，或以滑鼠右鍵按一下**伺服器總管**上**資料連線**節點，然後選取**加入連接**。 從這裡開始，您也可以連接到另一部伺服器、 SharePoint 服務或 Azure 服務上的資料庫。

![伺服器總管新增連接 圖示](../data-tools/media/raddata-server-explorer-new-connection-icon.png)

這會帶來**加入連接** 對話方塊。 我們在這裡，輸入 SQL Server LocalDB 執行個體的名稱。

![加入新的連接](../data-tools/media/raddata-add-new-connection-dialog.png)

## <a name="change-the-provider"></a>變更提供者

如果不是您想要的資料來源，請按一下**變更** 按鈕，選擇新的資料來源及/或新的 ADO.NET 資料提供者。 新的提供者可能會要求您提供認證，根據您設定的方式。

![變更 AD0.NET 資料提供者](../data-tools/media/raddata-change-ad0.net-data-provider.png)

## <a name="test-the-connection"></a>測試連接

您已選擇資料來源之後，請按一下**測試連接**。 如果不成功，您必須疑難排解根據廠商的文件。

![測試連接](../data-tools/media/raddata-test-connection.png)

如果測試成功，您已準備好建立*資料來源*，這指的是 Visual Studio，真正的意義*資料模型*為基礎的基礎資料庫或服務。

## <a name="see-also"></a>另請參閱

- [適用於 .NET 的 Visual Studio Data Tools](../data-tools/visual-studio-data-tools-for-dotnet.md)