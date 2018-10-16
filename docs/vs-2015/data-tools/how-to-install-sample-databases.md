---
title: 如何： 安裝範例資料庫 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
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
- sample databases, Adventure Works
- data [Visual Studio], sample databases
- sample databases, Northwind
- Northwind sample database
- Adventure Works sample database
ms.assetid: ed1291f6-604c-4972-ae22-0345c6dea12e
caps.latest.revision: 56
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: fd51bd397e6db3728c10f52db68d45e226fb605b
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49251028"
---
# <a name="how-to-install-sample-databases"></a>如何：安裝範例資料庫
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

許多資料範例都必須能夠連接到 Northwind、Pubs 和 AdventureWorks 範例資料庫。 您可以使用下列程序來安裝及連接至這些資料庫。  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="installing-databases"></a>安裝資料庫  
 許多資料範例都必須使用可從網站下載的範例資料庫。 這些範例資料庫包括 AdventureWorks、Northwind 和 Pubs 資料庫。  
  
#### <a name="to-install-the-northwind-and-pubs-sample-databases-for-sql-server"></a>若要安裝 SQL Server 適用的 Northwind 和 Pubs 範例資料庫  
  
1.  移至[Northwind 和 Pubs 範例資料庫](http://go.microsoft.com/fwlink?linkid=64296)網站。  
  
2.  下載並執行安裝程式。  
  
     安裝程式將資料夾加入**SQL Server 2000 Sample Databases**到您的電腦上的根資料夾。 (例如： **C:\SQL Server 2000 Sample Databases**)。  
  
3.  找出您要的資料庫 (Northwind 或 Pubs) 的 SQL 指令碼。  
  
    > [!WARNING]
    >  .MDF 資料庫檔案無法輕易地轉換成您在目前 SQL Server 版本中可以使用的格式，因此，最好是使用指令碼來建立資料庫。  
  
4.  在 **伺服器總管**，建立您想要用來安裝資料庫的 SQL Server 執行個體的連接。 如果您沒有想要使用的特定 SQL Server，您可以使用自動與 Visual Studio 一起安裝的資料庫。 若要這樣做，請指定`(localdb)\v11.0`作為伺服器名稱。  
  
     依照下列步驟來建立連接。  
  
    ###### <a name="to-create-a-connection-to-an-instance-of-sql-server"></a>若要建立與 SQL Server 執行個體的連接  
  
    1.  中**伺服器總管**，開啟捷徑功能表**資料連接**節點，然後選擇 **加入連接**。  
  
         **加入連接** 對話方塊隨即出現。  
  
    2.  輸入您要在其中建立 Northwind 或 Pubs 資料庫的 SQL Server 的名稱，或輸入 (localdb)\v11.0。  
  
    3.  底下**選取或輸入資料庫名稱**，從清單中，例如，tempdb 中選擇任何資料庫。  
  
    4.  選擇**測試連接**按鈕以確認一切正常，然後再選擇**確定** 按鈕。  
  
         新的連線節點會出現在**伺服器總管**。  
  
5.  在您的伺服器連接節點的捷徑功能表，然後選擇 [**新的查詢**] 按鈕。  
  
     編輯器視窗隨即開啟並顯示空的 .sql 指令碼檔。  
  
6.  將 instnwnd.sql 或 instpubs.sql 的內容貼到編輯器視窗中。  
  
7.  選擇 [執行查詢] 按鈕 (查詢視窗右上方的開啟綠色三角形圖示)。  
  
     如果查詢成功，訊息**命令已順利完成**隨即出現。 這表示已建立 Northwind 或 pubs 資料庫。  
  
     您還是需要新增連線至範例資料庫。 在 **伺服器總管**，開啟捷徑功能表**資料連接**節點，然後選擇 **加入連接**。  
  
8.  選擇在相同資料庫之前，但這次請選取在您選擇的伺服器，或輸入資料庫名稱，選擇 Northwind 或 pubs 資料庫，然後選擇**確定** 按鈕。  
  
     在 [資料連線] 下，會出現範例資料庫的新節點。  
  
9. 關閉編輯器視窗，並確認您不要儲存查詢檔案。 建立資料庫之後，並不需要儲存資料庫建立指令碼。  
  
#### <a name="to-install-the-adventureworks-sample-databases"></a>若要安裝 AdventureWorks 範例資料庫  
  
-   下載 AdventureWorks 範例資料庫，從[CodePlex 網站](http://go.microsoft.com/fwlink/?linkid=87843)。  
  
#### <a name="to-install-the-northwind-sample-database-for-microsoft-access"></a>若要安裝 Microsoft Access 適用的 Northwind 範例資料庫  
  
1.  在 Microsoft Access 2010 或更新版本中，Northwind，搜尋線上範本，然後選擇**Desktop Northwind 2007 範例資料庫**。  
  
2.  在 Microsoft Access 中，將資料庫檔案儲存為 Northwind.accdb。  
  
 新的 Access 資料庫副檔名為 .accdb。 請參閱[Microsoft Access 2010 的資料程式設計](http://msdn.microsoft.com/library/office/ff965871.aspx)。 若要使用的存取，以連接至 Northwind 資料庫，請參閱[如何： 連接到 Northwind 資料庫](../data-tools/how-to-connect-to-the-northwind-database.md)。  
  
## <a name="net-framework-security"></a>.NET Framework 安全性  
 範例資料庫是僅供說明使用，不一定會示範最佳安全性作法。  
  
## <a name="see-also"></a>另請參閱  
 [如何判斷 SQL Server 及其元件的版本](http://support.microsoft.com/kb/321185)   
 [使用設計工具建立 SQL database](../data-tools/create-a-sql-database-by-using-a-designer.md)   
 [如何：連接到 Northwind 資料庫](../data-tools/how-to-connect-to-the-northwind-database.md)