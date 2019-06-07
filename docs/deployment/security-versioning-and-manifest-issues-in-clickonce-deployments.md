---
title: 在 ClickOnce 部署資訊清單的安全性/版本設定問題
ms.date: 11/04/2016
ms.topic: conceptual
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bb2ec5229132265feb1095c9ee921d73a1568dd2
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2019
ms.locfileid: "66745598"
---
# <a name="security-versioning-and-manifest-issues-in-clickonce-deployments"></a>ClickOnce 部署中的安全性、版本控制和資訊清單問題

有各種不同的問題[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]安全性、 應用程式版本和資訊清單的語法和語意，可能會導致[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]部署不成功。

## <a name="clickonce-and-windows-vista-user-account-control"></a>ClickOnce 和 Windows Vista 使用者帳戶控制

在  [!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)]，預設的應用程式會執行以標準使用者身分，即使目前的使用者是否登入的帳戶具有管理員權限。 如果應用程式必須執行的動作需要系統管理員權限，它會告訴作業系統，則會提示使用者輸入其系統管理員認證。 這項功能稱為使用者帳戶控制 (UAC)，防止應用程式可能會影響整個作業系統不需要使用者的明確核准的變更。 Windows 應用程式可讓您宣告它們藉由指定需要此權限提高`requestedExecutionLevel`屬性中`trustInfo`其應用程式資訊清單區段。

因為公開安全性權限提高攻擊，應用程式的風險[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]如果 UAC 已啟用用戶端應用程式無法要求權限提高權限。 任何[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]嘗試設定的應用程式及其`requestedExecutionLevel`屬性設定為`requireAdministrator`或`highestAvailable`不會安裝[!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)]。

在某些情況下，您[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]應用程式可能會嘗試使用系統管理員權限執行由於安裝程式偵測邏輯[!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)]。 在此情況下，您可以設定`requestedExecutionLevel`屬性中的應用程式資訊清單，以`asInvoker`。 這會導致應用程式本身不提高權限執行。 [!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)] 自動將所有的應用程式資訊清單的這個屬性。

如果您正在開發的應用程式需要系統管理員權限的應用程式的整個存留期間，您應該考慮改為使用 Windows Installer (MSI) 技術部署應用程式。 如需詳細資訊，請參閱 < [Windows Installer 基本概念](../extensibility/internals/windows-installer-basics.md)。

## <a name="online-application-quotas-and-partial-trust-applications"></a>線上應用程式的配額和部分信任應用程式

如果您[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]應用程式執行而不是透過安裝線上時，它必須符合針對線上應用程式擱置在一旁的配額。 此外，網路應用程式，會在部分信任，這類的一組有限的安全性權限，不能大於配額大小的一半。

如需詳細資訊，以及有關如何變更線上應用程式配額的指示，請參閱[ClickOnce 快取概觀](../deployment/clickonce-cache-overview.md)。

## <a name="versioning-issues"></a>版本控制問題

如果您將強式名稱指派給您的組件，並遞增組件版本號碼，以反映應用程式更新，您可能會遇到的問題。 任何以強式名稱組件的參考編譯的組件必須本身重新編譯，或組件就會嘗試參考較舊的版本。 組件會嘗試這項因為組件在其繫結要求中使用舊的版本值。

例如，假設您有強式名稱組件 1.0.0.0 版具有其專屬專案中。 編譯組件之後, 您將它新增為包含您主要的應用程式專案的參考。 如果您更新組件、 遞增的版本為 1.0.0.1，並嘗試將它部署不需要也重新編譯應用程式，應用程式將無法載入組件在執行階段。

只有當您在編輯時，才會發生此錯誤您[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]資訊清單以手動的方式; 如果您產生您使用 Visual Studio 的部署，您應不至於遇到這個錯誤。

## <a name="specify-individual-net-framework-assemblies-in-the-manifest"></a>指定個別的.NET Framework 組件資訊清單中

您的應用程式將無法載入，如果您已經手動編輯[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]參考較舊版本的.NET Framework 組件的部署。 比方說，如果您加入資訊清單中指定的版本之前的.NET framework 版本的 System.Net 組件的參考，則會發生錯誤。 一般情況下，您應該嘗試指定個別的.NET Framework 組件的參考，針對您的應用程式執行的.NET framework 的版本指定為應用程式資訊清單中的相依性。

## <a name="manifest-parsing-issues"></a>資訊清單剖析問題

資訊清單檔案，可供[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]是 XML 檔案，而且必須是格式正確而且有效： 它們必須遵循 XML 語法規則，而且只會使用項目和相關的 XML 結構描述中定義的屬性。

資訊清單檔中可能會造成問題的項目就選取您的應用程式包含特殊字元，例如單引號或雙引號括標記的名稱。 應用程式的名稱並屬於其[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]身分識別。 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 目前不會剖析包含特殊字元的身分識別。 如果您的應用程式無法啟動，請確定您使用只有字母和數字字元做為名稱，並嘗試再次部署。

如果您已經手動編輯您的部署或應用程式資訊清單，您可能會不小心損壞了。 損毀的資訊清單可防止正確[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]安裝。 您可以按一下這類錯誤偵錯執行階段**詳細資料**上**ClickOnce 錯誤** 對話方塊中，以及讀取記錄檔中的錯誤訊息。 記錄檔會列出下列訊息之一：

- 語法錯誤的行號和字元的描述發生錯誤的位置。

- 項目或屬性中的資訊清單結構描述的違規所使用的名稱。 如果您已手動新增 XML，以您的資訊清單，您必須比較您新增至資訊清單的結構描述。 如需詳細資訊，請參閱 < [ClickOnce 部署資訊清單](../deployment/clickonce-deployment-manifest.md)並[ClickOnce 應用程式資訊清單](../deployment/clickonce-application-manifest.md)。

- ID 衝突。 部署和應用程式資訊清單中的相依性參考必須是唯一在其`name`和`publicKeyToken`屬性。 如果這兩個屬性符合資訊清單內任何兩個項目之間，資訊清單剖析將不會成功。

## <a name="precautions-when-manually-changing-manifests-or-applications"></a>如果以手動方式變更的資訊清單或應用程式的預防措施

當您更新應用程式資訊清單時，您必須重新簽署應用程式資訊清單和部署資訊清單。 部署資訊清單包含應用程式資訊清單，其中包含該檔案的雜湊和數位簽章的參考。

### <a name="precautions-with-deployment-provider-usage"></a>部署提供者使用的預防措施

[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]部署資訊清單有`deploymentProvider`屬性指向位置的完整路徑，應該安裝和服務應用程式：

```xml
<deploymentProvider codebase="http://myserver/myapp.application" />
```

這個路徑時，會設定[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]會建立應用程式，並已安裝的應用程式的。 路徑指向標準位置其中[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]installer 將安裝的應用程式和更新的搜尋。 如果您使用**xcopy**命令來複製[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]應用程式以不同的位置，但不是會變更`deploymentProvider`屬性，[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]仍將參考回原始位置時，它會嘗試下載應用程式。

如果您想要移動或複製的應用程式，您也必須更新`deploymentProvider`路徑，以便在用戶端實際安裝從新位置。 如果您已安裝應用程式時，就更新此路徑是尤其重要。 針對透過原始 URL，設定永遠啟動的線上應用程式`deploymentProvider`是選擇性的。 如果`deploymentProvider`時，就會生效; 否則用來啟動應用程式的 URL 用以做為基底 URL 下載應用程式檔案。

> [!NOTE]
> 將資訊清單更新每次您必須再次加以簽署。

## <a name="see-also"></a>另請參閱

[疑難排解 ClickOnce 部署](../deployment/troubleshooting-clickonce-deployments.md)
[保護 ClickOnce 應用程式](../deployment/securing-clickonce-applications.md)
[選擇 ClickOnce 部署策略](../deployment/choosing-a-clickonce-deployment-strategy.md)
