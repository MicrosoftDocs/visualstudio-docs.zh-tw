---
title: "安全性、 版本控制和 ClickOnce 部署中的資訊清單問題 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- versioning, ClickOnce applications
- ClickOnce applications, Windows Vista User Account Control
- ClickOnce applications, versioning issues
- security, ClickOnce applications
- Windows 7, ClickOnce deployments
- ClickOnce applications, manifest issues
- User Account Control, ClickOnce applications
- Windows Vista, ClickOnce deployments
- manifests [ClickOnce]
- ClickOnce applications, security issues
ms.assetid: d5d0c90b-ac1a-44e2-88dc-0d0ffd881624
caps.latest.revision: "21"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: 603ff665e2c01abe62954e4e65e49a095d358b29
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="security-versioning-and-manifest-issues-in-clickonce-deployments"></a>ClickOnce 部署中的安全性、版本控制和資訊清單問題
有各種不同的問題[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]安全性、 應用程式版本和資訊清單的語法和語意，可能會導致[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]部署未順利完成。  
  
## <a name="clickonce-and-windows-vista-user-account-control"></a>ClickOnce 和 Windows Vista 使用者帳戶控制  
 在[!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)]，應用程式預設為執行標準的使用者，即使目前的使用者是否登入的帳戶具有管理員權限。 如果應用程式必須執行需要系統管理員權限的動作，它會告訴作業系統，則會提示使用者輸入其管理員認證。 這項功能稱為使用者帳戶控制 (UAC)，防止應用程式可能會影響整個作業系統中沒有使用者的明確核准的變更。 Windows 應用程式可讓您宣告它們藉由指定需要此權限提高`requestedExecutionLevel`屬性`trustInfo`其應用程式資訊清單的區段。  
  
 因為暴露安全性權限提高攻擊，應用程式的風險[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]應用程式不要求權限提高權限，如果用戶端已啟用 UAC。 任何[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]嘗試設定的應用程式及其`requestedExecutionLevel`屬性`requireAdministrator`或`highestAvailable`上未安裝[!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)]。  
  
 在某些情況下，您[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]應用程式可能會嘗試使用系統管理員權限執行因為安裝程式偵測邏輯[!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)]。 在此情況下，您可以設定`requestedExecutionLevel`中應用程式資訊清單屬性`asInvoker`。 這會導致執行應用程式本身不提高權限。 [!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)]自動將此屬性加入至所有應用程式資訊清單。  
  
 如果您正在開發的應用程式需要系統管理員權限的應用程式的整個存留期間，您應該考慮改為使用 Windows Installer (MSI) 技術來部署應用程式。 如需詳細資訊，請參閱[Windows 安裝程式的基本概念](../extensibility/internals/windows-installer-basics.md)。  
  
## <a name="online-application-quotas-and-partial-trust-applications"></a>線上應用程式配額和部分信任應用程式  
 如果您[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]應用程式會執行，而不是透過安裝線上，它必須符合為線上應用程式設定的配額。 此外，會在部分信任，這類的一組有限的安全性權限的網路應用程式不能大於配額大小的一半。  
  
 如需詳細資訊和有關如何變更線上應用程式配額的指示，請參閱[ClickOnce 快取概觀](../deployment/clickonce-cache-overview.md)。  
  
## <a name="versioning-issues"></a>版本控制的問題  
 如果您指派強式名稱組件，並遞增組件版本號碼，以反映應用程式更新，您可能遇到的問題。 任何以強式名稱組件的參考所編譯的組件必須自行重新編譯，或組件就會嘗試參考較舊的版本。 組件會嘗試這項因為組件在其繫結要求中使用舊版本的值。  
  
 例如，假設您有強式名稱組件 1.0.0.0 版其專屬專案中。 編譯組件之後, 您將它加入為包含主應用程式的專案參考。 如果您更新組件、 遞增的版本為 1.0.0.1，並嘗試部署而不會重新編譯應用程式，應用程式將無法載入執行階段組件。  
  
 只有當您正在編輯時，才會發生此錯誤您[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]資訊清單以手動方式; 您不應該發生此錯誤，如果您可以產生您的部署使用[!INCLUDE[vsprvslong](../code-quality/includes/vsprvslong_md.md)]。  
  
## <a name="specifying-individual-net-framework-assemblies-in-the-manifest"></a>指定個別的.NET Framework 組件資訊清單中  
 您的應用程式將無法載入，如果您已經手動編輯[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]參考較舊版本的部署[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]組件。 例如，如果您加入之版本的 System.Net 組件的參考[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]之前指定資訊清單中的版本，然後就會發生錯誤。 一般情況下，您不應嘗試指定個別的參考[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]組件的版本為[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]針對執行應用程式指定為應用程式資訊清單中的相依性。  
  
## <a name="manifest-parsing-issues"></a>資訊清單剖析問題  
 資訊清單檔案，可供[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]是 XML 檔案，而且必須是格式正確而且有效： 它們必須遵循 XML 語法規則，而且只會使用項目和相關的 XML 結構描述中定義的屬性。  
  
 資訊清單檔中可能會造成問題的項目選取包含特殊字元，例如單引號或雙引號引號的應用程式的名稱。 應用程式的名稱並屬於其[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]身分識別。 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]目前不會剖析包含特殊字元的身分識別。 如果您的應用程式無法啟動，請確定您的名稱，使用只有字母和數字字元，並嘗試再次部署它。  
  
 如果您已經手動編輯您的部署或應用程式資訊清單，您可能會不小心損壞它們。 資訊清單損毀將導致正確[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]安裝。 您可以按一下此類錯誤偵錯執行階段**詳細資料**上**ClickOnce 錯誤**對話方塊，並讀取記錄檔中的錯誤訊息。 記錄檔會列出下列訊息之一：  
  
-   語法錯誤的行號和字元的描述發生錯誤的位置。  
  
-   元素或屬性的資訊清單結構描述的違規情形中使用的名稱。 如果您有 XML 手動加入資訊清單，您必須比較您新增至資訊清單結構描述。 如需詳細資訊，請參閱[ClickOnce 部署資訊清單](../deployment/clickonce-deployment-manifest.md)和[ClickOnce 應用程式資訊清單](../deployment/clickonce-application-manifest.md)。  
  
-   ID 衝突。 部署和應用程式資訊清單中的相依性參考中必須是唯一同時其`name`和`publicKeyToken`屬性。 如果資訊清單中任何兩個項目之間的這兩個屬性相符，資訊清單剖析將不會成功。  
  
## <a name="precautions-when-manually-changing-manifests-or-applications"></a>預防措施以手動方式變更資訊清單或應用程式時  
 當您更新應用程式資訊清單時，您必須重新簽署應用程式資訊清單和部署資訊清單。 部署資訊清單包含應用程式資訊清單，其中包含該檔案的雜湊和數位簽章的參考。  
  
### <a name="precautions-with-deployment-provider-usage"></a>部署提供者使用的預防措施  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]部署資訊清單有`deploymentProvider`屬性指向位置的完整路徑應該安裝和服務應用程式：  
  
```  
<deploymentProvider codebase="http://myserver/myapp.application" />  
```  
  
 此路徑時，會設定[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]建立應用程式，且已安裝應用程式強制。 路徑會指向標準位置其中[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]installer 將安裝的應用程式和更新的搜尋。 如果您使用**xcopy**命令來複製[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]應用程式以不同的位置，但不要變更`deploymentProvider`屬性，[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]仍將參考回原始位置時，它會嘗試下載應用程式。  
  
 如果您想要移動或複製的應用程式，您也必須更新`deploymentProvider`路徑，以便在用戶端實際安裝從新位置。 如果您已安裝應用程式時，就更新此路徑是尤其重要。 針對線上應用程式，都會執行原始的 URL，設定透過`deploymentProvider`是選擇性的。 如果`deploymentProvider`已經設定，則會採用; 否則用來啟動應用程式的 URL 就會使用做為基底 URL 下載應用程式檔案。  
  
> [!NOTE]
>  您更新的資訊清單每次您必須再次加以簽署。  
  
## <a name="see-also"></a>另請參閱  
 [疑難排解 ClickOnce 部署](../deployment/troubleshooting-clickonce-deployments.md)   
 [保護 ClickOnce 應用程式](../deployment/securing-clickonce-applications.md)   
 [選擇 ClickOnce 部署策略](../deployment/choosing-a-clickonce-deployment-strategy.md)