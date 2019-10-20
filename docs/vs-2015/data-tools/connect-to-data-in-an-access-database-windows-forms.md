---
title: 連接到 Access 資料庫中的資料（Windows Forms） |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- databases, connecting to
- databases, Access
- data [Visual Studio], connecting
- connecting to data, from Access databases
- Access databases, connecting
ms.assetid: 4159e815-d430-4ad0-a234-e4125fcbef18
caps.latest.revision: 32
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8426e9fcaa29bef36b6701c78d622f6f42fd1171
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651136"
---
# <a name="connect-to-data-in-an-access-database-windows-forms"></a>連線至 Access 資料庫中的資料 (Windows Forms)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以使用 Visual Studio 連接到 Access 資料庫（.mdf 檔案或 .accdb 檔案）。 在您定義連線後，資料就會出現在 [資料來源] 視窗中。 您可以從這個視窗將資料表或檢視表拖曳至表單上。

## <a name="prerequisites"></a>Prerequisites
 若要使用這些程式，您需要 Windows Forms 應用程式專案，以及 Access 資料庫（.accdb 檔案）或 Access 2000 –2003資料庫（.mdb 檔案）。 依照對應您的檔案類型的程序進行。

## <a name="creating-the-dataset-for-an-accdb-file"></a>為 .accdb 檔案建立資料集
 您可以使用下列程式，連接到透過存取2013、Office 365、存取2010或存取2007所建立的資料庫。

#### <a name="to-create-the-dataset"></a>建立資料集

1. 開啟資料要連線的 Windows Forms 應用程式。

2. 在 [ **View** ] 功能表上，選取 [**其他 Windows**  > **資料來源**]。

     ![查看其他 Windows 資料來源](../data-tools/media/viewdatasources.png "ViewDataSources")

3. 在 [ **資料來源** ] 視窗中，按一下 [ **加入新資料來源**]。

     ![加入新的資料來源](../data-tools/media/dataaddnewdatasource.png "dataAddNewDataSource")

4. 選取 [**選擇資料來源類型**] 頁面上的 [**資料庫**]，然後選取 **[下一步]** 。

5. 在 [**選擇資料庫模型**] 頁面上選取 [**資料集**]，然後選取 **[下一步]** 。

6. 在 [資料連線] 頁面上，選取 [新增連線]，設定新的資料連線。

7. 將**資料來源**變更為**OLE DB 的 .NET Framework Data Provider**。

     ![將 Data Provider 變更為 OLE DB](../data-tools/media/datachangedatasourceoledb.png "dataChangeDataSourceOLEDB")

    > [!IMPORTANT]
    > 雖然**Microsoft Access 資料庫檔案（OLE DB）** 的資料來源看起來可能像是正確的選擇，但您只會針對 .mdb 資料庫檔案使用該資料來源類型。

8. 在**OLE DB 提供者** 中，選取  **Microsoft Office 12.0 存取資料庫引擎 OLE DB 提供者**。

     ![OLE DB 提供者 Microsoft Office 12.0 存取](../data-tools/media/dataoledbprovideroffice12access.png "dataOLEDBProviderOffice12Access")

9. 在 [**伺服器] 或 [檔案名**] 中，指定您要連接的 .accdb 檔案路徑和名稱，然後選取 **[確定]** 。

    > [!NOTE]
    > 如果資料庫檔案具有使用者名稱和密碼，請在選取 **[確定]** 之前先指定這些檔案。

10. 在 [**選擇您的資料連線**] 頁面上選取 **[下一步]** 。

11. 選取 [將**連接字串儲存到應用程式佈建檔**] 頁面上的 [**下一步]** 。

12. 在 [選擇您的資料庫物件] 頁面上，展開 [資料表] 節點。

13. 選取您想要在資料集中的任何資料表或視圖，然後選取 **[完成]** 。

     資料集會新增至專案中，而且資料表和檢視表會出現在 [資料來源] 視窗中。

## <a name="creating-the-dataset-for-an-mdb-file"></a>建立 .mdb 檔案的資料集
 藉由執行**資料來源組態精靈**來建立資料集。

#### <a name="to-create-the-dataset"></a>建立資料集

1. 開啟資料要連線的 Windows Forms 應用程式。

2. 在 [ **View** ] 功能表上，選取 [**其他 Windows**  > **資料來源**]。

     ![查看其他 Windows 資料來源](../data-tools/media/viewdatasources.png "ViewDataSources")

3. 在 [ **資料來源** ] 視窗中，按一下 [ **加入新資料來源**]。

4. 選取 [**選擇資料來源類型**] 頁面上的 [**資料庫**]，然後選取 **[下一步]** 。

5. 在 [**選擇資料庫模型**] 頁面上選取 [**資料集**]，然後選取 **[下一步]** 。

6. 在 [資料連線] 頁面上，選取 [新增連線]，設定新的資料連線。

7. 如果資料來源不是**Microsoft Access 資料庫檔案（OLE DB）** ，請選取 **[變更**] 開啟 [**變更資料來源**] 對話方塊，並選取 [ **Microsoft Access 資料庫**檔案]，然後選取 **[確定]** 。

8. 在 [**資料庫檔案名**] 中，指定您要連接的 .mdb 檔案的路徑和名稱，然後選取 **[確定]** 。

     ![新增連接存取資料庫檔案](../data-tools/media/dataaddconnectionaccessmdb.png "dataAddConnectionAccessMDB")

9. 在 [**選擇您的資料連線**] 頁面上選取 **[下一步]** 。

10. 選取 [將**連接字串儲存到應用程式佈建檔**] 頁面上的 [**下一步]** 。

11. 在 [選擇您的資料庫物件] 頁面上，展開 [資料表] 節點。

12. 選取您想要在資料集中的任何資料表或視圖，然後選取 **[完成]** 。

     資料集會新增至專案中，而且資料表和檢視表會出現在 [資料來源] 視窗中。

## <a name="security"></a>安全性
 儲存敏感資料 (如密碼) 會影響應用程式的安全性。 使用 Windows 驗證 (也稱為整合式安全性) 是控制資料庫存取的更安全方式。 如需詳細資訊，請參閱[保護連線資訊](https://msdn.microsoft.com/library/1471f580-bcd4-4046-bdaf-d2541ecda2f4)。

## <a name="next-steps"></a>後續步驟
 您剛才建立的資料集現在可以在 [**資料來源**] 視窗中使用。 現在您可以執行下列任一項工作：

- 選取 [**資料來源**] 視窗中的專案，並將其拖曳至您的表單（請參閱將[Windows Forms 控制項系結至 Visual Studio 中的資料](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)）。

- 在 DataSet 設計工具中開啟資料來源，以加入或編輯組成資料集的物件。

- 將驗證邏輯加入至資料集內資料表的 <xref:System.Data.DataTable.ColumnChanging> 或 <xref:System.Data.DataTable.RowChanging> 事件中（請參閱[驗證資料集中的資料](../data-tools/validate-data-in-datasets.md)）。

## <a name="see-also"></a>請參閱

 [準備您的應用程式以接收資料](https://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)將控制項系結至 Visual Studio[驗證資料](https://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)[資料](https://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)逐步解說[中的資料](../data-tools/bind-controls-to-data-in-visual-studio.md)