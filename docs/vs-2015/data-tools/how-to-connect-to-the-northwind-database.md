---
title: 如何： 連接到 Northwind 資料庫 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- connections [Visual Studio], Northwind database
- Northwind sample database
ms.assetid: cc6cb79f-d035-41f8-b398-8d4a45922bfb
caps.latest.revision: 29
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 45e8e1bcab3af0c55a541b589574eca37fc7f2ec
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47499752"
---
# <a name="how-to-connect-to-the-northwind-database"></a>如何：連接到 Northwind 資料庫
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

由於您學習如何使用 Visual Studio 建立資料庫應用程式，所以需要連接 Northwind 資料庫以遵循該產品文件中的許多範例進行。 根據所遵循的範例，您將連接至 SQL Server 或資料庫檔案 (例如 Microsoft Access 或 SQL Server 的資料庫檔案) 中的資料庫。  
  
## <a name="creating-data-connections-to-the-northwind-database"></a>建立與 Northwind 資料庫的資料連接  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
#### <a name="to-create-a-data-connection-to-the-northwind-database-sql-server"></a>建立與 Northwind 資料庫的資料連接 (SQL Server)  
  
1.  在 **檢視**功能表上，選擇**伺服器總管**/**資料庫總管**。  
  
2.  在 **伺服器總管**/**資料庫總管**，開啟捷徑功能表**資料連接**，然後選擇 **加入連接**.  
  
     選擇之後**加入連接**，可以是**選擇資料來源**對話方塊或**加入連接**對話方塊會隨即出現。  
  
3.  如果**選擇資料來源** 對話方塊出現時，選取**Microsoft SQL Server**，然後選擇**確定**。  
  
     如果**加入連接** 對話方塊隨即出現並**資料來源**不**Microsoft SQL Server (SqlClient)**，選擇**變更**按鈕，開啟**變更資料來源**對話方塊中，選取**Microsoft SQL Server**，然後選擇**確定**  按鈕。  
  
4.  在 **伺服器名稱**清單中，指定 Northwind 資料庫所在伺服器的名稱。  
  
5.  根據您的 SQL Server 和 Northwind 資料庫版本需求，選擇**使用 Windows 驗證**，或選擇**使用 SQL Server 驗證**，然後輸入使用者名稱和若要執行 SQL Server 的電腦登入的密碼。  
  
6.  選擇 Northwind 資料庫中的**選取或輸入資料庫名稱**清單。  
  
7.  選擇**測試連接**來確認與 Northwind 資料庫的連線能力。  
  
8.  選擇 [確定] 。  
  
     資料連接到 Northwind 資料庫加入至**伺服器總管**/**資料庫總管**。  
  
 除了連接至 SQL Server 資料庫的遠端執行個體之外，您也可以直接連接至含有資料庫的實際檔案。 這可讓您將資料庫檔案直接加入至可將它們部署為應用程式一部分的專案。 目前支援下列本機資料庫檔案： SQL Server Compact 資料庫檔案 (.sdf)、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]和 SQL Server Express 資料庫檔案 (.mdf) 和 Microsoft Access 資料庫檔案 （.mdb 或.accdb）。  
  
#### <a name="to-create-a-data-connection-to-the-northwind-databasesql-server-database-file-mdf"></a>建立與 Northwind 資料庫的資料連接 (SQL Server 資料庫檔案 (.mdf))  
  
1.  在 **檢視**功能表上，選擇**伺服器總管**/**資料庫總管**。  
  
2.  在 **伺服器總管**/**資料庫總管**，開啟捷徑功能表**資料連接**，然後選擇 **加入連接**.  
  
     選擇之後**加入連接**，可以是**加入連接**對話方塊或**選擇資料來源**對話方塊會隨即出現。  
  
3.  如果**選擇資料來源** 對話方塊出現時，選取**Microsoft SQL Server 資料庫檔案**，然後選擇**確定**。  
  
4.  如果**加入連接** 對話方塊隨即出現，確認**資料來源**設定為**Microsoft SQL Server 資料庫檔案 (SqlClient)**。 如果未設定為**Microsoft SQL Server 資料庫檔案 (SqlClient)**，選擇**變更**以開啟**變更資料來源**對話方塊方塊中，選擇**Microsoft SQLServer 資料庫檔案**，然後選擇**確定**  按鈕。  
  
5.  選擇**瀏覽**找到含有 Northwind 資料庫的.mdf 檔案。  
  
6.  根據您的 Northwind 資料庫版本需求，選擇**使用 Windows 驗證**，或選擇**SQL Server 驗證**並輸入使用者名稱和密碼來登入執行 SQL Server 的電腦。  
  
7.  選擇 [確定]  按鈕。  
  
     資料連接到 Northwind 資料庫加入至**伺服器總管**/**資料庫總管**。  
  
> [!NOTE]
>  [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] 具有適用於 Northwind 資料庫檔案 (.mdf) 的變更。 如需資訊，請參閱[如何： 安裝範例資料庫](../data-tools/how-to-install-sample-databases.md)。  
  
#### <a name="to-create-a-data-connection-to-the-northwind-databaseaccess-database-file-mdb-or-accdb"></a>若要建立資料連接至 Northwind 資料庫 - Access 資料庫檔案 (.mdb 或 .accdb)  
  
1.  在 **檢視**功能表上，選擇**伺服器總管**/**資料庫總管**。  
  
2.  在 **伺服器總管**/**資料庫總管**，開啟捷徑功能表**資料連接**，然後選擇 **加入連接**.  
  
     選擇之後**加入連接**，可以是**加入連接**對話方塊或**選擇資料來源**對話方塊會隨即出現。  
  
3.  如果**選擇資料來源** 對話方塊出現時，選取**Microsoft Access 資料庫檔案**，然後選擇**確定**。  
  
4.  如果**加入連接** 對話方塊隨即出現，確認**資料來源**設定為**Microsoft Access 資料庫檔案**。 如果未設定為**Microsoft Access 資料庫檔案**，選擇**變更**以開啟**變更資料來源**對話方塊方塊中，選擇**Microsoft Access 資料庫檔案**，然後選擇**確定**  按鈕。  
  
5.  選擇**瀏覽**找到含有 Northwind 資料庫的.mdb 或.accdb 檔案。  
  
6.  如果您的 Northwind 資料庫版本需要使用者名稱和密碼，則請予以輸入。  
  
7.  選擇 [確定] 。  
  
     資料連接到 Northwind 資料庫加入至**伺服器總管**/**資料庫總管**。  
  
## <a name="see-also"></a>另請參閱  
 [如何： 安裝範例資料庫](../data-tools/how-to-install-sample-databases.md)   
 [Microsoft Access 2010 的資料程式設計](http://msdn.microsoft.com/library/office/ff965871.aspx)   
 [資料逐步解說](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)