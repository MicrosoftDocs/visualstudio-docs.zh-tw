---
title: '存取本機 & 遠端資料 (ClickOnce 應用程式) '
description: 瞭解 ClickOnce 提供的各種選項，可讓您在本機和遠端讀取和寫入資料。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, data
- data access, ClickOnce applications
ms.assetid: be5cbe12-6cb6-49c9-aa59-a1624e1eef3d
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: cbffa062e1115264f9496081cdcf63d17d2a36c7
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2021
ms.locfileid: "106217485"
---
# <a name="access-local-and-remote-data-in-clickonce-applications"></a>在 ClickOnce 應用程式中存取本機和遠端資料
大部分應用程式都會取用或產生資料。 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 提供您許多選項，以進行本機和遠端的資料讀取及寫入。

## <a name="local-data"></a>本機資料
 經由使用 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]，您可以利用下列任何一種方法在本機載入及儲存資料：

- [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 資料目錄

- 隔離儲存區

- 其他本機檔案

### <a name="clickonce-data-directory"></a>ClickOnce 資料目錄
 在本機電腦安裝的每個 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式，都有資料目錄儲存在使用者的 [Documents and Settings] 資料夾中。 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式所含並標記為「資料」檔案的任何檔案，都會在安裝應用程式時複製到這個目錄。 資料檔案可以是任何檔案類型，最常使用的是文字、XML 和資料庫檔案 (例如 Microsoft Access.mdb 檔案)。

 資料目錄的用途是要保存應用程式 Managed 資料，也就是應用程式所明確儲存和維護的資料。 應用程式資訊清單中所有不是標記為「資料」的靜態、非相依檔案都是位於應用程式目錄中， 這個目錄是應用程式可執行檔 (*.exe*) 以及組件所在的位置。

> [!NOTE]
> 在解除安裝 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式時，也會移除其資料目錄。 請絕對不要使用資料目錄來儲存由終端使用者所管理的資料 (例如文件)。

#### <a name="mark-data-files-in-a-clickonce-distribution"></a>標記 ClickOnce 散發中的資料檔案
 若要將現有檔案置於資料目錄中，您必須在 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式的應用程式資訊清單檔中將此現有檔案標記為資料檔案。 如需詳細資訊，請參閱 [How to: Include a data file in a ClickOnce application](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md) (如何：如何在 ClickOnce 應用程式中包含資料檔案)。

#### <a name="read-from-and-write-to-the-data-directory"></a>讀取和寫入資料目錄
 若要從資料目錄讀取，需具備 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式要求讀取權限；同樣地，寫入目錄則需要寫入權限。 如果設定以完全信任狀態執行，您的應用程式就會自動擁有這種權限。 如需使用許可權提升或受信任的應用程式部署來提升應用程式許可權的詳細資訊，請參閱 [安全的 ClickOnce 應用程式](../deployment/securing-clickonce-applications.md)。

> [!NOTE]
> 如果您的組織不使用受信任的應用程式部署，並關閉了權限提升，判斷提示權限就會失敗。

 一旦您的應用程式具有這些權限之後，即可使用方法呼叫 <xref:System.IO>內部的類別以存取資料目錄。 您可以使用定義於 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 之 <xref:System.Deployment.Application.ApplicationDeployment.DataDirectory%2A> 屬性上的 <xref:System.Deployment.Application.ApplicationDeployment.CurrentDeployment%2A> 屬性，來取得 Windows Form <xref:System.Deployment.Application.ApplicationDeployment>應用程式內的資料目錄路徑。 這是最方便的存取資料方法，也是建議的方法。 下列程式碼範例將示範如何針對已作為資料檔納入部署中的 *CSV.txt* 文字檔執行這個動作。

 :::code language="csharp" source="../snippets/csharp/VS_Snippets_Winforms/ClickOnce.OpenDataFile/CS/Form1.cs" id="Snippet1":::
 :::code language="vb" source="../snippets/visualbasic/VS_Snippets_Winforms/ClickOnce.OpenDataFile/VB/Form1.vb" id="Snippet1":::

 如需在您的部署中將檔案標示為資料檔案的詳細資訊，請參閱 [How to: Include a Data File in a ClickOnce Application](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md)。

 您也可以使用 <xref:System.Windows.Forms.Application> 類別上的相關變數 (例如 <xref:System.Windows.Forms.Application.LocalUserAppDataPath%2A>)，來取得資料目錄路徑。

 要管理其他檔案類型可能需要其他權限。 例如，如果您想要使用 Access 資料庫 (*.mdb*) 檔案，則您的應用程式必須判斷提示完全信任，才能使用相關的 \<xref:System.Data> 類別。

#### <a name="data-directory-and-application-versions"></a>資料目錄和應用程式版本
 應用程式的每個版本都有自己的資料目錄，並與其他版本隔離。 不論在部署中是否包含任何資料檔，[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 都會建立此目錄，以便讓應用程式在執行階段有位置建立新的資料檔。 在安裝應用程式的新版本時， [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 將會從上一版的資料目錄中，將所有的現有資料檔都複製到新版的資料目錄。不論這些資料包含在原始部署中，或是由應用程式建立都是如此。

 如果資料檔在應用程式的舊版中，具有和新版不同的雜湊值，[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 就會以伺服器的新版取代檔案的較舊版本。 而且，如果舊版應用程式所建立的檔案，和新版部署所包含的檔案具有相同名稱， [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 就會以新的檔案覆寫舊版的檔案。 在這兩種情況下，舊檔都會包含在資料目錄內名為 `.pre`的子目錄中，如此應用程式就仍然能為移轉目的存取舊的資料。

 如果您需要進行更精細的資料移轉，可以使用 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 部署 API 來執行自訂移轉，以便從舊的資料目錄移轉到新的資料目錄。 您必須使用 <xref:System.Deployment.Application.ApplicationDeployment.IsFirstRun%2A>來測試可用的下載程式、使用 <xref:System.Deployment.Application.ApplicationDeployment.Update%2A> 或 <xref:System.Deployment.Application.ApplicationDeployment.UpdateAsync%2A>下載更新，並在更新完成之後自己執行任何自訂的資料移轉工作。

### <a name="isolated-storage"></a>隔離儲存區 (Isolated Storage)
 隔離儲存區使用簡單的 API 以提供建立和存取檔案的 API。 儲存檔案的實際位置對開發人員和使用者都是隱藏的。

 隔離儲存區適用于所有版本的 .NET Framework。 此外，隔離儲存區也適用於部分信任的應用程式，而不需要授與額外的權限。 如果應用程式必須以部分信任執行，並且必須維護應用程式特定資料，您就應該使用隔離儲存。

 如需詳細資訊，請參閱 [隔離儲存區](/dotnet/standard/io/isolated-storage)。

### <a name="other-local-files"></a>其他本機檔案
 如果應用程式必須處理或儲存使用者資料 (例如報表、影像、音樂等等)，應用程式就需要 <xref:System.Security.Permissions.FileIOPermission> ，才能對本機檔案系統讀取和寫入資料。

## <a name="remote-data"></a>遠端資料
 有些時候，應用程式很可能必須從遠端網站擷取資訊，像是客戶資料或市場資訊。 本節會討論擷取遠端資料最常見的技巧。

### <a name="access-files-with-http"></a>使用 HTTP 存取檔案
 您可以使用 <xref:System.Net.WebClient> 命名空間中的 <xref:System.Net.HttpWebRequest> 或 <xref:System.Net> 類別，從 Web 伺服器存取資料。 資料可以是靜態檔案，或是傳回未經處理文字或 XML 資料的 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 應用程式。 如果您的資料是 XML 格式，擷取資料的最快方法，就是使用 <xref:System.Xml.XmlDocument> 類別，此類別的 <xref:System.Xml.XmlDocument.Load%2A> 方法採用 URL 做為引數。 如需範例，請參閱 [將 XML 檔讀入 DOM](/dotnet/standard/data/xml/reading-an-xml-document-into-the-dom)。

 如果應用程式會透過 HTTP 存取遠端資料，您就必須考慮安全性的問題。 根據預設，您當初部署應用程式的方式，可能會限制 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式對網路資源的存取。 套用這些限制主要是為了防止惡意程式存取有權限的遠端資料，或是利用使用者的電腦來攻擊網路上的其他電腦。

 下表列出您可能使用的部署策略，以及這些策略的預設 Web 使用權限。

|部署類型|預設網路權限|
|---------------------|---------------------------------|
|Web 安裝|只能存取做為應用程式安裝來源的 Web 伺服器|
|檔案共用安裝|無法存取任何 Web 伺服器|
|CD-ROM 安裝|可以存取任何 Web 伺服器|

 如果 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式由於安全性限制而無法存取 Web 伺服器，此應用程式就必須為該網站判斷提示 <xref:System.Net.WebPermission> 。 如需為應用程式增加安全性許可權的詳細資訊 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] ，請參閱 [安全的 ClickOnce 應用程式](../deployment/securing-clickonce-applications.md)。

### <a name="access-data-through-an-xml-web-service"></a>透過 XML Web Service 存取資料
 如果您將資料公開為 XML Web Service，就可以使用 XML Web Service Proxy 來存取資料， Proxy 是您使用其中一種方式建立的 .NET Framework 類別 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 。 XML Web Service 的作業 (例如擷取客戶、下訂單等等)，都會公開為 Proxy 上的方法。 這讓 Web 服務比未經處理的文字或 XML 檔案更加容易使用。

 如果 XML Web Service 透過 HTTP 進行作業，此服務就會承受與 <xref:System.Net.WebClient> 和 <xref:System.Net.HttpWebRequest> 類別相同的安全性限制。

### <a name="access-a-database-directly"></a>直接存取資料庫
 您可以使用 <xref:System.Data> 命名空間內的類別，建立與資料庫伺服器 (例如網路上的 SQL Server) 的直接連線，不過您必須承擔安全性的問題。 不同於 HTTP 要求，資料庫連接要求根據預設會始終在部分信任下遭到禁止；根據預設，只有從 CD-ROM 安裝 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式，您才會擁有這種權限。 這會讓應用程式擁有完全信任權限。 若要啟用對於特定 SQL Server 資料庫的存取，您的應用程式必須對其要求 <xref:System.Data.SqlClient.SqlClientPermission> ；若要啟用對於非 SQL Server 資料庫的存取，則必須要求 <xref:System.Data.OleDb.OleDbPermission>。

 大部分的情況下，您都不需要直接存取資料庫，而是會從以 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 撰寫的 Web 伺服器應用程式，或是 XML Web Service 來進行存取。 如果 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式是從 Web 伺服器進行部署，以這種方式存取資料庫通常是最佳的方式。 您可以使用部分信任來存取伺服器，而不需提升應用程式的權限。

## <a name="see-also"></a>另請參閱

- [如何：在 ClickOnce 應用程式中包含資料檔案](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md)