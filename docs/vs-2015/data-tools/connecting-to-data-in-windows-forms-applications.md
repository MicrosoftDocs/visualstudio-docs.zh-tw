---
title: 連接資料的 Windows Forms 應用程式 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- System.Data.SqlClient.SqlConnection
- System.Data.Odbc.OdbcConnection
- System.Data.OleDb.OleDbConnection
- System.Data.OracleClient.OracleConnection
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- connection objects, tools for working with
- OleDbConnection class, ADO.NET connection objects
- databases [Visual Studio], connecting to
- data adapters, connections
- connection pooling, ADO.NET connections
- connection strings [Visual Studio], ADO.NET
- connection objects, types of
- dynamic properties, ADO.NET connections
- connections, about connections
- data [Visual Studio], connecting
- design-time connections
- connections, design-time
- TableAdapters, connections
- connection objects
- SqlConnection class, ADO.NET connection objects
- connecting to databases, ADO.NET connections
- transactions, ADO.NET
- database connections [Visual Studio], ADO.NET
ms.assetid: 184cbd0d-3b26-418d-a11c-f9f8f004fbff
caps.latest.revision: 31
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: d1132ee07e892886e49fbaa4670b309afc448da6
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47498733"
---
# <a name="connecting-to-data-in-windows-forms-applications"></a>連接至 Windows Forms 應用程式中的資料
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 提供您工具，讓您將應用程式連接至不同來源 (例如資料庫、Web 服務及物件) 的資料。 若您使用 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 中的資料設計工具，則通常不需要明確地為表單或元件建立連接物件。 連接物件的建立通常是完成其中一個資料精靈，或是將資料物件拖曳至表單中所產生的結果。 若要連接您的應用程式資料庫、 web 服務或物件中的資料，請執行[資料來源組態精靈](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f)藉由選取**加入新的資料來源**從[資料來源視窗](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992).  
  
 下圖示範透過執行 TableAdapter 查詢連接至資料，以擷取資料，並將資料顯示在 Windows 應用程式中的表單時的標準作業流程。  
  
 ![用戶端應用程式中的資料流程](../data-tools/media/clientdatadiagram.gif "ClientDataDiagram")  
  
 在某些情況中，不經由任何資料設計工具的協助而建立連接物件是很方便的。 如需以程式設計方式建立的連線資訊，請參閱[連接到資料來源](http://msdn.microsoft.com/library/9abc3f92-1be3-4e1a-b360-762dc689650e)。  
  
> [!NOTE]
>  如需連接至資料的 web 應用程式的資訊，請參閱[ASP.NET 資料存取內容對應](http://msdn.microsoft.com/en-us/f9219396-a0fa-481f-894d-e3d9c67d64f2)。  
  
## <a name="walkthroughs-for-connecting-windows-forms-applications-to-data"></a>將 Windows Forms 應用程式連接至資料的逐步解說  
 下列逐步解說提供連接至 Windows Forms 應用程式中資料的相關程序：  
  
-   [逐步解說： 連接至資料庫 (Windows Form) 中的資料](http://msdn.microsoft.com/library/02d39aa6-8993-4602-be13-a13536af3d1c)  
  
-   [逐步解說：連接至本機資料庫檔案中的資料 (Windows Forms)](../data-tools/walkthrough-connecting-to-data-in-a-local-database-file-windows-forms.md)  
  
-   [逐步解說： 連接至 Web 服務 (Windows Form) 中的資料](http://msdn.microsoft.com/library/079fb9b0-c733-40c1-acd1-d0d68834354d)  
  
-   [逐步解說： 連接至資料物件 (Windows Form)](http://msdn.microsoft.com/library/21a7fba2-b38b-4726-8cbe-d22154b75a05)  
  
-   [連接至 Access 資料庫中的資料 (Windows Forms)](../data-tools/connect-to-data-in-an-access-database-windows-forms.md)  
  
## <a name="creating-connections"></a>建立連接  
 在  [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]，連線會設定為使用**加入/修改連接**對話方塊。 **加入連接** 對話方塊隨即出現，當您編輯或建立連接的其中一個資料精靈或[伺服器總管/資料庫總管](http://msdn.microsoft.com/library/4ea29b3b-bbb2-45e4-9082-eaf635c41c4d)或當您正在編輯中的連接屬性**屬性**視窗。  
  
 當您執行下列其中一個動作時，會自動設定資料連線。  
  
|動作|描述|  
|------------|-----------------|  
|執行[資料來源組態精靈](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f)。|在選擇的資料庫路徑時，已設定連線**資料來源組態精靈**。 如需詳細資訊，請參閱 <<c0> [ 如何： 連接到資料庫中的資料](../data-tools/how-to-connect-to-data-in-a-database.md)。|  
|執行[TableAdapter 組態精靈](http://msdn.microsoft.com/library/3a373dd9-7b34-4d3c-a48b-69414512bac8)。|中建立連接**TableAdapter 組態精靈**。 如需詳細資訊，請參閱 <<c0> [ 建立和設定 Tableadapter](../data-tools/create-and-configure-tableadapters.md)。|  
|執行[編輯 TableAdapters](../data-tools/editing-tableadapters.md)。|中建立連接**TableAdapter 查詢組態精靈**。 如需詳細資訊，請參閱 <<c0> [ 如何： 建立 TableAdapter 查詢](../data-tools/how-to-create-tableadapter-queries.md)。|  
|將項目從[資料來源 視窗](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)拖曳至表單或[Component Designer](http://msdn.microsoft.com/library/61a3a450-5b15-465e-bd9a-72a6c8c2b282)。|當您拖曳項目時，會建立連接物件**資料來源**視窗拖曳至**Windows Form 設計工具**或是**Component Designer**。 如需詳細資訊，請參閱 <<c0> [ 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-controls-to-data-in-visual-studio.md)。|  
|若要新增的資料連接[伺服器總管/資料庫總管](http://msdn.microsoft.com/library/4ea29b3b-bbb2-45e4-9082-eaf635c41c4d)。|中的資料連接**伺服器總管/資料庫總管**會出現在資料精靈中的可用連接清單|  
  
## <a name="connection-strings"></a>連接字串  
 連接字串可以儲存在編譯過的應用程式中，或是儲存在應用程式組態檔中。 如需詳細資訊，請參閱 <<c0> [ 如何： 儲存並編輯連接字串](~/E:/Repos/visualstudio-docs-pr/docs/data-tools/how-to-save-and-edit-connection-strings.md)。  
  
## <a name="connection-information-and-security"></a>連接資訊及安全性  
 由於開啟連接涉及取得重要資源，也就是資料庫的存取權，因此設定及使用連接通常會牽扯到安全性問題。  
  
 您要如何根據您的系統架構，保護應用程式以及其對資料來源的存取。 例如，在 Web 應用程式中，使用者一般會獲得對網際網路資訊服務 (IIS) 的匿名存取權，而因此沒有提供安全性認證。 在該情況中，應用程式會維護並使用其自己的登入資訊 (而不是任何特定使用者的資訊)，來開啟連接並存取資料庫。  
  
> [!IMPORTANT]
>  儲存密碼之類的連接字串詳細資料，會影響應用程式的安全性。 使用 Windows 整合式安全性是控制資料庫存取的更安全方式。 如需詳細資訊，請參閱[保護連線資訊](http://msdn.microsoft.com/library/1471f580-bcd4-4046-bdaf-d2541ecda2f4)。  
  
 您可以在內部網路或多介層應用程式中，利用 Windows、IIS 及 SQL Server 提供的整合式安全性選項。 在該模型中，也會運用使用者的區域網路驗證認證存取資料庫資源，且不會在連接字串中使用明確的使用者名稱或密碼。 一般而言，是透過群組將權限建立在資料庫伺服器電腦上，因此您不需要為每個可能存取資料庫的使用者建立個別權限。 在此模型中，您完全不需要為連接儲存登入資訊，也不需要為保護連接字串資訊採取任何其他步驟。  
  
 如需安全性的詳細資訊，請參閱下列主題：  
  
-   [設定 ADO.NET 應用程式的安全性](http://msdn.microsoft.com/library/005a1d43-6ee5-471e-ad98-1d30a44d49d5)  
  
-   [Windows Forms 中更安全的檔案和資料存取](http://msdn.microsoft.com/library/3cd3e55b-2f5e-40dd-835d-f50f7ce08967)  
  
## <a name="design-time-connections-in-server-explorerdatabase-explorer"></a>伺服器總管/資料庫總管中的設計階段連接  
 **伺服器總管/資料庫總管**可讓您能夠建立設計階段連接到資料來源。 這可以讓您瀏覽可使用的資料來源，以及顯示資料來源所包含的資料表、資料行及其他項目的相關資訊，還可以編輯及建立資料庫項目。  
  
 您的應用程式不會直接使用中的可用連接**伺服器總管/資料庫總管**。 這些連接是由 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 在設計階段使用您資料庫時使用。 如需詳細資訊，請參閱 < [Visual Database Tools](http://msdn.microsoft.com/en-us/6b145922-2f00-47db-befc-bf351b4809a1)。  
  
 例如，在設計階段您可能會使用**伺服器總管/資料庫總管**來建立資料庫的連接。 更新版本中，設計表單時，您可以瀏覽資料庫、 資料行從資料表選取，並將其拖曳至[Dataset 設計工具](../data-tools/creating-and-editing-typed-datasets.md)。 這會建立[TableAdapter](../data-tools/tableadapter-overview.md)在您的資料集。 而這也會建立新的連接物件，且此連接物件會包含在最新建立的 TableAdapter 中。  
  
 關於設計階段連接的資訊，會在特定專案或方案之外，分別儲存在您本機電腦中。 因此，一旦您已建立設計階段連接的應用程式中工作時，它會出現在**伺服器總管/資料庫總管**每當您使用[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]，只要伺服器連接使用點。 如需詳細資訊，請參閱 <<c0> [ 如何： 從伺服器總管連接到資料庫](http://msdn.microsoft.com/en-us/7c1c3067-0d77-471b-872b-639f9f50db74)。  
  
 [!INCLUDE[SQLObjectExplorer](../includes/sqlobjectexplorer-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [連接到 Visual Studio 中的資料](../data-tools/connecting-to-data-in-visual-studio.md)   
 [如何：連接至資料庫中的資料](../data-tools/how-to-connect-to-data-in-a-database.md)   
 [逐步解說： 連接至資料庫 (Windows Form) 中的資料](http://msdn.microsoft.com/library/02d39aa6-8993-4602-be13-a13536af3d1c)   
 [ASP.NET 資料存取內容對應](http://msdn.microsoft.com/en-us/f9219396-a0fa-481f-894d-e3d9c67d64f2)   
 [準備您的應用程式接收資料](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [將資料擷取至您的應用程式](../data-tools/fetching-data-into-your-application.md)   
 [將控制項繫結至 Visual Studio 中的資料](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [在您的應用程式中編輯資料](../data-tools/editing-data-in-your-application.md)   
 [驗證資料](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [儲存資料](../data-tools/saving-data.md)