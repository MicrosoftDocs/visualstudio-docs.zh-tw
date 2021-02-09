---
title: " (ClickOnce) 的安全性/版本控制/資訊清單問題"
description: 瞭解 ClickOnce 安全性、應用程式版本控制以及資訊清單語法和語義的問題，這些問題可能會導致 ClickOnce 部署不成功。
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 55758f67c845cbf753d51ebfb94b87af6cf55cde
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99877625"
---
# <a name="security-versioning-and-manifest-issues-in-clickonce-deployments"></a>ClickOnce 部署中的安全性、版本控制和資訊清單問題

[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]安全性、應用程式版本控制和資訊清單語法和語義有許多問題，可能會導致 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 部署不成功。

## <a name="clickonce-and-windows-vista-user-account-control"></a>ClickOnce 和 Windows Vista 使用者帳戶控制

在中 [!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)] ，應用程式預設會以標準使用者身分執行，即使目前的使用者是以具有系統管理員許可權的帳戶登入也一樣。 如果應用程式必須執行需要系統管理員許可權的動作，它會告訴作業系統，然後提示使用者輸入其系統管理員認證。 這項功能稱為使用者帳戶控制 (UAC) ，可防止應用程式在不需要使用者明確核准的情況下，進行不會影響整個作業系統的變更。 Windows 應用程式會 `requestedExecutionLevel` 在 `trustInfo` 應用程式資訊清單的區段中指定屬性，以宣告其需要提高許可權。

由於將應用程式公開給安全性提高許可權攻擊的風險， [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 如果用戶端已啟用 UAC，則應用程式無法要求許可權提升許可權。 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]嘗試將其屬性設定為或的任何應用程式 `requestedExecutionLevel` `requireAdministrator` `highestAvailable` 都不會安裝在上 [!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)] 。

在某些情況下，您 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 的應用程式可能會嘗試以系統管理員許可權執行，因為上的安裝程式偵測邏輯 [!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)] 。 在此情況下，您可以將 `requestedExecutionLevel` 應用程式資訊清單中的屬性設定為 `asInvoker` 。 這會導致應用程式本身執行，而不需要提高許可權。 [!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)] 會自動將此屬性新增至所有應用程式資訊清單。

如果您要開發的應用程式需要整個應用程式存留期的系統管理員許可權，您應該考慮改為使用 Windows Installer (MSI) 技術來部署應用程式。 如需詳細資訊，請參閱 [Windows Installer 基本概念](../extensibility/internals/windows-installer-basics.md)。

## <a name="online-application-quotas-and-partial-trust-applications"></a>線上應用程式配額和部分信任的應用程式

如果您 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 的應用程式是在線上執行，而不是透過安裝，則必須放在為線上應用程式設定的配額內。 此外，在部分信任中執行的網路應用程式（例如具有一組受限制的安全性許可權），不能大於配額大小的一半。

如需詳細資訊，以及如何變更線上應用程式配額的指示，請參閱 ClickOnce 快取 [總覽](../deployment/clickonce-cache-overview.md)。

## <a name="versioning-issues"></a>版本控制問題

如果您將強式名稱指派給元件，並將元件版本號碼遞增以反映應用程式更新，您可能會遇到問題。 任何以強式名稱元件的參考編譯的元件都必須重新編譯，否則元件會嘗試參考較舊的版本。 元件將會嘗試這項功能，因為元件在其系結要求中使用舊的版本值。

例如，假設您在自己的專案中有一個具有1.0.0.0 版的強式名稱元件。 編譯元件之後，您可以將它新增為包含主應用程式之專案的參考。 如果您更新元件、將版本遞增至1.0.0.1，並嘗試在未重新編譯應用程式的情況下部署，則應用程式將無法在執行時間載入元件。

只有當您手動編輯資訊清單時，才會發生此錯誤 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] ; 如果使用 Visual Studio 產生您的部署，您應該不會遇到此錯誤。

## <a name="specify-individual-net-framework-assemblies-in-the-manifest"></a>在資訊清單中指定個別 .NET Framework 元件

如果您已手動編輯 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 部署以參考舊版 .NET Framework 元件，則您的應用程式將無法載入。 例如，如果您在資訊清單中指定的版本之前，將 System.Net 元件的參考加入至其中的 .NET Framework，則會發生錯誤。 一般而言，您不應該嘗試指定個別 .NET Framework 元件的參考，因為您的應用程式執行所在的 .NET Framework 版本會指定為應用程式資訊清單中的相依性。

## <a name="manifest-parsing-issues"></a>資訊清單剖析問題

所使用的資訊清單檔案 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 是 XML 檔案，而且必須是格式正確且有效：它們必須遵守 XML 語法規則，而且只使用相關 XML 架構中定義的元素和屬性。

可能會在資訊清單檔中造成問題的某個情況是選取包含特殊字元的應用程式名稱，例如單引號或雙引號。 應用程式的名稱是其身分識別的一部分 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 。 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 目前不會剖析包含特殊字元的身分識別。 如果您的應用程式無法啟動，請確定您只使用字母和數位字元作為名稱，然後再次嘗試部署。

如果您已手動編輯您的部署或應用程式資訊清單，可能會不慎損毀。 損毀的資訊清單會導致無法正確 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 安裝。 您可以在執行時間中，按一下 [ **ClickOnce 錯誤**] 對話方塊上的 [**詳細資料**]，然後在記錄檔中讀取錯誤訊息，來偵測這類錯誤。 記錄檔將會列出下列其中一則訊息：

- 語法錯誤的描述，以及發生錯誤的行號和字元位置。

- 用來違規資訊清單架構的元素或屬性名稱。 如果您已手動將 XML 新增至資訊清單，就必須將您的新增專案與資訊清單架構進行比較。 如需詳細資訊，請參閱 [clickonce 部署資訊清單](../deployment/clickonce-deployment-manifest.md) 和 [clickonce 應用程式資訊清單](../deployment/clickonce-application-manifest.md)。

- 識別碼衝突。 部署和應用程式資訊清單中的相依性參考在其和屬性中必須是唯一的 `name` `publicKeyToken` 。 如果兩個屬性在資訊清單內的任何兩個專案之間相符，資訊清單剖析將會失敗。

## <a name="precautions-when-manually-changing-manifests-or-applications"></a>手動變更資訊清單或應用程式時的預防措施

當您更新應用程式資訊清單時，您必須重新簽署應用程式資訊清單和部署資訊清單。 部署資訊清單包含應用程式資訊清單的參考，其中包含該檔案的雜湊和其數位簽章。

### <a name="precautions-with-deployment-provider-usage"></a>使用部署提供者的預防措施

[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]部署資訊清單具有一個 `deploymentProvider` 屬性，指向應安裝及服務應用程式之位置的完整路徑：

```xml
<deploymentProvider codebase="http://myserver/myapp.application" />
```

此路徑是在 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 建立應用程式時設定的，而且對於已安裝的應用程式而言是強制的。 路徑會指向安裝 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 程式將在其中安裝應用程式的標準位置，並搜尋更新。 如果您使用 **xcopy** 命令將 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式複製到不同的位置，但不變更 `deploymentProvider` 屬性，則 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 在嘗試下載應用程式時，仍會回頭參考原來的位置。

如果您想要移動或複製應用程式，也必須更新 `deploymentProvider` 路徑，讓用戶端從新位置實際安裝。 如果您已安裝應用程式，則更新此路徑大多是問題。 對於永遠透過原始 URL 啟動的線上應用程式，設定 `deploymentProvider` 是選擇性的。 如果 `deploymentProvider` 設定，則會接受此值; 否則，用來啟動應用程式的 url 將會用來做為下載應用程式檔的基底 url。

> [!NOTE]
> 每次更新資訊清單時，您也必須重新簽署它。

## <a name="see-also"></a>另請參閱

針對[ClickOnce 部署](../deployment/troubleshooting-clickonce-deployments.md) 
 進行疑難排解[保護 ClickOnce 應用程式](../deployment/securing-clickonce-applications.md) 
[選擇 ClickOnce 部署策略](../deployment/choosing-a-clickonce-deployment-strategy.md)
