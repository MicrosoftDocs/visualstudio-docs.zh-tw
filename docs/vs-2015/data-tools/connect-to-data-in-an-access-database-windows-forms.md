---
title: 連接到 Access 資料庫 (Windows Form) 中的資料 |Microsoft Docs
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 120297a7e1b3c1e973f1775d769ab6deb8c2902a
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65705567"
---
# <a name="connect-to-data-in-an-access-database-windows-forms"></a>連線至 Access 資料庫中的資料 (Windows Forms)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以使用 Visual Studio 連線至 Access 資料庫 （.mdf 檔案或.accdb 檔案）。 在您定義連線後，資料就會出現在 [資料來源] 視窗中。 您可以從這個視窗將資料表或檢視表拖曳至表單上。  
  
## <a name="prerequisites"></a>必要條件  
 若要使用這些程序，您需要的 Windows Form 應用程式專案，以及 Access 資料庫 （.accdb 檔案） 或 Access 2000 – 2003年資料庫 （.mdb 檔）。 依照對應您的檔案類型的程序進行。  
  
## <a name="creating-the-dataset-for-an-accdb-file"></a>為 .accdb 檔案建立資料集  
 您可以連接到使用下列程序建立透過 Access 2013、 Office 365、 Access 2010 或 Access 2007 的資料庫。  
  
#### <a name="to-create-the-dataset"></a>建立資料集  
  
1. 開啟資料要連線的 Windows Forms 應用程式。  
  
2. 在 **檢視**功能表上，選取**其他 Windows** > **Zdroje dat**。  
  
     ![檢視其他 Windows 資料來源](../data-tools/media/viewdatasources.png "ViewDataSources")  
  
3. 在 [ **資料來源** ] 視窗中，按一下 [ **加入新資料來源**]。  
  
     ![加入新的資料來源](../data-tools/media/dataaddnewdatasource.png "dataAddNewDataSource")  
  
4. 選取 [**資料庫**上**選擇資料來源類型**頁面，然後再選取**下一步]**。  
  
5. 選取 [**資料集**上**選擇資料庫模型**頁面，然後再選取**下一步]**。  
  
6. 在 [資料連線] 頁面上，選取 [新增連線]，設定新的資料連線。  
  
7. 變更**資料來源**要 **.NET Framework Data Provider for OLE DB**。  
  
     ![將 OLE DB 資料提供者](../data-tools/media/datachangedatasourceoledb.png "dataChangeDataSourceOLEDB")  
  
    > [!IMPORTANT]
    > 雖然資料來源**Microsoft Access 資料庫檔案 (OLE DB)** 可能看起來是正確的選擇，您可以使用該資料來源類型僅適用於.mdb 資料庫檔案。  
  
8. 在  **OLE DB 提供者**，選取**Microsoft Office 12.0 Access 資料庫引擎 OLE DB 提供者**。  
  
     ![OLE DB 提供者 Microsoft Office 12.0 Access](../data-tools/media/dataoledbprovideroffice12access.png "dataOLEDBProviderOffice12Access")  
  
9. 在 **伺服器或檔案名稱**，指定您想要連線，，然後選取的.accdb 檔案的名稱與路徑**確定**。  
  
    > [!NOTE]
    > 如果資料庫檔案的使用者名稱和密碼，請在您選取之前指定它們**確定**。  
  
10. 選取 **下一步**上**選擇資料連接**頁面。  
  
11. 選取 **下一步**上**將連接字串儲存到應用程式組態檔**頁面。  
  
12. 在 [選擇您的資料庫物件] 頁面上，展開 [資料表] 節點。  
  
13. 選取任何資料表或檢視您想要在您的資料集，然後選取**完成**。  
  
     資料集會新增至專案中，而且資料表和檢視表會出現在 [資料來源] 視窗中。  
  
## <a name="creating-the-dataset-for-an-mdb-file"></a>建立資料集為.mdb 檔案  
 藉由執行**資料來源組態精靈**來建立資料集。  
  
#### <a name="to-create-the-dataset"></a>建立資料集  
  
1. 開啟資料要連線的 Windows Forms 應用程式。  
  
2. 在 **檢視**功能表上，選取**其他 Windows** > **Zdroje dat**。  
  
     ![檢視其他 Windows 資料來源](../data-tools/media/viewdatasources.png "ViewDataSources")  
  
3. 在 [ **資料來源** ] 視窗中，按一下 [ **加入新資料來源**]。  
  
4. 選取 [**資料庫**上**選擇資料來源類型**頁面，然後再選取**下一步]**。  
  
5. 選取 [**資料集**上**選擇資料庫模型**頁面，然後再選取**下一步]**。  
  
6. 在 [資料連線] 頁面上，選取 [新增連線]，設定新的資料連線。  
  
7. 如果資料來源不是**Microsoft Access 資料庫檔案 (OLE DB)**，選取**變更**以開啟**變更資料來源** 對話方塊中，然後選取**Microsoft存取資料庫檔案**，然後選取**確定**。  
  
8. 在 **資料庫檔名**，指定您想要連線，，然後選取.mdb 檔案的名稱與路徑**確定**。  
  
     ![新增連接 Access 資料庫檔案](../data-tools/media/dataaddconnectionaccessmdb.png "dataAddConnectionAccessMDB")  
  
9. 選取 **下一步**上**選擇資料連接**頁面。  
  
10. 選取 **下一步**上**將連接字串儲存到應用程式組態檔**頁面。  
  
11. 在 [選擇您的資料庫物件] 頁面上，展開 [資料表] 節點。  
  
12. 選取任何資料表或檢視您想要在您的資料集，然後選取**完成**。  
  
     資料集會新增至專案中，而且資料表和檢視表會出現在 [資料來源] 視窗中。  
  
## <a name="security"></a>安全性  
 儲存敏感資料 (如密碼) 會影響應用程式的安全性。 使用 Windows 驗證 (也稱為整合式安全性) 是控制資料庫存取的更安全方式。 如需詳細資訊，請參閱[保護連線資訊](https://msdn.microsoft.com/library/1471f580-bcd4-4046-bdaf-d2541ecda2f4)。  
  
## <a name="next-steps"></a>後續步驟  
 您剛才建立的資料集現已推出**Zdroje dat**視窗。 現在您可以執行下列任一項工作：  
  
- 選取中的項目**資料來源**視窗中將它們拖曳到您的表單 (請參閱[繫結 Windows Form 控制項加入 Visual Studio 中的資料](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md))。  
  
- 若要新增或編輯組成資料集的物件以 Dataset 設計工具中開啟資料來源。  
  
- 將驗證邏輯加入<xref:System.Data.DataTable.ColumnChanging>或是<xref:System.Data.DataTable.RowChanging>事件的資料集內的資料表 (請參閱[驗證資料集中](../data-tools/validate-data-in-datasets.md))。  
  
## <a name="see-also"></a>另請參閱

 [準備您的應用程式以接收資料](https://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)  \(機器翻譯\)  
 [將控制項繫結至 Visual Studio 中的資料](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [驗證資料](https://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [資料逐步解說](https://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)