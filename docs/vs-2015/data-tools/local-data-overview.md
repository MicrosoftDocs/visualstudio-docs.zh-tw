---
title: 本機資料概觀 |Microsoft Docs
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
- SQL Server Express
- local data
- SQL Server LocalDB
- LocalDB
- SQLEXPRESS
- SQL Server, local data
- SQL Express
- SQL Server Compact
- data access [Visual Studio], troubleshooting
- Access, .mdb files in Visual Studio
- data [Visual Studio], local
ms.assetid: d6afa5ac-2bb8-49f2-a50e-f71f611ed506
caps.latest.revision: 71
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 312dbee46f13bf1f8f5d0666dcba18adc1116cdf
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49210479"
---
# <a name="local-data-overview"></a>區域資料概觀
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

在開發資料應用程式時，它通常最好是使用本機資料庫的複本，以便不會產生錯誤到實際執行資料。 如果兩位開發人員引進硬偵測的方式互動的錯誤，甚至與其他開發人員共用測試資料庫就會建立潛在的問題。 您可以在本機電腦上使用您自己的測試資料，以避免所有這些陷阱。 大部分不是所有的資料庫系統可讓您建立的本機資料檔。 .NET 專案，Visual Studio，請為本機的 SQL Server 資料庫檔案 (.mdf) 和 Microsoft Access 資料庫檔案 (.mdb) 提供特殊支援。  
  
 Visual Studio 支援這些案例：  
  
1.  
  
2.  
  
-  
  
-  
  
-   建立 SQL Server 資料庫專案，按一下 [方案總管] 中的方案節點，然後選擇**新增&#124;新的專案**。  在左窗格中，選擇**SQL Server&#124;資料庫**專案，然後按一下 [確定]。 在 [方案總管] 中，匯入本機資料庫檔案，在資料庫專案節點上按一下滑鼠右鍵，然後開發連接到資料庫專案所產生的應用程式。 當您開發和修改資料庫結構描述在相同的時間，您正在開發應用程式的良好。  
  
     ![資料庫匯入資料庫專案](../data-tools/media/raddata-import-database-into-database-project.png "raddata 匯入資料庫到資料庫專案")  
  
-   如果您要建立新的資料庫，先將**服務架構資料庫檔案**至您的專案 (**專案&#124;加入新項目)**。 這會建立新的.mdf 檔案附加至預設 SQL Server 執行個體，其預設值是 (localdb) \MSSQLocalDB 在本機電腦上。 資料庫應該會出現在 [伺服器總管] 中。 展開節點，並以滑鼠右鍵按一下要新增新的資料庫物件，例如資料表、 檢視、 函數和等等的節點。  
  
 如需有關 SQL Server Express LocalDB 的詳細資訊，請參閱 < [LocalDB 簡介-、 增強的 SQL Express](http://go.microsoft.com/fwlink/?LinkId=234375)並[LocalDB： 其中是我的資料庫？](http://go.microsoft.com/fwlink/?LinkId=234376) Microsoft 網站上。  
  
 下表將提供說明如何將應用程式連接至本機資料的主題連結：  
  
|主題|描述|  
|-----------|-----------------|  
|[使用設計工具建立 SQL 資料庫](../data-tools/create-a-sql-database-by-using-a-designer.md)|提供逐步指示，說明如何建置可用來測試資料功能和建立應用程式的本機資料庫檔案。|  
|[逐步解說：連接至本機資料庫檔案中的資料 (Windows Forms)](../data-tools/walkthrough-connecting-to-data-in-a-local-database-file-windows-forms.md)|針對如何在建立簡單 Windows 應用程式時連接至 SQL Server Express LocalDB 資料庫，提供逐步指示。|  
|[連接至 Access 資料庫中的資料 (Windows Forms)](../data-tools/connect-to-data-in-an-access-database-windows-forms.md)|提供如何連接至 Microsoft Access 資料庫的逐步指示。|  
|[如何：連接到 Northwind 資料庫](../data-tools/how-to-connect-to-the-northwind-database.md)|提供如何連接到 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]、SQL Server Compact、SQL Server Express 和 Access 中的 Northwind 範例資料庫的指示。|  
  
## <a name="use-the-connection-string"></a>使用連接字串  
 這是最簡單的方法，而且當您的應用程式只會從資料庫讀取，並使用協力廠商資料庫時，是不錯的選擇。 資料庫檔案可以是任何位置，您的應用程式具有的存取權限和資料庫系統支援在本機電腦上。  
  
1.  （選擇性）建立新的連接中所述[新增連線](../data-tools/add-new-connections.md)。 協力廠商資料庫和.mdf 檔案，您已經知道連接字串和將不會進行資料繫結或使用資料來源，例如 Entity Framework 類別或資料集，不需要進行此步驟。 只要使用的連接字串連接到本機檔案。 .Mdf 檔案，請參閱 <<c0> [ 升級的.mdf 檔案](../data-tools/upgrade-dot-mdf-files.md)並[建立連線](https://msdn.microsoft.com/en-us/library/ms254507.aspx)。  
  
2.  （選擇性）如果您使用資料集，Entity Framework 或 LINQ to SQL，然後使用資料來源組態精靈 建立資料來源。 如需詳細資訊，請參閱[新增資料來源](../data-tools/add-new-data-sources.md)。  
  
## <a name="add-an-existing-mdf-to-your-project"></a>將現有的.mdf 新增至您的專案  
 如果您的應用程式將會插入、 刪除或更新資料，而且您想要保留一份原始的檔案，請考慮將檔案新增至您的專案。 只要這麼做時，您還可以設定項目屬性，以**複製到輸出目錄**要**永遠複製**或**才複製**，及開發應用程式。 每次建置應用程式時，原始的資料庫複製到輸出資料夾，並在複本上執行您的應用程式變更。 這樣一來，您永遠有全新的原始資料。  
  
1.  使用**Windows 檔案總管**拖放的.mdf 檔案從 Visual Studio 中的 [方案總管] 中的專案節點上目前的位置。  如果檔案已經附加到 localDB 執行個體，您必須先中斷其連結。 拖放到專案之後，Visual Studio 會自動重新附加它的預設 localDB 執行個體。  
  
2.  以滑鼠右鍵按一下 新的 資料庫 節點，然後選擇屬性。 選取複製行為，即**永遠複製**或是**才複製**。  
  
## <a name="create-a-sql-server-database-project-and-import-your-database"></a>建立 SQL Server 資料庫專案並匯入您的資料庫  
 當您將開發資料庫本身，或許是加入資料行或資料表，或變更資料類型時，這會是個不錯的選項。  
  
## <a name="each-project-contains-two-copies-of-the-database"></a>每個專案都包含兩個資料庫複本  
 當您建置專案時，可能資料庫檔案從根專案資料夾複製到輸出中， **bin**，資料夾。 這個行為取決於**複製到輸出目錄**屬性的檔案，以及該屬性的預設值取決於您使用的資料庫檔案的類型。  
  
 若要檢視**bin**資料夾中的**方案總管**，選擇**顯示所有檔案**工具列上的按鈕。  
  
> [!NOTE]
>  **複製到輸出目錄**屬性不會套用至 web 或 c + + 專案。  
  
 只有在您藉由編輯資料庫結構描述或資料時，才變更專案根資料夾中的資料庫檔案**伺服器總管**/**資料庫總管**或其他[視覺化資料庫工具](http://msdn.microsoft.com/en-us/6b145922-2f00-47db-befc-bf351b4809a1)。  
  
 當您變更應用程式開發期間的資料，您要變更的資料庫中**bin**資料夾。 例如，當您選擇 F5 鍵偵錯應用程式時，便會連接至該資料夾中的資料庫。  
  
|值**複製到輸出目錄**屬性|行為|  
|----------------------------------------------------|--------------|  
|**有更新時才複製**（預設值為.sdf 檔案）|資料庫檔案從專案目錄複製到**bin**第一次建置專案的目錄。 **修改日期**檔案的屬性接著會比較每次您重新建置專案。 如果專案資料夾中的檔案新時，它會複製到**bin**資料夾中，取代先前的檔案。 否則不會複製任何檔案。 **注意：** 我們不建議此值使用於.mdb 或.mdf 檔案。 即使資料沒有變更，資料庫檔案也可能會變更。 檔案可以標記為較新如果您只是開啟連接 (例如，依序展開**資料表**中的節點**伺服器總管**)。|  
|**永遠複製**（預設值為.mdf 和.mdb 檔案）|資料庫檔案從專案目錄複製到**bin**每次建置您的應用程式的目錄。 對輸出資料夾中的資料檔案所做的任何變更，都會在下次執行應用程式時加以覆寫。|  
|**不要複製**|系統絕不會覆寫中的檔案**bin**目錄。 您的應用程式會建立一個動態連接字串，以指向輸出目錄中的資料庫檔案。 因此，如果您要讓輸出目錄中的資料符合專案目錄中的資料，就必須手動將檔案複製到輸出目錄。|  
  
## <a name="common-issues-with-local-data"></a>本機資料的常見問題  
 下表說明您在使用本機資料檔案時可能會遇到的常見問題。  
  
|問題|說明|  
|-----------|-----------------|  
|每次當我測試應用程式並修改資料後，這些變更在下次執行應用程式時就會消失|值**複製到輸出目錄**屬性是**才複製**或是**永遠複製**。 在您每次建置專案時，都會覆寫輸出資料夾中的資料庫 (測試應用程式時所修改的資料庫)。 如需詳細資訊，請參閱 <<c0> [ 如何： 在您的專案中的管理本機資料檔](../data-tools/how-to-manage-local-data-files-in-your-project.md)。|  
|出現一則訊息，表示資料檔已鎖定。|Access (.mdb 檔)：確定檔案沒有在其他應用程式中開啟，例如 Access。<br /><br /> SQL Server Express (.mdf 檔)：如果您嘗試在 Visual Studio IDE 外部複製、移動或重新命名資料檔，SQL Express 就會將它鎖定。|  
|當一位以上的使用者同時嘗試存取同一個資料庫時，存取遭拒。|Visual Studio 會利用*使用者執行個體*，這是一項功能的 SQL Server Express，建立每一位使用者不同的 SQL Server 執行個體。 在某位使用者存取檔案之後，任何後續的使用者皆無法連接。 例如，如果您嘗試同時在 ASP.NET 程式開發伺服器和 Internet Information Services (IIS) 中執行 Web 應用程式，就可能會發生這個問題，因為 IIS 通常是在不同的帳戶下執行。|  
  
## <a name="see-also"></a>另請參閱  
 [逐步解說： 連接至本機資料庫檔案 (Windows Form) 中的資料](../data-tools/walkthrough-connecting-to-data-in-a-local-database-file-windows-forms.md)   
 [連接至 Access 資料庫中的資料 (Windows Forms)](../data-tools/connect-to-data-in-an-access-database-windows-forms.md)