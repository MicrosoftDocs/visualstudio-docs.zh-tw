---
title: "連接到 Access 資料庫 (Windows Form) 中的資料 |Microsoft 文件"
ms.custom: 
ms.date: 09/15/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- databases, connecting to
- databases, Access
- data [Visual Studio], connecting
- connecting to data, from Access databases
- Access databases, connecting
ms.assetid: 4159e815-d430-4ad0-a234-e4125fcbef18
caps.latest.revision: "29"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 1f67a87f4a704d3f76ccddba62112983c058a9f3
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2017
---
# <a name="connect-to-data-in-an-access-database-windows-forms"></a>連接到 Access 資料庫 (Windows Form) 中的資料
您可以使用 Visual Studio 連接至 Access 資料庫 （.mdf 檔案或.accdb 檔案）。 定義連接之後，資料會出現在**資料來源**視窗。 您可以從這個視窗將資料表或檢視表拖曳至表單上。   
  
## <a name="prerequisites"></a>必要條件  
 若要使用這些程序，您需要的 Windows Form 應用程式專案，以及 Access 資料庫 （.accdb 檔案） 或 Access 2000-2003年資料庫 （.mdb 檔案）。 依照對應您的檔案類型的程序進行。  
  
## <a name="creating-the-dataset-for-an-accdb-file"></a>建立資料集為.accdb 檔案  
 您可以連接到使用下列程序建立透過 Access 2013、 Office 365、 Access 2010 或 Access 2007 的資料庫。  
  
#### <a name="to-create-the-dataset"></a>建立資料集  
  
1.  開啟您要連接的資料 Windows Form 應用程式。  
  
2.  在**檢視**功能表上，選取**其他視窗** > **資料來源**。  
  
     ![檢視其他視窗資料來源](../data-tools/media/viewdatasources.png "ViewDataSources")  
  
3.  在 [ **資料來源** ] 視窗中，按一下 [ **加入新資料來源**]。  

     **資料來源組態精靈**隨即開啟。  
  
4.  選取**資料庫**上**選擇資料來源類型**頁面，然後再選取**下一步**。  
  
5.  選取**資料集**上**選擇資料庫模型**頁面，然後再選取**下一步**。  
  
6.  在**選擇資料連線**頁面上，選取**新連線**設定新的資料連接。  

     **加入連接**對話方塊隨即開啟。  
  
7.  選取**變更**旁邊**資料來源**文字方塊。

     **變更資料來源**對話方塊隨即開啟。  
  
8.  在資料來源清單中，選擇  **\<其他\>**。 在**資料提供者**下拉式清單中，選取**.NET Framework Data Provider for OLE DB**，然後選擇 **確定**。  

9. 回到**加入連接**對話方塊中，選取**Microsoft Office 12.0 Access 資料庫引擎 OLE DB 提供者**從**OLE DB 提供者**下拉式清單。  
  
     ![OLE DB 提供者 Microsoft Office 12.0 Access](../data-tools/media/dataoledbprovideroffice12access.png "dataOLEDBProviderOffice12Access")  

     > [!NOTE]
     >  如果您沒有看到**Microsoft Office 12.0 Access 資料庫引擎 OLE DB 提供者**在 OLE DB 提供者 下拉式清單，您可能需要安裝[2007 Office System 驅動程式： 資料連線元件](https://www.microsoft.com/download/confirmation.aspx?id=23734)。
  
9. 在**伺服器或檔案名稱** 文字方塊中，指定的路徑和檔案名稱，您想要連接的.accdb 檔案，然後選取**確定**。 (如果資料庫檔案的使用者名稱和密碼，請在您選取之前指定它們**確定**。)    
  
10. 選取**下一步**上**選擇資料連線**頁面。  

     您可能會得到對話方塊，告知您的資料檔案不在目前的專案。 選取 [是]  或 [否] 。
  
11. 選取**下一步**上**將連接字串儲存到應用程式組態檔**頁面。  
  
12. 展開**資料表**節點上的**選擇您的資料庫物件**頁面。  
  
13. 選取現有的任何資料表或檢視您想要在您的資料集，然後選取**完成**。  
  
     資料集加入至專案，並會出現在資料表和檢視表**資料來源**視窗。  
  
## <a name="creating-the-dataset-for-an-mdb-file"></a>建立資料集為.mdb 檔案  
 您建立資料集執行**資料來源組態精靈**。  
  
#### <a name="to-create-the-dataset"></a>建立資料集  
  
1.  開啟您要連接的資料 Windows Form 應用程式。  
  
2.  在**檢視**功能表上，選取**其他視窗** > **資料來源**。  
  
     ![檢視其他視窗資料來源](../data-tools/media/viewdatasources.png "ViewDataSources")  
  
3.  在 [ **資料來源** ] 視窗中，按一下 [ **加入新資料來源**]。  

     **資料來源組態精靈**隨即開啟。
  
4.  選取**資料庫**上**選擇資料來源類型**頁面，然後再選取**下一步**。  
  
5.  選取**資料集**上**選擇資料庫模型**頁面，然後再選取**下一步**。  
  
6.  在**選擇資料連線**頁面上，選取**新連線**設定新的資料連接。  
  
7.  如果資料來源不是**Microsoft Access 資料庫檔案 (OLE DB)**，選取**變更**開啟**變更資料來源**對話方塊並選取**Microsoft存取資料庫檔案**，然後選取**確定**。  
  
8.  在**資料庫檔名**，指定您想要連接到，然後再選取.mdb 檔案的名稱與路徑**確定**。  
  
     ![加入連接 Access 資料庫檔案](../data-tools/media/dataaddconnectionaccessmdb.png "dataAddConnectionAccessMDB")  
  
9. 選取**下一步**上**選擇資料連線**頁面。  
  
10. 選取**下一步**上**將連接字串儲存到應用程式組態檔**頁面。  
  
11. 展開**資料表**節點上的**選擇您的資料庫物件**頁面。  
  
12. 選取現有的任何資料表或檢視您想要在您的資料集，然後選取**完成**。  
  
     資料集加入至專案，並會出現在資料表和檢視表**資料來源**視窗。  
  
## <a name="security"></a>安全性  
 儲存敏感資料 (如密碼) 會影響應用程式的安全性。 使用 Windows 驗證 (也稱為整合式安全性) 是控制資料庫存取的更安全方式。 如需詳細資訊，請參閱[保護連線資訊](/dotnet/framework/data/adonet/protecting-connection-information)。  
  
## <a name="next-steps"></a>後續步驟  
 您剛才建立的資料集現已推出**資料來源**視窗。 您現在可以執行任何下列工作：  
  
-   選取項目中的**資料來源**視窗並拖曳至表單 (請參閱[繫結 Windows Form 控制項加入 Visual Studio 中的資料](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md))。  
  
-   開啟資料來源中的**Dataset 設計工具**新增或編輯組成資料集的物件。  
  
-   將驗證邏輯加入<xref:System.Data.DataTable.ColumnChanging>或<xref:System.Data.DataTable.RowChanging>事件資料中之資料表的資料集 (請參閱[驗證資料在資料集中](../data-tools/validate-data-in-datasets.md))。  
  
## <a name="see-also"></a>請參閱
[加入連接](../data-tools/add-new-connections.md)
