---
title: 存取 ClickOnce 應用程式中的本機和遠端資料 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, data
- data access, ClickOnce applications
ms.assetid: be5cbe12-6cb6-49c9-aa59-a1624e1eef3d
caps.latest.revision: 23
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 95f863a8b33f6cbff7e592b0a7a45e664494d826
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63427240"
---
# <a name="accessing-local-and-remote-data-in-clickonce-applications"></a>在 ClickOnce 應用程式中存取本機和遠端資料
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

大部分應用程式都會取用或產生資料。 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 提供您許多選項，以進行本機和遠端的資料讀取及寫入。  
  
## <a name="local-data"></a>本機資料  
 經由使用 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]，您可以利用下列任何一種方法在本機載入及儲存資料：  
  
- [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 資料目錄  
  
- 隔離儲存區  
  
- 其他本機檔案  
  
### <a name="clickonce-data-directory"></a>ClickOnce 資料目錄  
 在本機電腦安裝的每個 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 應用程式，都有資料目錄儲存在使用者的 [Documents and Settings] 資料夾中。 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 應用程式所含並標記為「資料」檔案的任何檔案，都會在安裝應用程式時複製到這個目錄。 資料檔案可以是任何檔案類型，最常使用的是文字、XML 和資料庫檔案 (例如 Microsoft Access.mdb 檔案)。  
  
 資料目錄的用途是要保存應用程式 Managed 資料，也就是應用程式所明確儲存和維護的資料。 應用程式資訊清單中所有不是標記為「資料」的靜態、非相依檔案都是位於應用程式目錄中， 這個目錄是應用程式的可執行檔 (.exe) 以及組件所在的位置。  
  
> [!NOTE]
> 在解除安裝 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 應用程式時，也會移除其資料目錄。 請絕對不要使用資料目錄來儲存由使用者所管理資料 (例如文件)。  
  
#### <a name="marking-data-files-in-a-clickonce-distribution"></a>標示 ClickOnce 散發中的資料檔案  
 若要將現有檔案置於資料目錄中，您必須在 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 應用程式的應用程式資訊清單檔中將此現有檔案標記為資料檔案。 如需詳細資訊，請參閱[如何：在 ClickOnce 應用程式中納入資料檔案](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md)。  
  
#### <a name="reading-from-and-writing-to-the-data-directory"></a>對資料目錄進行讀取和寫入  
 若要從資料目錄讀取，需具備 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 應用程式要求讀取權限；同樣地，寫入目錄則需要寫入權限。 如果設定以完全信任狀態執行，您的應用程式就會自動擁有這種權限。 如需有關為您的權限提升或受信任的應用程式部署的應用程式提升權限的詳細資訊，請參閱[保護 ClickOnce 應用程式](../deployment/securing-clickonce-applications.md)。  
  
> [!NOTE]
> 如果您的組織不使用受信任的應用程式部署，並關閉了權限提升，判斷提示權限就會失敗。  
  
 一旦您的應用程式具有這些權限之後，即可使用方法呼叫 <xref:System.IO>內部的類別以存取資料目錄。 您可以使用定義於 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 之 <xref:System.Deployment.Application.ApplicationDeployment.DataDirectory%2A> 屬性上的 <xref:System.Deployment.Application.ApplicationDeployment.CurrentDeployment%2A> 屬性，來取得 Windows Form <xref:System.Deployment.Application.ApplicationDeployment>應用程式內的資料目錄路徑。 這是最方便的存取資料方法，也是建議的方法。 下列程式碼範例將示範如何針對已做為資料檔加入部署中的 CSV.txt 文字檔執行這個動作。  
  
 [!code-csharp[ClickOnce.OpenDataFile#1](../snippets/csharp/VS_Snippets_Winforms/ClickOnce.OpenDataFile/CS/Form1.cs#1)]
 [!code-vb[ClickOnce.OpenDataFile#1](../snippets/visualbasic/VS_Snippets_Winforms/ClickOnce.OpenDataFile/VB/Form1.vb#1)]  
  
 如需有關如何標記您的部署與資料檔案中的檔案的詳細資訊，請參閱[How to:在 ClickOnce 應用程式中納入資料檔案](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md)。  
  
 您也可以使用 <xref:System.Windows.Forms.Application> 類別上的相關變數 (例如 <xref:System.Windows.Forms.Application.LocalUserAppDataPath%2A>)，來取得資料目錄路徑。  
  
 要管理其他檔案類型可能需要其他權限。 例如，如果要使用 Access 資料庫 (.mdb) 檔案，您的應用程式必須判斷提示完全信任，才能使用相關的 <xref:System.Data> 類別。  
  
#### <a name="data-directory-and-application-versions"></a>資料目錄和應用程式版本  
 應用程式的每個版本都有自己的資料目錄，並與其他版本隔離。 不論在部署中是否包含任何資料檔，[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 都會建立此目錄，以便讓應用程式在執行階段有位置建立新的資料檔。 在安裝應用程式的新版本時， [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 將會從上一版的資料目錄中，將所有的現有資料檔都複製到新版的資料目錄。不論這些資料包含在原始部署中，或是由應用程式建立都是如此。  
  
 如果資料檔在應用程式的舊版中，具有和新版不同的雜湊值，[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 就會以伺服器的新版取代檔案的較舊版本。 而且，如果舊版應用程式所建立的檔案，和新版部署所包含的檔案具有相同名稱， [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 就會以新的檔案覆寫舊版的檔案。 在這兩種情況下，舊檔都會包含在資料目錄內名為 `.pre`的子目錄中，如此應用程式就仍然能為移轉目的存取舊的資料。  
  
 如果您需要進行更精細的資料移轉，可以使用 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 部署 API 來執行自訂移轉，以便從舊的資料目錄移轉到新的資料目錄。 您必須使用 <xref:System.Deployment.Application.ApplicationDeployment.IsFirstRun%2A>來測試可用的下載程式、使用 <xref:System.Deployment.Application.ApplicationDeployment.Update%2A> 或 <xref:System.Deployment.Application.ApplicationDeployment.UpdateAsync%2A>下載更新，並在更新完成之後自己執行任何自訂的資料移轉工作。  
  
### <a name="isolated-storage"></a>隔離儲存區  
 隔離儲存區使用簡單的 API 以提供建立和存取檔案的 API。 儲存檔案的實際位置對開發人員和使用者都是隱藏的。  
  
 隔離儲存區適用於 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]的所有版本。 此外，隔離儲存區也適用於部分信任的應用程式，而不需要授與額外的權限。 如果應用程式必須以部分信任執行，並且必須維護應用程式特定資料，您就應該使用隔離儲存。  
  
 如需詳細資訊，請參閱 [隔離儲存區](http://msdn.microsoft.com/library/aff939d7-9e49-46f2-a8cd-938d3020e94e)。  
  
### <a name="other-local-files"></a>其他本機檔案  
 如果應用程式必須處理或儲存使用者資料 (例如報表、影像、音樂等等)，應用程式就需要 <xref:System.Security.Permissions.FileIOPermission> ，才能對本機檔案系統讀取和寫入資料。  
  
## <a name="remote-data"></a>遠端資料  
 有些時候，應用程式很可能必須從遠端網站擷取資訊，像是客戶資料或市場資訊。 本節會討論擷取遠端資料最常見的技巧。  
  
### <a name="accessing-files-by-using-http"></a>使用 HTTP 存取檔案  
 您可以使用 <xref:System.Net.WebClient> 命名空間中的 <xref:System.Net.HttpWebRequest> 或 <xref:System.Net> 類別，從 Web 伺服器存取資料。 資料可以是靜態檔案，或是傳回未經處理文字或 XML 資料的 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 應用程式。 如果您的資料是 XML 格式，擷取資料的最快方法，就是使用 <xref:System.Xml.XmlDocument> 類別，此類別的 <xref:System.Xml.XmlDocument.Load%2A> 方法採用 URL 做為引數。 如需範例，請參閱 [Reading an XML Document into the DOM](http://msdn.microsoft.com/library/a4fb291f-5630-49ba-a49a-5b66c3b71e49)。  
  
 如果應用程式會透過 HTTP 存取遠端資料，您就必須考慮安全性的問題。 根據預設，您當初部署應用程式的方式，可能會限制 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 應用程式對網路資源的存取。 套用這些限制主要是為了防止惡意程式存取有權限的遠端資料，或是利用使用者的電腦來攻擊網路上的其他電腦。  
  
 下表列出您可能使用的部署策略，以及這些策略的預設 Web 使用權限。  
  
|部署類型|預設網路權限|  
|---------------------|---------------------------------|  
|Web 安裝|只能存取做為應用程式安裝來源的 Web 伺服器|  
|檔案共用安裝|無法存取任何 Web 伺服器|  
|CD-ROM 安裝|可以存取任何 Web 伺服器|  
  
 如果 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 應用程式由於安全性限制而無法存取 Web 伺服器，此應用程式就必須為該網站判斷提示 <xref:System.Net.WebPermission> 。 如需增加安全性權限的詳細資訊[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]應用程式，請參閱 <<c2> [ 保護 ClickOnce 應用程式](../deployment/securing-clickonce-applications.md)。  
  
### <a name="accessing-data-through-an-xml-web-service"></a>透過 XML Web Service 存取資料  
 如果您將資料公開為 XML Web Service，就可以使用 XML Web Service Proxy 來存取資料， 此 Proxy 是使用 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 所建立的 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]類別。 XML Web Service 的作業 (例如擷取客戶、下訂單等等)，都會公開為 Proxy 上的方法。 這讓 Web 服務比未經處理的文字或 XML 檔案更加容易使用。  
  
 如果 XML Web Service 透過 HTTP 進行作業，此服務就會承受與 <xref:System.Net.WebClient> 和 <xref:System.Net.HttpWebRequest> 類別相同的安全性限制。  
  
### <a name="accessing-a-database-directly"></a>直接存取資料庫  
 您可以使用 <xref:System.Data> 命名空間內的類別，建立與資料庫伺服器 (例如網路上的 SQL Server) 的直接連線，不過您必須承擔安全性的問題。 不同於 HTTP 要求，資料庫連接要求根據預設會始終在部分信任下遭到禁止；根據預設，只有從 CD-ROM 安裝 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 應用程式，您才會擁有這種權限。 這會讓應用程式擁有完全信任權限。 若要啟用對於特定 SQL Server 資料庫的存取，您的應用程式必須對其要求 <xref:System.Data.SqlClient.SqlClientPermission> ；若要啟用對於非 SQL Server 資料庫的存取，則必須要求 <xref:System.Data.OleDb.OleDbPermission>。  
  
 大部分的情況下，您都不需要直接存取資料庫，而是會從以 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 撰寫的 Web 伺服器應用程式，或是 XML Web Service 來進行存取。 如果 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 應用程式是從 Web 伺服器進行部署，以這種方式存取資料庫通常是最佳的方式。 您可以使用部分信任來存取伺服器，而不需提升應用程式的權限。  
  
## <a name="see-also"></a>另請參閱  
 [如何：在 ClickOnce 應用程式中納入資料檔案](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md)
